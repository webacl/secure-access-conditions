# Secure Access Conditions

**WAC 2.0: Secure Access Conditions** extends [Web Access Control (WAC)](https://webacl.org) with `acl:condition` — additional requirements on authorizations such as client identity and issuer restrictions — using **fail-closed evaluation semantics**.

## Key Principle: Fail-Closed

If a server encounters a condition type it does not support, the authorization is treated as **non-applicable**. This prevents silent privilege expansion — unsupported security constraints are never ignored.

> *"The server MUST treat the Authorization as non-applicable if any condition's type is not signalled via ACL Resource Condition Discovery."*

## Spec

- **Latest draft:** [index.html](index.html)
- **Published:** [webacl.org/secure-access-conditions/](https://webacl.org/secure-access-conditions/)

## Implementations

| Implementation | Language | Status |
|----------------|----------|--------|
| [JavaScriptSolidServer (JSS)](https://github.com/JavaScriptSolidServer/JavaScriptSolidServer) | JavaScript | Implemented |
| [VisionClaw](https://github.com/DreamLab-AI/VisionClaw) (via JSS) | Rust/JS | In use |

## Editors

- Melvin Carvalho

*Seeking co-editors. Open an issue or reach out if interested.*

## How It Differs from WAC 1.1

Both proposals use the same `acl:condition` syntax and condition types (`acl:IssuerCondition`, `acl:ClientCondition`). They differ in one critical aspect:

| | WAC 1.1 (PR #134) | WAC 2.0 (this spec) |
|-|-------------------|---------------------|
| Unsupported condition | Silently ignored | Authorization non-applicable |
| Security model | Fail-open | **Fail-closed** |
| Risk | Silent privilege expansion | None — unknown constraints deny access |

## Background

- [WAC 1.0 specification](https://webacl.org)
- [NACK on public-solid mailing list](https://lists.w3.org/Archives/Public/public-solid/2026Mar/0032.html)
- [Discussion on PR #134](https://github.com/solid/web-access-control-spec/pull/134)

## License

MIT
