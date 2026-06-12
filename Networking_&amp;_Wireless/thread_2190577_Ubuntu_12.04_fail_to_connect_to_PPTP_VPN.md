---
title: "Ubuntu 12.04 fail to connect to PPTP VPN"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by banz on 2013-11-28
I'm running ubuntu 12.04 in vmware. The network connection is running in bridge mode. I'm trying to connect to my vpn server using command line [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

I'm sure the vpn works, as it connects fine with my windows machine and android phone.

This is my vpn log so it seems to establish the connection fine.

> using channel 9
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5d1a0bd> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xc65ae795> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xc65ae795> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5d1a0bd> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x5d1a0bd]
rcvd [LCP EchoReq id=0x0 magic=0xc65ae795]
sent [LCP EchoRep id=0x0 magic=0x5d1a0bd]
rcvd [CHAP Challenge id=0x1d <e1a713ac563e9796d19b53a80e508df6>, name = "pptpd"]
sent [CHAP Response id=0x1d <2c1b2fc24ee76a1dcb18ac30712c0c7e0000000000000000d2190880ae45acc1009f0db52a812809120fca16176b409c00>, name = "banz"]
rcvd [LCP EchoRep id=0x0 magic=0xc65ae795]
rcvd [CHAP Success id=0x1d "S=B3DD9D98BCB681671598BDC4AAF21A94BF3BA081 M=Access granted"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.5.1>]
sent [IPCP ConfAck id=0x1 <addr 192.168.5.1>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 192.168.5.10>]
sent [IPCP ConfReq id=0x3 <addr 192.168.5.10>]
rcvd [IPCP ConfAck id=0x3 <addr 192.168.5.10>]
local  IP address 192.168.5.10
remote IP address 192.168.5.1
Script /etc/ppp/ip-up started (pid 12796)
Script /etc/ppp/ip-up finished (pid 12796), status = 0x0

This is the routing table
> default         192.168.61.253  0.0.0.0         UG    100    0        0 eth0
192.168.5.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.61.0    *               255.255.255.0   U     0      0        0 eth0
spmental2.info  192.168.61.253  255.255.255.255 UGH   0      0        0 eth0

However no traffic goes through it
> ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.5.10  P-t-P:192.168.5.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:60 (60.0 B)  TX bytes:234 (234.0 B)



Is there something that I missed out?

---

