---
title: "Network Manager + WUSB54Gv2"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by Melcar on 2006-11-24
I'm trying to get my WUSB54Gv2 to work with Edgy.  This device connects my main desktop which is out in the detached office and the only way to get internet connection is by wireless.  I managed to get it working with ndiswrapper and it does connect with the default gnome network manager; but I use WPA.  I already have network-manager-gnome installed, but now it won't detect wireless networks (the applet itself), but iwlist does detect them.  Any ideas?

---

### Post by Melcar on 2006-11-24
Never mind.  Was able to fix it by adding my MAC address to /etc/iftab.  Strange that it didn't copy itself automatically to the file, since that is how it happened in my laptop.

---

