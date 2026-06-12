---
title: "IBM R60 Thinkpad Wireless Help"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by troymcdavis on 2006-10-13
Hello all.

I'm currently using Ubuntu 6.06 on an IBM (Loveno) R60 Thinkpad. Just about everything works great, except the wireless.

[I've heard]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06_on_a_ThinkPad_R60#Network") that the built-in wireless card should work out of the box, but this was most certainly not the case for me. Since I got the computer this summer, I've made several attempts to get the wireless working in any capacity.

The computer rarely acknowledges the card's existence. If I go to System -> Administration -> Device Manager, it shows the card there as an Atheros Communications, Inc. (Vendor) AR5212 802.11abg NIC (Device). It's status is listed as "Status", it's type "PCI", device type and capabilities "Unkown". An lspci confers, with an entry for "0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)". The Network Manager has too, begun listing wireless connections. I'm not sure how that happened. However, the Network Monitor does not acknowledge the presence of such a device (nothing but eth0 and lo). Certainly, the wireless does not connect to any wireless connections.

I'll just list off some of the software I've installed to remedy the situation:
[LIST]
[*]ieee80211
[*]ipw3945
[*]ipw3945d
[*]madwifi
[*]sharedutils
[*]wireless tools
[/LIST]

I was going to try ndiswrapper, but I cannot find any windows drivers for download.

The stopping point for any wireless work is the dhcp connection. Allow me to show you:

```
snakes@plane:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:ce:7b:86:6a
Sending on   LPF/ath0/00:16:ce:7b:86:6a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Unfortunately, I cannot set up a static IP because I cannot find out the default gateway to the router.

Honestly, I've hit an impasse. I have no idea where to go from here. I am considering reinstalling Ubuntu all together. Would this do anything? Any suggestions are greatly appreciated. Feel free to ask questions if you think they would make you better able to help me.

---

