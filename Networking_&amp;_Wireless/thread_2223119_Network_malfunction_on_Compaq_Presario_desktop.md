---
title: "Network malfunction on Compaq Presario desktop"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by dome1970 on 2014-05-09
This is Compaq Presario sr1789IT desktop machine, with Realtek RTL8139/810x Family Fast Ethernet NIC and WinXP  preinstalled. Internet connection worked fine (with usb modem and thereby windows driver). I installed  Xubuntu 14.04 after some difficulties  (without the noapic option I would receive a kernel panic screen concerning apic).

The wired internet connection using the  ethernet port works but it is in fact so slow that it is completely useless. I tried this in various places with a fast LAN and at home with a modem-router. I also bought a usb wireless adapter which works (in the sense that it sees the various wireless access points) but cannot establish a connection.
The same problem presented with a live  cd of xubuntu as well as lubuntu, mint and puppy which I also tried. In each case however the noapic option was necessary to avoid the kernel panic problem mentioned above. 
Any suggestion is welcome.
Thank you,
domenico

---

### Post by dome1970 on 2014-05-12
Someone suggested updating the bios as a possibility. Supposing I were able to do so (which I doubt), would it be worth trying?
Thanks,
d

---

### Post by dome1970 on 2014-05-13
Update: using a live cd I found out that the option "acpi=off" instead of "noapic" solves the connection problem (which returns to normal speed). However it creates a problem of very low screen resolution (800x600) without chance to improve on it.

---

