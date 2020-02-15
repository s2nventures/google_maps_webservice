# google_maps_webservice

[![Build Status](https://travis-ci.org/lejard-h/google_maps_webservice.svg?branch=master)](https://travis-ci.org/lejard-h/google_maps_webservice)
[![codecov](https://codecov.io/gh/lejard-h/google_maps_webservice/branch/master/graph/badge.svg)](https://codecov.io/gh/lejard-h/google_maps_webservice)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/HLejard?locale.x=fr_FR)

Google Maps Web Services [API](https://developers.google.com/maps/web-services)

## API key

To use this library you need a ***Web*** API key. [Here](https://developers.google.com/places/web-service/get-api-key)

This is not compatible with Android and iOS API key but can be use inside a Flutter app.

## Availables API

- [x] [Geocoding](https://developers.google.com/maps/documentation/geocoding/start)
- [ ] [Places](https://developers.google.com/places/web-service/)
    - [x] nearby search
    - [x] text search
    - [x] details
    - [ ] add
    - [ ] delete
    - [x] photo
    - [x] autocomplete
    - [x] queryautocomplete
- [x] [Directions](https://developers.google.com/maps/documentation/directions/)
- [x] [Distance Matrix](https://developers.google.com/maps/documentation/distance-matrix/)
- [ ] [Geolocation](https://developers.google.com/maps/documentation/geolocation/intro)
- [ ] [Elevation](https://developers.google.com/maps/documentation/elevation/start)
- [ ] [Roads](https://developers.google.com/maps/documentation/roads/intro)
- [x] [Timezone](https://developers.google.com/maps/documentation/timezone/start)


## Usage

### Geocoding

```dart
import "package:google_maps_webservice/geocoding.dart";

final geocoding = new GoogleMapsGeocoding(apiKey: "<API_KEY>");
final geocoding = new GoogleMapsGeocoding(apiKey: "<API_KEY>", httpClient: new BrowserClient());
final geocoding = new GoogleMapsGeocoding(baseUrl: "http://myProxy.com");

GeocodingResponse response = await geocoding.searchByAddress("1600 Amphitheatre Parkway, Mountain View, CA");
```

### Places

```dart
import "package:google_maps_webservice/places.dart";

final places = new GoogleMapsPlaces(apiKey: "<API_KEY>");
final places = new GoogleMapsPlaces(apiKey: "<API_KEY>", httpClient: new BrowserClient());
final places = new GoogleMapsPlaces(baseUrl: "http://myProxy.com");

PlacesSearchResponse reponse = await places.searchNearbyWithRadius(new Location(31.0424, 42.421), 500);
PlacesSearchResponse reponse = await places.searchNearbyWithRankby(new Location(31.0424, 42.421), "distance");
PlacesSearchResponse reponse = await places.searchByText("123 Main Street");

PlacesDetailsResponse response = await places.getDetailsByPlaceId("PLACE_ID");
PlacesDetailsResponse response = await places.getDetailsByReference("REF");
```

### Timezone

```dart
import "package:google_maps_webservice/timezone.dart";

final timezone = new GoogleMapsTimezone(apiKey: "<API_KEY>");
final timezone = new GoogleMapsTimezone(apiKey: "<API_KEY>", httpClient: new BrowserClient());
final timezone = new GoogleMapsTimezone(baseUrl: "http://myProxy.com");

TimezoneResponse response = await timezone.getByLocation(new Location(31.0424, 42.421));
TimezoneResponse response = await timezone.getByLocation(new Location(31.0424, 42.421), timestamp: DateTime.utc(2019, 4, 24));
TimezoneResponse response = await timezone.getByLocation(new Location(31.0424, 42.421), timestamp: DateTime.utc(2019, 4, 24), language: 'es');
```

### Proxy

In case of using a proxy the baseUrl can be set.
The apiKey is not required in case the proxy sets it. (Not storing the apiKey in the app is good practice)

### Feature Requests and Issues

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: https://github.com/lejard-h/google_maps_webservice/issues/new
