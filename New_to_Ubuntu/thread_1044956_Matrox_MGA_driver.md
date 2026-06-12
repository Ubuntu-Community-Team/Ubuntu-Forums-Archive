---
title: "Matrox MGA driver"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by djenner on 2009-01-19
I have the impression variants of this have come up, but not quite the same. I have installed 8.10 ubuntu on older hardware, which has a matrox millenium II PCI display adapter.  There appears to be a driver for that card included in the installation package, but it appears not to be installing.  One indicator of this: I get only an 800x600 resolution (and then only if I force the system to not see my 22" standard aspect ratio acer flatpanel monitor; I toggle to my other system using the KVM switch while linux boots). I believe I should be seeing an MGA variant xorg.conf file? The one on my system (/etc/X11/xorg.conf) has no content.  I am assuming that for some reason, the installer did not read the hardware correctly (possibly because of the need to boot with nolapic and acpi=off parameters at boot time?).  Can this be fixed easily?  It is not a major concern, it would be nice, but this system is maintained just to allow me to check things on similar (but less troublesome...) systems at a client site.

---

### Post by tyeo098 on 2009-01-20
Im in the same boat as you man.
I was tired of only having very little  desktop realestate, so I put two (VERY) old PCI cards in my dell. (It ONLY has PCI go figure...)
I have the Matrox Mentioned here along with an Ati 3d Rage II+, and I havent gotten either of them to work at all, theyre just blank. (power save mode)

Are you using duals or are you just using the Matrox as your primary?

---

