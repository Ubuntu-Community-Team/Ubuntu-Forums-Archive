---
title: "airmon-ng MAC address Gusty"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by burnticarus on 2008-02-26
Why would my card MAC address change when switching to rfmon mode?  It only changes by one number ex. the begining (00:etc) changes to (06:etc)  the rest of the MAC address stays the same.

Using ```
airmon-ng stop ath0
airmon-ng start wifi0 3
```

everything works fine after that just slightly different MAC address

Thinkpad z60t upgraded to Gusty

Atheros
Madwifi_ng

Before switching to monitor mode I check address with```
 ifconfig
``` list MAC address as HWaddr: (00:etc)
Once in monitor mode I use ```
iwconfig
```has  Access Point: (06:etc) Which is the card I am monitoring from (client) which I then used for authentication
Just thought this was strange.
Do you know whats up?

---

### Post by Junglizer on 2008-02-27
I know that this same issue happens with several other cards (specifically Cisco Aironet 350's) I do not know the specific reasoning behind it, but it is not a big issue. You cannot connect to specific networks while in rfmon mode anyway, so its not a big deal.

---

