# ČSOBi — clickable concept prototype

**Your money, your colours.** A mobile-first concept for a digital banking brand for 18–34 year olds.
Everything is in one file, `index.html` (HTML + CSS + vanilla JS). It has no dependencies and no backend, and it works offline (it uses Google Fonts when online and falls back to system fonts).
All names, numbers, banks, branches and funds are fictional examples.

Open `index.html` in a browser. On a laptop the app sits in a phone frame. On a phone (≤ 520 px wide) it fills the screen.

## Presenter controls

| Control | What it does |
|---|---|
| **Demo** pill (top-right; on a phone, a slim tab on the right edge) | Opens the presenter panel |
| `R` | Restart demo (resets all state, back to splash) |
| `S` | Skip 6 months: 6 payday buys plus round-ups, 6 more streak dots, salary rises to 40 500 Kč, the pay-rise card appears and new shirts unlock |
| `M` | Simulate a market drop of 4%: the Pocket value falls 4%, a red alert appears on Invest, the home banner and tip turn calm and blue, then the AI coach opens |
| `D` | Toggle the panel. The panel also has **Jump to any screen** (25 targets) |
| `Esc` | Back, or close the open sheet or panel |

## Screens

0. **Splash.** Kamil waves, with the wordmark, tagline, *Enter*, and the link *Open an account in 3 minutes with Bankovní identita*
   - **Onboarding (3 steps):** choose a bank → confirm data (two consent boxes) → *Your account is ready* with the new virtual card
1. **Home.** Greeting and avatar (leads to Profile), search, notifications, a swipeable account carousel (Main · Invest Pocket · Kids jar), quick actions (Add money · Send · Request · More), the *Salary arrived* banner, Kamil's tip card (tap to cycle; it changes colour with context), and transactions with round-ups
   - **Search:** live filtering of actions and transactions
2. **Payments.** The *Approve payments right here* note, friends row, Send / Request / QR pay / Split a bill
   - Contact picker → amount keypad (also takes keyboard digits) → Face ID approval sheet → instant-payment animation
   - QR pay (scan → merchant found → approve, or *My code*), Split a bill (choose a bill and friends, share calculated live)
3. **Invest.** Intro, then a 5-step flow with a progress bar:
   a) Goal (First flat / Safety reserve / Big trip)
   b) Plan: a 1–15% slider, live projection with `FV = c·((1+r)^n − 1)/r`, r = 5%/12, a progress bar against the goal, and toggles for round-ups, cashback and DIP
   c) DIP explainer: yearly contributions (capped at 48 000) × 15% = tax back
   d) MiFID II check: 3 questions → Cautious / Balanced / Growth with an ETF mix and default fund
   e) Confirm summary, then **Hold to start plan** (press for about 1 s)
   f) Success: Kamil jumps and cycles shirt colours, then lands on Mint, with confetti
   - **Pocket dashboard:** value, invested amount, gain or loss, sparkline, goal progress (actual and projected), next payday buy, 12-dot streak, small money in, the pay-rise card, ETF mix, and links to the coach, plan settings and *Open Patria* (mock)
   - **AI coach (Kamil):** chat with suggestion chips, prepared answers, keyword matching and a generic fallback, plus links to a video call
4. **Cards.** Orange virtual card with a scale pattern, show details, freeze, limits, Apple Pay / Google Pay (mock), online and contactless toggles, PIN, and ordering a physical card (by post, or same-day pickup at one of 3 example Prague branches with a map)
5. **Rewards.** Kamil's wardrobe (shirts unlock at 1, 3, 6 and 12 months), quests, invite a friend (rule, code `ADAM-27KB` with copy, share), the *Find Kamil* mini-game (badge), Family / Kids jar (pocket money, the child's investment jar, a daily limit slider, toggles, always-blocked categories), and badges

**Profile:** plan pause and amount, notifications, security, CZ/EN language switch (main labels), *Talk to a human* (mock video call), and log out.

## 3-minute demo path

1. **Splash** → *Enter*
2. **Home** → tap the *Salary arrived: 38 000 Kč. Put 5% to work?* banner
3. **Goal:** *First flat* → Continue
4. **Plan:** move the slider (try 7% and the projection goes past the goal), then back to 5% → Continue
5. **DIP** (≈ 3 798 Kč back) → Continue
6. **Suitability:** answer 3 questions → *Balanced* → Continue
7. **Confirm:** press and hold *Hold to start plan* → **You're an investor!** → *Open my Pocket*
8. Press **S** (Skip 6 months): the streak fills, new shirts unlock, and the *Pay rise spotted* card appears → *Raise to 6 % · one tap*
9. Press **M** (Simulate −4%): a red alert, and the coach opens with *Markets fell 4%…* → tap *Should I sell?*
10. Close the coach → **Rewards** tab → *Copy* the code → *Share invite*

## Tech notes

- Navigation is a stack router with push, pop, fade and slide-up transitions using the Web Animations API (transform and opacity only). `prefers-reduced-motion` switches to short fades and turns off the mascot animation.
- Kamil is an original inline SVG. His skin and shirt are CSS variables, so he can change colour in the tip card, the wardrobe, the success screen and the jungle camouflage.
- Text is at least 13 px, tap targets are at least 44 px, and toggles use `role="switch"` with keyboard support.
