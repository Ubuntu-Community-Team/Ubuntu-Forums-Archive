---
title: "How to get forcedeth working?"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by lzap on 2006-08-16
Hi, I have upgraded my motherboard. I was using a cheap Realtek PCI ethernet card, now my motherboard has nForce 430 with integradet ethernet chipset.

When I tried to boot ubuntu it couldnt find the eth0 device:

# /etc/init.d/networking restart

eth0: no such device...

# ifconfig

...only lo...

# lsmod | grep forcedeth
forcedeth        33124 0

It seems the driver is not binded with eth0. How can I "bind" them?

---

### Post by lzap on 2006-08-16
I have tried to create a file /etc/modprobe.d/test with "alias eth0 forcedeth". I have run sudo update-modules and tried to restart networking - with no luck. The eth0 is still not found...

---

