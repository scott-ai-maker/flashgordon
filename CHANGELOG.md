# Flash Gordon — Changelog

## v2.3.0 — 2026-03-16

### Shot outcome log — process vs result separation

- **Outcome row** appears above the error log after each rep: ✓ MADE · ✗ MISSED · ⊙ POS ERR
- Tapping an outcome saves the shot record immediately; tapping again updates it
- **Per-shot error tracking** (`shotErrors`) separate from session totals — resets
  each time PLAY is tapped so errors are attributed to the correct rep
- Shot data stored as `fg_shots` in localStorage: `{ id, date, sessionStart, outcome, errors }`
- **Analytics extended** (renamed to SHOT ANALYSIS):
  - Outcome distribution bar chart (MADE / MISSED / POS ERR)
  - Process vs Result table: make rate on clean reps vs error-flagged reps
  - Automated diagnostic insight:
    - Low make rate even on clean reps → aim/speed problem, not mechanics
    - Large gap between clean and flawed → fixing #1 fault directly improves results
    - Higher make rate on flawed reps → compensations forming under pressure

---

## v2.2.0 — 2026-03-16

### Session tracking & practice stats

- **Session panel**: explicit START / END SESSION button with live MM:SS timer
  while active. Replaces per-routine time tracking with whole-session logging.
- **Stats strip**: always-visible DAY · WEEK · MONTH · STREAK row beneath the
  session button. Week is calculated Mon–Sun.
- **Streak counter**: consecutive calendar days with at least one logged session.
  Streak survives if you practiced yesterday but not yet today.
- **Session data model**: each session stored as `{ date, start, end, duration,
  shots }` in `localStorage` key `fg_sessions` — persists across app restarts.
- **Auto-save on close**: `beforeunload` listener ends any open session so data
  is never lost if the app is closed without tapping END.
- **Shot attribution**: shots fired during an active session are recorded per
  session, enabling future shot-rate analytics.
- Tightened vertical spacing throughout to accommodate new elements on small
  screens (iPhone SE and up).

---

## v2.0.0 — 2026-03-16

### Orthodox Fundamentals System — Full Rewrite

Complete replacement of the 17-step wisdom-based routine with a strict
10-beat Orthodox Fundamentals pre-shot system based on Mark Wilson's
*Play Great Pool*. Tempo fixed at 60 BPM (1 second per beat).

**Sequence (10 beats):**
1. COMMIT — Decision: lock in shot, speed, leave
2. STEP — Approach: lead foot into the line of aim
3. DOWN — Placement: drop into stance, tip near cue ball
4. CHECK — Verify: CB → OB → CB eye travel, confirm aim
5. STROKE — Rhythm 1: first slow straight practice swing
6. MATCH — Rhythm 2: second swing, match intended length
7. STILL — Final Pause: total stillness, final visual check
8. SHIFT — Transition: eyes lock target, slow backswing begins
9. THROUGH — Delivery: fixed elbow, smooth acceleration
10. HOLD — Evaluate: total stillness, evaluate tip position

**Audio additions:**
- `pause` click type (380 Hz, longer decay) for Beat 7 — distinctly
  lower than all other beats to signal the non-negotiable stop
- Beat 9 "Through" spoken at rate 0.70 (vs 0.84 standard) for a
  warmer, slower voice cadence on the delivery cue
- Crystal singing bowl (432 Hz fundamental + 864 Hz shimmer + 216 Hz
  sub, 3.5s natural decay) plays on routine completion
- Post-stroke "Read" voice cue spoken 800ms into the bowl tone (0.72 rate)

**Error log panel:**
- Appears after each completed shot
- 8 error types: RUSHED, LIFTED, DROPPED, PEEKED, DRIFTED, SHORT,
  TENSION, EARLY
- Each tap: flashes button, speaks the label, increments session count badge

**UI:**
- Beat indicator expanded from 4 dots to 10 (one per beat)
- Removed wisdom library and category filter (replaced by fixed sequence)

**Branding alignment (flashgordonpool.com):**
- Gold updated from `#f5c400` to `#C9A84C` (muted antique brass)
- Title treatment changed to FLASH (white) · GORDON (gold) matching site
- All gold glows/shadows updated to `rgba(201,168,76,…)`
- Play button gradient updated to muted brass

---

## v1.0.0 — prior

Initial pre-shot routine trainer. 17-step sequence with shuffled wisdom
library (62 tips across 5 categories), adjustable BPM 50–120, PWA
with offline support and wake lock.
