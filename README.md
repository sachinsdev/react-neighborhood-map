# Neighborhood Map: Orlando Attractions

A React single page app that shows Orlando area amusement parks and attractions on a Google Map. Places are loaded live from the Foursquare API, and you can filter them, open details with photos, and keep using the app offline once it has loaded.

Built in 2018 as the final project for Udacity's Front End Web Developer Nanodegree.

## Features

* **Live place data:** fetches nearby attractions from the Foursquare Venues API (`venues/explore`) and plots each one as a Google Maps marker.
* **Filter as you type:** a search box filters the list and the map markers together by name.
* **Info windows with photos:** clicking a marker or list item pans the map, bounces the marker and opens an info window with the venue's address and a Foursquare photo.
* **Two level caching:** venue photos are cached in memory and in `localStorage`, so repeat visits don't use up the Foursquare API quota.
* **Offline support:** a service worker caches the app shell, so it still loads without a connection.
* **Error handling:** clear messages when the map or Foursquare fails to load or the API rate limit (HTTP 429) is reached, plus a fallback image when a photo can't be retrieved.
* **Responsive and accessible:** the search pane collapses behind a menu button on small screens, and the UI uses ARIA roles and labels plus keyboard focus support.

## Tech

* React 16 (Create React App)
* Google Maps JavaScript API
* Foursquare Places API (v2)
* Service Worker and `localStorage`
* JavaScript (ES6+), CSS

## How it is structured

The app was written as small React components, with the Google Maps objects wrapped so React controls when they are created and updated.

```
src/
  App.js                    state, Foursquare calls, photo caching, marker animation
  components/
    MapContainer.js         hosts the map, markers and the shared info window
    GoogleMap.js            loads the Google Maps script and creates the map
    Marker.js               wraps google.maps.Marker
    InfoWindow.js           wraps google.maps.InfoWindow
    SearchPane.js           side panel with search box and results list
    SearchPlace.js          filter input
    SearchList.js / SearchItem.js   results list
    NavigationBar.js        menu button that shows or hides the search pane
    Place.js                place model
  helpers/
    PlacesAPI.js            Foursquare explore and venue photo requests
    CacheManager.js         localStorage cache
    JSHtmlWrappers.js       info window content, error display and logging
  registerServiceWorker.js
```

## Running it

This repository contains the production build. To serve it locally:

```
npx serve .
```

Then open the URL it prints, usually http://localhost:3000.

## Status

This project is archived and kept as a record of my nanodegree work. Foursquare has since retired the v2 API this app calls, so live place data may no longer load.
