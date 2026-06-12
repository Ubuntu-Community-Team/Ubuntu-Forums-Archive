---
title: "Ndiswrapper with WPA"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by UrbenLegend on 2006-08-29
I've got ndiswrapper-utils installed and I installed the drivers for my belkin 54g card properly (using bcmwl5.inf), following the directions from the WifiDocs, but I still can't connect even with encryption off. The wireless card in the Administration->Network settings shows the wireless card as on interface eth0, even though the WifiDocs said it should be on wlan0. I've tried changing the /etc/modprobe.d/ndiswrapper settings to alias eth0 but that didn't work either. Anyone know what's wrong?!

Okay, I've also noticed that there's no WPA configuration tool in Ubuntu (what the heck), so I need a step-by-step newbie guide on how to enable wpa. I've tried Googling but that didn't help me at all.

I really need the internet working on Ubuntu, please help!

By the way I am using the install from the live cd.

EDIT: I found out that Ubuntu was using the bcm43xx driver instead, so I blacklisted it, but now Ubuntu won't boot anymore! It gets stuck at the configuring network interfaces section. Please help!

---

### Post by UrbenLegend on 2006-08-30
Okay I have finally got ndiswrapper working without encryption. But my wireless card is still registered as eth0. How do I change this?

Also has anyone had any luck with using the network manager with ndiswrapper? I can't get this to work. Please help!

---

