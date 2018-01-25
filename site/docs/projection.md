---
layout: docs
menu: docs
title: Projection
permalink: /docs/projection.html
---
## Projection Overview
A cartographic projection maps longitude and latitude pairs to x, y coordinates. As with Vega, one can use projections in Vega-lite to layout both geographic points (such as locations on a map) represented by longitude and latitude coordinates, or to project geographic regions (such as countries and states) represented using the GeoJSON format. Projection's are specified at the unit specification level, alongside encoding.

For example, this example chart shows all airports in the United States by projecting `latitude`, `longitude` as `x`, `y` coordinates using the albersUsa projection.

<span class="vl-example" data-name="geo_point"></span>

{:#properties}
## Projection Properties
{% include table.html props="type,clipAngle,clipExtent,center,rotate,precision" source="Projection" %}

If you want to explore the various available properties in more depth, Vega's projection documentation [hosts a useful demo](https://vega.github.io/vega/docs/projections/)

In addition to the shared properties above, the following properties are supported for specific projection types in the [d3-geo-projection](https://github.com/d3/d3-geo-projection) library: [`coefficient`](https://github.com/d3/d3-geo-projection#hammer_coefficient), [`distance`](https://github.com/d3/d3-geo-projection#satellite_distance), [`fraction`](https://github.com/d3/d3-geo-projection#bottomley_fraction), [`lobes`](https://github.com/d3/d3-geo-projection#berghaus_lobes), [`parallel`](https://github.com/d3/d3-geo-projection#armadillo_parallel), [`radius`](https://github.com/d3/d3-geo-projection#gingery_radius), [`ratio`](https://github.com/d3/d3-geo-projection#hill_ratio), [`spacing`](https://github.com/d3/d3-geo-projection#lagrange_spacing), [`tilt`](https://github.com/d3/d3-geo-projection#satellite_tilt).

*Note*: All [properties](#properties) of projections are **optional** with defaults as defined in the [Vega projection properties](https://vega.github.io/vega/docs/projections/#properties). Because of this, marks that don't have explicitly defined projections may implicitly derive a projection. Implicit projections will be added for any [`geoshape`](geoshape.html) mark or any mark that has fields of type [`latitude`](type.html#latitude), [`longitude`](type.html#longitude), or [`geojson`](type.html#geojson)


{:#projection-types}
## Projection Types

Vega-lite includes all cartographic projections provided by the [d3-geo](https://github.com/d3/d3-geo#) library.

| Type          | Description   |
| :------------ |:------------- |
| [albers](https://github.com/d3/d3-geo#geoAlbers)          | The Albers’ equal-area conic projection. This is a U.S.-centric configuration of `"conicEqualArea"`. |
| [albersUsa](https://github.com/d3/d3-geo#geoAlbersUsa) | A U.S.-centric composite with projections for the lower 48 states, Hawaii, and Alaska (scaled to 0.35 times the true relative area). |
| [azimuthalEqualArea](https://github.com/d3/d3-geo#geoAzimuthalEqualArea) | The azimuthal equal-area projection. |
| [azimuthalEquidistanct](https://github.com/d3/d3-geo#geoAzimuthalEquidistant) | The azimuthal equidistant projection. |
| [conicConformal](https://github.com/d3/d3-geo#geoConicConformal) | The conic conformal projection. The parallels default to [30&deg;, 30&deg;] resulting in flat top. |
| [conicEqualArea](https://github.com/d3/d3-geo#geoConicEqualArea) | The Albers’ equal-area conic projection. |
| [conicEquidistant](https://github.com/d3/d3-geo#geoConicEquidistant) | The conic equidistant projection. |
| [equirectangular](https://github.com/d3/d3-geo#geoEquirectangular) | The equirectangular (plate carr&eacute;e) projection, akin to use longitude, latitude directly. |
| [gnomonic](https://github.com/d3/d3-geo#geoGnomonic) | The gnomonic projection. |
| [mercator](https://github.com/d3/d3-geo#geoMercator) | The spherical Mercator projection. Uses a default `clipExtent` such that the world is projected to a square, clipped to approximately ±85&deg; latitude. |
| [orthographic](https://github.com/d3/d3-geo#geoOrthographic) | The orthographic projection. |
| [stereographic](https://github.com/d3/d3-geo#geoStereographic) | The stereographic projection. |
| [transverseMercator](https://github.com/d3/d3-geo#geoTransverseMercator) | The transverse spherical Mercator projection. Uses a default `clipExtent` such that the world is projected to a square, clipped to approximately ±85&deg; latitude. |

{:#config}
## Projection Configuration

{: .suppress-error}
```json
// Top-level View Specification
{
  ...,
  "config": {          // Configuration Object
    "projection": { ... },   // - Projection Configuration
    ...
  }
}
```

The `projection` property of the [`config`](config.html) object determines the default properties and transformations applied to different types of [projections](projection.html).
The projection config can contain any of the projection properties [as specified above](#properties).