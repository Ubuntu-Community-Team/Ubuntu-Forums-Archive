---
title: "changing mtu for networkmanager-vpn"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by martijndenerd on 2007-08-22
Hi, 

I am using network-manager-vpn + vpnc to setup a vpn connection over a wired network. The mtu of this connection (tun0) is set on 1412 by default. However, I need it to be on 1200, otherwise many sites don't work. So my solution now is to connect my vpn using network-manager, then do sudo ifconfig tun0 mtu 1200 and all is fine. 
Of course it would be nicer to change the default setting of a vpn connection somewhere, so i can skip the ifconfig step. Anyone who knows where i can do this?  

Thanks!

Martijn
ps
 i know i can set this all up in /etc/network/interfaces but i'd like to keep using networkmanager...

---

