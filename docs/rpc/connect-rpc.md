<!--- Hugo front matter used to generate the website version of this page:
linkTitle: Connect
--->

# Semantic conventions for Connect RPC

**Status**: [Development][DocumentStatus]

The Semantic Conventions for [Connect](https://connectrpc.com/) extend and override the [RPC spans](rpc-spans.md) and [RPC metrics](rpc-metrics.md) Semantic Conventions
that describe common RPC operations attributes in addition to the Semantic Conventions
described on this page.

## Connect RPC attributes

`rpc.system` MUST be set to `"connect_rpc"`.

Below is a table of attributes that SHOULD be included on client and server Connect RPC measurements.

<!-- semconv rpc.connect_rpc.attributes -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`rpc.connect_rpc.error_code`](/docs/registry/attributes/rpc.md) | string | The [error codes](https://connectrpc.com//docs/protocol/#error-codes) of the Connect request. Error codes are always string values. | `cancelled`; `unknown`; `invalid_argument` | `Conditionally Required` [1] | ![Development](https://img.shields.io/badge/-development-blue) |
| [`rpc.connect_rpc.request.metadata.<key>`](/docs/registry/attributes/rpc.md) | string[] | Connect request metadata, `<key>` being the normalized Connect Metadata key (lowercase), the value being the metadata values. [2] | `["1.2.3.4", "1.2.3.5"]` | `Opt-In` | ![Development](https://img.shields.io/badge/-development-blue) |
| [`rpc.connect_rpc.response.metadata.<key>`](/docs/registry/attributes/rpc.md) | string[] | Connect response metadata, `<key>` being the normalized Connect Metadata key (lowercase), the value being the metadata values. [3] | `["attribute_value"]` | `Opt-In` | ![Development](https://img.shields.io/badge/-development-blue) |

**[1] `rpc.connect_rpc.error_code`:** If response is not successful and if error code available.

**[2] `rpc.connect_rpc.request.metadata.<key>`:** Instrumentations SHOULD require an explicit configuration of which metadata values are to be captured.
Including all request metadata values can be a security risk - explicit configuration helps avoid leaking sensitive information.

For example, a property `my-custom-key` with value `["1.2.3.4", "1.2.3.5"]` SHOULD be recorded as
the `rpc.connect_rpc.request.metadata.my-custom-key` attribute with value `["1.2.3.4", "1.2.3.5"]`

**[3] `rpc.connect_rpc.response.metadata.<key>`:** Instrumentations SHOULD require an explicit configuration of which metadata values are to be captured.
Including all response metadata values can be a security risk - explicit configuration helps avoid leaking sensitive information.

For example, a property `my-custom-key` with value `"attribute_value"` SHOULD be recorded as
the `rpc.connect_rpc.response.metadata.my-custom-key` attribute with value `["attribute_value"]`

---

`rpc.connect_rpc.error_code` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `aborted` | aborted | ![Development](https://img.shields.io/badge/-development-blue) |
| `already_exists` | already_exists | ![Development](https://img.shields.io/badge/-development-blue) |
| `cancelled` | cancelled | ![Development](https://img.shields.io/badge/-development-blue) |
| `data_loss` | data_loss | ![Development](https://img.shields.io/badge/-development-blue) |
| `deadline_exceeded` | deadline_exceeded | ![Development](https://img.shields.io/badge/-development-blue) |
| `failed_precondition` | failed_precondition | ![Development](https://img.shields.io/badge/-development-blue) |
| `internal` | internal | ![Development](https://img.shields.io/badge/-development-blue) |
| `invalid_argument` | invalid_argument | ![Development](https://img.shields.io/badge/-development-blue) |
| `not_found` | not_found | ![Development](https://img.shields.io/badge/-development-blue) |
| `out_of_range` | out_of_range | ![Development](https://img.shields.io/badge/-development-blue) |
| `permission_denied` | permission_denied | ![Development](https://img.shields.io/badge/-development-blue) |
| `resource_exhausted` | resource_exhausted | ![Development](https://img.shields.io/badge/-development-blue) |
| `unauthenticated` | unauthenticated | ![Development](https://img.shields.io/badge/-development-blue) |
| `unavailable` | unavailable | ![Development](https://img.shields.io/badge/-development-blue) |
| `unimplemented` | unimplemented | ![Development](https://img.shields.io/badge/-development-blue) |
| `unknown` | unknown | ![Development](https://img.shields.io/badge/-development-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

## Connect RPC status

If `rpc.connect_rpc.error_code` is set, [Span Status](https://github.com/open-telemetry/opentelemetry-specification/tree/v1.47.0/specification/trace/api.md#set-status) MUST be set to `Error` and left unset in all other cases.

[DocumentStatus]: https://opentelemetry.io/docs/specs/otel/document-status
