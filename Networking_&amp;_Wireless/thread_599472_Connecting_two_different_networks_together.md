---
title: "Connecting two different networks together"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by z00s on 2007-11-01
I have two different networks set up. One network configuration runs as such:

Netopia T1 > Juniper Router > 24-port Linksys Switch > PCs

The second network is much smaller and is set up as follows:

DSL Modem > 4-port Linksys Router > PCs

What I'd like to do is connect these two networks such that the systems on each network still receive their DHCP configuration from their respective routers, but at the same time still see each other so that file sharing can take place.

As far as physically setting this up, what would be the procedure? Thanks in advance.

---

### Post by mpokrywka on 2007-11-03
Few clarifications needed:
0) I assume PCs in both networks have private IP addresses (i.e. 10.0.0.0 or 192.168.0.0), "routers" perform NAT on Internet connection?
1) "each network still receive their DHCP configuration from their respective routers" - but can you configure it so that addresses are not the same?
If IP addresses may be the same in both networks then connection can be done but only one side would be able to start "file sharing" connection.
2) "file sharing" - you mean Microsoft Network/Network Neighbourhood/Samba?
3) "at the same time still see each other" - do you require samba network browsing to work across both networks?

Overall solution would be:
- different addresses in networks (i.e. 192.168.0.0/24 and 192.168.1.0/24),
- PC with linux in each network with OpenVPN to interconnect networks (will also require tweaking routing on routers and port forwarding on one router),
- if samba browsing is required, then samba server in one network and adding DHCP option "Wins server" in other network.

---

