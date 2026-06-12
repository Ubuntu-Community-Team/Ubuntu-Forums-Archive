---
title: "Juniper VPN with Ubuntu Hardy"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by sevaho on 2008-05-26
Hi,

I'm not sure if this is the right section to post but here it goes:

To access one of our client's network i use the Juniper web interface to initiate a VPN connection. 

After i log in i start the "network connect" java client which runs just fine and connects to the vpn server. I get an internal ip assigned to a new interface tun0 and i checked my resolv.conf, nameservers get updated after the connection but ...

Whenever i try to actually connect to an internal resource, exchange server or webserver etc, using RDP the connection times out. When checking the vpn client there is no incomming data from the other network only outgoing data from my side..


Any idea's? Works fine on any Windows pc but i'm trying to convert to Ubuntu and this is holding me back a bit.

---

