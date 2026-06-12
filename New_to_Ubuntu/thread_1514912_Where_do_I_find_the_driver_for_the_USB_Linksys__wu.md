---
title: "Where do I find the driver for the USB Linksys  wusb54GC"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by montana68 on 2010-06-21
Hello Everyone
I am a newbie, could you please help me find out where I go to download a driver for a Linksys wusb54GC  wireless internet adapter.
Thank you for your help.
Montana68

---

### Post by warfacegod on 2010-06-21
Go to the Linksys site and look in drivers for Linux. Something with a .deb file extension would probably be easiest to install. You can also check Synaptic Package Manager to see if there's one in the repos.

---

### Post by davidmohammed on 2010-06-21
that particular usb wireless is not very linux friendly - problem is it comes in various forms - some dont work, some do.

in a terminal - type

lsusb | more

find the entry that has wusb54GC in it.

can you see the numbers 1737:0077?

if so,
  suggest you look at [this thread]("http://swiss.ubuntuforums.org/showthread.php?t=1489883") for further advice.

---

