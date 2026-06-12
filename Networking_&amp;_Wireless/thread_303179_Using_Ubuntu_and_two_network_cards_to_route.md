---
title: "Using Ubuntu and two network cards to route"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by bforbes on 2006-11-19
I have a cluster of 10 Ubuntu machines on a switch. There is an eleventh machine on the switch which has a second network card hooked up to the Internet. I'd like to use this net-facing machine to allow the cluster to access the net. Is there any simple way to do this?

---

### Post by stream303 on 2006-11-21
Sure - configure the 11th machine as a nice Ubuntu router.

Easier than that would be to just purchase an inexpensive router and make the 11th machine part of the cluster too.  Place your isp's dns addresses in the primary and backup dns boxes in the router setup page, set the router for dhcp and away you go!  To be on the safe side, be sure to check with your isp if this type of service is ok.

---

### Post by Sencer on 2006-11-21
> Is there any simple way to do this?

Assuming that you also want to activate the firewall on the router and you want to run Ubunto on it, you can take a look at this howto in conjunction with Firestarter (very simple GUI front-end for iptables):

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

The better alternative would probably be to have a headless, dedicated machine for routing. There are several linux distributions that are built for that specific goal:
[http://distrowatch.com/dwres.php?resource=firewalls](http://distrowatch.com/dwres.php?resource=firewalls)

In all cases, the basic steps will be the same:

1) Configure all ten clients to use DHCP.
2) Set-up the 11th machine's internet access, enable DHCP server and manipulate routing table accordingly (the last two step all distros will probably do for you).

---

