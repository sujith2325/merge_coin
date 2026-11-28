🎮 Core Game Mechanics
1. Board Layout (10 Chute Columns)
The board is styled as a carved, polished mahogany tray with 10 vertical chute columns arranged in a 
5 × 2
5×2 grid:
Columns 1–5 (Upper Row): Unlocked and ready to receive coins from the start.
Columns 6–10 (Lower Row): Locked initially with multiple progression pathways:
Column 6: Unlocks free at Level 10 (or for 100 Credits).
Column 7: Unlocks free at Level 20 (or for 100 Credits).
Column 8: Unlocks free at Level 30 (or for 100 Credits).
Column 9 (Extra 60 Sec): Temporary 60-second boost slot for 50 Credits with a live countdown timer, or permanent unlock for 100 Credits.
Column 10 (VIP Lock): Permanent unlock for 100 Credits.

3. 3D Coin Stacking (Up to 10 Coins per Chute)
Each chute holds a stack of up to 10 cylindrical coins.
The base of a stack or color group displays its circular embossed face with the tier numeral (1, 2, 3...).
Coins stacked above display realistic 3D milled metallic rims with alternating serration teeth and specular highlights.
A live occupancy badge at the top tracks height (0/10 to 10/10).

5. Dual Controls: Drag-and-Drop + Click-to-Select + Pocket Sort 🟢 DEAL

Players can interact with coins using three flexible methods:

🟢 DEAL Action Button (Pocket Sort Style):
Click the prominent green  DEAL button in the supply shelf to instantly auto-deal the active supply coin into the best valid column on the board (matching group with room first, or the first empty column).
Click-to-Select / Click-to-Move ("Select One and Select One"):
Click or tap any source column (or the active supply coin) to select it. The selected column elevates with a golden 3D lift and radiant pulsating halo (col-selected).
Click any target column to transfer coins immediately.
Clicking the same column deselects it; clicking another column with coins switches the selection.
Direct 3D Drag & Drop:
Click and drag the top coin group with a 3D perspective shadow proxy and drop directly into another column.
Placement Rules: A column accepts coins if it has available room (total coins 
<10 
<10) and either the column is empty or its top coin matches the incoming coin's tier (or is a Rainbow wildcard).
Visual Validation: Columns highlight with a radiant green track for valid drops and red for full/invalid placements.

4. Partial Transfer Algorithm
Unlike simple sorting games that block moves when a column cannot fit an entire stack, this engine implements an exact Partial Fill Algorithm:
availableSpace
=capacity(10)
−
targetCount
availableSpace=capacity(10)−targetCount
transferCount
=
min
(sourceCoins.length,availableSpace)
transferCount=min(sourceCoins.length,availableSpace)
remainingCount=sourceCoins.length
−
transferCount
remainingCount=sourceCoins.length−transferCount

Real Gameplay Example:
Column 1 has 7 coins (capacity 10, space for 3).
Column 2 has 4 coins of the same tier.
Moving Column 2 
→
→ Column 1 transfers 
min
⁡
(
4
,
3
)
=
3
min(4,3)=3 coins into Column 1.
Column 1 reaches 
7
+
3
=
10
/
10
7+3=10/10 and immediately triggers the 10-to-1 fusion cascade into a single higher-tier coin!
Column 2 retains the leftover 
4
−
3
=
1
4−3=1 coin!
5. Base-10 Fusion (
10
×
Coin 
𝑁
→
1
×
Coin 
𝑁
+
1
10×Coin N→1×Coin N+1)
When 10 matching coins accumulate in a single column:
The column shakes and flashes with golden light (anim-merge-fuse).
The board performs a subtle haptic screen-shake.
A 60FPS canvas particle firework bursts sparkling golden stars and glowing embers.
The 10 coins collapse and fuse into 1 single coin of the next level.
Floating bonus score text (+100 PTS, +1,000 PTS, etc.) rises upward.
Checks if the fusion triggers a cascading chain reaction or satisfies the level target!
💎 Credit Economy & Unlock System
Action	Cost / Reward	Details
Clear a Level	+1 Credit (💎)	Awarded every time the level target is achieved.
Unlock Column Permanently	100 Credits	Click any locked column card or the 🔓 Unlock (100 💎) button.
Milestone Level Unlocks	Free	Columns 6, 7, and 8 unlock automatically at Levels 10, 20, and 30.
60-Second Timed Boost	50 Credits	Opens Column 9 for 1 minute with a live ticking countdown timer.
Testing Helpers	+10 💎 & +100 💎	Quick buttons in the top header for instant sandbox testing.
🎨 12-Tier Coin Visual Palette

