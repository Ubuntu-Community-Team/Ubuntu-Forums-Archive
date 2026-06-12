---
title: "Micrisoft VX-6000 webcam help"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by jeremyblake on 2009-01-07
I've gone into terminal and found what i need to search for a driver.. but when i google it, i find 50 different things, and no one seems to have answers. Here's the device info:

045e:00f4

Anyone know of a working cam AND microphone driver? Thanks in advance!

---

### Post by Crafty Kisses on 2009-01-07
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this, there are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post the results of the following command:
```
lsusb
```

---

### Post by jeremyblake on 2009-01-07
Thanks for helping.. I got n picture at all no matter what i changed on the video.

Here's the output of the lsusb command...

jeremy@jeremy-desktop:~$ lsusb
Bus 005 Device 004: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:1702 Hewlett-Packard Photosmart 380 Series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c525 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jeremy@jeremy-desktop:~$

---

### Post by jeremyblake on 2009-01-08
Bump.

---

