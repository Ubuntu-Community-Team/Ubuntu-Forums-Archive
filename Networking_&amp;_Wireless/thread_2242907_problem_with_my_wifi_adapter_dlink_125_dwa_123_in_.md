---
title: "problem with my wifi adapter dlink 125 dwa 123 in monitor mode"
date: 2014-09-04
forum: Networking &amp; Wireless
---

### Post by yellowdog3 on 2014-09-04
hi. i installed driver.(rtl8188eu)(i use kali)
Bus 001 Device 003: ID 2001:3310 D-Link Corp.

 wlan0     IEEE 802.11bgn  ESSID:"my with"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: A0:E4:53:B8:AD:6B   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
when i disconect to network  via wifi adapter wifite give

[+] scanning for wireless devices...
 [!] no wireless interfaces were found.
 [!] you need to plug in a wifi device or install drivers.
and airmon-ng not detect wlan0

when i conect to network from via wifi adapter wifite give
[+] scanning for wireless devices...
 [+] enabling monitor mode on wlan0... done
 [+] enabling monitor mode on wlan0... done
... no endless
and airmon-ng detect wlan0
Interface    Chipset        Driver

wlan0        Unknown         r8188eu
i cant enable monitor mode
root@dhcppc0:~# wash -i wlan0

Wash v1.4 WiFi Protected Setup Scan Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>

[X] ERROR: Failed to compile packet filter
 help

---

