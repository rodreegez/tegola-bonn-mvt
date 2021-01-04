# Tegola issue with jumping data at low zoom levels when using MVT

This repo uses the [Tegola Getting Started example](https://tegola.io/documentation/getting-started/) but converts it to using Mapbox Vector Tiles. The repo includes `index.html` which is the same as the example in the getting started guide. However, because the example doesn't have a basemap, the issue of jumping polygons is difficult to see. This repo therefore includes `index_mapbox.html` that loads a basic mapbox basemap and layers on the same data from the getting started guide. These layers are filled in solid black to help illustrate the issue.

## The issue

At low levels of zoom, the data drawn on the map starts to skew north. In this dataset, the effect is first noticible when zooming from level 7 to level 6. (The mapbox version of the map loggs the current zoom level to the javasctipt conosle to help illustrate this).

## Steps to reproduce

1. Clone this repo (it includes the Tegola v0.12.1 binary for Linux AMD 64 - you may wish to use another [release](https://github.com/go-spatial/tegola/releases)),
2. Follow the steps in the [getting started guide](https://tegola.io/documentation/getting-started/) to get the Bonn dataset loaded into PostGIS as described there.
3. Update the config with your database credentials.
4. Add your Mapbox API key in `index_mapbox.html`
5. Start the tegola server (from this repo simply run `tegola serve`) and open `index_mapbox.html` in your local browser.
6. Zoom out to zoom level 7 (open the javascript console to check what level you are currently on - level 7 is really quite far out).
7. Watch carefully and then zoom to level 6 - you'll notice the data start to jump northwards.

The issue is kind of difficult to notice as the data being shown at this level of zoom is hard to see, however it is definately happening, and is much more noticable with e.g. polygons covering larger areas.