Strict Visual Rule: Coin #1 is always sleek Jet Black (Onyx) with a platinum rim and white numeral. All subsequent tiers are vibrant, saturated precious metals and gems.

Tier	Name	Base Color	Visual Details
1	Onyx Black	#18181b (Jet Black)	Obsidian core, diamond-cut platinum milled rim, engraved white #1.
2	Silver Platinum	#94a3b8	High-gloss platinum chrome with deep navy numeral.
3	Radiant Gold	#eab308	Rich 24K gold with warm amber specular glow and dark numeral.
4	Sapphire Blue	#3b82f6	Royal sapphire with cyan reflections and crisp white numeral.
5	Emerald Lime	#84cc16	Saturated lime green with forest green numeral.
6	Amethyst Lavender	#a855f7	Royal lavender purple with white numeral.
7	Rose Ruby Pink	#ec4899	Radiant ruby pink with white numeral.
8	Bronze Copper	#d97706	Metallic warm copper bronze with white numeral.
9	Royal Violet	#6366f1	Deep indigo violet with white numeral.
10	Sunset Orange	#f97316	Fiery flame orange with white numeral.
11	Caribbean Teal	#14b8a6	Tropical ocean teal with white numeral.
12	Prismatic Cyan	#06b6d4	Iridescent cyan diamond crown (ultimate tier).
🛠️ Booster Tools (Pocket Sort Architecture)
🔨 Hammer: Click to arm, then click any column to smash and remove its top coin.
🧲 Magnet: Automatically searches the board and pulls matching loose coins into the best available column.
🔀 Shuffle: Pocket Sort-style Solvable Shuffle that gathers all loose, un-frozen coins across unlocked columns and redistributes them via a constrained Fisher-Yates algorithm, guaranteeing a fresh solvable board state.
↩️ Undo: Reverses the last move and restores the previous board state.
🧩 Special Coin Types & Obstacles (Pocket Sort Progression)

While maintaining our signature Jet Black Onyx #1 and 12 luxury gemstone tiers, the game incorporates Pocket Sort's rich puzzle obstacle architecture:

❓ Mystery Coins (?) (Introduced in Level 2):
Lower coins in stacks start face-down with an engraved golden question mark.
When top coins are cleared and a mystery coin reaches the top of the stack, it executes a 3D coin flip (anim-coin-flip), chimes an ASMR discovery tone, and reveals its true tier!
🌈 Rainbow Wild Coins (🌈) (Introduced in Level 3):
Iridescent prismatic coin that can be placed on any column, and onto which any coin can be stacked.
Morphs to match the dominant tier during a 10-to-1 merge, bridging difficult gaps.
❄️ Ice / Frozen Coins (❄️) (Introduced in Level 4+):
Encased in crystalline frost and cannot be picked up or moved.
Shockwave Shatter: When an adjacent column executes a 10-to-1 merge cascade, the shockwave shatters the ice block with a glass-break sound effect and frees the coin!
⚠️ Automatic Deadlock Detection:
Evaluates valid moves across all columns and incoming supply coins after every move.
If no valid moves exist, a warning banner gently pulses at the top: "⚠️ No moves left! Try 🔀 Shuffle or ↩️ Undo", and highlights the booster buttons with a golden halo.
📦 3-Coin Conveyor Preview Queue & True Random Tier Dispenser:
Upgrades the bottom shelf into a conveyor belt showing the active coin plus a mini-preview of the next 3 upcoming coins.
Any Coin in Random Order: Unlike basic prototypes, the next coin supply dispenses across all 12 luxury gemstone tiers at random order, alongside occasional Rainbow wildcards.
🎯 Pocket Sort Milestone Chain & Progress Percentage:
The top HUD features Pocket Sort's signature milestone chain track ([✓] ── [2] ── [4] ── [Target]) with a live progress bar fill and completion percentage readout (Level 1 · 80%).
💥 Floating Comic Combo Callouts:
Executing consecutive merges triggers floating celebratory popups: "Cool! ✨", "Combo x2! 🔥", "Amazing x3! ⚡", "Incredible x4! 🌟", "Unstoppable! 💥".
❤️ 5 Full Hearts Indicator:
Prominently displays the classic 5 lives indicator in the top header.
🔊 4.9 AAA Audio Engine & ASMR Sound

