---
title: "pppd IPCP request"
date: 2023-08-29
forum: Networking &amp; Wireless
---

### Post by michaelgu2 on 2023-08-29
Runng device with IPV6 address only.
Starting PPP establishment and want to reject IPCP request from pppd.
pppd recived reject , but not stopping to send IPCP request in a loop.

 sudo pppd noauth /dev/ttyUSB2 921600 +ipv6 kdebug 0 nodetach debug crtscts
using channel 22
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x73766d93> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1428> <asyncmap 0x0> <magic 0xe3509b2b> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1428> <asyncmap 0x0> <magic 0xe3509b2b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x73766d93> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x73766d93> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x73766d93]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
sent [IPV6CP ConfReq id=0x1 <addr fe80::bc25:4652:3e8a:32d9>]
rcvd [IPV6CP ConfReq id=0x1 <addr fe80::d4a9:a766:893c:1fbd>]
sent [IPV6CP ConfAck id=0x1 <addr fe80::d4a9:a766:893c:1fbd>]
rcvd [LCP EchoRep id=0x0 magic=0xe3509b2b]
rcvd [CCP ConfReq id=0x1]
sent [CCP ConfAck id=0x1]
rcvd [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [CCP ConfReq id=0x2]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <addrs 0.0.0.0 0.0.0.0>]
rcvd [IPV6CP ConfAck id=0x1 <addr fe80::bc25:4652:3e8a:32d9>]
local  LL address fe80::bc25:4652:3e8a:32d9
remote LL address fe80::d4a9:a766:893c:1fbd
Script /etc/ppp/ipv6-up started (pid 77545)
Script /etc/ppp/ipv6-up finished (pid 77545), status = 0x0
rcvd [CCP ConfAck id=0x2]
rcvd [IPCP ConfRej id=0x2 <addrs 0.0.0.0 0.0.0.0>]
sent [IPCP ConfReq id=0x3]
rcvd [IPCP ConfRej id=0x3]
sent [IPCP ConfReq id=0x4]
rcvd [IPCP ConfRej id=0x4]
sent [IPCP ConfReq id=0x5]
rcvd [IPCP ConfRej id=0x5]
sent [IPCP ConfReq id=0x6]




Any ideas

---

