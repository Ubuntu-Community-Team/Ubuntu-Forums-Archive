---
title: "IBM X21 Ubuntu Edgy no internet connection"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by ozooha on 2006-12-23
Has anyone got Ubuntu configured for the internet connection on IBM X21?
I seem to have a ethernet plug point at the back of my IBM X21 and I have connected that to my netgear wpn824 router. However there seems to be not internet connection.
Has one got theirs to work?
Did one use the wired connection or a wireless connection?
I do have the wpn511 wireless card but do not seem to have it working?
Any help would be appreciated.
OZ

---

### Post by jogege on 2006-12-31
Try to use the cheatcode "linux acpi=off pnpbios=off" when booting up. It seems the acpi module doest play very well with the ethernet drivers.

You might look into getting Ndiswrapper for making your wireless card work. I use ndiswrapper myself for my wireless cards.

And I am also using an X21

---

