# ContentCreationPack

Backup of Antigravity plugins, skills, and MCP server configuration.

## Contents of `antigravity-customizations.zip`

- `plugins/`
  - `cartoon-3d-short`
  - `ffmpeg-skill`
  - `vercel-plugin`
- `skills/`
  - `roblox-animation`
  - `roblox-engine`
- `mcp_config.json` (`Roblox_Studio`, `voicestudio`)

> **Note:** `directing-stickman-videos` is intentionally excluded from the zip due to its large bundled `assets/` (~478 MB) and `node_modules/` (~56 MB). Clone it directly from its source repo on the new machine (see below).

---

## Restore on another Antigravity machine

1. Extract `antigravity-customizations.zip` into your Antigravity config directory:
   - **Windows:** `C:\Users\<username>\.gemini\config\`
   - **macOS / Linux:** `~/.gemini/config/`
2. *(Optional)* Reinstall `directing-stickman-videos`:
   ```bash
   git clone https://github.com/kaomei/stickman-video-director ~/.gemini/config/skills/directing-stickman-videos
   cd ~/.gemini/config/skills/directing-stickman-videos
   npm ci
   ```
3. Restart or reload Antigravity, then sign in to any plugin accounts (e.g., Vercel) in the Plugins Manager.

---

## Required dependencies to install on the new machine

### Plugins
- **`cartoon-3d-short`**: Node.js, a Remotion + Three.js project, Python 3, FFmpeg
- **`ffmpeg-skill`**: FFmpeg 6.1+ (with `ffprobe` on `PATH`), Python 3.10+
- **`vercel-plugin`**: Vercel account (sign in via Plugins Manager), Vercel CLI (`vercel`), Node.js

### Skills
- **`directing-stickman-videos`**:
  - *Director mode (A1–A5):* No local runtime dependencies
  - *Autopilot mode (B1–B6):* Node.js 20+, `npm ci` (`@napi-rs/canvas`, `sharp`), FFmpeg & FFprobe on `PATH`, Python 3 (optional OpenAI Whisper for local alignment), image generation & TTS API keys/tools
- **`roblox-animation`**: Roblox Studio
- **`roblox-engine`**:
  - Blender 5.2 (or `BLENDER` env var)
  - FFmpeg & FFprobe on `PATH`
  - Python 3.10+ with `numpy` and `pillow` (`pip install numpy pillow`)
  - Roblox Studio + Roblox Studio MCP (`%LOCALAPPDATA%\Roblox\mcp.bat`) to run `fetch_library.py` jobs
  - *Optional:* NVIDIA GPU, `ELEVENLABS_API_KEY`, `BLOTATO_API_KEY`

### MCP Servers (`mcp_config.json`)
- **`Roblox_Studio`**: Roblox Studio + `%LOCALAPPDATA%\Roblox\mcp.bat`
- **`voicestudio`**: Local VoiceStudio server running at `http://localhost:3900/mcp`
