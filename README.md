# Strange Ground

A field guide to the eerie and historical ground nearby.

Strange Ground maps the *interesting* points of interest around wherever you
physically are — myths, legends, murder sites, old graves, ghost stories, ruins,
barrows, war relics and the like — rather than bars, shops and amenities. It uses
your device's location, finds everything notable within a chosen radius, and plots
it on a dark ordnance-survey-style map with a filterable key.

It's a single, self-contained HTML file. No build step, no backend, no dependencies
to install.

## How it works

All data is fetched live in the browser from two free, open sources and merged:

- **Wikipedia geosearch** — every geotagged article within the radius, filtered
  down to historical and mysterious subjects and sorted into categories
  (crime, folklore, war, ancient, graves, ruins, monuments).
- **OpenStreetMap (Overpass API)** — physical features that often have no article:
  pillboxes, bunkers, war memorials, old crosses, tombs, ruins, archaeological sites.

Duplicates are collapsed, results are sorted by distance, and each site links back
to its source.

## Running it

Because it relies on browser geolocation, it must be served over **HTTPS** (or
`localhost`) — `file://` and plain `http://` will have location blocked by mobile
browsers.

- **Quickest:** host it on GitHub Pages / Cloudflare Pages / Netlify (all free,
  all HTTPS by default). See deployment below.
- **Local testing:** from this folder run `python3 -m http.server` and open
  `http://localhost:8000`. Desktop browsers allow location on localhost.

## Deploying to GitHub Pages

1. Create a new repository on GitHub (e.g. `strange-ground`).
2. Upload these files (`index.html`, `README.md`, `LICENSE`) and commit.
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a
   branch**, choose branch `main` and folder `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/strange-ground/`.

## Known limitations

- Pure folklore with no Wikipedia article (un-documented local ghost stories,
  obscure murders) doesn't exist as structured data and won't appear. The intended
  fix is a hand-curated GeoJSON layer added as a third source.
- Wikipedia, Overpass and the CARTO map tiles all have fair-use limits. Fine for
  personal use; a public, high-traffic version would need its own caching backend.

## Roadmap

- A curated GeoJSON layer for hand-collected sites.
- Additional sources (Historic England listed buildings / scheduled monuments,
  the Megalithic Portal, war-memorial registers).
- A backend to save and submit sites and cache Overpass results.
- AI-generated atmospheric "field notes" for each location.

## Credits

- Map data © OpenStreetMap contributors
- Article content from Wikipedia
- Map tiles by CARTO
- Mapping by Leaflet

## Licence

MIT — see [LICENSE](LICENSE).
