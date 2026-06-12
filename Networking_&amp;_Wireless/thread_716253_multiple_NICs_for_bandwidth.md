---
title: "multiple NICs for bandwidth?"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by rotarymike on 2008-03-05
Is there any way in Ubuntu to get multiple NICs working? I've got several computers downstream of my Ubuntu server that need to pull heavy loads at the same time sometimes.

Machine: IBM S50 2.6GHz, built-in NIC
Additional NIC: Intel dual 10/100/1000 ethernet

all NICs seem to be up and running, but net traffic only seems to go through eth0 which is the built-in NIC. 

I'd like to use the two on the Intel card simultaneously to get double the bandwidth, if that is even possible. I seem to remember it as an option on Windoze boxes.

-Mike Harrington

---

### Post by tgalati4 on 2008-03-05
I don't think the default kernel can handle network traffic from two nics.  You can assign descrete IP's to many nics, but I don't Linux can stripe data between them.   You have to manually specify which link is "up" with the ifconfig command:  sudo ifconfig eth7 up

I think virtual machines can be set up such that each uses a different nic, but that doesn't really increase bandwidth, it just allows each virtual machine to have it's own IP address for its own purposes.

There may be a specialty kernel for this situation, but I've never seen it.

---

### Post by rotarymike on 2008-03-05
Bummer.

Oh well, I guess that's what I get for having a $50 server :)

---

### Post by netztier on 2008-03-06
> **tgalati4 said:**
> I don't think the default kernel can handle network traffic from two nics.  You can assign descrete IP's to many nics, but I don't Linux can stripe data between them.   You have to manually specify which link is "up" with the ifconfig command:  sudo ifconfig eth7 up

I think virtual machines can be set up such that each uses a different nic, but that doesn't really increase bandwidth, it just allows each virtual machine to have it's own IP address for its own purposes.

There may be a specialty kernel for this situation, but I've never seen it.


Nah, every kernel can do that - at least the server kernels as they come with Ubuntu Server. Read up about **bonding** ethernet interfaces, there's plenty of documentation around about it, also in this forum, for example [http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding](http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding)

However: for some bonding modes, especially if you want to increase inbound performance, your LAN switch will have to support bonding too (most often in it's IEEE 802.3ad "LACP" flavour). 

Be aware: Bonding four 100Mbps links will *not* get you one 400Mbps link, but one 4x100Mbps link. Like a freeway with the same speed limit, but more lanes. A single connection from client A to server B will (in most bonding modes) only ever use one of the links in the bundle, while connections from client C to server B will probably use the other one (in the LACP bonding mode, the number of the link that is going to be used is calculated from source and destination MAC addresses).

regards

Marc

---

### Post by tgalati4 on 2008-03-06
I stand corrected.

---

