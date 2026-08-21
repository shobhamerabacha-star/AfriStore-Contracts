# AfriStore-Contracts


The core Soroban smart contract for the [Afristore Marketplace](https://github.com/Afristore/marketplace) — extracted from the monorepo into its own dedicated repository.

This contract implements:
- `create_listing` — List an NFT for sale with price and expiry
- `buy_item` — Purchase a listed NFT and distribute funds
- `place_bid` — Place a bid on an auction listing
- `finalize_auction` — Settle an auction and transfer the NFT to the highest bidder
- `cancel_listing` — Cancel an active listing (creator only)
- Protocol fee management, pause/unpause, and TTL bump logic

---

##  Getting Started (once code is populated)

```bash
# Build the contract WASM
cargo build --target wasm32-unknown-unknown --release

# Run all tests
cargo test --features testutils

# Optimize the WASM binary
stellar contract optimize --wasm target/wasm32-unknown-unknown/release/soroban_marketplace.wasm

# Deploy to testnet
stellar contract deploy --wasm target/wasm32-unknown-unknown/release/soroban_marketplace.optimized.wasm --network testnet
```

---

##  Prerequisites

- Rust (stable)
- `wasm32-unknown-unknown` target: `rustup target add wasm32-unknown-unknown`
- Stellar CLI: `cargo install --locked stellar-cli`

---

##  Source Location (Monorepo)

This repository is being extracted from [`afristore/contracts/soroban-marketplace/`](https://github.com/Afristore/marketplace/tree/master/contracts/soroban-marketplace) in the main monorepo.

**Tracked in:** [ui-ux-issues.md — Issue 122](https://github.com/Afristore/marketplace/blob/master/ui-ux-issues.md)

---

##  Contributing

1. Fork this repository
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Make your changes and ensure all CI checks pass:
   - `cargo fmt --check` — must exit 0
   - `cargo clippy -- -D warnings` — zero warnings
   - `cargo test --features testutils` — all tests must pass
   - `cargo build --target wasm32-unknown-unknown --release` — must produce a valid WASM
4. Open a PR — **all CI must pass before a PR is eligible for review and merge**

---

##  Tech Stack

- Rust + `soroban-sdk v25.3.0`
- Stellar / Soroban smart contract platform

---

## 📄 License

MIT — see [LICENSE](./LICENSE)
