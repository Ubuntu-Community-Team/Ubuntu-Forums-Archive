---
title: "Two networks cards to different networks?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by TitanKing on 2007-07-09
Hi there thank you for looking at my thread!

I have two network cards;

eth0 = Static IP to ADSL router, ADSL router is not connected anywhere else on the internal network.
eth1 = DHCP connected to internal network, must have DHCP. 

How can I set the network to use eth1 when local and eth0 when accessing the internet?

Thanks in advance!

---

### Post by Andra on 2007-07-09
configure eth0 with its own address and and subnet mask, and default gateway, and configure eth1 for dhcp but if you can do not use (set for this interface) default gateway.
Suppossing, eth0 and eth1 are in diiferent subnets

---

### Post by spd106 on 2007-07-09
The problem you might run into is that the DHCP server used by eth1 might assign the wrong gateway and DNS name server addresses. 

To solve this edit the /etc/dhcp3/dhclient.conf file to not request a gateway or name server. Then set these statically in either the System -> Admin -> Networks utility or in the /etc/network/interfaces file for eth0.

You can check the current routing table with ip route. You should see that the local address subnet is directed to eth1 and the default gateway to the router's address via eth0.

---

### Post by TitanKing on 2007-07-10
Thanks for the replies guys will keep you updated! Thanks you all very much!

---

