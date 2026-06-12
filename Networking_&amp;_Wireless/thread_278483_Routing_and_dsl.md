---
title: "Routing and dsl"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by feathers on 2006-10-16
Routing is one of the topics I don't seem to understand. I have a computer action as firewall for a lan with two ethernet cards. Connection to the internet was done through a hardware router. I now want to get rid of the hardwarerouter as it is not configurable. I ran pppoeconf to connect to the internet via the dsl modem. pppstatus tells me that the connection is up but I don't get a connection anywhere. Neither ping with ip address nor with host name works. I think this has to do with routing and gateway. As gateway, the ip address of the hardware router was used. Changing this to the local ip address of eth0 (card formerly connecting to the hardware router) did not help. Now what can I do?
1. In the firewall as well as in the routing table, eth0 is used as one of the devices. Do I have to exchange this for ppp0?
2. Where can I look for misconfiguration?
Thanks for your help.

---

### Post by mips on 2006-10-16
Uhm, you dont provide must info, some config files might help.

btw, your gateway is usually your next-hop address and not a local one.

---

### Post by DJ Scribblinni on 2006-10-16
From what are you saying, it seems that you are reusing the info that your router would be using, now that it is gone, the modem is what will be giving your computer the configuration it needs to access the internet.  Now most modems I have used, you need to use dhcp, rather than statically changing everything, in which the modem will provide you with and address and gateway.

---

### Post by feathers on 2006-10-18
It is working now, it really was a routing issue. I have been fiddling with the settings long enough now but unfortunately I don't know what really did it. Thanks for your help.

---

