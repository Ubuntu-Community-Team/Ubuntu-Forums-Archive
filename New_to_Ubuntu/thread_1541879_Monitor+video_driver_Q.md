---
title: "Monitor+video driver Q"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by tyler9 on 2010-07-29
I just plugged a new Asus 19" widescreen LCD monitor into Ubuntu 10.04 using a DVI connection. Ubuntu's Monitor Preferences dbox shows the monitor at the native resolution of 1440 x 900. No setting adjustments needed, apparently.

Problem: This monitor displays text a little fuzzily with an overlay/trace of grey like a shadow; photos and larger text are jagged.

Is it safe to assume this is a driver problem, and not intrinsic to the monitor? How does a user confirm they have the latest drivers? Are video drivers provided/included by Canonical/Ubuntu community, or by the video card/chipset manufacturer?

'Scuse the elementary questions, but dealing with monitor hw, pixels, pitch, resolutions, video cards, video chipsets, drivers, firmware updates, compatibility, etc has always confused me a bit...

Video: Onboard ATI Radeon HD 4200, on Gigabyte mobo GA-785GMT-USB3.

Thanks for help!

---

### Post by Naitsirhc Hsem on 2010-07-29
If you want the AMD-ATI drivers, download the Calalyst driver for ubuntu and install it from the terminal, sudo sh Downloads/ati-239-23-4whatever.sh

To check for new ubuntu drivers, System>Administration>Hardware Drivers

---

### Post by 3rdalbum on 2010-07-30
> **Naitsirhc Hsem said:**
> To check for new ubuntu drivers, System>Administration>Hardware Drivers

This is the preferred way of installing the ATI driver.

Note that Ubuntu's font rendering is different to Windows' and Mac OS X's font rendering (each OS does it a little differently). You might just need a bit of time to get used to it if you've been looking at Windows for years.

---

