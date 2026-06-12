---
title: "Trying to run pptpd server in conjunction with an openvpn client"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by justin44 on 2014-04-30
Hi.. I have an openvpn connection to a remote vpn (tun0) and am running a pptp server (pptp0) on my computer.  I'd like any connected pptp client's traffic to route through the openvpn connection like the computer in question would do if you were sitting in front of it.  Now, I can get this to work just fine if I open a pptp connection from my android phone when i'm connected to my lan.  When I disable my wifi and go over the 4g network a connection can't even be established with pptp and nothing gets logged in syslog.  If I stop the openvpn connection and tun0 goes down I can connect from my android on the 4g network fine (but of course it won't route out my stopped openvpn connection).

My lan is on a 192.168.x.x subnet, pptpd assigns clients an ip on the same subnet, and the openvpn connection gets a 10.10.1.x ip from the openvpn server it is connecting to.

Anybody know how to accomplish this or can help?

Thanks.

---

### Post by justin44 on 2014-05-01
I abandoned pptpd and setup an openvpn server and I have the same problem. Something about the openvpn client connection is preventing establishment of a connection to the servers.... as I've said, if I take down the client I can connect to the server just fine.

---

### Post by justin44 on 2014-05-02
I know the traffic is at least getting to my computer.


I ran "tcpdump -i eth0 udp port 4201" and attempted to connect from my android phone's 4g connection and it replied:


17:50:35.136639 IP 45.sub-70-XXX-XXX.myvzw.com.2064 > Magicbox.local.4201: UDP, length 14
17:50:37.041610 IP 45.sub-70-XXX-XXX.myvzw.com.2064 > Magicbox.local.4201: UDP, length 14


That, of course, was as far as it got. Next I connected to my wifi and ran the same command:


17:50:51.964877 IP myrouter.local.32932 > Magicbox.local.4201: UDP, length 14
17:50:51.965358 IP Magicbox.local.4201 > myrouter.local.32932: UDP, length 26
17:50:51.967367 IP myrouter.local.32932 > Magicbox.local.4201: UDP, length 26


This connected instantly to the VPN.  So I guess I have some routing problem or something?  Hopefully this is a big enough clue for someone to bail me out.  Thanks.

(Also, I am pushing the route 10.20.30.0 255.255.255.0 in the server conf too rather than the 192.168.2.0)

---

