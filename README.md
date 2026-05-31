<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sanjeev Reddy — ML Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0c0c10;
    --surface: #13131a;
    --surface2: #1a1a24;
    --border: rgba(255,255,255,0.07);
    --border-bright: rgba(255,255,255,0.14);
    --text: #f0eff5;
    --muted: #8b8a9b;
    --faint: #4a4960;
    --accent: #a78bfa;
    --accent2: #34d399;
    --accent3: #f472b6;
    --accent-dim: rgba(167,139,250,0.12);
    --accent2-dim: rgba(52,211,153,0.1);
    --serif: 'DM Serif Display', Georgia, serif;
    --sans: 'Outfit', sans-serif;
    --mono: 'DM Mono', monospace;
  }

  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 16px;
    line-height: 1.6;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* — NOISE TEXTURE OVERLAY — */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  .container {
    max-width: 820px;
    margin: 0 auto;
    padding: 0 2rem 6rem;
    position: relative;
    z-index: 1;
  }

  /* — GLOW ORB — */
  .glow-orb {
    position: fixed;
    top: -200px;
    right: -200px;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(167,139,250,0.08) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }
  .glow-orb2 {
    position: fixed;
    bottom: -200px;
    left: -150px;
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, rgba(52,211,153,0.06) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  /* — HEADER / HERO — */
  .hero {
    padding: 5rem 0 3.5rem;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 2rem;
    align-items: center;
    border-bottom: 1px solid var(--border);
    margin-bottom: 3.5rem;
    animation: fadeUp 0.7s ease both;
  }
  .hero-tag {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .hero h1 {
    font-family: var(--serif);
    font-size: clamp(2.8rem, 6vw, 4.5rem);
    font-weight: 400;
    line-height: 1.05;
    letter-spacing: -0.02em;
    color: var(--text);
    margin-bottom: 0.6rem;
  }
  .hero h1 em {
    font-style: italic;
    color: var(--accent);
  }
  .hero-sub {
    font-size: 15px;
    color: var(--muted);
    margin-bottom: 1.75rem;
    font-weight: 300;
    letter-spacing: 0.01em;
  }
  .hero-links {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    align-items: center;
  }
  .pill {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 7px 14px;
    border-radius: 999px;
    font-size: 13px;
    font-weight: 400;
    text-decoration: none;
    transition: all 0.2s;
    border: 1px solid var(--border-bright);
    color: var(--muted);
    background: transparent;
  }
  .pill:hover { border-color: var(--accent); color: var(--accent); background: var(--accent-dim); }
  .pill svg { width: 14px; height: 14px; flex-shrink: 0; }
  .pill-status {
    border-color: rgba(52,211,153,0.3);
    color: var(--accent2);
    background: rgba(52,211,153,0.07);
  }
  .pill-status::before {
    content: '';
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent2);
    animation: pulse 2s infinite;
  }
  .avatar-block {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background: linear-gradient(135deg, #534AB7 0%, #7F77DD 50%, #34d399 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--serif);
    font-size: 32px;
    color: #fff;
    flex-shrink: 0;
    position: relative;
    box-shadow: 0 0 0 1px rgba(167,139,250,0.25), 0 0 40px rgba(167,139,250,0.15);
  }
  .avatar-block::after {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 50%;
    border: 1px solid rgba(167,139,250,0.2);
  }

  /* — SECTION HEADERS — */
  .section-head {
    display: flex;
    align-items: baseline;
    gap: 1rem;
    margin-bottom: 1.75rem;
    animation: fadeUp 0.5s ease both;
  }
  .section-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--faint);
    letter-spacing: 0.08em;
  }
  .section-title {
    font-family: var(--serif);
    font-size: 1.6rem;
    font-weight: 400;
    color: var(--text);
    letter-spacing: -0.01em;
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  section { margin-bottom: 4rem; }

  /* — ABOUT — */
  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem 2.25rem;
  }
  .about-quote-inline {
    font-family: var(--serif);
    font-style: italic;
    font-size: 1.15rem;
    color: var(--text);
    border-left: 2px solid var(--accent);
    padding-left: 14px;
    margin-bottom: 1rem;
    line-height: 1.5;
  }
  .about-body {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 1.5rem;
  }
  .about-facts {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  .about-fact-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 13px;
    color: var(--muted);
    line-height: 1.45;
  }
  .about-fact-item strong { color: var(--text); font-weight: 500; }
  .fact-icon { font-size: 15px; flex-shrink: 0; margin-top: 1px; }

  /* — ABOUT MODERN — */
  .about-modern {
    display: grid;
    grid-template-columns: 1.1fr 0.9fr;
    gap: 14px;
    align-items: start;
  }
  .about-left {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.75rem 2rem;
    display: flex;
    flex-direction: column;
    gap: 1.25rem;
  }
  .about-quote-inline {
    font-family: var(--serif);
    font-style: italic;
    font-size: 1.1rem;
    color: var(--text);
    border-left: 2px solid var(--accent);
    padding-left: 14px;
    line-height: 1.5;
  }
  .about-body {
    font-size: 13.5px;
    color: var(--muted);
    line-height: 1.75;
  }
  .about-facts {
    display: flex;
    flex-direction: column;
    gap: 12px;
    border-top: 1px solid var(--border);
    padding-top: 1.25rem;
  }
  .about-fact-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }
  .fact-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    flex-shrink: 0;
    margin-top: 5px;
  }
  .fact-key {
    display: block;
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.09em;
    text-transform: uppercase;
    color: var(--faint);
    margin-bottom: 2px;
  }
  .fact-val {
    display: block;
    font-size: 13px;
    color: var(--muted);
    line-height: 1.45;
  }

  /* right column */
  .about-right {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .cert-section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--faint);
    margin-bottom: 10px;
  }
  .cert-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.1rem 1.25rem;
    display: flex;
    align-items: center;
    gap: 14px;
    position: relative;
    transition: border-color 0.2s;
  }
  .cert-card:hover { border-color: rgba(52,211,153,0.35); }
  .cert-logo {
    flex-shrink: 0;
    width: 44px; height: 44px;
    border-radius: 10px;
    background: rgba(98,216,78,0.1);
    border: 1px solid rgba(98,216,78,0.2);
    display: flex; align-items: center; justify-content: center;
  }
  .cert-info {
    display: flex;
    flex-direction: column;
    gap: 3px;
    flex: 1;
  }
  .cert-name {
    font-size: 13px;
    font-weight: 500;
    color: var(--text);
    line-height: 1.3;
  }
  .cert-issuer {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--faint);
  }
  .cert-badge {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    font-size: 11px;
    color: var(--accent2);
    background: rgba(52,211,153,0.08);
    border: 1px solid rgba(52,211,153,0.2);
    border-radius: 999px;
    padding: 3px 9px;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .interest-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .itag {
    font-size: 12px;
    font-family: var(--mono);
    padding: 4px 10px;
    border-radius: 6px;
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--muted);
    transition: border-color 0.2s, color 0.2s;
  }
  .itag:hover { border-color: var(--accent); color: var(--accent); }

  @media (max-width: 640px) {
    .about-modern { grid-template-columns: 1fr; }
  }

  /* — ABOUT (old grid, unused) — */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }
  .about-quote {
    grid-column: 1 / -1;
    padding: 2rem 2.25rem;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
  }
  .about-quote blockquote {
    font-family: var(--serif);
    font-style: italic;
    font-size: 1.25rem;
    color: var(--text);
    line-height: 1.5;
  }
  .about-quote blockquote::before {
    content: '"';
    font-size: 3rem;
    line-height: 0;
    vertical-align: -0.5rem;
    color: var(--accent);
    margin-right: 4px;
    font-family: var(--serif);
  }
  .about-fact {
    padding: 1.25rem 1.75rem;
    background: var(--surface);
    display: flex;
    flex-direction: column;
    gap: 4px;
  }
  .fact-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.1em;
    color: var(--faint);
    text-transform: uppercase;
  }
  .fact-val {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.4;
  }
  .fact-val strong { color: var(--text); font-weight: 500; }

  /* — STACK — */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }
  .stack-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.25rem;
    transition: border-color 0.2s;
  }
  .stack-card:hover { border-color: var(--border-bright); }
  .stack-card-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.1em;
    color: var(--faint);
    text-transform: uppercase;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .stack-card-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  .badge-row { display: flex; flex-wrap: wrap; gap: 6px; }
  .badge {
    font-size: 12px;
    padding: 4px 10px;
    border-radius: 6px;
    font-weight: 400;
    font-family: var(--mono);
    letter-spacing: 0.02em;
    border: 1px solid transparent;
  }
  .b-purple { background: rgba(167,139,250,0.1); color: #c4b5fd; border-color: rgba(167,139,250,0.2); }
  .b-teal   { background: rgba(52,211,153,0.08); color: #6ee7b7; border-color: rgba(52,211,153,0.18); }
  .b-pink   { background: rgba(244,114,182,0.08); color: #f9a8d4; border-color: rgba(244,114,182,0.18); }

  /* — PROJECTS — */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .proj-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 10px;
    text-decoration: none;
    color: inherit;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
  }
  .proj-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .proj-card:hover { border-color: var(--border-bright); transform: translateY(-2px); }
  .proj-card:hover::before { opacity: 1; }
  .proj-icon {
    width: 38px; height: 38px;
    border-radius: 10px;
    background: var(--accent-dim);
    border: 1px solid rgba(167,139,250,0.2);
    display: flex; align-items: center; justify-content: center;
    font-size: 17px;
  }
  .proj-name {
    font-size: 15px;
    font-weight: 500;
    color: var(--text);
  }
  .proj-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.55;
    flex: 1;
  }
  .proj-tags { display: flex; gap: 5px; flex-wrap: wrap; }
  .proj-tag {
    font-size: 11px;
    font-family: var(--mono);
    padding: 3px 8px;
    border-radius: 4px;
    background: var(--surface2);
    color: var(--faint);
    border: 1px solid var(--border);
  }
  .proj-arrow {
    position: absolute;
    top: 1.25rem; right: 1.25rem;
    font-size: 16px;
    color: var(--faint);
    transition: color 0.2s, transform 0.2s;
  }
  .proj-card:hover .proj-arrow { color: var(--accent); transform: translate(2px, -2px); }

  /* — CONNECT — */
  .connect-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2.5rem;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 2rem;
    align-items: center;
    position: relative;
    overflow: hidden;
  }
  .connect-card::after {
    content: '';
    position: absolute;
    bottom: -60px; right: -60px;
    width: 200px; height: 200px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(167,139,250,0.08) 0%, transparent 70%);
    pointer-events: none;
  }
  .connect-eyebrow {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }
  .connect-card h2 {
    font-family: var(--serif);
    font-size: 1.8rem;
    font-weight: 400;
    color: var(--text);
    line-height: 1.2;
    margin-bottom: 0.5rem;
  }
  .connect-card p {
    font-size: 14px;
    color: var(--muted);
    max-width: 380px;
  }
  .connect-btns { display: flex; flex-direction: column; gap: 8px; }
  .cta-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 10px;
    font-size: 13px;
    font-weight: 500;
    font-family: var(--sans);
    text-decoration: none;
    transition: all 0.2s;
    white-space: nowrap;
    cursor: pointer;
    border: none;
  }
  .cta-btn svg { width: 15px; height: 15px; flex-shrink: 0; }
  .cta-primary {
    background: var(--accent);
    color: #0c0c10;
  }
  .cta-primary:hover { background: #c4b5fd; }
  .cta-secondary {
    background: transparent;
    border: 1px solid var(--border-bright);
    color: var(--muted);
  }
  .cta-secondary:hover { border-color: var(--accent); color: var(--accent); background: var(--accent-dim); }

  /* — FOOTER — */
  footer {
    border-top: 1px solid var(--border);
    padding-top: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--faint);
    letter-spacing: 0.06em;
  }

  /* — ANIMATIONS — */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0.4; }
  }
  section:nth-child(1) { animation: fadeUp 0.6s 0.1s ease both; }
  section:nth-child(2) { animation: fadeUp 0.6s 0.2s ease both; }
  section:nth-child(3) { animation: fadeUp 0.6s 0.3s ease both; }
  section:nth-child(4) { animation: fadeUp 0.6s 0.4s ease both; }

  /* — GITHUB STATS — */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    margin-bottom: 12px;
  }
  .stat-card {
    background: var(--surface);
    padding: 2rem 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }
  .stat-center {
    align-items: center;
    text-align: center;
    padding: 1.75rem 2rem;
    border-left: 1px solid var(--border);
    border-right: 1px solid var(--border);
  }
  .stat-num {
    font-family: var(--serif);
    font-size: 3.5rem;
    font-weight: 400;
    line-height: 1;
    letter-spacing: -0.03em;
  }
  .stat-label {
    font-size: 13px;
    color: var(--muted);
    font-weight: 400;
  }
  .stat-sub {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--faint);
    letter-spacing: 0.04em;
  }
  .streak-ring {
    position: relative;
    width: 120px;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .streak-ring svg { position: absolute; inset: 0; }
  .streak-inner {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0;
    position: relative;
    z-index: 1;
  }
  .streak-flame { font-size: 20px; line-height: 1; }
  .streak-num {
    font-family: var(--serif);
    font-size: 2.4rem;
    font-weight: 400;
    color: #c4b5fd;
    line-height: 1.1;
  }
  .gh-img-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .gh-img-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 8px;
  }
  .gh-img-card img {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 8px;
  }

  /* — RESPONSIVE — */
  @media (max-width: 640px) {
    .hero { grid-template-columns: 1fr; }
    .avatar-block { display: none; }
    .about-grid { grid-template-columns: 1fr; }
    .about-fact:nth-child(even) { border-left: none; }
    .stack-grid { grid-template-columns: 1fr; }
    .projects-grid { grid-template-columns: 1fr; }
    .connect-card { grid-template-columns: 1fr; }
    .connect-btns { flex-direction: row; flex-wrap: wrap; }
    .stats-grid { grid-template-columns: 1fr; }
    .stat-center { border-left: none; border-right: none; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
    .gh-img-row { grid-template-columns: 1fr; }
    
  }

  /* — CERTIFICATIONS — */
  .cert-full-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem 2.25rem;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 2.5rem;
    align-items: start;
    position: relative;
    overflow: hidden;
    transition: border-color 0.2s;
  }
  .cert-full-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(98,216,78,0.4), transparent);
  }
  .cert-full-card:hover { border-color: rgba(98,216,78,0.3); }
  .cert-full-left {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 14px;
    min-width: 90px;
    text-align: center;
    padding-top: 4px;
  }
  .cert-full-logo {
    width: 80px; height: 80px;
    border-radius: 14px;
    background: #fff;
    border: 1px solid rgba(255,255,255,0.1);
    display: flex; align-items: center; justify-content: center;
    padding: 12px;
  }
  .cert-full-issuer {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--faint);
    display: block;
    margin-bottom: 4px;
  }
  .cert-full-name {
    font-size: 18px;
    font-weight: 500;
    color: var(--text);
    line-height: 1.3;
    margin-bottom: 6px;
    font-family: var(--sans);
  }
  .cert-full-code {
    display: inline-block;
    font-family: var(--mono);
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 5px;
    background: rgba(167,139,250,0.1);
    border: 1px solid rgba(167,139,250,0.2);
    color: #c4b5fd;
    letter-spacing: 0.08em;
  }
  .cert-full-right {
    display: flex;
    flex-direction: column;
    gap: 14px;
  }
  .cert-verified-badge {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-size: 12px;
    color: var(--accent2);
    background: rgba(52,211,153,0.08);
    border: 1px solid rgba(52,211,153,0.2);
    border-radius: 999px;
    padding: 4px 12px;
    width: fit-content;
  }
  .cert-full-desc {
    font-size: 13.5px;
    color: var(--muted);
    line-height: 1.7;
  }
  .cert-skills {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
  }
  .cert-skill-tag {
    font-size: 11px;
    font-family: var(--mono);
    padding: 4px 10px;
    border-radius: 6px;
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--muted);
  }
  @media (max-width: 640px) {
    .cert-full-card { grid-template-columns: 1fr; gap: 1.25rem; }
  }
