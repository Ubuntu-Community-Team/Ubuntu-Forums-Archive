---
title: "Dark camera in Skype 2.0.72"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by bubbhasdance on 2009-06-25
My Skype works perfectly, with no hassles, except for a very, very dark camera. Whenever I call people, they say that they cannot see me, just a silhouette, mostly. I have to get 1-2 lamps for them to be able to see me, and it's still not great. It wasn't a problem in Vista, so I think the problem must be the OS. Is there any way to remedy this? Thanks in advance! :D

---

### Post by gradinaruvasile on 2009-06-25
What camera is it? Post the output of 
lsusb

in a terminal.

---

### Post by bubbhasdance on 2009-06-25
Bus 002 Device 004: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

This is it. I had to go through a number of commands to get it to work in Skype, and have to do certain things to be able to call people (close all other programs using audio at the time), but that's no problem, I can live with that.

---

### Post by gradinaruvasile on 2009-06-25
Does that uses the gspca driver by chance?
run

gstreamer-properties

in a terminal. Go to the video tab and test the camera. Is it dark?

---

### Post by bubbhasdance on 2009-06-25
Yes, it runs gspca. I tested it, and yes, it's the same darkness as on Skype.

---

### Post by gradinaruvasile on 2009-06-25
Hm. I have a gspca based camera too and it is dark. But in time the auto correction manages to make the image brighter to a bearable/acceptablle level. I used a little trick when it was too dark. I covered for a moment the camera with my hand and it turned the brightness automatically up and it remained at that level.

---

### Post by bubbhasdance on 2009-06-25
The covering trick worked a lot, the brightness went up some. This + a small lamp, and I should be fine. Thanks!

---

