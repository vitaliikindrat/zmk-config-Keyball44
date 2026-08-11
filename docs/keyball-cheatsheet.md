# Keyball44 · semantic-redesign (Linux-truth + mac swap)

> The keyboard emits **Linux-native chords**. On macOS, a per-device Ctrl↔Cmd swap
> (set once, this keyboard only) turns them into mac natives. Same finger = same
> intent on both OSes. **Bold** = new. Visual map: `keyball-cheatsheet.html`.

## One-time OS setup

**macOS (do this first, or everything feels wrong):**
1. System Settings → Keyboard → Keyboard Shortcuts… → Modifier Keys → select **Keyball44** → swap ⌃ Control ↔ ⌘ Command. (Repeat later for Cornix. MacBook internal keyboard: untouched.)
2. Keyboard Shortcuts → Mission Control: enable "Switch to Desktop 1–4" (they arrive as ⌃1–4); re-record **App Exposé (same-app windows) → ⌘F7** and **Mission Control → ⌘F9** — easiest by pressing the physical SYM-palm keys while the shortcut field records. That's the only pair of your currently-working mac bindings the swap breaks.
3. App Shortcuts → All Applications: "Show Next Tab" → ⌘PgDn, "Show Previous Tab" → ⌘PgUp.
4. On the keyboard: **FUN + M → MAC mode** (display shows "MAC"). Not persisted — retoggle after a power cycle.

**KDE (bind once, natively — no daemon):**
1. Shortcuts → KWin: Meta+←/→ = switch desktop, Meta+↑ = Overview, Meta+↓ = Grid/Present Windows, Meta+1–4 = desktops 1–4.
2. Window snaps: bind the quad Meta+Ctrl+←/↓/↑/→ (clear Plasma defaults that collide).
3. KRunner → Ctrl+Space.
4. Terminal: conditional copy (`performable:copy_to_clipboard` in ghostty / `copy_and_clear_or_interrupt` in kitty) so CMD+C copies selection, else SIGINT.
5. MAC mode **off** (default after boot).

## Entry points

| Hold / action        | Layer  | What it is                                 |
| -------------------- | ------ | ------------------------------------------ |
| hold `esc`           | NAV    | motion, helix, swappers                    |
| **hold thumb-2**     | **CMD**| **semantic OS commands (old ctrl slot)**   |
| hold thumb-3         | SYM    | numbers & symbols                          |
| **tap thumb-3**      | **MUX**| **sticky, 1 s — next key goes to zellij**  |
| tap-then-hold thumb-3| MUX    | held (the old Vial gesture)                |
| NAV + `ret` thumb    | **WS** | **windows & desktops (was DE)**            |
| NAV + `:` thumb      | FUN    | F-keys, BT, bootloader, **MAC toggle**     |
| **FUN + M**          | **MAC**| **OS mode flag (display shows MAC)**       |
| roll the ball        | MOUSE  | auto (700 ms), **left hand = controls**    |
| hold `\` or **MOUSE-F** | SCROLL | ball = wheel                            |
| **MOUSE-D**          | SNIPE  | 400 CPI precision                          |

## How do I… (same fingers on both OSes)

| Intent                        | Do this                              |
| ----------------------------- | ------------------------------------ |
| copy / paste (even mousing)   | **CMD + C / V**                      |
| undo / redo                   | **CMD + Z / Y**                      |
| cut / select all / save       | **CMD + X / A / S**                  |
| find / find next              | **CMD + F / G**                      |
| new tab / close / reopen      | **CMD + T / W / U**                  |
| prev / next tab               | **CMD + H / L**                      |
| zoom − / +                    | **CMD + J / K**                      |
| quit app / new window / minimize | **CMD + Q / N / M**               |
| reload / inspect / open       | **CMD + R / I(F12) / O**             |
| launcher (Spotlight/KRunner)  | **CMD + P**                          |
| desktop/space ← →             | **NAV → WS-thumb → H / L**           |
| overview (Mission Ctl) / exposé | **WS + K / J**                     |
| desktop 1–4                   | NAV + 1/2/3/4                        |
| move window (quad)            | **WS + U / I / O / P** (swap-proof)  |
| app / window / tab switcher   | NAV thumbs (tri-states, both modes)  |
| zellij: one command           | **tap SYM-thumb, then key**          |
| zellij: several               | tap-then-hold SYM-thumb              |
| scroll / snipe                | ball → **hold F / hold D**           |
| browser back / forward        | **ball → U / O (MB4 / MB5)**         |
| select text                   | NAV + thumb-⇧ + arrows               |
| raw terminal ^C on **Linux**  | cross-hand HRM: hold **K** + key     |
| raw terminal ^C on **mac**    | hold **;** (or A) + key — Gui arrives as Ctrl |
| any chord not listed          | cross-hand HRMs (mod opposite hand)  |

## CMD layer (hold thumb-2)

```
 ·    quit  close  ·    reload ntab │ redo  reopen inspect open  laun  ·
 ·    selAll save  bkmk  find  fnd→ │ tab←  zoom−  zoom+   tab→   ·    ·
 ·    undo  cut   copy  paste  ·    │ nwin  minim   ·       ·     ·    ·
