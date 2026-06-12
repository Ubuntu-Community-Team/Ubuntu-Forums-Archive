---
title: "Firewall WAN is DHCP, I would like to add google DNS to WAN interface"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by LGSONE on 2014-01-03
First post so I don't even think I'm a coffee ground much less a bean... Anyway

Setup
13.10 headless server with webmin as config tool.
eth0
WAN interface copper ethernet to cable modem
eth1
Lan interface fiber ethernet to switch 10.2.1.0/24
Linux Firewall set up as NAT for LAN
DDNS account set up and DDNS Bind9 plug in for webmin.  WAN
DHCP LAN set to defaults.
Squid Proxy running for Wan http filtering

Everything is working fine, internet access on LAN, DHCP serves up as intended.  DNS server is 10.2.1.1

Instead of just using the DNS name servers from my ISP I would like to add the google DNS name servers to the WAN interface.
  
The preference would be to have name servers ordered like:
  google 8.8.8.8, 
ISP main DNS, 
google 8.8.4.4, 
ISP secondary DNS.

To the DHCP clients on the LAN side all they need to have is the 10.2.1.1 address as the DNS server but for the WAN I'd like to set as stated.

Please advise.  I have found a TON of info but much of it is old and I figured a fresh question here and I'd write a how to that spells this out.  That is unless someone points me to one I have yet been able to find.

Thank you,

LGSONE
KC USA

---

