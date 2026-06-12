---
title: "Problems with ogr2ogr"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by jdshelby on 2010-09-16
Hi All,

I'm working on a GIS project, and I need to convert a bunch of shapefiles into KML.  I followed the instruction found here: [http://code.google.com/apis/kml/articles/vector.html](http://code.google.com/apis/kml/articles/vector.html)    . I downloaded and installed GDAL (sudo apt-get install gdal-bin) and then used this syntax (my file is named Burkina.shp): ogr2ogr -f "KML" Burkina.kml Burkina.shp.

I get an error that reads: 

 Unable to open Burkina.shx or Burkina.SHX.
FAILURE:
Unable to open datasource `Burkina.shp' with the following drivers.
  -> ESRI Shapefile
  -> MapInfo File
  -> UK .NTF
  -> SDTS
  -> TIGER
  -> S57
  -> DGN
  -> VRT
  -> REC
  -> Memory
  -> BNA
  -> CSV
  -> GML
  -> GPX
  -> KML
  -> GeoJSON
  -> Interlis 1
  -> Interlis 2
  -> GMT
  -> SQLite
  -> ODBC
  -> PGeo
  -> OGDI
  -> PostgreSQL
  -> MySQL
  -> XPlane
  -> AVCBin
  -> AVCE00
I'm gonna keep banging away at it, but I'd appreciate any help, since it's for work!

THanks a bunch in advance
J.

---

