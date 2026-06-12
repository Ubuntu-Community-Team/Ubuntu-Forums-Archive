---
title: "VNC, Fesity, and a flood of windows"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by MKR. on 2007-04-29
I'm trying to connect to the VNC server that came with feisty (testing it for eventual use when wandering around the house), and this happened:

[http://i176.photobucket.com/albums/w186/herebepixels/crazyvnc.png](http://i176.photobucket.com/albums/w186/herebepixels/crazyvnc.png)

The output is:
> mkr@Ninjamatic:~$ vncviewer localhost:0
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "mkr@Ninjamatic"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 20000 kbit/s - changing to Hextile
Throughput 20000 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Throughput 20000 kbit/s - changing to Raw
CleanupSignalHandler called
ShmCleanup called


Nothing about the output seems to indicate a problem, and I haven't made any changes to the VNC configuration, so I don't know what's going on.

---

### Post by bmathis on 2007-04-29
It looks like you're connecting to the localhost instead of another machine which is probably the reason for the "2 mirrors facing each other" look. Try connecting from a different computer.

---

