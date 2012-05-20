Carto 2.0
=====================

_Notes, sketches, and frameworks inspired by October 2011 map styling workshop held in SF_

===

#Goals:

1. CSS-like map design language. Syntax extends the foundation laid by Cascadenik and Carto (implied 1.0) and the power of Less.js
2. Better support for reference-style maps by formalizing the use of @variables for color swatches, graphic styles, and text character styles
3. Add support for thematic data cartography with data statistics like MIN, MAX, MEAN and use of those keywords in high-level filters that are under a dozen lines of code. Allow for both loose and hard connections between data and symbology.


#Result should be:

1. Reference documentation and examples that are compelling.
2. Syntax should be easy to write for average designer, reusable, and shareable. 
3. Syntax should be fast for the renderer draw. Text and shields are special cases we want to allow for. Mike put this as it's </div> friendly.
4. Should have reasonable style defaults / implementation routines that make sense for the designer and for the renderer. Reasonable defaults make it quick to explore a dataset (not just present the final results). Example: draw points to see a distribution, classify points, lines and polygons by thematic attribute and color quickly.
5. Core syntax is interoperable with other style languages. Extensions allow extra awesome things. 
6. Clearly identify ambiguities (and document recommended solutions).
7. Standard adhers to [Semantic Versioning](http://semver.org/). Watch background video ([youtube](http://www.youtube.com/watch?v=k2h2lvhzMDc)). _- MM and NVK add 18 May 2012._
8. First principles so it's easy to implement across software. _- NVK add 19 May 2012._

NOTE: Extensions might include data formats (csv, shp in zip), data statistics (count, min, max), data locations (local/remote/offline), experimental styling keywords (feature class heigherachy ala scalemaster.org?), styles with absolute and relative values (gradients, choropleth/quantiles/nat'lbreaks/etc, lighter, darker, smaller text, larger text), and rendering (like for shields?), interactivity (one layer, multiple layers).


#Atomic bits (nouns, verbs):

* **Object geometry type**: point, line, polygon, continuous-field aka raster. _Even the component polys, rings, & vertex_
* **CSS target**: anchor, stroke, fill, label/text, data
* **Rendering target** (optional/implied in 2.0): (pivots off geometry type) registration, edge, interior, LABEL, INTERACTIVITY. _With optional masks and positioning/attachment hints._
* **Ink with**: rgb, cmyk, hsv, gradient, image (with repeat options). _With alpha. All color spaces/images/gradient are coallpsed in "ink" in Carto 2.0_
* **Size by**: anchors, strokes, and labels have a 2d extrusion measurement (eg: 2px) _For images, the size is implied by a non-repeat dimension of the source image. Others are determined by default style CSS._


#Selectors, attachments, rules, filters, features, data.

* from cascadenik: **Filters** for feature attributes (FIELDNAME=value)
* from carto  1.0: **Attachments** (::) are a repeated version of the exact selection, but with a different appearance styling.
* new  carto  2.0: **Point geoms have an edge** available for stroking.
* new  carto  2.0: **Special rendering targets w/r/t attachemtns**: interior, edge, registration.
* new  carto  2.0: **Selectors** for object **geometry type** (point, line, polygon, raster) and _advanced_ **geometry components**: inner outer rings, vertex index and first, last. eg: _.classname geom_type_selector { ... }_
* new  carto  2.0: **Rendering/compositing targets** are implied but can be explicate or overridden: fill-, stroke-, anchor-, and data-. _Note: color:#hex is implied as fill-color:#hex._
* from carto  2.0: **Dependant attachments** (&&) depend on the previous bits being rendered in that selection. Useful for text labels to require the anchor symbolization being placed. eg: point&&stroke


#Reasonable defaults:

* Point: style="width:2px; color:#000000; cap:round;" --**or**-- { stroke-width:2px; stroke-color:#000000; cap:round; }
* Line: style="width:1px; color:#000000; cap:square;" --**or**-- { stroke-width:1px; stroke-color:#000000; cap:square; }
* Polygon: style="color:#eeeeee;" --**or**-- { fill-color:#eeeeee; }
* Raster: tk tk tk


#&etc

* What promises are we making, what is arbitrary up to the user?
* Set reasonable expectations


#Full details:

[Read more »](https://github.com/nvkelso/carto-css-map-styling/blob/master/full_details.md)


#Sketches

Basic:

![Carto2_basic](https://github.com/nvkelso/carto-css-map-styling/raw/master/images/carto_simple.png)

Medium:

![Carto2_medium](https://github.com/nvkelso/carto-css-map-styling/raw/master/images/carto_medium.png)

Complex:

![Carto2_complex](https://github.com/nvkelso/carto-css-map-styling/raw/master/images/carto_complex.png)