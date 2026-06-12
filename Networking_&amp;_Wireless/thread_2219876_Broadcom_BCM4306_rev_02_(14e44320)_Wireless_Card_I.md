---
title: "Broadcom BCM4306 rev 02 (14e4:4320) Wireless Card Install Issue in Lubuntu 14.04"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by n4rps2 on 2014-04-25
Hello!

In Lubuntu 14.04, I had an issue installing the driver for a Broadcom BCM4306 rev 02 (14e4:4320) wireless adapter on a Compaq Presario 2500 series laptop (2570US). Seems as if 14.04 loads b43-pci-bridge by default. This driver interferes with the installation of firmware-b43legacy-installer, which this card needs to operate.

To get around this, simply add b43-pci-bridge to the list of blacklisted drivers in /etc/modprobe.d/blacklist.conf file, then install firmware-b43legacy-installer from the repositories.

73 DE N4RPS
Rob

---

### Post by varunendra on 2014-04-27
Actually, there is no driver called "b43-pci-bridge" in the kernel or anywhere else. It is just an alias name that the kernel gives to the b43 driver itself when it works in combination with the "bcma" driver.

So blacklisting "b43-pci-bridge" is pointless and is going to gain nothing (although won't harm anything either). It is the firmware installation part that does the trick.

Simply install the firmware, and reboot, or reload the driver. Please see the sticky thread in this Networking & Wireless forum for details, and easy-to-follow instructions.

---

