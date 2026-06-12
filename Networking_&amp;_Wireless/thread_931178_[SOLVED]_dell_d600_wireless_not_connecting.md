---
title: "[SOLVED] dell d600 wireless not connecting"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by pjizz on 2008-09-27
hi all.  just got a new to me old laptop, dell d600.  since it's older and i only need it for work, i threw xubuntu on it.  install went great, now i just need to get the wireless card up and working.

the card seems to be recognized, however it never sees any area connections, and it cannot establish a connection with networks even when i know the network name and password information.

the forum gods have been wonderful in the past...don't let me down!

---

### Post by pjizz on 2008-09-27
just ran lspci -v 

here was the output:

[PHP]02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
Flags: bus master, fast devsel, latency 32, IRQ 5
Memorty at fafee000 (32-bit, non-prefetchable) [size=8K]
[/PHP]


i've looked at the compatibility guide and it seems people have had differing returns on the BCM4306, and have used various methods to fix it.  also, maybe dumb question, but, is my wireless NIC the Dell 1350 or the BCM4306??

again, all help appeciated

---

### Post by pjizz on 2008-09-27
okay...apparently this was nothing a little hooking up to hardline and updating couldn't fix.  anyone with the same problem should try that.

---

### Post by richhop25 on 2009-11-05
What do you mean a little updating?  Did you go to Dell and download a driver or someplace else?   I am new to Ubuntu so speak softly.

---

