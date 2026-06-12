---
title: "Looking for rt2500.inf to use with ndiswrapper."
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Bastanteroma on 2008-02-17
I'm having trouble finding a .inf file to use with ndiswrapper for my rt2500 pci card.  The .exe from the ralink site doesn't seem extractable and I don't have a cd.

Anyone have it, or know where to get it?

---

### Post by jhetrick62 on 2008-02-17
If it's a .exe, it may need to be extracted with cabextract which you can install through synaptic.

Jeff

---

### Post by Bastanteroma on 2008-02-17
Cabextract is installed, but there is no option in nautilus to extract the file, and no program associated with it.

---

### Post by pebo on 2008-02-17
```
man cabextract
```
PS rt2500 module is included in later kernels -at least as of 2.6.23 - I'm using it now

---

### Post by Bastanteroma on 2008-02-17
Cabextract found no valid cab files.  Orange, which advertises that it extracts cab files from .exe's didn't seem to do anything.

I'm using the built in rt2x00 driver in Hardy right now, but it's a lot slower than the old driver (which won't compile on the newer kernel), so I want to try the windows driver with ndiswrapper.

It's a common enough approach - there's a stickied post showing how to blacklist the native drivers and use the rt2500.inf, but I'm having the darndest time finding the driver.  Maybe I should look for other devices using the same chipset and see if they offer the driver for download apart from the .exe.

---

### Post by Sonic Reducer on 2008-05-18
you are wasting your time trying to extract the .exe, i know for a fact it does not work. it's not a zipped file, it's an executable program that installs the driver as it installs the RaLink network monitoring software

send me a private message if you need the .inf file still. i got the RaLink one and the Linksys one, but IMO the RaLink one works best (i hit ~3 meg/s once on bit-torrent)

.:EDIT:. i remembered you can attach files here, i attached the (good) Linksys WMP54G v4.0 driver and the (best) RaLink RT2500 driver

---

