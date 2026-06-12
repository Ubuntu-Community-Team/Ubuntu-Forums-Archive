---
title: "Wireless, manual key, non-broadcasting AP"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2006-12-14
Hi,

The company where I work use an access point that does not broadcast it's SSID and then you need to enter a manual key. In windows I have a BroadComm config utility that does this. How would the lines look in the Interfaces file for pointing my wireless connection at this access point?

the settings that I need are:

SSID, THE KEY, The Authentication(Open, 802.1x, WEP), IP, Subnet, Gateway.

The last three I can do but the first couple I'm scratching my head about.

Thanks for any help,

Rudolf

---

### Post by tturrisi on 2006-12-14
This is for dhcp (not static ips)
#where ath1 = your interface
#where essid = your ssid, case sensitive name
#where wireless-key = your wep key
iface ath1 inet dhcp
wireless-essid xxxxxxxx
wireless-key xxxxxxxxxx

---

### Post by RudolfMDLT on 2006-12-14
thank you! It works!

---

