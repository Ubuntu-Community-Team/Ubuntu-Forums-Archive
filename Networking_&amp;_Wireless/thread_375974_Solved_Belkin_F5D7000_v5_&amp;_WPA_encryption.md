---
title: "Solved: Belkin F5D7000 v5 &amp; WPA encryption"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-03-04
[B]Kubuntu Edgy
Belkin F5D7000 v5 (Atheros) PCI card
WPA 1 or 2[/B]
**Router with *hidden ESSID* (pay exact attention to Wieman's WPA:How To)**

***_Software required_***
Windows driver (unzipped)
WPA-Supplicant
Ndiswrapper 1.8 (only) Uninstall any prior versions installed by default

***_Process_***
1) Follow *Wieman's "WPA:How To".*....to an exacting T!!!:guitar: 
2) Add "*pre-up sleep 1*0" to your /network/interfaces file (between "iface ath0 inet dhcp" &    "wpa-driver wext" .......**ONLY** if your internet network connection **DOES NOT** automatically connect at startup.
3) Reboot


That should have you connected!
:popcorn:

---

