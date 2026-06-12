---
title: "Bridging through XP box"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by wildbillnj1975 on 2008-09-09
I need to use a VPN to connect to my company's network (and they don't support a Linux client).  Theoretically it should be possible to configure the routing on my Ubuntu box, so that it goes through the VPN connection on my Windows PC (ideally, it should do this only through a certain range of IP addresses).

For example, if my company's network uses IPs matching 123.45.*.*

I would like any communication from my Linux box to be routed to my PC (on the same home network, of course).  We are assuming here that my PC already has the VPN client running and connected.  The 123.45.*.* traffic should then go through the VPN connection and I should be able to complete the connection from the Ubuntu box straight to my company's network.

Any suggestions on where I should start?

I assume that this would also involve special configuration on my router, and possibly on my PC as well (particularly with the firewall).

P.S. I know I could use VirtualBox to stuff a Windows OS onto my Linux box, but I'd still have to configure a bridge of some sort, and I'd rather not waste the disk space or CPU power.

---

