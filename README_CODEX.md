# FIN556 · Run OpenAI Codex CLI on the lab VM

Same idea as the Claude guide: an AI agent in the VM terminal (through Guacamole), with a rules file that keeps it
from damaging the shared system or leaking the licensed data. **Main goal: never fill the shared disk.**

> **Disclaimer:** shared by a student as a starting point. Use at your own risk. You are responsible for what your
> agent does on the VM, for following the course and data rules, and for your own usage and cost.
> Commands are from public docs; check them against the tool's current docs if something has changed.

## 1. Install Node.js (once, no sudo needed)
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```
```bash
source ~/.bashrc && nvm install 22 && node --version
```
Expected: `v22.x.x`.

## 2. Install Codex CLI
```bash
npm install -g @openai/codex
```

## 3. Add the rules
Codex reads `AGENTS.md`.
1. Download [`AGENTS.md`](AGENTS.md) from this repo.
2. In Guacamole press **Ctrl+Alt+Shift** (Mac: **Control+Option+Shift**) → **Devices** → your home folder →
   **Upload Files** → `AGENTS.md`. Close the menu the same way.
3. Move it into your project folder:
```bash
mkdir -p ~/myproject && mv ~/AGENTS.md ~/myproject/
```

## 4. Start and sign in
```bash
cd ~/myproject && codex
```
On first run sign in with your ChatGPT account (open the link in the VM's browser) or use an OpenAI API key.
Always start it from the project folder so it reads `AGENTS.md`.

## 5. Use it
- Upload your code as **one zip** through Guacamole, then ask Codex to unzip, build and run it.
- Something broke? Paste the error from the terminal into Codex.

## 6. Clean up: leave nothing behind
- Delete uploaded zips after unzipping, and temporary files after every task.
- Move results to approved storage, then **delete them from the VM**.
- When your project is done:
```bash
npm uninstall -g @openai/codex && rm -rf ~/myproject ~/.codex
```

**Other tools:** [Claude](README.md) · [Gemini](README_GEMINI.md) · [GitHub Copilot](README_COPILOT.md)
