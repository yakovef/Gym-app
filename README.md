# Gym Log

A complete workout tracker in **one HTML file**. Open it on your phone, add it to your Home Screen,
and it works like an app: offline, private, no account.

## Open it on your phone

**Easiest: GitHub Pages (a link you can bookmark)**
1. In this repository on GitHub go to **Settings → Pages**.
2. Under *Build and deployment* choose **Deploy from a branch**, pick the branch that holds
   `index.html` (e.g. `main`) and the **/ (root)** folder, then **Save**.
3. After a minute the app is live at `https://<your-user>.github.io/<repo>/`.
4. On the phone open that link, then:
   - **iPhone (Safari):** Share → **Add to Home Screen**.
   - **Android (Chrome):** ⋮ menu → **Install app** / **Add to Home screen**.

**Or as a file:** download `index.html` and open it in your phone's browser. (A web link is better:
on iPhone, files opened from the Files app can't keep data.)

## Your data

- Everything is stored **on your device** (browser storage). Nothing is uploaded anywhere.
- **Back up regularly:** Profile → Backup & data → *Export backup* (saves or shares a `.json` file).
  The app reminds you when your last backup is old.
- **Moving phones / browsers:** export a backup on the old one and *Import* it on the new one
  (choose **Merge** to combine, or **Replace**).
- **Coming from the original Gym Log?**
  - Same link/file as before: your workouts, rest-day logs, variant choices, theme and any
    unfinished workout are **migrated automatically** the first time you open the new version.
    The old data is left untouched as a fallback.
  - New link: in the *old* app tap the backup button → **Export data (.json)**, then in the new app
    go to Profile → Backup & data → **Import** (or choose *Restore a backup* on the welcome screen).

## Features

**Training**
- Weekly schedule *or* rotation ("up next") planning, with weekly targets and week streaks
- Routines editor: sets, rep ranges, rest times, supersets, start weights, rest-day routines
- 6 ready-made programs (incl. the original 4-day split), recommendation during onboarding
- Exercise library with 150+ exercises, muscles, equipment, how-to steps and common mistakes;
  custom exercises
- Fast set logging: previous-set column, ghost values, Enter-to-next, ±increment keypad bar,
  set types (warm-up / drop / failure), optional RPE, swap exercise, warm-up generator
- Progressive-overload suggestions (double progression with deload / welcome-back guardrails)
- Live PR detection, rest timer with sound/vibration/flash that survives a locked screen
- Workout summary with PRs, achievements, rating, notes and a shareable image

**Progress**
- History list and calendar, session details with "vs last time"
- Weekly workouts & volume charts, muscle balance (sets per muscle), consistency heatmap
- Per-exercise charts (est. 1RM, heaviest, volume), records, rep-max table
- Bodyweight & body measurements with trends and goals
- Achievements, lift goals, plate / 1RM / warm-up calculators

**Polish**
- Dark & light themes, accent colours, kg / lb, Sunday or Monday week start
- Works offline once loaded, installable, keeps the screen awake during workouts
- Android back button / iOS swipe-back close sheets and screens correctly
- Undo for deletes, automatic safety snapshot before imports and resets

## For developers

The whole app is `index.html`: CSS in one `<style>`, then several `<script>` blocks
(core → data → feature modules → boot). Each feature module is an isolated IIFE that registers
routes with `Router.register(...)` and actions with `Act.on(...)`. State lives in the global `S`
(saved under the `gymlog.v2` localStorage key; the in-progress workout under `gymlog.v2.active`).
