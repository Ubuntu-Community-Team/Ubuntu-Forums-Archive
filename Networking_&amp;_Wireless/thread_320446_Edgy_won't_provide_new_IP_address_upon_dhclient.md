---
title: "Edgy won't provide new IP address upon dhclient"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Azalin on 2006-12-17
For reasons I shall not go into right now, I have had to change the whole network here. I went from 192.168.0.0 network to a 192.168.1.0 network where the router is 192.168.1.254
My Edgy computer used to have an IP address 192.168.0.13 after the network change, the only way for me to get online is to specify a static IP address. :-k 
However, I am also using (not at the moment since it can not handle static IP addresses in network/interfaces) network-manager (with the pptp plugin for vpn connections to my work).
So I need to have the dhcp assigned IP addresses otherwise network-manager doesn't work.
Now, when I do sudo dhclient I get the following:

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:31:b2:f0:4b
Sending on   LPF/eth0/00:17:31:b2:f0:4b
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
SIOCADDRT: Network is unreachable
bound to 192.168.0.13 -- renewal in 381404 seconds.

And the network card is assigned the old ip address instead of getting the new ip address from the router. What am I doing wrong? Where can I force Edgy to update this IP address?

**_Please help!_** Since I am forced to have a static IP and am not able to VPN to work because I can not use network-manager because of the static IP... ](*,)

---

### Post by Azalin on 2006-12-17
Resetting the router helped... ](*,) :confused: Weird router...:rolleyes:

---

