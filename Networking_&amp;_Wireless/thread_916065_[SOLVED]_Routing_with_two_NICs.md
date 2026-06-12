---
title: "[SOLVED] Routing with two NICs ?"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by erland on 2008-09-10
Does anyone know how to setup the routing with a machine with two NIC's.

My setup looks as follows:
NIC1: Connected to 192.168.0.x  network
NIC2: Connected to 192.168.1.x network

Both networks has a NAT router in front of them which gives them internet access, that is, one router for each network.

What I want is:
- All incomming and outgoing requests from/to the 192.168.0.x network should use NIC1
- All incomming and outgoing requests from/to the 192.168.1.x network should use NIC2
- All incomming and outgoing requests from/to other networks should use NIC2

The current situation is that sometimes when I boot NIC1(eth0) is used as primary network interface and sometimes NIC2(eth1) is used as primary network interface. The result is that incomming traffic from internet is received correctly on NIC2(eth1) but I strongly suspect that the answer is going out on NIC1(eth0) which of course results in that the answer is sent through the other NAT router and lost.

It works correctly the times when NIC2(eth1) is considered to be the primary network interface after a reboot.

So is there some way to set this up so it works the same after each reboot ?

I'm using Ubunu 8.04 and I've tried to switch eth0 and eth1 but it doesn't make the situation any better.

---

### Post by fwre01 on 2008-09-10
sure, you need to write a one line script that looks like this...

```
route add default gw <gateway address on 192.168.1.0 subnet> metric 1
```

save it, and chmod 755 it.

Then add a line to /etc/rc.local that points to the script. Then, when you PC boots up NIC2 will be considered your primary default route. you can check its working by using the route command, this will print your routing table.

hope that helps!!

---

### Post by erland on 2008-09-11
Thanks, that solved it.

---

### Post by fwre01 on 2008-09-11
Could you mark this as solved? :-) Thanks

---

