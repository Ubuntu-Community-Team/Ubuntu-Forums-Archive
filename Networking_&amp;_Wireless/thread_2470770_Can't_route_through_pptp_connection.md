---
title: "Can't route through pptp connection"
date: 2022-01-10
forum: Networking &amp; Wireless
---

### Post by emiked on 2022-01-10
Running Ubuntu 18.04.4 LTS

Got PPTP working (I know, but that's what I'm connecting to requires).

Got UFW working with PPTP.

From the Ubuntu box (192.168.2.6), I can ping my endpoint address (10.1.0.236) , the remote endpoint address (10.1.0.6), and a remote server (10.1.0.49).

Ip forwarding is turned on.

Masquerading is turned on.

From a another box on the local lan, I can ping 10.1.0.236, but not 10.1.0.6 or 10.1.0.49.  This acts like ip forwarding is turned off, but it's not.

Static route on the Ubuntu box: route add -net 10.1.0.0 netmask 255.255.255.0 gw 10.1.0.6

Static route on the other local box: route add -net 10.1.0.0 netmask 255.255.255.0 gw 192.168.2.6

Again, from the pptp gateway box (Ubuntu):

##### LOCAL INTERFACE: SUCCESS
##### REMOTE INTERFACE: SUCCESS
##### SERVER INTERFACE: SUCCESS


And from the local box:

##### LOCAL INTERFACE: SUCCESS
##### REMOTE INTERFACE: failed
##### AMTOTE INTERFACE: failed

Any ideas on what else I should look at??

Is there a pptp setting that I need to add???

Thanks!

---

