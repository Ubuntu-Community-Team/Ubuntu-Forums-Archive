---
title: "Xubuntu + WG111v2 works, but not WPA"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by nuck on 2006-08-05
I've just installed the latest version of Xubuntu (Dapper Drake) and my WG111v2 adapter seemed to work without much effort at all.  It shows up in Network Configuration (or whatever it's called) but the only security options presented are "none" and WEP.

It works when the Access Point's security is turned off, but it generally uses WPA.  Is there a way to get WPA working in Xubuntu?

---

### Post by nuck on 2006-08-07
The adapter works fine with the standard ubuntu driver (r8187) but the Network Manager does not support WPA so, following advice elsewhere on the internet, I added the line "blacklist r8187" to /etc/modprobe.d/blacklist.  The device now uses the ndiswrapper driver.

I don't have the original CD for the WG111v2, so I downloaded the latest XP driver from the Netgear website.

"iwlist scan" shows my AP showing up, so I try "sudo iwconfig wlan0 essid MyNetwork" and then "iwconfig wlan0", but ESSID is always "off/any" and the Access Point is "Not-Associated".  (even with the AP's WPA security turned off!)

This is probably the reason why "sudo wpa_supplicant -dd -Dwext -iwlan0 -c/etc/wpa_supplicant.conf" never manages to associate with the AP, even though it reaches ASSOCIATING state:
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - EAP portControl=0
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b04 len=12
Wireless event: cmd=0x8b1a len=12
Authentication with 00:00:00:00:00:00:00 timed out.
Added BSSSID 00:00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED


Any ideas on how to make "sudo iwconfig wlan0 essid MyNetwork" work?

---

### Post by nuck on 2006-08-07
I've got it working!  I found that the latest drivers from the netgear site don't work.

I downloaded the drivers mentioned in [this ]("http://www.ubuntuforums.org/showthread.php?t=226163&highlight=wg111v2")post, it works now.

---

