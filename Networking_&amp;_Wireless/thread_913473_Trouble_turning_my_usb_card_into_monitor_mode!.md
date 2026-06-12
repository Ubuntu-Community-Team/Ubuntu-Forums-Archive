---
title: "Trouble turning my usb card into monitor mode!"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by silverleaf on 2008-09-07
Dear all i am new to ubuntu and i have installed the latest version 8.04 i think.
I have a project to do and i want to turn my card into monitor mode so i can use kismet.
I have bought two cards D-link G132 and linksys Wusb54g.
i have tried to set both in monitor mode by iwconfig, using also sudo infront, but i always seem to get a msg :
Error for wireless request "Set Mode" (8B06):
SET failed on device wlan0 ;
or invalid argument.

the thing is that i can not change any mode in both my cards?
is there some adjustment that has to be done or that my current cards doesnt support monitor mode? what can i do?

Thank you in advance!

---

### Post by silverleaf on 2008-09-08
i have managed to make those cards work with ndswapper if i write

sudo airmon-ng start wlan0

i get

nterface	Chipset		Driver

wlan0		Unknown		ndiswrapper (MONITOR MODE NOT SUPPORTED)

it is possible to find other drivers with the exact chipset so it can support monitor mode ????

---

