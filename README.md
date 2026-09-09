# Makwana Family - Ganpati invitation (Kailash design)

A self-contained copy of the invitation website published from the InviteO
editor. It is a static site: no database, no API, no environment variables.
Everything a guest's phone loads is in this folder.

## What is inside

| Path | What it is |
|---|---|
| `index.html` | The invitation page. Your content is the `window.__INVITE__` JSON in its `<head>`. |
| `t/kailash/` | The built Kailash design (JavaScript, CSS, artwork). Do not rename this folder: the page loads it from `/t/kailash/`. |
| `media/photos/` | The six gallery photographs you uploaded. |
| `media/music/ganpati-aale.m4a` | The background track. |
| `assets/hero-invite.jpg` | The card WhatsApp shows when the link is shared. |
| `vercel.json` | Clean URLs, cache headers, and `/i/<anything>` serving the same page. |

## Deploy to Vercel

1. Install the Vercel CLI once: `npm i -g vercel` (or use `npx vercel`).
2. From inside this folder run:

       vercel --prod

   Accept the defaults. There is no build step and no output directory to set.
   Vercel serves the folder as-is. You can also push this folder to a Git
   repository and import it in the Vercel dashboard with framework "Other".

3. Put your real address into the share tags. `index.html` carries the
   placeholder `https://your-domain.vercel.app` in three places (canonical,
   `og:url`, `og:image`). WhatsApp needs the absolute address to show the
   preview card. Replace it with the domain Vercel gave you, for example:

       sed -i '' 's#https://your-domain.vercel.app#https://makwana-ganpati.vercel.app#g' index.html
       vercel --prod

The invitation is then live at `https://<your-domain>/` and also at
`https://<your-domain>/i/invite-aa3b6c`.

## Changing the content

Open `index.html` and edit the JSON inside `window.__INVITE__` (family name,
dates, programme, venue, gallery). Photo entries point at files in
`media/photos/`; drop new photographs there and update the paths. Redeploy
with `vercel --prod`.

This copy is a snapshot. Edits made later in the InviteO editor do not reach
it. The page keeps `<meta name="robots" content="noindex">` so search engines
leave a family invitation alone; guests with the link see it as usual.
