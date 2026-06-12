---
title: "Ubuntu to responding to Router Advertisement (DHCPv6 or SLAAC)"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by Blair_Ellis on 2014-08-06
I have a juniper router configured as a IPv6 router.  that router will respond to a Router Solicitation from my Ubuntu server using rdisc6.  The RA shows up on my Ubuntu machine using wireshark.

BUT.. my Ubuntu server will not send a request on its own.

accept_ra set to 1
autoconfig set to 1
forwarding set to 0

In both all and for the specific interface.

This has been way too difficult for something 'automatic!'  I've tried wide-dhcp6c but no luck. 

Any ideas?  Basically Ubuntu gets the RA from rdisc6 but doesnt respond..

---

