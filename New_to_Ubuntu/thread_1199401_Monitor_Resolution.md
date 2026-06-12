---
title: "Monitor Resolution"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-06-28
I am trying to run an application in Ubuntu 9.04 32-bit which I would like to run in 1280x1024 resolution. I normally run my desktop at a resolution of 1920x1200. I have a 24" monitor. Unfortunately Ubuntu doesn't switch the resolution to 1280x1024 when I start the application and instead it stays at 1920x1200 even though in the application's own settings I have selected in the settings that I want it to run at 1280x1024.

I do not have this problem using this application in windows. I guess another way of asking would be is there a way to force Ubuntu to drop to a lower resolution for an application and come back up to 1920x1200 when you quit that application?

The application in question here is the x-plane flight simulator. My system specs are below:

Ubuntu 9.04 32 bit / Windows XP SP2 (Dual Boot w/ Grub)

Processor: Intel Core 2 Duo 2.666 MHZ (8 x333)
System Ram: 4GB RAM
Display Adapter: 2x Nvidia 8600 GeForce (512MB) in SLI (nvidia driver 185.18.14 for Ubuntu)

Motherboard: Abit Fatalty FP-IN9 SLI (2 PCI, 2 PCI-E x1, 2 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN)
Motherboard Chipset: nVIDIA nForce 650i SLI
BIOS: Award (05/10/07)

---

### Post by Steelmourne on 2009-06-28
Open up terminal and type gksu nvidia-settings and manually change the settings saving to the xorg file.

---

### Post by ncc1701e on 2009-06-29
I do not wish to change my resolution permanently. I would like to keep my desktop resolution at 1920x1200. I just want Ubuntu to run x-plane in 1280x1024 (i.e. drop down to that resolution when I start x-plane and come back to 1920x1200 when I quit it). Is there a way to make Ubuntu do this?

---

