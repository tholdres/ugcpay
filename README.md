# UGCPay Protocol

**Trustless UGC creator payments on Stacks Bitcoin L2.**

UGCPay is a set of three open-source Clarity smart contracts and an x402-compatible HTTP endpoint that let brands pay UGC creators directly — no platform commission, no PayPal delays, no FX conversion losses. Payment releases automatically when the creator delivers. The contract holds the money. No intermediary.

> ⚠️ **Status: Pre-mainnet · Testnet deployment in progress · MIT License**  
> This protocol is funded by a [Stacks Endowment Getting Started Grant](https://stacksendowment.co/grants). Contracts are not yet audited. Do not use in production with real funds outside the supervised pilot.

---

## The Problem

A UGC creator in Brazil delivering a $100 video to a US brand loses:

| Fee Type | Cut |
|---|---|
| Billo / Collabstr platform commission | 20–35% |
| PayPal receive fee + FX spread | 6–9% |
| Local bank withdrawal | ~1.5% |
| **Total leakage** | **27–44%** |

For TikTok Shop affiliate commissions below $5, the math is worse: PayPal's $0.30 minimum fee makes sub-$5 payments structurally unviable to collect.

UGCPay replaces this with a 2.5% protocol fee and settlement in USDCx (a 1:1 USD-backed stablecoin on Stacks). Payment is guaranteed by the contract — not by brand goodwill.

---

## How It Works

```
Brand  →  opens escrow (USDCx locked on-chain)
Creator  →  delivers content
Contract  →  verifies SHA-256 hash match
Payment  →  auto-releases to creator after 72h window
```

No platform approval. No PayPal. No waiting 15 business days.

---

## Contracts

| Contract | Purpose | Testnet | Mainnet |
|---|---|---|---|
| `ugcpay-registry.clar` | Creator identity, pricing, delivery history | `pending M2` | `pending M5` |
| `ugcpay-escrow.clar` | Hold USDCx, verify delivery, release payment | `pending M3` | `pending M5` |
| `ugcpay-reputation.clar` | On-chain score derived from escrow history | `pending M4` | `pending M5` |

> Addresses will be updated here as each contract is deployed. All deployments are verifiable at [explorer.hiro.so](https://explorer.hiro.so).

---
