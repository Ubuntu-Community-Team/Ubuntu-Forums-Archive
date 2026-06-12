---
title: "WLIU2KG54L (Noob exasperation - help!)"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Sneekster on 2008-08-14
I've had a search; no solution to be found. I looked [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo#USB") and see that my Buffalo AirStation Wireless-G (WLIU2KG54L) is supposed to "work out of the box" (whatever that means) and will work with a custom kernel if I "Add Device ID to zd1211rw.c or install 2.6.23 Kernel", but there is no driver, network install is not supported and it isn't supported in the installed system.

That said, it can see the router and connect to it, but can't log on to the router admin or see past it. I have Xubuntu 8.4.1. The dongle works fine from another OS, so I'm not convinced that range is an issue - signal strength is in the 80-something-percents in Xubuntu. I am so noobish at Linux it hurts, but am able to follow clear instructions. Help.

---

### Post by chili555 on 2008-08-14
> there is no driver> it can see the router and connect to itIf you can see the router and connect to it, you have a working driver, probably *zd1211rw*. Please open a terminal and type in:```
iwconfig
ping -c3 209.85.165.99
ping -c3 www.google.com
```Post the result here and let's see what needs a tweak.

---

### Post by Sneekster on 2008-08-17
@ chili555

A reboot solved the problem; it was useful to see the iwconfig and ping results though, so thanks. BTW, the USB dongle definitely has some random performance issues under Xubuntu not apparent under the other OS. Something to do with power management, maybe?

---

