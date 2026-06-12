---
title: "Integrated Camera"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Taster on 2009-09-13
Hi guys! This is my first post, and I just recently installed Ubuntu onto my laptop that I just purchased a few days ago. I was wondering, if there is any way to enable the integrated webcam--I have tried using Kopete to see if the camera is even recognized, and it isn't. I have also tried to install (and reinstall) cheese, and that didn't work. Is there anything that I can do to fix it?

This is the laptop that I ended up purchasing: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834152127](http://www.newegg.com/Product/Product.aspx?Item=N82E16834152127)[B].

[/B]I have included the output from the command lspci, and it doesn't appear to be listed either.

Thanks in advance!

---

### Post by aljoriz on 2009-09-13
try easycam2, google it.  it has worked with many web cam.  It made my a4 webcam work on jaunty

---

### Post by Jose Catre-Vandis on 2009-09-13
Have a look through dmesg to see if any drivers are loading for camera, trys lsusb and also sudo dmidecode to try to identify your camera

---

### Post by Taster on 2009-09-13
lsusb yields nothing useful. It doesnt seem the camera is a USB device. The only thing I managed to find that seems relevant is a few lines from dmesg:

```
[14217.314301] Linux video capture interface: v2.00
[14217.343012] usbcore: registered new interface driver uvcvideo
[14217.343018] USB Video Class driver (v0.1.0)

```

---

