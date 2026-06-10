# simbi-mesh releases

Public binaries for the **Simbi mesh credit-protocol node** — the engine behind
[Simbi](https://simbi.com)'s community credit ledger. Run a node on any spare
x86-64 Linux machine (an old laptop, a Pi-class box, a home server) and donate
its uptime to power the network.

## Quick start

Grab the latest release binary, then follow [RUN-A-NODE.md](RUN-A-NODE.md) —
four commands from download to a peered, syncing node on the staging mesh.

```sh
curl -fsSL -o simbi-mesh \
  https://github.com/simbi-inc/simbi-mesh-releases/releases/latest/download/simbi-mesh-x86_64-linux-musl
chmod +x simbi-mesh
sha256sum -c <(curl -fsSL https://github.com/simbi-inc/simbi-mesh-releases/releases/latest/download/simbi-mesh-x86_64-linux-musl.sha256)
```

The binary is **fully static** (musl, static-PIE): no libc version coupling, no
container, no dependencies — one file runs on any x86-64 Linux.

## What your node does

Sync, verify, relay, and serve the mesh (relay/light role). Witnessing is
committee-gated; devices **earn witness candidacy through proven uptime**
(`simbi-mesh uptime beat`) — the rung-5 graduation path.

## Provenance

Each release states the source commit and its sha256. Binaries are built with
the repo's `deploy/build-static-binary.sh` (pinned `rust:1-alpine` toolchain +
locked dependencies), so a given source tree reproduces the same hash.

Staging network: test data only; identities and the genesis can re-seed — the
gateway's `mesh-bootstrap.json` manifest is always the live truth.
