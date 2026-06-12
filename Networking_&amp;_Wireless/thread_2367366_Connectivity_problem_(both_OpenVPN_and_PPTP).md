---
title: "Connectivity problem (both OpenVPN and PPTP)"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by pdbc on 2017-07-29
Hi everybody.

I have a PC with Ubuntu 16.04, connected via eth to a router and then WAN. I set up on this Ubuntu machine a VPN connection with PureVPN, both in OpenVPN and PPTP. No problem with the connection to PureVPN servers, but...every now and then, it starts to exchange no packet at all. It is not a problem of PureVPN, because an other PC (Windows 7) connected to the same router and with the same VPN connection is working properly, so the problem is inside the Ubuntu machine. I tried deactivating firewall (by GUI) and flushing iptables ("iptables -F"), but the problem is still there: after the PC is started, everything goes well for maximum a minute, then no way to exchange packets, and I have to deactivate VPN connection in order to be online.

What must I check and how in order to understand where is the problem to be fixed?

Thanks.

---

### Post by TheFu on 2017-07-31
Since nobody else has tried to help .... 

Can't help either, I've never used any GUI for VPN stuff.  Much prefer to use straight openvpn and setup the .ovpn config for each different exit node I need.  L2TP+IPSec are preferred from a security standpoint.  Privacy is harder.

[https://restoreprivacy.com/vpn-server-locations/](https://restoreprivacy.com/vpn-server-locations/) might be of interest for your consideration.

Also, pptp shouldn't be used if you care at all about security or privacy.  The protocol has been hacked for about 15 yrs, but tools to break it became widely available to everyone in 2012.

---

### Post by pemicool on 2017-11-28
I have a very similar problem. In my case I can establish the connection  with the VPN provider but I cannot access any internet location after  that.

The same configuration with the same provider works in all other devices  I have and it was working in Ubuntu until a few months back.

Thank you.

---

### Post by photonxp on 2017-11-28
@pdbc
Do you know where to see the log file of PureVPN? Does its official document/website/support-team handle this kind of problem? Perhaps you can try to get in contact with the support of the official site if that's possible. 

Probably PureVPN would react quickly if they don't want to lose a customer, unless they don't like customers.

---

### Post by pemicool on 2017-12-09
Already did. do not think the problem is on their side.

By the way this is what I get in the IP route list:
default@PO-UBUNTU:~$ ip route list
  default dev ppp0  proto static  scope link  metric 50
  default via 192.168.1.1 dev enp7s0  proto static  metric 100
  79.172.193.105 via 192.168.1.1 dev enp7s0  src 192.168.1.2
  169.254.0.0/16 dev enp7s0  scope link  metric 1000
  172.111.129.2 via 192.168.1.1 dev enp7s0  src 192.168.1.2
  172.111.129.4 dev ppp0  proto kernel  scope link  src 172.111.129.15  metric 50
  192.168.1.0/24 dev enp7s0  proto kernel  scope link  src 192.168.1.2  metric 100

---

