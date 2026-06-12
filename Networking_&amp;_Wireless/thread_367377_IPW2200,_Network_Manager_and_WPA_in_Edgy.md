---
title: "IPW2200, Network Manager and WPA in Edgy"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by wizbit on 2007-02-22
I had WPA working with my ipw2200 via Network Manager but decided to update the drivers to 1.2.1 along with the firmware.

After updating I can't connect to my WPA network (haven't tried WEP yet) but I can connect to unsecured APs.

The output from dmesg is :-

[17179595.164000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1mprq
[17179595.164000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179595.388000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179596.904000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

so the driver is updated and seems to be working fine.

I didn't need to use the /etc/wpa_supplicant.conf file before as everything worked out the box with Network Manager, do I have to use it now?

The versions I've upgraded to are:-

ipw2200 - v1.2.1
ieee80211 - v1.2.16
ipw2200 firmware - v3.0

Anyone got any ideas?

---

### Post by Falkon MX-5 on 2007-02-22
How and why do you update the IPW2200 firmware?  I'm using the firmware for ipw2200 built into the kernel.  Before, I was setting everything up in wpa_supplicant with roaming profiles, but it just doesn't play well, especially if the network has a hidden ssid.  
[http://www.ubuntuforums.org/showthread.php?t=341357](http://www.ubuntuforums.org/showthread.php?t=341357)

---

