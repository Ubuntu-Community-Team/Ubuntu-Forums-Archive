---
title: "One way traffic thro' router"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by b0rk on 2007-03-10
I have recently installed Ubuntu 6.06 and although I can log into my router thro' firefox and make changes I cannot access any web sites.  

The router is a D-Link G604T and works perfectly with my mac-mini and XP,  I can even use Traceroute on Network-Tools in Ubuntu to sites on the internet without any problems.  It just seems that the router is unable to recognize ubuntu as a host,  under DHCP it either leaves the hostname blank or gives it the name of my other computer. I have now made a static address for it and disabled DHCP but it has not made any difference.

Any ideas would be appreciated because I've run out of them

---

### Post by Floppyjoe on 2007-03-11
This may be a DNS misconfiguration issue.  Check your /etc/resolv.conf file or Click on System/Administration/Networking and click on the DNS tab.

---

### Post by b0rk on 2007-03-11
Thanks Floppyjoe

I borrowed a friends Netgear router and everything worked first time so the problem is with my D-Link router.  I will check out the DNS configuration but apart from the difference in the IP address etc. between them I did everything else the same.

Cheers

---

