---
title: "[server]openvpn not working"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by gijs007 on 2014-06-05
I've got a small Linux VPS which I want to setup as a VPN to benefit of better networking at a different datacenter, without the need to move our servers.

I've followed the tutorial on: [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html) and I'm trying to connect to my openvpn server with Viscosity on windows server 2012 R2.

I keep getting the following error: Jun 5 03:21:13: read UDPv4: Connection reset by peer (WSAECONNRESET) (code=10054)
On linux: When I type service openvpn status it says VPN "server" is not running.

I'm new to openvpn and ubuntu and was hoping someone could help me out with this.

---

### Post by gijs007 on 2014-06-05
I've also tried this tutorial but I still get the connection reset by peer error..

Update:
I checked the syslog file and found the following error
 --server directive network/netmask combination is invalid

I fixed this by changing: server 23.246.204.10 255.255.255.248 to server 23.246.204.0 255.255.255.248

I was able to setup the vpn connection, but it assigned IP server 23.246.204.6 to my VPN and I only have access to 23.246.204.10 to 23.246.204.15
I put it to: server 23.246.204.8 Then it said: --local addresses must be distinct from --ifconfig addresses

How can I fix this?

---

