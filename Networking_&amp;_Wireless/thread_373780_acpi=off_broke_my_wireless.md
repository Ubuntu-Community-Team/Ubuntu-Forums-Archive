---
title: "acpi=off broke my wireless"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by foznot on 2007-03-01
I am trying to use the dapper drake install cd. If I pass the switch acpi=off at boot, then dapper installs like a dandy. But then after the install, I have no wireless. When I use the live cd without the switch, acpi=off, then I have wireless, but if I use acpi=off, then I have no wireless.

Ok, I am using a Netgear wireless card with prism2. It is an athlon  x86 system with basic stuff.  The network is set to DHCP right out of the box.

Any help would be much appreciated.

---

### Post by wersdaluv on 2007-03-01
I have the same problem!

Whenever I use a parameter such as acpi=off, my broken USB starts to work but my wireless stops from working.

Please see [this thread for more details.]("http://ubuntuforums.org/showthread.php?t=356269")

Please help us! :guitar:

---

### Post by foznot on 2007-03-01
Ok, I removed acpi=off from my /boot/grub/menu.lst file and now my wireless works with my new install. However, now my USB drives don't work. Here is a reoccuring problem. Anyone have ideas why acpi is screwing up the wireless and usb. IRQ conflict of sorts, perhaps???

---

