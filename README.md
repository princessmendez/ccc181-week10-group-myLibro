# CCC181 Week 10: CampusConnect Mobile-First Login Page

React + TypeScript starter for the Week 10 group activity. The page is already
built. Your group's job is the **mobile-first CSS** and the **GitHub teamwork**.

## Run it

```bash
npm install
npm run dev          # open the local URL it prints
npm run dev:phone    # same, but your phone (same Wi-Fi) can open the Network URL
npm run build        # must finish with no errors before you submit
```

## Rules

- Edit only the CSS files in `src/styles/` (one member = one file). Do not edit `reset.css`.
- Plain CSS only. No Tailwind, Bootstrap, Material UI, styled-components, or any UI library.
- Phone styles first (no media query), then `min-width` queries only. Never `max-width`.
- Do not edit the `.tsx` files or rename classes. If you must, tell the group first.

## Group information (fill in)

| Item | Your answer |
| --- | --- |
| Group number | myLibro |
| Section |IT3-B |
| Repository URL | https://github.com/princessmendez/ccc181-week10-group-myLibro.git |

## Members (each member fills in their own row in their own commit)

| Member | Name | GitHub username | CSS file | What I did |
| --- | --- | --- | --- | --- |
| 1 (leader) | Princess Beth R. Mendez | princessmendez | `base.css` | I edited src/styles/base.css using a mobile-first approach with CSS Grid and rem units, and added the viewport meta tag to index.html. On phones, the layout is a single column with a full-width .container (1rem side padding) and a centered brand panel with a 1.75rem heading and hidden perks list. At 768px and up, the container padding grows to 2rem and the brand panel gets more padding. At 1024px and up, the layout becomes two equal columns (brand panel left, login card right), the heading grows to 2.5rem, and the perks list appears. At 1280px and up, .container stops at max-width: 1200px and is centered. |
| 2 | Jonathan S. Geronimo Jr.| Jansoiiiey | `nav.css` | I edited src/styles/nav.css. On phones, the navbar uses Flexbox in a column with the brand on top and links stacked, all at least 48px tall with :hover and :focus-visible styles (--navy-hover and a gold outline), while the footer uses CSS Grid in one column with gold titles and 48px links. At 768px and up, the navbar becomes a row with the brand on the left and links on the right, and .nav-list lines up in one row. At 1024px and up, .footer-grid becomes three equal columns. Nothing changes at 1280px since .container (Member 1) handles centering. |
| 3 | Nicanor Gabriel S. Damalerio | nicanorgabrieldamalerio-debug | `form.css` | I edited src/styles/form.css, using Flexbox to style the login card, fields, and buttons. On phones, the card is full width with a single column, 48px inputs, and full-width buttons with :hover and :focus-visible styles. At 768px and up, the card is centered with a 32rem max width and the alternative buttons sit side by side. At 1024px and up, padding and title size increase, and 1280px needs no new rules because .container (Member 1) handles centering. |

## Experiment 0: the page without the viewport tag

What did the page look like in DevTools phone mode **before** adding the viewport meta tag?
What changed **after** adding it?

> Before adding the viewport meta tag:
In DevTools phone mode, the page looked like a zoomed-out desktop site. The mobile browser assumed a default layout width of about 980px and then shrank everything to fit the 360px screen, so the text, buttons, and login card appeared tiny and hard to read. The media queries (like min-width: 768px) also behaved unexpectedly because the browser reported a wider viewport than the real device width.

> After adding the viewport meta tag:
The page now uses the real device width (width=device-width) at 100% scale (initial-scale=1). Text and form fields are readable without zooming, the login card fits the screen, and the layout switches to the mobile version correctly because the media queries now match the actual 360px width.

## DevTools test results

| Width | What must be true | Pass? |
| --- | --- | --- |
| 360 px | 1 column. Nav links stacked and 48px tall. Options and buttons stacked. Footer in 1 column. No sideways scrollbar. | Passed |
| 768 px | Nav in one row (brand left, links right). Checkbox and link in one row. Two buttons side by side. | Passed |
| 1024 px | Brand panel and login card side by side. Footer in 3 columns. Heading is larger. | Passed |
| 1280 px | Content centered and stops at 1200px. | Passed |

### Breakpoints I observed

Using **Show media queries** and dragging slowly from 360 px to 1280 px, the layout changed at these exact widths:

