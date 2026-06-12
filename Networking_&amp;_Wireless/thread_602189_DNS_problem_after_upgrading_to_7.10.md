---
title: "DNS problem after upgrading to 7.10"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Doughy on 2007-11-04
I recently upgraded a computer from 7.04 to 7.10.  After the upgrade, I started having problems with accessing websites.  Some websites work fine, while others do not load at all.  I did some investigation and found that the websites that were not working correctly were because the DNS was returning a bogus IP for those sites (something like 1.0.0.1).

So, I opened up the network config and looked at the DNS servers.  The primary DNS server was incorrect, so I deleted it.  After I did this, the secondary DNS started working and the problem was fixed.

The problem now is that I can't get that change to stick.  Whenever I reboot, I have to load the network panel and delete the primary DNS entry.  I am using a DSL connection with a modem,  and it uses DCHP for IP assignment.  Why can't I get the primary DNS server to stick?  I don't think it's a DHCP problem because my windows boot works fine.  Ideas?

---

### Post by jasontan6 on 2007-11-04
I am using the Aztech DSL600EW router. Upgrading the router firmware solved the problem for me.

My current firmware version is 66.53.2

Download from here [http://www.aztech.com/retail_malaysia/support.html](http://www.aztech.com/retail_malaysia/support.html)

---

