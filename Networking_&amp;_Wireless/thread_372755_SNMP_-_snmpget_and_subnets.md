---
title: "SNMP - snmpget and subnets"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by rezet on 2007-02-28
Hi.

I'm having some difficulties with snmpget from another subnet.
The Ubuntu-server which is running Nagios is on subnet x.x.41.x and most of the printers hangs on the x.x.42.x subnet. 
I am able to use snmpget towards the printer in the same subnet as the ubuntu-server, but not towards the other printers.

I think I have seen something about this somewhere, but can'r recall where.

Anyone have any hints?

---

### Post by mouseclone on 2007-06-01
I'm not sure if you have figured this out or not, so i'm going to explain some things.

x.x.41.x and x.x.42.x really doesn't explain anything at all.  10.1.42.x and 100.1.41.x are better they they are not even in the same subnet.

so lets break some of this down

we have a server on network 10.1.41.0
we have printers on network 10.1.42.0
IF your subnet is 255.255.0.0 they will be able to talk with each other.
IF your subnet is 255.255.255.0 they will not be able to talk with each other and you will need a router.

You router will have to allow the snmp protocol to route though the different subnets.  You cannot block the port number for snmp.

I use snmp over several networks and have no problems.  The ports are open and the routers will route the protocol.

---

