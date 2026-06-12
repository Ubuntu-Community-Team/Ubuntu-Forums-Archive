---
title: "IPv6 sublet prefix delegation and routing"
date: 2020-08-10
forum: Networking &amp; Wireless
---

### Post by BatteryKing on 2020-08-10
With IPv6 delegating addresses from the ISP with PD (prefix delegation) and then having a secondary mechanism for RA (router advertisements), is there any way I can sublet some of these prefixes out to a firewall behind the main firewall?  In this case I am using a scratch built Ubuntu 20.04 based firewall.  The goal here is to test a firewall system as fully as I can inside of my network before moving it to a direct connection to the Internet.  By default what happens is the internal firewall system can get a public IPv6 address on the WAN interface, but cannot get a PD for the internal network.

---

