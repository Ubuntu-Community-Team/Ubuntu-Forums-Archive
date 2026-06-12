---
title: "Installing Atheros Driver"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Spono on 2007-08-15
I know that the wifi driver for Atheros chipsets, MADwifi, comes with 6.10 and 7.04 in linux-restricted-modules, but is there a way to install this driver without having the linux-restricted-modules?

I ask because in order to install my video drivers, I need to get rid of restricted modules, and I'd like to have my video and my wifi work at the same time, not one or the other.

If anyone knows of a way to do this in any version of Ubuntu, it would be greatly appreciated!

---

### Post by spd106 on 2007-08-17
The best way would be to disable the graphics driver in the /etc/default/linux-restricted-modules-common file and continue to use the included version of madwifi. In your case it will probably be nv or nvidia (try both).

If you want to you can download the source code from madwifi.org and build the driver yourself, However you will need to install the linux-headers and bulid-essential packages from the Ubuntu main repo first.

---

