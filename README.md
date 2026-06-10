# Vasanthakumar KM — Cinematic Portfolio

> **Live site → [vasanthakumarkm.github.io](https://vasanthakumarkm.github.io)**

A high-performance, Awwwards-inspired personal portfolio built with **pure HTML, CSS, and vanilla JavaScript** — no frameworks, no build tools, no dependencies (except GSAP for scroll animations). Designed to showcase enterprise transformation leadership and make a strong first impression on Irish and European recruiters.

---

## 🎯 Why I Built This

After 7+ years at Amazon delivering $270M+ in business impact across 15+ global markets, I needed a portfolio that matched the scale and quality of the work — not a generic template. The goal was to:

- **Stand out** in the ATS-heavy Irish job market with a human signal
- **Demonstrate digital fluency** — not just claim it on a CV
- **Quantify impact** visually, so recruiters absorb it in seconds
- **Signal design thinking** and attention to detail at a senior level

---

## 🛠️ How I Built It

### The Stack

| Layer | Technology |
|---|---|
| Structure | Semantic HTML5 |
| Styling | Pure CSS3 (custom properties, grid, flexbox) |
| Animations | GSAP 3 + ScrollTrigger (CDN) |
| Fonts | Cabinet Grotesk · DM Sans · Instrument Serif (Google Fonts) |
| Hosting | GitHub Pages (free, custom domain-ready) |
| Version Control | Git + GitHub |

**Zero frameworks. Zero npm. Zero build step.** The entire site is a single `index.html` file — it loads fast, deploys instantly, and has no dependency rot.

---

### Design Philosophy

I approached this like a brand identity project, not a CV upload:

1. **Dark-first aesthetic** — deep `#080a0d` background with gold (`#c9a84c`) as the primary accent. Inspired by luxury finance and premium SaaS product sites.
2. **Typography hierarchy** — Cabinet Grotesk (display, 900 weight) for impact headings, DM Sans for body readability, Instrument Serif italics for editorial accent moments.
3. **Motion with purpose** — every animation serves a narrative goal: reveal sequences guide the eye, counters dramatise impact numbers, scroll-triggered entries reward exploration.
4. **Light/Dark toggle** — CSS custom properties (`--color-bg`, `--color-text`, etc.) swap via a single `data-theme` attribute on `<html>`. No JavaScript re-renders needed.

---

### Key Sections & How Each Was Built

#### Hero
- **Particle canvas** — vanilla JS `requestAnimationFrame` loop drawing 80 particles with proximity-based connection lines
- **Headline reveal** — CSS `clip-path: inset(0 0 100% 0)` animated to `inset(0 0 0% 0)` with staggered delays per line
- **Stat counters** — `setInterval` counting from 0 to target on page load
- **Animated orbs** — CSS `@keyframes` with `blur()` and `scale()` transforms
- **Ghost watermark text** — oversized `::after` pseudo-element with `-webkit-text-stroke` and a slow `translateX` drift animation

#### Navigation
- Transparent on load → frosted glass (`backdrop-filter: blur(20px)`) on scroll via scroll event listener
- Active section highlighting using `IntersectionObserver` on each `<section>` element
- Smooth anchor scrolling via `scrollIntoView({ behavior: 'smooth' })`

#### Impact Grid
- CSS Grid with `grid-column: span N` for the asymmetric bento-box layout
- GSAP `ScrollTrigger` animates each card into view with staggered `opacity` + `scale` transitions
- Animated number counters in the grid driven by GSAP `gsap.to(obj, { val: target })` on scroll entry

#### 3D Tilt Cards
- `mousemove` event calculates cursor offset from card centre
- Applies `perspective(700px) rotateY() rotateX()` CSS transforms for depth
- Resets to `transform: ''` on `mouseleave`

#### Magnetic Buttons
- `mousemove` tracks cursor relative to button centre
- Applies a fractional `translate()` (30% of offset) for the magnetic pull effect
- Smooth return via CSS `transition: transform 0.3s cubic-bezier(0.16,1,0.3,1)`

#### Custom Cursor
- Two `<div>` elements: a small filled dot (immediate position) and a larger ring (lagged position)
- Ring uses lerp-style smoothing: `rx += (cx - rx) * 0.12` per frame
- `mix-blend-mode: difference` on the dot creates the invert effect over light elements

#### Page Load Curtain
- Full-screen `<div>` with `transform-origin: top` scales to `scaleY(0)` on load
- CSS `transition` handles the reveal animation; element is removed from DOM after 1.5s

#### Marquee
- Doubled content in a single `<div>` with `width: max-content`
- Pure CSS `@keyframes` translating `translateX(0)` → `translateX(-50%)` infinitely
- `animation-play-state: paused` on hover

#### Transformation Engine SVG
- Hand-coded inline SVG with concentric circles, radial lines, and text labels
- `filter: drop-shadow()` adds the ambient glow effect
- No external SVG editor — built directly in markup

---

### Performance Choices

- **Single file** — eliminates HTTP round-trips for CSS/JS files
- **System font stack fallback** — fonts load progressively; layout doesn't shift
- **CDN-hosted GSAP** — leverages browser cache if already loaded from another site
- **No images** — all visuals are CSS gradients, SVG, and canvas; zero image requests
- **CSS custom properties** — theme switching is instant with zero JS layout recalculation

---

### Deployment

Hosted on **GitHub Pages** — free, fast, and zero-config for a `username.github.io` repository.

```bash
# Clone the repo
git clone https://github.com/vasanthakumarkm/vasanthakumarkm.github.io.git

# Edit index.html with any text editor
# No build step, no npm install, no config

# Push to deploy
git add .
git commit -m "Update portfolio"
git push origin main
# Live in ~60 seconds
```

---

### Iterative Build Process

This site was built iteratively using an **AI-assisted workflow**:

1. **Defined the brief** — target roles (Digital Transformation, Change Management, Programme Delivery in Ireland), tone (premium, data-led, confident), and content structure
2. **Designed the architecture** — sections mapped to recruiter decision points: hero → thesis → impact → framework → career → expertise → credentials → contact
3. **Built in layers** — layout and typography first, then interactions, then GSAP animations, then performance polish
4. **Refined via feedback** — each section reviewed against real Irish job descriptions to ensure keyword alignment and narrative clarity
5. **Deployed and iterated** — GitHub Pages enabled live preview after each push

---

## 📁 File Structure

```
vasanthakumarkm.github.io/
├── index.html        # Entire site — HTML + CSS + JS in one file
└── README.md         # This file
```

---

## 🎨 Colour Palette

| Name | Hex | Usage |
|---|---|---|
| Background | `#080a0d` | Page background |
| Surface | `#0d1117` | Card backgrounds |
| Gold | `#c9a84c` | Primary accent, headings, CTAs |
| Gold Bright | `#e0b85a` | Hover states |
| Ice Blue | `#4fa8d5` | Secondary accent, particle dots |
| Text | `#e8edf2` | Body copy |
| Text Muted | `#8a96a3` | Secondary text |

---

## ✍️ Typography

- **Cabinet Grotesk** (900, 700, 500, 400) — Display headings, nav, stats. Chosen for its geometric confidence and tight letter-spacing at large sizes.
- **DM Sans** (300, 400, 500) — Body text. Clean, readable, professional.
- **Instrument Serif** (italic) — Editorial accent for the italic moments in headings. Adds warmth and personality to an otherwise data-heavy layout.

---

## 📬 Contact

**Vasanthakumar KM** · Digital Transformation Leader · Dublin, Ireland

- 💼 [linkedin.com/in/vasanthakumar-km](https://linkedin.com/in/vasanthakumar-km)

---

*Built with curiosity, iterated with discipline, deployed with confidence.*
