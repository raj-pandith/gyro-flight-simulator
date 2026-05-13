# ✈️ Gyro Flight Simulator 

A mobile-first gyroscope-based flight simulator that runs entirely in the browser — no installs, no dependencies.

🔗 **[Live Demo](https://zhadowvalker.github.io/gyro-flight-simulator/)**

## Features


- **Gyro controls** — tilt your phone to pitch and roll the aircraft
- **Touch drag fallback** — drag on the canvas when gyro is unavailable
- **Mouse fallback** — works on desktop for testing
- **Live sensor debug panel** — shows β/γ/α values and event count in real time
- **HTTPS detection** — warns and falls back gracefully on plain HTTP
- **iOS 13+ permission flow** — handles `requestPermission()` correctly
- **Android dual-event** — listens to both `deviceorientation` and `deviceorientationabsolute`
- **Physics** — drag, gravity, climb = v × sin(pitch), stall detection
- **HUD** — artificial horizon, pitch ladder, roll indicator, stall warning

## Controls

| Control | Action |
|---------|--------|
| Tilt phone forward | Pitch up (climb) |
| Tilt phone back | Pitch down (descend) |
| Tilt phone left/right | Bank / turn |
| Throttle slider | Increase/decrease thrust |
| Set Neutral | Calibrate current tilt as level |

## Usage

1. Open the [live demo](https://zhadowvalker.github.io/gyro-flight-simulator/) on your phone
2. Tap **Enable Gyro** and grant permission when prompted
3. Watch the sensor panel light up — β/γ/α values confirm the gyro is live
4. Tap **Set Neutral** while holding the phone at your preferred flying angle
5. Use the throttle slider to build speed, then tilt to fly

> ⚠️ Gyro requires **HTTPS**. The GitHub Pages deployment satisfies this automatically.

## Running Locally

```bash
# Any local HTTPS server works. Quickest option:
npx serve .
# Then open https://localhost:3000
```

Or use VS Code Live Server with HTTPS enabled.

## CI/CD

GitHub Actions runs on every push to `main`:

1. **HTML Validate** — checks `index.html` for structural errors
2. **Deploy to GitHub Pages** — publishes the site automatically

## Physics Model

| Parameter | Value | Notes |
|-----------|-------|-------|
| Gravity | 0.08 alt/frame | Constant downward force |
| Drag | 0.985×/frame | Air resistance on velocity |
| Climb rate | v × sin(pitch) × 0.12 | Velocity-dependent lift |
| Stall speed | < 1.5 kts | Below this, high pitch = stall |
| Stall pitch | > 18° | Nose-up threshold |
| Turn rate | roll × velocity × 0.005 | No turn when stationary |

## License

MIT
