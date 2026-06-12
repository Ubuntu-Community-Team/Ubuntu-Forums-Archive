---
title: "rt2570 or rt2500 usb problems"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by silenceofnight on 2008-05-16
I am trying to get a d-link dwl-g122 rev b1 to work in xubuntu 8.04 (I chose xubuntu not ubuntu because it fits on a cd-rw).
I tried the tutorials that tell you to blacklist the rt2570 driver, but they didn't work.
I tried downloading the serialmonkey rt2500 driver on a windows computer and moving it via thumbdrive, but couldn't compile it because of (I think) lacking build-essential and the kernel headers. I got the kernel headers to build and install, but not build-essential. It wanted something (dpkg-dev, if I remember the order right), which in turn wanted lib6-dev, which wanted libc6-udeb (again, I may have the order of these wrong), which wanted libnss-dns and libnss-files, both of which failed to install complaining about overwriting a file which didn't exist. 

In windows, the card uses a rt2500usb driver, but, oddly enough, in puppy linux 4.0, it works fine as a rt2570 device. :confused:

I've spent many hours searching the forums for a solution, but none of them worked.  Help please!

---

