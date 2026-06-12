---
title: "Network, routing problem"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Maxymillion on 2008-07-12
Hello, having a minor issue with my default routes. 2 interfaces in the server, with only 1 default gateway route. However after some time the second interface gets a default gateway route added for it.

To explain

Vlan0 
router/net
Virtual machines (guests on host)

Vlan1
router/net
Host (ubuntu server)
local lan machines

eth0 supplies internet to my server, eth1 is bridged to the virtual machines.

Everything works when I have a single default route (route add default gw 192.168.0.1 eth0). However after some time period I find it broken, and looking at route shows a second route has been automatically added for eth1 the bridge device. Doing (route del default route) makes everything work again. However after some arbitrary time period the route gets readded.

Please point me in the right direction to find the cuplrit :)

I tried googling this, but only found people seeking to setup double default gateways with 2 routes.

Thx for any advice

---

### Post by Maxymillion on 2008-07-12
My route tables to illustrate

WORKING  (i.e. host gets net via eth0 (aka bond0), VMs get net via bridge)

server@octocain:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.11    *               255.255.255.255 UH    0      0        0 tap1
192.168.0.10    *               255.255.255.255 UH    0      0        0 tap0
192.168.0.12    *               255.255.255.255 UH    0      0        0 tap2
192.168.0.0     *               255.255.255.0   U     0      0        0 bond0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap1
192.168.0.0     *               255.255.255.0   U     0      0        0 tap2
192.168.0.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 bond0
default         homewrt.lan     0.0.0.0         UG    100    0        0 bond0



10 minutes later without doing anything I get a second default route host no longer gets net :0
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.11    *               255.255.255.255 UH    0      0        0 tap1
192.168.0.10    *               255.255.255.255 UH    0      0        0 tap0
192.168.0.12    *               255.255.255.255 UH    0      0        0 tap2
192.168.0.0     *               255.255.255.0   U     0      0        0 bond0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap1
192.168.0.0     *               255.255.255.0   U     0      0        0 tap2
192.168.0.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 bond0
default         homewrt.lan     0.0.0.0         UG    0      0        0 br0
default         homewrt.lan     0.0.0.0         UG    100    0        0 bond0


sudo route del default removes the br0 default route and makes everything work

Stuck short of writing a script to sudo route del default every 5 minutes

---

### Post by andycwb on 2008-09-30
Did you ever find an answer to this, I've got the same problem?

---

