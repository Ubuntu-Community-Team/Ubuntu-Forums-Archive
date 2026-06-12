---
title: "Netgear WG111GT 108 Mbps Wireless USB 2 adapter"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by chrismine on 2006-08-04
I have got the adapter to work with Ndiswrapper version 1.21 compiled from source. I also had to compile the kernel to version 2.6.18-rc1 from source.

So far it works fine. :D It works at ubuntu startup unlike with the previous version 1.19 of ndiswrapper I used. There I had to unplug the adapter from the USB port and then had to do sudo rrmod ndiswrapper and the sudo modprobe ndiswrapper.

Just thought I will let everybody know.

---

