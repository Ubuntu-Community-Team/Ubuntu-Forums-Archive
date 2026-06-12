---
title: "WMS server Exception"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by bijay_panda on 2009-02-16
Hi All,
I am using qgis 1.0.0 in ubuntu 8.04.Actually i want to add a WMS layer to an existing map.But i m getting an error like below

Could not draw DM Solutions GMap because:
(No error code was reported)
The WMS vendor also reported: 
msDrawMap(): Image handling error. Unable to initialize image.
msCalculateScale(): General error message. Invalid image extent, minx=nan, miny=nan, maxx=nan, maxy=nan.

Tried URL: [http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&BBOX=-148.059000,35.882000,-33.774500,72.550300&SRS=EPSG:4326&WIDTH=1&HEIGHT=1&LAYERS=road&STYLES=&FORMAT=image/gif&TRANSPARENT=TRUE](http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&BBOX=-148.059000,35.882000,-33.774500,72.550300&SRS=EPSG:4326&WIDTH=1&HEIGHT=1&LAYERS=road&STYLES=&FORMAT=image/gif&TRANSPARENT=TRUE)

Please any one help me out.
Thanks in advance.
Bijay

---

### Post by blastus on 2009-02-21
Why are you using a width and height of 1x1 pixel? Send a request like this with a width and height of say 256x256...

[http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&BBOX=-148.059000,35.882000,-33.774500,72.550300&SRS=EPSG:4326&WIDTH=256&HEIGHT=256&LAYERS=road&STYLES=&FORMAT=image/gif&TRANSPARENT=TRUE](http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetMap&BBOX=-148.059000,35.882000,-33.774500,72.550300&SRS=EPSG:4326&WIDTH=256&HEIGHT=256&LAYERS=road&STYLES=&FORMAT=image/gif&TRANSPARENT=TRUE)

To find out more information about that server hit this...

[http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetCapabilities](http://www2.dmsolutions.ca/cgi-bin/mswms_gmap?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetCapabilities)

---