Nav
> Using Show media queries and dragging slowly from 360px to 1280px, the layout changed at exactly 768px and 1024px. At 768px, the navbar switched from a column to a row, with the brand on the left and the links in a single row on the right. At 1024px, the footer grid changed from one column to three equal columns. Nothing changed at 1280px. No width looked broken.

Form
> Using Show media queries and dragging slowly from 360px to 1280px, the layout changed at exactly 768px and 1024px. At 768px, the card centered at a 32rem max width, the checkbox and link split left and right, and the two alternative buttons sat side by side. At 1024px, the card padding and title size increased. Nothing changed at 1280px. No width looked broken.

Base
> Using Show media queries and dragging slowly from 360px to 1280px, the layout changed at exactly 768px, 1024px, and 1280px. At 768px, the container side padding grew to 2rem and the brand panel got more padding. At 1024px, the layout became two columns (brand panel left, login card right), the heading grew to 2.5rem, and the perks list appeared. At 1280px, the container stopped at a max-width of 1200px and became centered. No width looked broken.

Screenshots are in `screenshots/` as `360.png`, `768.png`, `1024.png`, `1280.png`.

## What our group learned (leader writes this last)

> Our group learned that designing for phones first makes responsive CSS simpler. We wrote the phone layout with no media query, then used only min-width queries at 768px, 1024px, and 1280px to add complexity as the screen grew. This was easier than shrinking a desktop layout down, because each breakpoint only added or adjusted rules instead of undoing them. We also learned how much the viewport meta tag matters. Without it, the phone view looked like a tiny zoomed-out desktop page and our media queries did not match the real 360px width. Adding it made the page readable and made the breakpoints work as expected.Splitting the CSS into three files (base.css, nav.css, form.css) taught us how layout responsibility can be shared. Member 1’s .container handled the max-width and centering at 1280px, so Members 2 and 3 did not need extra rules there. Using Flexbox for the navbar and form and CSS Grid for the page and footer layouts showed us that each tool fits different jobs. Using rem units and 48px minimum touch targets also helped keep the page readable and easy to tap on a phone. On the teamwork side, we practiced working in one GitHub repository with each member editing only their own file and filling in their own README row in their own commit. This kept us from overwriting each other’s work and gave us clear commit history. The main challenge was coordinating so our separate files still worked together, which we solved by testing at 360px, 768px, 1024px, and 1280px in DevTools.


## How to run?

backend
> # Part 2: Express backend login

## How to run

You need two terminals open at the same time.

**Terminal 1: backend (folder `server`)**

```bash
cd server
npm install
copy .env.example .env
npm start
```

You should see `API running on http://localhost:3000`.

**Terminal 2: front end (project root)**

```bash
npm install
copy .env.example .env
npm run dev
```

Open http://localhost:5173. The health check is http://localhost:3000/api/v1/health and must return `{"status":"ok"}`.

The real `.env` files are never committed. Only the two `.env.example` files (with fake values) are in the repo.

## API summary

| Method | Path | Success | Errors |
|---|---|---|---|
| GET | `/api/v1/health` | 200 `{"status":"ok"}` | none |
| POST | `/api/v1/sessions` | 200 `{token, user}` | 400 missing fields, 401 `Invalid email or password.` |
| GET | `/api/v1/users/me` | 200 user (needs `Authorization: Bearer <token>`) | 401 `Not logged in.` |

Other answers: unknown route is 404 `{"error":"Not found."}`, a crash is 500 `{"error":"Something went wrong."}`. Full details are in `docs/API-SPEC.md`. The Postman collection is in `docs/postman/CampusConnect.postman_collection.json`.

**Demo account:** `student@campusconnect.test` / `Campus26` (name: Demo Student)

## Who did what (Part 2)

| Member | Name | GitHub | What I did in Part 2 |
|---|---|---|---|
| 1 | Princess Beth R. Mendez | princessmendez | Set up `server/` (Express, dotenv, CORS, JSON). Built `POST /api/v1/sessions` with validation, bcryptjs password check, 1-hour JWT and the hashed demo user. |
| 2 | Jonathan S. Geronimo | Jansoiiiey |Built `GET /api/v1/users/me` with the token middleware, the 404 and 500 handlers, `docs/API-SPEC.md` (with the events design), the Postman collection and the Postman screenshots. Reviewed the Member 1 pull request. |
| 3 | | | |