```

Emissions (Linux-native): ^Q ^W ^R ^T · ⇧^Z ⇧^T F12 ^O ^␣ / ^A ^S ^D ^F ^G · ^PgUp ^− ^= ^PgDn / ^Z ^X ^C ^V · ^N ^M
On mac the swap delivers them as the ⌘ equivalents automatically.

## WS layer (NAV + ret-thumb)

```
 ·    ⌥F4  ⌃F8  ⊞E   ·    ·   │  ·     win←  win↓  win↑  win→   ·
 ·    ⌃F7  ⌃F9  ⊞D  ⌃F10  ·   │ desk←  grid  ovrvw desk→  ·    ·
 ·    ⌃⌥←  ⌃⌥→  ⌃⌥↓  ⌃⌥↑   ·   │  ·    ⌃⌥⇧←    ·   ⌃⌥⇧→   ·    ·
```

- hjkl = **Super+arrows**: KDE Meta-bindings; mac receives Ctrl+arrows = native spaces/MC/Exposé.
- win-quad = Cmd+Ctrl+arrows — **swap-invariant**, identical on both OSes.
- Old parked mystery trio: deleted (its emissions converged with hjkl under the swap).

## MAC mode (FUN + M) — what it actually changes

Only the chords the swap would poison; everything else is identical:
- NAV helix real-Ctrl keys (^U, ^D, ^⇧C, ^⇧V) re-emit as Gui → arrive as real Ctrl.
- NAV tab cyclers (^tab, ^⇧tab) likewise.
- Swappers cross-assign themselves: app switcher arrives as ⌘Tab, window cycle as ⌘`, in-app tabs as ⌃Tab.
- The whole zellij grid re-emits as Gui+Alt → arrives as Ctrl+Alt — **zellij config identical on both OSes**.
- Pointer motion is scaled **2×** (macOS's accel curve starves the ~300 effective CPI). Linux feel and scrolling untouched. Ratio lives in `keyball44_right.overlay` (`zip_xy_scaler 2 1`); LinearMouse is the mac-side alternative if you'd rather tune live.
- MAC lives at **layer 3**, deliberately below MOUSE/SCROLL/SNIPE: the driver detects ball modes via the highest active layer. Display in mac mode: idle = MAC, ball = MOUSE, holds = SCROLL/SNIPE. If you ever see MAC while rolling the ball, something regressed.

## Rules of the system

1. **One intent, one finger position.** OS mess stays inside the layer table (and the swap).
2. **Ctrl-chords = commands. Super-chords = windows/desktops.** Both OSes consume both.
3. **App disagrees?** mac: App Shortcuts (menu-title rebind). KDE: global shortcuts. Fix the app/OS, never the finger.
4. **Not on CMD?** Cross-hand HRMs are the closure — nothing can strand you.
5. **NAV moves the cursor; WS moves containers.**

## Watch-outs

- **Flash → then set the mac modifier swap → then FUN+M.** Order matters; without the swap, mac mode is nonsense.
- MAC toggle is not persisted: after battery swap/reboot of the keyboard, retoggle (display tells you).
- Stray tap of SYM-thumb arms sticky MUX for 1 s → next key becomes a zellij chord. One-line revert if it bites.
- Automouse needs deliberate movement now (threshold 5) — drop to 2–3 if arming feels sluggish.
- Deep sleep enabled (15 min idle) — first press after sleep takes a beat.
- Flash **both halves**.
