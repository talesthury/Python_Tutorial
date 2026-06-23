# Git + GitHub Cheat Sheet

Your everyday survival guide. Run all commands inside your project folder in PowerShell
(e.g. `C:\Users\TalesThury\Documents\Stream_lit\Class_06`).

---

## ☀️ STARTING THE DAY

Before you touch anything, grab the latest version from GitHub so you don't work on stale files:

```powershell
git pull
```

That's it. If nothing changed online, it just says "Already up to date."

---

## 💾 SAVING & UPLOADING YOUR WORK (do this often!)

The three-step cycle. Think of it as: **stage → save → upload.**

```powershell
git add .                          # stage ALL your changes
git commit -m "what you changed"   # save a snapshot with a note
git push                           # upload it to GitHub
```

Write the commit message so future-you understands it, e.g.
`git commit -m "Finished class 06 exercises"`

---

## 🌙 FINISHING THE DAY

Just make sure everything is uploaded:

```powershell
git add .
git commit -m "End of day - work in progress"
git push
```

If you run `git status` and it says **"nothing to commit, working tree clean"**,
you're already safe — everything is on GitHub. Close the laptop. 😴

---

## 🔍 USEFUL "WHERE AM I?" COMMANDS

| Command | What it tells you |
|---|---|
| `git status` | What's changed, what's saved, what's not. **Use this constantly.** |
| `git remote -v` | Which GitHub repo this folder is linked to |
| `git log --oneline` | History of your saved snapshots (press `q` to exit) |
| `git branch` | Which branch you're on (usually `main`) |

---

## 🆕 STARTING A BRAND NEW PROJECT

### Option A — repo already exists on GitHub (the easy way)
Download it; this also creates the folder and links it automatically:

```powershell
git clone https://github.com/talesthury/REPO_NAME.git
cd REPO_NAME
```

### Option B — you have a local folder and want to link it to a new repo
First create the empty repo on github.com, then:

```powershell
cd C:\path\to\your\folder
git init
git remote add origin https://github.com/talesthury/REPO_NAME.git
git add .
git commit -m "First commit"
git branch -M main
git push -u origin main
```

You only do `-u origin main` on the **very first** push. After that, plain `git push` works.

---

## 🚑 COMMON ERRORS & FIXES

**`remote origin already exists`**
The link is already set. Update it instead of adding:
```powershell
git remote set-url origin https://github.com/talesthury/REPO_NAME.git
```

**`! [rejected] ... (fetch first)`**
GitHub has commits your computer doesn't. Pull first, then push:
```powershell
git pull origin main --allow-unrelated-histories
git push
```

**A merge editor opened (scary blue/black screen with text)**
It's asking for a message. To get out: press `Esc`, type `:wq`, press `Enter`.

**You messed up files and want to throw away unsaved changes (DANGER)**
Resets everything back to your last commit. Only if you're SURE:
```powershell
git checkout -- .
```

---

## 🧠 THE MENTAL MODEL (so it finally sticks)

```
   YOUR FOLDER  ──git add──►  STAGING  ──git commit──►  LOCAL HISTORY  ──git push──►  GITHUB
   (your edits)               (picked)                  (saved on PC)                (saved online)

   GITHUB  ──git pull──►  YOUR FOLDER     (grabs the latest before you start)
```

- **add** = "I want to include these files"
- **commit** = "Save a snapshot on my computer"
- **push** = "Send my snapshots up to GitHub"
- **pull** = "Bring down whatever's on GitHub"

---

## ⚡ THE 90% RULE

Honestly, 90% of your days are just these two blocks:

**Start:**
```powershell
git pull
```

**Whenever you've done meaningful work / before closing:**
```powershell
git add .
git commit -m "describe it"
git push
```

Everything else above is just for when something breaks. Keep this handy and you're golden.
