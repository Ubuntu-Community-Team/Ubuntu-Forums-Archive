---
title: "Dual Network Card Problem"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by dbarszczak on 2008-01-16
Hi all,

I have a Ubuntu LAMP box that is running a vle system called Moodle. Moodle authenticates through our LDAP box so one of the NIC's is attached to the LAN. The other NIC is attached to the internet.

I think my problem is that our network is on a 10.4.x.x range which by an amazing coincidence so do our ISP.

Both cards will work on their own but not together. I feel that some sort of firewalling is required but im not sure.

Hope someone can help me.

Thanks.

---

### Post by sqrt2 on 2008-01-16
If both interfaces are connected to separate networks with the same IP address range (and netmask), things are bound to be broken. The kernel has no way of knowing which of both networks is meant (you will have duplicate entries in the routing table, just with different interfaces) and will choose one interface above the other (depending on the routing table).

By the way, your ISP assigning you an IP adress in a private address range (10.0.0.0/8) is a very strange thing. Why don't you have a public IP address?

---

### Post by dbarszczak on 2008-01-16
It's a school which gets it internet through the local authority so in reality we are just part of a WAN.

Can i tell the routing table to use the external NIC just for the DNS and gateway and the internal for the rest?

Im really struggeling with this one.

---

### Post by sqrt2 on 2008-01-16
You can define routes to certain hosts by using
[indent]route add -host <host-ipaddr> dev <interface>[/indent]
I wouldn't bet that solves the problem, though.

---

### Post by dbarszczak on 2008-01-17
Your a star!!!

That worked great.

I routed my gateway and DNS servers through eth0 and everything else through eth1 and changed my default gateway to that of my ISP.

Now all the machine can see the server internally and the server can see the internet.

This website was really useful:
[http://linux-ip.net/html/tools-route.html](http://linux-ip.net/html/tools-route.html)

Thanks for pointing me in the right direction.

---

