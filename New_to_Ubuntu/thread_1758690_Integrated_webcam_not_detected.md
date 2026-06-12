---
title: "Integrated webcam not detected"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by emanuel20 on 2011-05-14
I have a sony VGN FE 890 Laptop running Ubuntu 11.4. For some reason my  integrated webcam is not being detected, is not doing anything actually.  I have tried different applications, different video drivers etc and  nothing seems to work. Any help?

---

### Post by Quackers on 2011-05-15
See if you can find what chipset the camera is. What type of camera is it.
My Vaio has a Ricoh camera with the r5u87x chipset. If your Vaio is the same you should have a look here
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

---

### Post by emanuel20 on 2011-05-15
Thanks it did work.

---

### Post by Quackers on 2011-05-15
Aha! Very nice :-)
Please mark the thread as solved, using the Thread Tools near the top of the page.

---

### Post by no2498 on 2011-05-15
Ricoh camera's need there own drivers
open a terminal type dmesg click enter
after it stops
type lsusb click enter
that should give you a number and a name for your cam
if its a Ricoh camera follow quackers
if not in the terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

