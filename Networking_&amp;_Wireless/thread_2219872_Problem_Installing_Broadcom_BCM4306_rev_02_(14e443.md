---
title: "Problem Installing Broadcom BCM4306 rev 02 (14e4:4320) WLAN card in Lubuntu 14.04"
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

### Post by oldos2er on 2014-04-27
Duplicate of [http://ubuntuforums.org/showthread.php?t=2219876](http://ubuntuforums.org/showthread.php?t=2219876) closed.

---