The game features an entirely procedural physical-modeling acoustic engine built with the Web Audio API (zero external .mp3 or .wav dependencies):

Inharmonic Metallic Coin Clinks: Synthesizes the exact acoustic resonance of struck metal discs using multi-mode inharmonic frequencies (
𝑓
0
f
0
	​

, 
1.68
𝑓
0
1.68f
0
	​

, 
2.74
𝑓
0
2.74f
0
	​

, 
4.12
𝑓
0
4.12f
0
	​

).
Dual-Layer Hardwood Thud: A dampened 
160
Hz
→
75
Hz
160Hz→75Hz low-pass transient simulates coins landing on dense hardwood.
Randomized Micro-Detuning: 
±
2.5
%
±2.5% subtle pitch detuning on each drop ensures no two coin collisions sound identical.
Tactile Slide on Pickup: High-frequency bandpass friction scrape simulates fingers sliding across milled coin rims.
Grand 10-to-1 Fusion Climax: A multi-stage acoustic sequence with a fast 10-coin collapse clatter, ascending crystalline glissando over Gmaj9 chords, and a deep sub-bass bloom (
140
Hz
→
45
Hz
140Hz→45Hz).
Device Haptics: Integrates the Web Vibration API (navigator.vibrate) for physical micro-haptic pulses on touch devices.
🚀 How to Run the Game
Method 1: Local Node.js Server (Recommended)

From the project folder, run:

bash
node server.js

Then open your browser to: 👉 http://localhost:8080/

Method 2: Direct File Launch (Zero Server Required)

Simply double-click index.html in Windows Explorer or open it in any web browser (Chrome, Edge, Firefox, Safari).

📁 Project Structure
text
coin-merge-game/
├── index.html            # Main game entry point & UI structure
├── server.js             # Lightweight zero-dependency Node.js HTTP server
├── README.md             # Complete game documentation & guide
├── css/
│   ├── style.css         # Polished mahogany wood tray & 10-chute layout
│   ├── coins.css         # 3D coin shaders, specular sweeps & milled rims
│   └── animations.css    # Fusion collapse, screen shake & padlock rattle
└── js/
    ├── config.js         # Central configuration, chute capacity & 12 coin tiers
    ├── storage.js        # LocalStorage persistence (credits, unlocked columns, scores)
    ├── audio.js          # Procedural Web Audio API ASMR synthesizer & haptics
    ├── particles.js      # 60FPS canvas diamond star particle fireworks engine
    ├── levels.js         # Level goals & player progression
    ├── board.js          # 10-chute column mechanics, 3D stack rendering & locks
    ├── dragdrop.js       # Pointer Events direct mouse/touch drag system
    ├── game.js           # 10-to-1 fusion engine, boosters & credit economy
    └── main.js           # DOM initialization & bootstrap
🕹️ Controls
Control	Action
Click-to-Select ("Select One & Select One")	Click a column/supply coin to select (golden 3D lift), then click destination column to transfer matching coins.
Left Click + Drag / Touch + Drag	Pick up coin(s) from a column or the supply shelf and drop into any valid column.
Click on Locked Column	Opens confirmation dialog to unlock for 100 Credits (or activate 60-Sec boost for 50 Credits).
Click 🔨 Hammer	Arms the hammer; click any column to smash and remove its top coin.
Click 🧲 Magnet	Automatically groups matching loose coins together into one column.
Click 🔀 Shuffle	Runs solvable shuffle to rearrange loose coins into workable combinations.
Click ↩️ Undo	Reverses the last move.
Click 🔊 Sound	Toggles procedural sound effects ON / OFF.
Click 🔄 Restart	Resets the game to Level 1.
📄 License

MIT License. Free to use, modify, and distribute.
