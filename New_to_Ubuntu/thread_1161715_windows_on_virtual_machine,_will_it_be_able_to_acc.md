---
title: "windows on virtual machine, will it be able to access the comms ports"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-05-17
I have subject for uni next year that requires the use of windows and programming a board using the comms ports (I assume either rs323 or usb atm)

So if I set up xp on a virtual machine would it be able to access the comms ports?

Thanks in advance

Mick

---

### Post by nhasian on 2009-05-17
with Sun's Virtualbox 2.2 just click on the Serial Ports button to enable them from the main menu.

---

### Post by lkraemer on 2009-05-17
Absolutely, just don't install the OSE version. Download your
Distro's version from [www.VirtuaxBox.org](www.VirtuaxBox.org).

And if you need a USB to 9 Pin Serial Converter try one of these:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

In Linux they will be /dev/ttyAMC0 or /dev/ttyUSB0, etc....

These work wonderful with wvdial, KPPP, Gnome-PPP, etc.
wvdial will find the correct /dev/ttyxxxy

lkraemer

---

