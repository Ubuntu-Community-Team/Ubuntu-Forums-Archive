---
title: "Bind network response to incoming NIC?"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by Gaven on 2015-01-08
I'm in the middle of a massive in-place network overhaul.  Part of the migration requires that I temporarily have my RADIUS server on the old and new subnet at the same time.  For what it's worth, routing is in place between both subnets.  I need a configuration like this:

eth0:  10.0.0.2/24  gw: 10.0.0.1
eth1:  10.0.1.2/24  gw: 10.0.1.1

It would appear that with my current configuration, that breaks all traffic coming through either gateway.  As best I can tell, if I (for example) ping 10.0.0.2 from the other subnet (let's just say 10.0.1.3) it attempts to cut out the middle-man and reply directly from eth1.  That is the behavior I need to disable.  Is there a way to tell Ubuntu to always return network traffic via the interface it came in as opposed to the most direct route?

---

