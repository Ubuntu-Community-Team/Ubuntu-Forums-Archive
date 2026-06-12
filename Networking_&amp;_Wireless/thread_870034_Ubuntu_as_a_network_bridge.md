---
title: "Ubuntu as a network bridge?"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Arbiter on 2008-07-25
Hi all,

I've searched high and low for a possible answer to this, which has been plaguing me for some time now, I would greatly appreciate any help at all on this...

I have to manage a network, but truth be told, I'm not all that saavy about the details of IP and routing, but I'm working on getting up to speed with it.

Is it possible to use Ubuntu as a bridge (or router?) to have two subnets talk to each other seamlessly (no mucking about with firewalls) like they are on the same subnet?  The main network has the address of 192.168.19.* and the new subnet i've put together has an address range of 192.168.20.*

So basically, is it possible to have these two talk together seamlessly and have all sides see each other and have internet access?  I'd like to do this with an ubuntu box.

---

### Post by Fire_Chief on 2008-07-25
You will need to configure the Ubuntu box as a router between the networks. Have one NIC configured for each network with the default route on the Ubuntu box pointing to your Internet router. For example, if the Internet router is IP 192.168.20.254, then the Ubuntu "router" will look something like this (your IPs may vary)...

eth0  192.168.20.1  netmask 255.255.255.0   gw 192.168.20.254
eth1  192.168.19 1  netmask 255.255.255.0   no gateway

The PCs on the .19 network would have 192.168.19.1 set as their default gateway. The Internet router needs to have a static route configured on it that points traffic for the .19 network to 192.168.20.1.

192.168.19.0  netmask 255.255.255.0  gw 192.168.20.1

Systems on the .20 network should only need to have their default gateway set to the Internet router to reach the .19 PCs.

Cheers!

---

### Post by Arbiter on 2008-07-25
> **Fire_Chief said:**
> You will need to configure the Ubuntu box as a router between the networks. Have one NIC configured for each network with the default route on the Ubuntu box pointing to your Internet router. For example, if the Internet router is IP 192.168.20.254, then the Ubuntu "router" will look something like this (your IPs may vary)...

eth0  192.168.20.1  netmask 255.255.255.0   gw 192.168.20.254
eth1  192.168.19 1  netmask 255.255.255.0   no gateway

The PCs on the .19 network would have 192.168.19.1 set as their default gateway. The Internet router needs to have a static route configured on it that points traffic for the .19 network to 192.168.20.1.

192.168.19.0  netmask 255.255.255.0  gw 192.168.20.1

Systems on the .20 network should only need to have their default gateway set to the Internet router to reach the .19 PCs.

Cheers!

Awesome, thank you!  Only one slight question...where do I define these routs?  I know for the NICs its in /etc/network/interfaces (or somesuch) but where do i set the "static route" you spoke of?

---

### Post by Arbiter on 2008-07-25
bump?

---

### Post by Fire_Chief on 2008-07-30
Hey Arbiter,

Have you made any progress since the PM conversation a couple of days ago?

Cheers!

---

### Post by dmizer on 2008-07-30
Have a look at the wiki: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Let me know if you have any problems with it.

---

