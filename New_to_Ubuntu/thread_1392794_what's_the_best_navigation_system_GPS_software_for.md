---
title: "what's the best navigation system GPS software for LINUX for Europe?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-28
Hello

I found this one, but [http://linux-7110.sourceforge.net/screenshots/screendumpnet_04.png](http://linux-7110.sourceforge.net/screenshots/screendumpnet_04.png)
this one is only for US. Is there something for linux for Europe.

Cheers

---

### Post by J V on 2010-01-28
tomtom runs on linux :)

but seriously, planning on getting drugged kidnapped and sent to mexico in a suitcase without them stealing your laptop much?

---

### Post by Hospadar on 2010-01-28
I like tango gps, it uses openstreetmap maps, which may or may not be good for your area.  Where I live in michigan in the US the maps are pretty decent, definitely good enough to get me in the right area.  It does need a constant internet connection, and I don't know of any linux open-source gps programs that don't.  The reason for this is that rendering the maps based on geo data is somewhat tricky, so most apps just download tiles from openstreetmap or someone else, and a full set of tiles of even a small area is a huge amount of data.

The package name is tangogps, they also have a website for you to google.

---

### Post by newkirk on 2010-01-30
> **Hospadar said:**
> I like tango gps, it uses openstreetmap maps, which may or may not be good for your area.  Where I live in michigan in the US the maps are pretty decent, definitely good enough to get me in the right area.  It does need a constant internet connection, and I don't know of any linux open-source gps programs that don't.  The reason for this is that rendering the maps based on geo data is somewhat tricky, so most apps just download tiles from openstreetmap or someone else, and a full set of tiles of even a small area is a huge amount of data.

The package name is tangogps, they also have a website for you to google.

Actually TangoGPS can predownload.  If you right-click on the map view the bottom option in the context menu is 'Map Download'.  Choose that and it asks you how may zoom levels you want to retrieve, with an estimate of the space it will use.  I've been using tangoGPS on my FreeRunner for quite some time now, with about 3gb of map tiles downloaded and saved in advance covering about two states. (southeast USA, NC & VA) 

Manually zoom and drag until the view covers the entire region you want, and then select the map download and get several additional zoom levels.  Manually zoom in on more important points and download closer zoom levels if desired.  You can zoom in on a portion of the expected route for a longer trip and download closer zooms, then drag to the next section of the route and repeat - this can save a huge amount of download time and space by skipping portions of the zoomed-out rectangle outside your travel route.  (You might want to go to 'Config' tab and 'Edit' the current map repository, and ensure that the designated cache dir points somewhere with sufficient free space) 

More recently I've been playing with it on my netbook, but plan in a few weeks to build an in-dash touchscreen system and want to have the option of turn-by-turn navigation instead of just mapping my location...  Unfortunately all I've found for linux with GPS is mapping, not navigation.

Apart from not offering navigation prompting, TangoGPS is a great program, I highly recommend it.  And it's great that it's in the standard Ubuntu feeds these days.  Unfortunately the one in the feeds is currently 0.9.6, while 0.99.2 is the actual latest version right now.  Get that one in .deb package at tangogps.org.

j

---

### Post by newkirk on 2010-01-30
Oh, and the newer (post-ubuntu-feed) versions are starting to support route planning.  You can input two locations (GPS coords only right now, but you can click the map for each point or use GPS for the starting point) and it will retrieve a proposed travel route from one of three online servers.

j

---

