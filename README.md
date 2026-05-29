# Seokbeom Kwon — Personal Site

A modern, editorial-style academic homepage. Built with plain HTML, CSS, and a tiny bit of JS so it deploys to GitHub Pages with zero configuration.

---

## What's in here

```
site/
├── index.html              ← Home (hero, research, updates, recruit CTA)
├── research.html           ← Detailed research areas
├── publications.html       ← Filterable publication list
├── students.html           ← Prospective student page
├── cv.html                 ← CV summary + PDF link
├── contact.html            ← Contact details
├── assets/
│   ├── css/main.css        ← Design system + all styles
│   ├── js/main.js          ← Nav, scroll reveal, filtering
│   └── images/             ← Drop profile photo here
└── README.md
```

## Quick local preview

```bash
cd site
python3 -m http.server 8000
# open http://localhost:8000
```

Or just double-click `index.html` — it works offline too.

---

## Deploy to GitHub Pages (5 minutes)

### One-time setup

1. **Create a GitHub repo.** Recommended name: `seokbeomkwon.github.io` (this gives you a clean URL: `https://seokbeomkwon.github.io`). Or use any other name — your site will live at `https://seokbeomkwon.github.io/<repo-name>/`.

2. **Push these files.** From the `site/` folder:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/seokbeomkwon/seokbeomkwon.github.io.git
   git push -u origin main
   ```

3. **Enable GitHub Pages.** In the repo on GitHub:
   - Settings → Pages
   - Source: **Deploy from a branch**
   - Branch: **main** / **root (/)**
   - Save

4. Wait ~1 minute. Your site is live.

### Custom domain (optional)

If you want `skwon.kaist.ac.kr` or similar:
1. Settings → Pages → Custom domain → enter your domain.
2. Add a `CNAME` record at your DNS provider pointing to `seokbeomkwon.github.io`.
3. Check "Enforce HTTPS".

KAIST IT may host academic personal domains — worth asking.

---

## Redirect from the old Google Site

Keep your Google Site live but point visitors to the new one. Edit the home page on the Google Site and add an embed block with this:

```html
<div style="text-align:center; padding:2rem; font-family:sans-serif;">
  <p style="font-size:18px;">This site has moved.</p>
  <p>
    <a href="https://seokbeomkwon.github.io" style="font-size:20px;">
      seokbeomkwon.github.io →
    </a>
  </p>
</div>
<script>
  setTimeout(() => location.href = "https://seokbeomkwon.github.io", 2500);
</script>
```

---

## How to update content

Every page is plain HTML. Open the file, find the section, edit the text. A few common edits:

### Add your profile photo

1. Drop a square or 4:5 photo at `assets/images/profile.jpg`.
2. In `index.html`, find the `.hero-photo` block and replace the placeholder `<div class="placeholder">…</div>` with:
   ```html
   <img src="assets/images/profile.jpg" alt="Seokbeom Kwon">
   ```

### Add a new publication

Open `publications.html`. Copy any `<li data-tags="…">` block and paste at the top of `<ul class="pub-list">`. Edit:
- `<span class="year">` → year
- `<span class="venue">` → journal (add class `tier-1` for top venues)
- `<p class="title">` → paper title
- `<span class="authors">` → authors (wrap your own name in `<span class="me">Kwon, S.</span>`)
- `<div class="links">` → link to the paper
- `data-tags` → space-separated tags. Used: `solo`, `coauth`, `tier1`, `2024-25`, `2020-23`

### Add a new update on the home page

Open `index.html`, find the `<div class="updates">` block. Copy any `<div class="update">` and paste at the top. Tag classes available:
- `tag publish` (blue, for publications)
- `tag award` (gold, for awards)
- `tag grant` (green, for grants)

### Change the accent color

Open `assets/css/main.css`. Top of the file, in `:root`, edit:
```css
--accent:      #2147D9;   ← change this
--accent-deep: #1933A8;   ← and this (a darker shade)
--accent-soft: #E8EDFD;   ← and this (a much lighter tint)
```

For KAIST blue, try: `#004191` / `#002A66` / `#E0E8F5`.

---

## Design notes

- **Fonts**: Instrument Serif (display) + Geist (body) + Geist Mono (eyebrows / numerals). Loaded from Google Fonts.
- **Type scale**: display headings use serif italic for accent words (`<em>`). Eyebrow labels use mono with section numbers (01, 02…).
- **Color**: warm off-white background (`#FBFAF7`), warm black text, single blue accent. No gradients.
- **Layout**: 1140 px max width, generous vertical rhythm, two-column section heads collapse on mobile.
- **Motion**: subtle fade-up on scroll via `IntersectionObserver`. Respects `prefers-reduced-motion`.

---

## Browser support

Modern evergreen browsers (Chrome, Safari, Firefox, Edge). Backdrop blur on the header degrades gracefully.

---

## License

Content © Seokbeom Kwon. Site template is free for personal use; attribution welcome.
