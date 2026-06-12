---
title: "Ubuntu 16.04 LTS wide-dhcpv6 broken again"
date: 2018-08-06
forum: Networking &amp; Wireless
---

### Post by BatteryKing on 2018-08-06
I have noticed that wide-dhcpv6 has broken in yet another way.  This time around it is assigning the routing wrong when dishing out to multiple subnets.  So instead of passing the request for a /60 group of networks, assigning network + 0 to the first subnet in the config with a /64 mask (as all individual IPv6 networks are /64, /60 is only used to grab a group of subnets for dishing out), assigning network + 1 to the next and so on (e.g. 1234.1234.1234.0000::, 1234.1234.1234.0001::, 1234.1234.1234.0002), it is assigning /60 for each and not adding the offset anymore, which brakes routing.  Before in this stable release it was not assigning the default IPv6 route, but that seems to have gotten fixed at the same time this got broken.  In Ubuntu 14.04 the problem was it did not do refreshes properly at the T1 interval and so the ISP was never informed of the routes and so would stop routing when the T2 interval rolled around.  There has never been a single time that wide-dhcpv6 has worked the way it was supposed to.  Apparently depending on update I have to rewrite the code to work right every time.  What gives?  IPv6 is the way everything is going because IPv4 ran out of addresses back in 2011.  Also IPv6 is vastly more efficient of a protocol than IPv4.  So it makes no sense to ignore this and just constantly have broken with anyone who realizes it is needed having to modify and recompile from source every time with nobody upstream paying attention to pull requests to get this stuff fixed.

---

