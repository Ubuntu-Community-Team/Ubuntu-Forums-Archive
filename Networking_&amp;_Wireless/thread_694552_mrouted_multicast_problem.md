---
title: "mrouted multicast problem"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by wtfman on 2008-02-12
hi all,
i use mrouted to route multicast between interfaces.
mrouted documentation is very poor and google does not help, maybe this is TOO simple to use or me is TOO stupid to understand basilar things, but my problem is still there.

this is the scenario:
1 linux machine with 3 interfaces
eth0 10.91.195.23
eth1 10.50.4.24
eth2 90.202.231.2

i just want to:
1.route multicast from eth2 to eth0
2.be able to do a join to the group 233.49.81.255 from eth0 network to eth2
3.stop working with this motherfxxk multicast and go out from this noisy office
nothing more
this is my mrouted.conf:
(just 2 lines)
---

phyint eth0 rate_limit 0 igmpv1
phyint eth2 rate_limit 0 igmpv1
----

what have i to add/remove from the config file??

my kernel is well compiled with multicast support.

thanx to everyone tries to help me

---

### Post by netztier on 2008-02-12
> **wtfman said:**
> hi all,
i use mrouted to route multicast between interfaces.
mrouted documentation is very poor and google does not help, maybe this is TOO simple to use or me is TOO stupid to understand basilar things, but my problem is still there.

this is the scenario:
1 linux machine with 3 interfaces
eth0 10.91.195.23
eth1 10.50.4.24
eth2 90.202.231.2


Looking at the AS number encoded in 233.*49.51*.255, I think you must be trying to connect to a certain Frankfurt based company, then. Which is also known for their somewhat questionable use of the 90.0.0.0 /8 address space inside a private network.

According to it's man page, mrouted is a routing deamon that implements Distance-Vector Multicast Routing Protocol (DVMRP), and  using it is only advised if the routers on the 90.202.231.0 /24 network also use this protocol. However, I suspect that these routers (probably Cisco devices) are only enabled for PIM (Protocol Independent Multicast), and hence your DVMRP-speaking mrouted will have problems interoperating with them. 

Can you check with the network connectivity guidelines of the well-known company if they support DVMRP? 

Ciscos have an interoperability mode to allow DVMRP routers to "connect" to PIM clouds - you might have to ask your network engineers to enable it on the router(s).


regards

Marc

---

### Post by wtfman on 2008-02-12
hi folks,
hi soved my problem,
the stupid developer setted the ttl of packets to 1!!!!!!!
:S
everything works fine right now!
---
kill the developers!

---

