---
title: "Bind socket to interface: no such device"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Bob Hunter on 2007-02-15
Hello,

I installed the latest ubuntu server on a machine, then had to move the disk temporarily to a second different machine. After fixing grub and xorg, it booted and it looks usable. However, the ethernet does not work. The script /etc/init.d/networking reports "Bind socket to interface: no such device", but /var/log/dmesg says that the hardware is recognized at boot. Besides, both machines have the same ethernet hardware. If I mount the disk back on the first machine, it all works as expected. What might cause this problem? What is, eventually, the command for hardware autodetection? (I am new of ubuntu.)

Tank you.
Bob

---

