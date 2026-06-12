---
title: "wpa supplicant"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by BlackAndWhite on 2006-10-19
Hi,

I currently have WPA working to a fashion with 6.06 LTS, but a few problems remain.
Current set up consists of a Linksys WPC54G v1.2, ndiswrapper and WPA supplicant.
My interfaces file for the wireless looks like this:

iface wlan0 inet dhcp
           pre-up wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w -B

If I run wpa_gui it displays 'Could not get status from wpa_supplicant', wpa_cli returns 'Could not connect to wpa_supplicant - re trying'. Odd as WPA supplicant seems to be working as I am connect to my wireless network.

Another issue is that if I eject the card and then re-insert it, the laptop does not connect back to the network.

Any help to get over this final hurdle would be apreciated!

Many thanks


Richard

---

