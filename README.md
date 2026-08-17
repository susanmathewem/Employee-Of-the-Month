# 🏆 Employee of the Month — 60-Second Runner

**Participant / Team name:** _[fill in before submission]_
**Team member names:** _[fill in before submission]_

## Brief description
A browser-based, 3-lane office-corridor runner built for **UST GameCraft 2026**. The
player picks an employee character and races for an exact 60-second sprint, weaving
between lanes to collect positive workplace moments, dodge everyday hazards, and grab
power-ups — all to earn the title of **Employee of the Month**.

## 🎯 Objective and rules
- Survive and score as high as possible during a single, **exact 60-second** run.
- Collect positive items to gain points; avoid hazards, which deduct points.
- Power-ups grant temporary advantages (invincibility, magnet pull, speed, etc.).
- The run always lasts the full 60 seconds — there is no early "lose" state — so every
  player gets a fair, equal-length attempt.
- When the timer hits 0, your score freezes instantly and the result screen appears.

## ▶️ How to play
1. Open `index.html` in your browser.
2. Enter your **name** (required — empty names are rejected, leading/trailing spaces
   are trimmed, 20-character limit).
3. Choose one of five **characters**.
4. Click **Continue**, review the **How To Play** screen, then click **Start 60-Second Run**.
5. The 60-second countdown begins immediately and is visible at all times. At **10
   seconds** remaining, the timer flashes and beeps as a warning.
6. When time reaches **0**, the game stops automatically and your final result is shown.
7. Click **Play Again** to instantly replay (timer, score, and track reset — same
   character), **Change Character** to pick someone new, or **View Leaderboard** to see
   the local Top 10.

## 🎮 Controls
| Action | Keyboard | Touch / Mobile |
|---|---|---|
| Move to upper lane | `↑` or `W` | Swipe up / ▲ button |
| Move to lower lane | `↓` or `S` | Swipe down / ▼ button |
| Jump over a hazard | `Space` or `→` | Tap track / JUMP button |
| Mute / unmute sound | 🔊 button (top-right of HUD) | Same |

## 🧑‍💼 Characters
🧑‍💻 Tech Innovator · 👩‍💻 Software Engineer · 🤖 Robo Associate · 🦸 Support Champion · 👨‍💼 Team Lead

## 🧮 Scoring rules (deterministic and explainable)
| Event | Score change |
|---|---|
| ✅ Collect a positive item (💡📚🤝🌟🚀🎯🏅✅) | **+10 points** |
| ⚠️ Hit a hazard (🐛🚨⏳📢💥🔥📉⚠️) — unless shielded/jumped/protected | **−5 points** |
| 📏 Distance travelled | **+1 point per ~10m** automatically, as a progress bonus |
| Score floor | Score **never drops below 0** |
| Score freeze | Score is **frozen immediately** when the 60-second timer expires; no input can change it afterward |

### ⭐ Power-ups (temporary effects, not direct points)
| Icon | Name | Effect |
|---|---|---|
| 🛡️ | Shield | 6 seconds of invincibility — hazards are blocked, not scored against you |
| 🧲 | Magnet | 6 seconds — nearby collectibles in your lane are pulled toward you |
| ⚡ | Speed Boost | 6 seconds — faster pace (more ground covered = more distance bonus) |
| ❤️ | Extra Life | Banks one "save" — your next hazard hit is absorbed with no penalty |
| 🧠 | Knowledge Boost | 5 seconds — everything slows down, easier to react |
| 🚀 | Hyper Sprint | 5 seconds — invincibility + fastest pace at once |

### 🏅 Rewards / Title tiers (shown on the result screen based on final score)
1. 🚀 Rising Talent (0+)
2. ⭐ Star Performer (100+)
3. 🥇 Gold Performer (200+)
4. 👑 Hall of Fame (320+)
5. 🏆 Employee of the Month (450+)

## ⏱️ Duration and result screen
- Countdown starts at **60 seconds** the moment Start is pressed and is visible throughout.
- A visual (flashing) and audio warning triggers at **10 seconds** remaining.
- At **0 seconds**, gameplay stops automatically and the result screen shows:
  player name, final score, personal best (this browser), completion status, and your
  earned title/reward tier.

## 📋 Local leaderboard
- A **Top 10** leaderboard is stored in browser **Local Storage** — it is device/browser
  specific, not a centralized event leaderboard.
- Personal best is also tracked locally and shown on every result screen.
- A **Clear Local Data** button is available on the leaderboard screen.
- No player data is transmitted anywhere; everything stays in your browser.

## 🛠️ Technologies used
- HTML5, CSS3, vanilla JavaScript (ES6) — no build step, no external frameworks or libraries.
- Web Audio API for simple procedural sound effects (mute-able).
- Browser Local Storage for the leaderboard and personal best.
- All character/collectible/hazard/power-up art is standard Unicode emoji (no external
  image, font, or audio assets used — nothing to credit).

## 🤖 AI usage declaration
**AI Tool Used:** Microsoft Copilot
**Purpose:** Brainstorming the runner concept, generating and refining the HTML/CSS/JS
structure, debugging a layout issue (track width collapsing to 0 due to flex alignment),
and drafting this documentation.
**Participant validation:** All AI-generated code was reviewed, manually tested end-to-end
in a real browser environment (including automated functional checks of scoring, timer,
collisions, and replay logic), and adjusted where needed. No confidential, client,
project, or personal employee information was entered into the AI tool at any point.

## 📁 Project structure
```
GameCraft-Submission/
  index.html
  README.md
  css/
    styles.css
  js/
    timer.js        — exact 60-second countdown, warning + expiry callbacks
    score.js         — deterministic scoring rules, freeze-on-expiry logic
    player.js        — character roster, lane position, power-up state
    leaderboard.js    — local Top-10 leaderboard + personal best (Local Storage)
    game.js           — screen flow, entity spawning, collisions, main game loop
```

## 🌐 Browsers tested
- ✅ Google Chrome (latest) — desktop and mobile-width viewport
- ✅ Microsoft Edge (Chromium-based, latest)
- Verified via both manual review and automated headless-browser functional testing
  (name validation, screen transitions, timer countdown/expiry, live scoring, collision
  detection for collectibles/hazards/power-ups, score-freeze on game end, replay reset,
  and leaderboard read/write) — zero console errors observed.

## ⚠️ Known limitations
- Leaderboard and personal best are stored per-browser via Local Storage; clearing
  browser data or switching browsers/devices will reset them.
- Sound effects use the Web Audio API; if a browser blocks audio autoplay policies,
  sound may only begin after the first user interaction (standard browser behavior).
- Difficulty (obstacle speed/spawn rate) increases gradually with distance travelled;
  it is not adjustable mid-run.
- No server/backend — this is a fully client-side, offline-capable single HTML page group.

## 🔒 Privacy and security notes
- No credentials, tokens, or internal endpoints are present in the source.
- No network calls are made by the game after the page loads (fully offline-playable).
- Only the player's chosen display name (used solely for on-screen display and the local
  leaderboard) is collected — no other personal information is requested.
