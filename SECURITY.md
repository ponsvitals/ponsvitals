# Security Policy

PonsVitals is a public-data product. It holds no user funds, requests no wallet
connection, and stores nothing about a visitor. The security surface is
correspondingly small — but it is not zero, and reports are welcome.

## Reporting a vulnerability

**Please do not open a public GitHub issue for a security report.**

Contact the maintainers privately:

- Telegram: https://t.me/ponsvitals
- Or the contact address listed on https://ponsvitals.com

Please include reproduction steps and, where relevant, the affected route,
address, or block range. We will acknowledge the report and agree a disclosure
window with you before anything is made public.

## Scope

In scope:

- The web tier in `app/` and `web/` — route handlers, input validation, decoding
- The chain reader in `app/lib/chain.ts` — decode correctness, cache poisoning,
  stale-state handling
- Container configuration in either `Dockerfile`
- Any rating that cannot be reproduced from public chain data using the
  published rule

Out of scope:

- The upstream launchpad contracts, which this project only reads
- The public RPC endpoint's own availability
- Volumetric denial of service against public endpoints
- Findings that require a compromised maintainer device

## Rating disputes are not vulnerabilities

If a published rating disagrees with your own recomputation, open a normal
public issue with your working attached. Rule changes are announced before they
take effect and prior ratings keep their version stamp, so a disagreement is a
correctness discussion, not a disclosure.

## Secrets

This repository is expected to contain no credentials of any kind. The
application runs against a public JSON-RPC endpoint and requires no key,
database, or account to build or serve.

If you believe a credential has been committed here, treat it as a live
incident: report it privately using the contacts above rather than opening an
issue, so it can be rotated before it is indexed.

Note that any variable prefixed `NEXT_PUBLIC_` is compiled into the browser
bundle and is public by definition. A secret must never be given that prefix.
