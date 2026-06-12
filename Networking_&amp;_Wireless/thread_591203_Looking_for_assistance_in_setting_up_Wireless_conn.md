---
title: "Looking for assistance in setting up Wireless connection"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by comfortablynumb on 2007-10-25
I did a clean install of Gusty, I can right click and say connect to existing network but soon as I reboot those settings are gone. I tried to configure my connection manual and it will not connect at all.

Is there a way to add a wireless connection and have it stay after a reboot? Having to create the connection each time I reboot isn't going to work for me.

Also I have downloaded all the latest updates after the clean install.

Hardware and specs:
- IBM T23 Laptop
- Cisco Aeronet 340 wireless PCMCIA
- Netgear MR814 V2(802.11B Router)
- Broadcast SSID off
- Wep 128 Bit

---

### Post by spd106 on 2007-10-25
Try turning ssid broadcast on

or configure the /etc/network/interfaces file directly using the with wpa_ap_scan 2.
You should probably use the Wireless security sticky as a guide [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

