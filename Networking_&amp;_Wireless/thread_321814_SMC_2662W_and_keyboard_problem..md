---
title: "SMC 2662W and keyboard problem."
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by recurrente on 2006-12-19
Hi, 

I  have a SMC 2662W v.4 wireless usb card. When I plug it, modules load, firmware loads, the green light of the card switch off, and the keyboard (yes, the keyboard) stops working (the mouse still works). When I unplug the card (which doesn't initialize and, of course, doesn't work), all the keys pressed meanwhile appears suddenly in the screen. 

I've tested this in:

- An Athlon XP 1500 (2001 bios, upgraded later to 2003 with same results).
- An Acer 1642LMI laptop with identical results. 

All this with Ubuntu 6.06 and 6.10. The card works perfectly with Windows XP, in the laptop. 

(btw, in a windows 98 and XP inside a VMWare virtual machine in Ubuntu, doesn't work neither).

Also, when I do many tests pluggin and unpluggin the card eventually makes the usb module unstable and freezes the computer (last time, sending a document to the usb printer).

I read that this card is supported with no problems in Ubuntu. What is happening??

Thanks!

P.D: The card worked perfectly with a 2.4 kernel in Debian.

---

### Post by recurrente on 2006-12-27
I think I have the solution (?)

If I manually load the modules at76_usb and at76_usbdfu before plugginf the card, it works without problems. Maybe a udev problem?

---

