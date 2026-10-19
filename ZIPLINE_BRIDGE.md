# Zipline RubyLLM 2.0 bridge

This temporary fork supports Zipline's transition from RubyLLM 1.16 to 2.0.
It must not be loaded with RubyLLM 2.1's native MCP implementation.

## Provenance

- Base: upstream `patvice/ruby_llm-mcp` main at
  `0d39bba245eadb51592f829e06b6e7145ec988dc`.
- Compatibility foundation: [upstream #161](https://github.com/patvice/ruby_llm-mcp/pull/161),
  original commit `a8cc59c1647905b81b56bfda4b82b1db17e7e967`.
- Follow-ups: [crmne #1](https://github.com/crmne/ruby_llm-mcp/pull/1),
  five commits ending at `22e389db69ba670822590bb86356acfbeed53de1`.
- The optional sampling content-array change in crmne #2 is excluded.

Using current upstream main retains its Origin-header, exception-safe teardown,
fixture readiness and OAuth discovery normalization fixes. Zipline's application
extensions still need verification against this exact source; the upstream
teardown implementation does not replace Zipline's reporting of multiple errors.

## Ownership and acceptance

Zipline's AI Foundations team owns this bridge. Consumers must pin a full commit
SHA. Runtime requirements exclude RubyLLM 2.1, and compatibility CI covers 1.16.0
and the 2.0 patch series on Ruby 3.4 and 4.0. The ordinary upstream suite stays on
1.16.0; passing the focused 2.0 checks is not a claim that the full suite passes
on 2.0. Application integration and persistence migration checks remain separate.

Retire this fork when Zipline completes its 2.0 persistence transition and its
separately validated migration to native MCP on 2.1.1 or a later verified patch.
