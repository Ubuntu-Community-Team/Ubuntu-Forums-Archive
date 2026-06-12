---
title: "Wireless issues with a TNET1130 chipset PCI adapter"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by gstrat on 2007-10-19
Hi folks. Just installed Ubuntu 7.10 on a PC and have problems with connecting to the home's wireless network.

The station is a Zyxel P-661HW-D, running DHCP server, operating a 802.11g network, broadcasting at channel 9, hidden SSID, WPA1-PSK security and MAC access control. Network works fine under windows and mobile wireless devices.

After installing Ubuntu, wireless card seems to be recognised fine, since the network manager appears on the top right and detects some of the networks in the area. My adapter is a Tornado 122 PCI card, which uses the Texas Instruments TNET1130 chipset. Haven't had any problems with it under Windows.

I used the network configuration tool in GUI to setup the connection. clicked on adapter to set it up, disabled roaming mode, entered the SSID name, set passkey and activated the DHCP option. After saving settings, a window appears saying that the network settings are updated. From that point onwards, after the window dissapears, system stops responding. Although the GUI doesn't crash, applications won't start. PC can only restart with a cold boot and trying to boot back into linux fails (while loading the Unix common printer driver I think - dont have any printers on this PC btw).

Any ideas on why this happens? Any help? Any other ways of making wireless work without killing linux? Would avoiding the GUI tool and using command line commands directly help?

---

