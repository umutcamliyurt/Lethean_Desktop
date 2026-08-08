# Lethean Desktop

## Desktop client for the Lethean zero-knowledge encrypted vault

Lethean Desktop packages the same zero-knowledge vault client as an installed
application, rather than a page fetched fresh from a server on every visit.

## Why a desktop client?

The web version re-downloads and re-trusts its JavaScript on every page
load. A compromised, coerced, or subpoenaed server could serve different
code to a specific user on a specific day, with no visible indication to
the person unlocking their vault. An installed binary removes that risk.

## Features

Everything in the [web client](https://github.com/umutcamliyurt/Lethean/blob/main/README.md), plus:

- Code fixed at install time, no re-fetch on launch
- No browser required

## Building

```bash
git clone https://github.com/umutcamliyurt/Lethean_Desktop
cd Lethean_Desktop/
npm install
npm run build
```

This produces an installable binary under `src-tauri/target/release/bundle/`.

**Pointing at a backend:** the backend URL appears in two places
in `src-tauri/tauri.conf.json`, both must match.

## Threat model

This extends the [web client's threat model](https://github.com/umutcamliyurt/Lethean/blob/main/README.md#threat-model).
Everything listed there still applies; below is only what changes with an
installed binary.

**In scope**
- **Server-pushed code tampering** — the web version's key weakness,
  a compromised or coerced server serving different JavaScript to a
  specific target, no longer applies.

**Out of scope**
- **OS, browser-engine, and hardware compromise** — a compromised OS,
  tampered webview runtime, or seized unlocked device remains outside
  this project's scope. That's device and operational-security territory,
  not something code delivery can fix.


## License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for full terms.
