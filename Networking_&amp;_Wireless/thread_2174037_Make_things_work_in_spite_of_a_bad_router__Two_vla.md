---
title: "Make things work in spite of a bad router?  Two vlans same hardware, no 802.1q"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by 1clue on 2013-09-12
Hi,

I have a customer with a crappy AT&T-supplied router.  My customer leases the router, they don't have configuration access.  If you google the router model, the first link is a review saying "not very good."

They have 4 public IPs and then the traditional local network on 192.168.x.y.  The router manufacturer's solution to port passthrough is to give these public addresses, which are completely open, and then everything else is on the 192.168.  There's no configuration of ports, and anyone who wants can just statically configure their system to one of the public addresses and it works.

The problem is, both 192.168.x.y packets and the public net packets are all traveling on the same wires and across wireless.  The first packet from one "net" to the other goes through the router, and then the TCP stack realizes it's the same and tries for direct.  This obviously breaks functionality.  I can reboot a system, then hit it exactly once from the other net, and then after that it's broken.  I can go from the private net to the private net as often as I like.

I've made my case to the customer to buy another router, but it might be tomorrow or it might be a couple months from now, I have no idea.

I want to make something that will work temporarily until the new hardware comes:

[LIST=1]
[*]I want to configure the Linux-based systems to ignore all traffic from another network which does not come from the router.
[*]I want to configure the Linux-based systems go through the router for all traffic on another subnet, even if the route could be direct.
[*]Is there something I can do which will survive the system being plugged into a different network?  Assume DHCP leases.
[/LIST]

Thanks.

---

### Post by s-bodet on 2013-09-15
> **1clue said:**
> and then the TCP stack realizes it's the same and tries for direct.


From a pure TCP/IP prospective, both IP source and destination have no clue they're onto the same cable therefore packets should go through their local IP gateway (the AT&T gawteway).

You should look at a Wireshark/tcpdump trace for a better understanding of the issue before going further.

Steve

---

### Post by 1clue on 2013-09-15
I have looked.  The packets start by going through the gateway and then switch to direct.  I don't know what's causing the switch, but I know it's not correct and that it breaks the connection in some cases, others seem to continue anyway.

---

