# TLS Quantum Risk Scorer

An interactive browser-based demo for a **layered quantum-threat risk scoring model** applied to individual TLS connections.

🔗 **[Live Demo](https://yulim4hyoung.github.io/tls-quantum-risk-scorer/)**

## Overview

This tool quantifies the quantum-threat exposure of a TLS session on a **0–100 scale** using five independent scoring layers:

| Layer | Name | Trigger |
|-------|------|---------|
| L1 | TLS Protocol Exposure | Legacy TLS version (1.0 / 1.1 / 1.2) |
| L2a | Legacy Key Exchange Vulnerability | RSA or ECDHE key exchange |
| L2b | AES-128 Grover Weakening | AES-128 cipher suite |
| L2c | PQC Level-1 Vulnerability | ML-KEM-512 or equivalent (optional) |
| L3 | Certificate Expiration Urgency | Certificate expiring within 30 days |

The **HNDL (Harvest Now, Decrypt Later) multiplier M** reflects the confidential data retention period, scaling the total score from ×1.0 (h = 0 yr) to ×2.0 (h = 20 yr).

## Normalization

**Score = ⌊ (L1 + L2a + L2b + L2c + L3) × M / 118 × 100 ⌋ ∈ [0, 100]**

118 is the practical upper bound derived from the worst-case scenario:
TLS 1.0 + RSA + AES-128 + expired certificate + maximum m values + M = 2.0 (h = 20 yr).

## Usage

Visit the [live demo](https://yulim4hyoung.github.io/tls-quantum-risk-scorer/) or open `index.html` locally in any modern browser.

Configure the TLS connection parameters and per-layer environmental correction multipliers (m) to compute a per-layer risk breakdown and final score.

## Paper

This demo accompanies an academic paper on layered quantum-threat risk scoring for TLS,
submitted to the **2026 Side-Channel Information Analysis Contest (부채널 정보분석 경진대회)**.
