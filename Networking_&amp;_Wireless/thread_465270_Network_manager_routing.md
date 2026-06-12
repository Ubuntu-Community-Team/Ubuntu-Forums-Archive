---
title: "Network manager routing"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by mac on 2007-06-05
Does any one know how to setup NM to add a route every time that it connects to a VPN?

I'm using pptp plugin and I'm able to connect, even the dns resolve names of the VPN, but I can not connect to them unless I add a route manually to the destination network through ppp0.

I have a routing tab in the pptp setup but it seems to do nothing. I did check the option "Only use VPN connection for these addresses" and I did enter the network ip, in my case is 192.168.2.0/24, I don't really know what /24 means but it seems to make no difference the value that I place in there since no route to ppp0 is being added.

Thanks
Mario

---

### Post by turinglabs on 2007-06-06
> **mac said:**
> Does any one know how to setup NM to add a route every time that it connects to a VPN?

I'm using pptp plugin and I'm able to connect, even the dns resolve names of the VPN, but I can not connect to them unless I add a route manually to the destination network through ppp0.


I don't think this is possible with the GUI, you'll have to jump to CLI. In /etc/network/interfaces, you could add a 'post-up' route command to the ppp0 stanza, something like this:

post-up route add -net 192.168.2.0 netmask 255.255.255.0 dev ppp0

This will add the route *after* ppp0 is up. Here 192.168.2.0 is the network on the other side of the VPN. 

You probably want to delete the route when the VPN goes down:

down route del -net 192.168.2.0 netmask 255.255.255.0  dev ppp0

The /24 you mentioned is the netmask, just a way of specifying 8-bits worth of host IP addresses (32 bits in an IPv4 address, 32-24=8 ),  /24 is equivalent to 255.255.255.0. In the case of this 8-bit mask, there are 256 IP addresses (2^8 = 256), with the first and last reserved, leaving 254 usable IP addresses. If you're interested, there's tons to know, I talk a bit about IP addresses and netmasks in a presentation I gave to a local LUG, it is here in various formats:

[http://geekpit.blogspot.com/2006/03/tcpip-and-linux-network-security-with.html](http://geekpit.blogspot.com/2006/03/tcpip-and-linux-network-security-with.html)

---