</style>
</head>
<body>

<div class="glow-orb"></div>
<div class="glow-orb2"></div>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div>
      <p class="hero-tag">// ML Engineer · Backend Dev · AI Enthusiast</p>
      <h1>Sanjeev<br><em>Reddy</em></h1>
      <p class="hero-sub">CS Graduate from Hyderabad — building ML-powered systems<br>and data-driven applications that actually solve problems.</p>
      <div class="hero-links">
        <span class="pill pill-status">Open to work</span>
        <a class="pill" href="https://www.linkedin.com/in/nersi-sai-venkata-sanjeev-reddy-a8b777291/" target="_blank">
          <svg fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a class="pill" href="mailto:sanjeev.reddy2004@gmail.com">
          <svg fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75"/></svg>
          Email
        </a>
        <a class="pill" href="https://sanjeev-reddy-13.github.io/MyPortfolio_website" target="_blank">
          <svg fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253"/></svg>
          Portfolio
        </a>
        <a class="pill" href="https://github.com/sanjeev-reddy-13" target="_blank">
          <svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
          GitHub
        </a>
      </div>
    </div>
    <div class="avatar-block">SR</div>
  </div>

  <!-- ABOUT -->
  <section>
    <div class="section-head">
      <span class="section-num">01</span>
      <h2 class="section-title">About me</h2>
      <div class="section-line"></div>
    </div>

    <div class="about-modern">

      <!-- Left: bio + facts -->
      <div class="about-left">
        <p class="about-quote-inline">"Turning data into decisions and ideas into products."</p>
        <p class="about-body">CS graduate from Hyderabad who loves building ML-powered backend systems and data-driven applications. I dig into messy datasets, train models, and ship clean APIs that solve real problems.</p>

        <div class="about-facts">
          <div class="about-fact-item">
            <div class="fact-dot" style="background:#a78bfa"></div>
            <div>
              <span class="fact-key">Education</span>
              <span class="fact-val">B.Tech, Computer Science — Recent Graduate</span>
            </div>
          </div>
          <div class="about-fact-item">
            <div class="fact-dot" style="background:#34d399"></div>
            <div>
              <span class="fact-key">Building</span>
              <span class="fact-val">AI/ML projects &amp; backend APIs</span>
            </div>
          </div>
          <div class="about-fact-item">
            <div class="fact-dot" style="background:#60a5fa"></div>
            <div>
              <span class="fact-key">Learning</span>
              <span class="fact-val">Deep Learning · NLP · System Design</span>
            </div>
          </div>
          <div class="about-fact-item">
            <div class="fact-dot" style="background:#f472b6"></div>
            <div>
              <span class="fact-key">Fun fact</span>
              <span class="fact-val">I debug with <code style="font-family:var(--mono);color:var(--accent);font-size:11px">print()</code> — no regrets</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Right: certification -->
      <div class="about-right">
        <p class="cert-section-label">Certifications</p>
        <div class="cert-card">
          <div class="cert-logo">
            <svg width="28" height="28" viewBox="0 0 40 40" fill="none">
              <rect width="40" height="40" rx="8" fill="#62D84E"/>
              <path d="M10 20h20M20 10v20" stroke="#fff" stroke-width="3" stroke-linecap="round"/>
              <circle cx="20" cy="20" r="6" fill="#fff" opacity="0.2"/>
            </svg>
          </div>
          <div class="cert-info">
            <span class="cert-name">Certified System Administrator</span>
            <span class="cert-issuer">ServiceNow · CSA</span>
          </div>
          <div class="cert-badge">
            <svg width="14" height="14" fill="none" viewBox="0 0 24 24" stroke="#34d399" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
            Verified
          </div>
        </div>

        <div class="interests-row">
          <p class="cert-section-label" style="margin-top:1.5rem">Interests</p>
          <div class="interest-tags">
            <span class="itag">Machine Learning</span>
            <span class="itag">Backend Dev</span>
            <span class="itag">Data Science</span>
            <span class="itag">NLP</span>
            <span class="itag">AI/ML</span>
            <span class="itag">System Design</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- STACK -->
  <section>
    <div class="section-head">
      <span class="section-num">02</span>
      <h2 class="section-title">Tech stack</h2>
      <div class="section-line"></div>
    </div>
    <div class="stack-grid">
      <div class="stack-card">
        <div class="stack-card-label">Languages</div>
        <div class="badge-row">
          <span class="badge b-purple">Python</span>
          <span class="badge b-purple">C++</span>
          <span class="badge b-purple">JavaScript</span>
          <span class="badge b-purple">SQL</span>
          <span class="badge b-purple">HTML</span>
          <span class="badge b-purple">CSS</span>
        </div>
      </div>
      <div class="stack-card">
        <div class="stack-card-label">AI / ML / Data</div>
        <div class="badge-row">
          <span class="badge b-teal">NumPy</span>
          <span class="badge b-teal">Pandas</span>
          <span class="badge b-teal">Scikit-Learn</span>
          <span class="badge b-teal">TensorFlow</span>
          <span class="badge b-teal">Matplotlib</span>
        </div>
      </div>
      <div class="stack-card">
        <div class="stack-card-label">Tools &amp; platforms</div>
        <div class="badge-row">
          <span class="badge b-pink">FastAPI</span>
          <span class="badge b-pink">MySQL</span>
          <span class="badge b-pink">ServiceNow</span>
          <span class="badge b-pink">Git</span>
          <span class="badge b-pink">VS Code</span>
          <span class="badge b-pink">Jupyter</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section>
    <div class="section-head">
      <span class="section-num">03</span>
      <h2 class="section-title">Featured projects</h2>
      <div class="section-line"></div>
    </div>
    <div class="projects-grid">

      <a class="proj-card" href="https://github.com/sanjeev-reddy-13/LexConnect" target="_blank">
        <span class="proj-arrow">↗</span>
        <div class="proj-icon">⚖️</div>
        <div class="proj-name">LexConnect</div>
        <div class="proj-desc">Legal services platform connecting clients with lawyers. Backend-driven architecture for seamless professional-to-client matching.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">Backend</span>
          <span class="proj-tag">API</span>
        </div>
      </a>

      <a class="proj-card" href="https://github.com/sanjeev-reddy-13/Stockmarket-Price-Prediction-with-sentimental-analysis" target="_blank">
        <span class="proj-arrow">↗</span>
        <div class="proj-icon">📈</div>
        <div class="proj-name">Stock Market Prediction</div>
        <div class="proj-desc">Predicts stock prices using ML combined with sentiment analysis on news data for smarter, context-aware forecasting.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">NLP</span>
          <span class="proj-tag">ML</span>
          <span class="proj-tag">Sentiment</span>
        </div>
      </a>

      <a class="proj-card" href="https://github.com/sanjeev-reddy-13/RestaurantFinder" target="_blank">
        <span class="proj-arrow">↗</span>
        <div class="proj-icon">🍽️</div>
        <div class="proj-name">RestaurantFinder</div>
        <div class="proj-desc">Smart web app to discover and filter nearby restaurants. Clean UI with real-time filtering for a frictionless user experience.</div>
        <div class="proj-tags">
          <span class="proj-tag">HTML</span>
          <span class="proj-tag">CSS</span>
          <span class="proj-tag">JavaScript</span>
        </div>
      </a>

      <a class="proj-card" href="https://github.com/sanjeev-reddy-13/Flight_price_prediction" target="_blank">
        <span class="proj-arrow">↗</span>
        <div class="proj-icon">✈️</div>
        <div class="proj-name">Flight Price Prediction</div>
        <div class="proj-desc">ML model forecasting airline ticket prices using advanced feature engineering — helping travelers find the best time to book.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">Scikit-Learn</span>
          <span class="proj-tag">Feature Eng.</span>
        </div>
      </a>

    </div>
  </section>

  <!-- CERTIFICATIONS -->
  <section>
    <div class="section-head">
      <span class="section-num">04</span>
      <h2 class="section-title">Certifications</h2>
      <div class="section-line"></div>
    </div>
    <div class="cert-full-card">
      <div class="cert-full-left">
        <div class="cert-full-logo">
          <img src="https://upload.wikimedia.org/wikipedia/commons/5/57/ServiceNow_logo.svg" alt="ServiceNow" style="width:52px;height:auto;display:block;"/>
        </div>
        <div>
          <span class="cert-full-issuer">ServiceNow</span>
          <h3 class="cert-full-name">Certified System Administrator</h3>
          <span class="cert-full-code">CSA</span>
        </div>
      </div>
      <div class="cert-full-right">
        <div class="cert-verified-badge">
          <svg width="14" height="14" fill="none" viewBox="0 0 24 24" stroke="#34d399" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
          Verified
        </div>
        <p class="cert-full-desc">Demonstrates expertise in administering and configuring the ServiceNow platform — managing users, data, workflows, and UI policies across enterprise environments.</p>
        <div class="cert-skills">
          <span class="cert-skill-tag">ITSM</span>
          <span class="cert-skill-tag">Workflow Automation</span>
          <span class="cert-skill-tag">Platform Config</span>
          <span class="cert-skill-tag">Scripting</span>
          <span class="cert-skill-tag">Access Control</span>
        </div>
      </div>
    </div>
  </section>

  <!-- GITHUB STATS -->
  <section>
    <div class="section-head">
      <span class="section-num">05</span>
      <h2 class="section-title">GitHub stats</h2>
      <div class="section-line"></div>
    </div>

    <div class="stats-grid">

      <!-- Total Contributions -->
      <div class="stat-card">
        <div class="stat-label">Total contributions</div>
        <div class="stat-num" style="color:#79c0ff">76</div>
        <div class="stat-sub">Aug 10, 2024 – Present</div>
      </div>

      <!-- Current Streak (ring) -->
      <div class="stat-card stat-center">
        <div class="streak-ring">
          <svg viewBox="0 0 120 120" width="120" height="120">
            <circle cx="60" cy="60" r="50" fill="none" stroke="rgba(255,255,255,0.06)" stroke-width="8"/>
            <circle cx="60" cy="60" r="50" fill="none" stroke="#79c0ff" stroke-width="8"
              stroke-dasharray="314" stroke-dashoffset="220"
              stroke-linecap="round" transform="rotate(-90 60 60)"/>
          </svg>
          <div class="streak-inner">
            <span class="streak-flame">🔥</span>
            <span class="streak-num">3</span>
          </div>
        </div>
        <div class="stat-label" style="color:var(--accent);font-weight:500;margin-top:12px">Current streak</div>
        <div class="stat-sub">May 29 – May 31</div>
      </div>

      <!-- Longest Streak -->
      <div class="stat-card">
        <div class="stat-label">Longest streak</div>
        <div class="stat-num" style="color:#c4b5fd">3</div>
        <div class="stat-sub">May 29 – May 31</div>
      </div>

    </div>

    <!-- Language & Repo cards via GitHub readme stats -->
    <div class="gh-img-row">
      <div class="gh-img-card">
        <img src="https://github-readme-stats.vercel.app/api?username=sanjeev-reddy-13&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true&title_color=a0c4ff&icon_color=79c0ff&text_color=c9d1d9&bg_color=13131a" alt="Sanjeev's GitHub stats"/>
      </div>
      <div class="gh-img-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=sanjeev-reddy-13&layout=compact&theme=tokyonight&hide_border=true&title_color=a0c4ff&text_color=c9d1d9&bg_color=13131a" alt="Top languages"/>
      </div>
    </div>

  </section>

  <!-- CONNECT -->
  <!-- (renumber heading) -->
  <section>
    <div class="section-head">
      <span class="section-num">06</span>
      <h2 class="section-title">Let's connect</h2>
      <div class="section-line"></div>
    </div>
    <div class="connect-card">
      <div>
        <p class="connect-eyebrow">// Available for hire</p>
        <h2>Got a role<br>in mind?</h2>
        <p>I'm actively looking for full-time roles in ML Engineering, Backend Development, or Data Science. If you think I'd be a good fit — let's talk.</p>
      </div>
      <div class="connect-btns">
        <a class="cta-btn cta-primary" href="https://www.linkedin.com/in/nersi-sai-venkata-sanjeev-reddy-a8b777291/" target="_blank">
          <svg fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          Connect on LinkedIn
        </a>
        <a class="cta-btn cta-secondary" href="mailto:sanjeev.reddy2004@gmail.com">
          <svg fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75"/></svg>
          Drop a mail
        </a>
        <a class="cta-btn cta-secondary" href="https://sanjeev-reddy-13.github.io/MyPortfolio_website" target="_blank">
          <svg fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253"/></svg>
          See my work
        </a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span>sanjeev.reddy2004@gmail.com</span>
    <span>Hyderabad, India</span>
  </footer>

</div>
</body>
</html>
