---
title: "Linksys WMP54GX"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by britt on 2006-08-19
Has anyone been able to get this card working?  

Using ndiswrapper I have been able to get Dapper to recognize the card and associate with my AP, but I can't send or receive data. With a static IP I just can't send anything and with DHCP I can't get a lease.  DHClient returns the following error:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 556

---

