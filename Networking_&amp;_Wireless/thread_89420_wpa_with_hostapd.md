---
title: "wpa with hostapd"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by Lambert on 2005-11-12
There's an app in the repositories I just saw called [COLOR=DarkRed]hostapd

[COLOR=Black]> It adds more features to the basic IEEE 802.11 management
included in the kernel driver: using external RADIUS authentication
server for MAC address based access control, IEEE 802.1X Authenticator
and dynamic WEP keying, RADIUS accounting, WPA/WPA2 (IEEE 802.11i/RSN)

hostapd works with the following drivers:

 * Host AP driver for Prism2/2.5/3,
 * Prism54 driver for Intersil/Conexant Prism GT/Duette/Indigo,
 * madwifi driver for cards based on Atheros chip set (ar521x),
 * Any wired Ethernet driver for wired IEEE 802.1X authentication.

Anybody out there using this or familiar with this? I have a card with the ar5212 chipset and I couldn't get wpa working. Wondering if this is a solution and anybodies experience with it.
[/COLOR][/COLOR]

---

### Post by firecat53 on 2005-11-13
wpa_supplicant I think works fine for most applications. I use it successfully at home with both ndiswrapper and madwifi drivers for connecting to my wpa-psk network. I'm not specifically familiar with the hostapd application, but if you post your wpa issues, we can probably get it working for you!

scott

---

