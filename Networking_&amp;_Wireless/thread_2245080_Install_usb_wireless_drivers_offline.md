---
title: "Install usb wireless drivers offline?"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by davethebrave on 2014-09-21
I'm trying to install drivers for a brand new D-Link USB wireless dongle that I was gifted to get a desktop rig's internet up and running. 

Situation 1: No feasible way to jack in with a cable. 

Situation 2 (the one that I need advice with): I want to grab drivers for the dongle on this laptop I'm typing on, save 'em to a usb stick and then install them on the desktop rig. Most of the instructions I see online are like, "Ok, make sure you have a wired connection first." so I can grab them from compat-wireless or wherever, but I'm hoping there's some way to do this without connecting to the internet so I can get the drivers for the dongle to install offline, so I can connect to the internet. 

Does all of that make sense? And, if it helps, the drivers I need to grab are rt2800usb **or** rt5572sta for a D-Link DWA-160 (rev B2). I have a tar.bz2 off of the mediatek website of the latter, and if there's no way to grab the rt2800usb for offline use then I'll just install that one. 

Which leads me to my next question: how do I install them in terminal? Again, most of what I've read talks about being connected to the internet while you install these things...I'm hoping there's some way to do all of this offline!

---

### Post by varunendra on 2014-09-23
Which version of Ubuntu are you using? The driver from mediatek is dated 2012, and won't build without patches on current kernel versions. Those Ubuntu version it will successfully build on are no more supported.

Besides, for both the compat drivers or the mediatek one, you will need 'build-essential' installed which can be a tricky one due to dependencies.

Does the following command give us any download URIs? -
```
apt-get install --print-uris build-essential linux-headers-generic
```
If it gives the URIs of the dependencies of build-essential along with those of itself and the headers, the rest would become quite easy.

But if you are using kernel version 3.11 or higher, the native rt2800usb driver should already have support for this card. If so, you shouldn't need to install anything manually at all. Please show us a [wireless_script]("http://ubuntuforums.org/showpost.php?p=13024222") report if you are not sure about it.

---

