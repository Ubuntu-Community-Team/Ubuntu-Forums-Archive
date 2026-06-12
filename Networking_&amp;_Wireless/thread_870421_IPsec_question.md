---
title: "IPsec question"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by tempus6 on 2008-07-25
I have a VPS linux box running ubuntu and I am trying to use it as a ipsec vpn endpoint than can be used to access the internet.  I got my router talking ipsec to the vps using freeswan ok but thats as far as I can get.  My setup is as follows:

LAN (192.168.2.xxx) <--> Router (Public IP A) <--IPsec tunnel--> VPS (Public IP B)

Now what I am trying to do is tunnel all internet borne traffic from my LAN through the tunnel, through the VPS to the internet.  Basically I would like to be able to access port 25 on the VPS public IP and have that port forwarded to port 25 on a LAN IP.

Anyone got any suggestions?  It seems that I am having problems port forwarding from the external address through the tunnel.

---

