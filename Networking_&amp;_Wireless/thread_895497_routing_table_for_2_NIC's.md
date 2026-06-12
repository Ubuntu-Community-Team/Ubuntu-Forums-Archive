---
title: "routing table for 2 NIC's"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by gnicezw on 2008-08-20
Hi, 

I have 2 linux machines; 1 ubuntu gutsy, 2 mandrake 2008 spring

both connect to a wireless router(192.168.1.1) and then the internet. 

they are also linked via a private network as I share alot of files between them. this is via an ethernet router (192.168.0.1)

I'd like to connect to both networks simultaneously but i'm having trouble configuring the routing tables on both computers and the automatic routes halt my wireless( and therefore internet) connection. 

on the ubuntu machine , eth0(192.168.0.3) = ethernet NIC 
and eth1(192.168.1.101) = wifi NIC . .. both dhcp from the routers 

route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

packets bound for 192.168.0.0 are fine but far as I can tell; anything going anywhere else is forwarded to 192.168.0.1 and not the internet via 192.168.1.1. 

How do I set up the routes correctly and permanently?

Thanks for reading. 

Gregg

---

### Post by ilrudie on 2008-08-20
just delete the default route for the network that will not be used to connect to the internet.  In your case I think it would be route del default dev eth0.  This route is not really necessary since you don't access the internet through it.  ARP is sufficient to handle the connection to the local network so routing shouldn't play a role in connecting to the lan on eth0.

As always with routing then route command is not permanent.  You must add the routing commands to the /etc/network/interfaces.  Put it in the correct stanza (eg routes concerning eth0 go in eth0's stanza) and use the up/down <route command> format.  Look at man interfaces if you aren't familiar with this.

You may also have to create a default route to the internet if for some reason it stops being created.  use route add default gw 192.168.1.1

This is probably happening because your routers are both advertising themselves as valid paths to the internet even though one of them isn't ubuntu believes them both and creates 2 default routes.  I can't think of a case when you would want 2 default routes though.

---

### Post by bab1 on 2008-08-20
Why route between to hosts that should be an the same segment?  Install a switch connecting the 2 hosts and the router.  They should all see each other.  The router only needs to be the GW to the internet.

---

### Post by gnicezw on 2008-08-23
Hi, 

Thanks for your replies, ilrudie i'll be attempting your solution this evening and I apologise for my tardiness which was due to a few deadlines last week. 

Babi; i'm connecting the 2 hosts so as not to strain the wireless network which has other users. these 2 hosts are in the same room and it made sense to connect them directly and I had as spare router handy.

---

