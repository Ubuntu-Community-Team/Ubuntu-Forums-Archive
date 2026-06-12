---
title: "speedtouch 330 rev 4 silver"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by teaker1s on 2006-12-26
for my grandparents I have set up 6.06LTS and following [here]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")
I appear to have successfully logged on the dsl with chap and resolved DNS and been allocated an ip address from the log the problem is this

Plugin pppoatm.so loaded.
using channel 4
Using interface ppp0
Connect: ppp0 <--> 0.38
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [LCP ConfReq id=0x1 <magic 0x712bec0f>]
rcvd [LCP ConfReq id=0x66 <mru 1492> <auth chap MD5> <magic 0x52160b6b>]
sent [LCP ConfAck id=0x66 <mru 1492> <auth chap MD5> <magic 0x52160b6b>]
rcvd [LCP ConfAck id=0x1 <magic 0x712bec0f>]
sent [LCP EchoReq id=0x0 magic=0x712bec0f]
rcvd [CHAP Challenge id=0x1 <06a3dfbb8c536568b2080a044ce30890>, name = "Enfield-GLN3000-BAS0001"]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x1 <546bfb0355392eb6b0a5d992fdc29c6c>, name = "gerald7078.freeserve.co.uk@fs"]
rcvd [LCP ConfReq id=0xd5 <mru 1492> <auth chap MD5> <magic 0x52160b6b>]
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [LCP ConfReq id=0x2 <magic 0x8d93188b>]
sent [LCP ConfAck id=0xd5 <mru 1492> <auth chap MD5> <magic 0x52160b6b>]
rcvd [LCP ConfAck id=0x2 <magic 0x8d93188b>]
sent [LCP EchoReq id=0x0 magic=0x8d93188b]
rcvd [CHAP Challenge id=0x1 <009e824c24546d5a688d0a87efc694d1>, name = "Telecity-OLO577-BAS0001"]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x1 <f21b085ce2afec8d7302de0ed16a2219>, name = "gerald7078.freeserve.co.uk@fs"]
rcvd [CHAP Success id=0x1 ""] 00 00 00 00
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 195.92.214.14>]
sent [IPCP ConfAck id=0x1 <addr 195.92.214.14>]
rcvd [LCP ProtRej id=0x1 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 62.136.118.57> <ms-dns1 195.92.195.94> <ms-dns3 195.92.195.95>]
sent [IPCP ConfReq id=0x3 <addr 62.136.118.57> <ms-dns1 195.92.195.94> <ms-dns3 195.92.195.95>]
rcvd [IPCP ConfAck id=0x3 <addr 62.136.118.57> <ms-dns1 195.92.195.94> <ms-dns3 195.92.195.95>]
[COLOR="Red"]Cannot determine ethernet address for proxy ARP[/COLOR]
local  IP address 62.136.118.57
remote IP address 195.92.214.14
primary   DNS address 195.92.195.94
secondary DNS address 195.92.195.95

---

### Post by teaker1s on 2007-01-05
turned out pppd package bug causing ARP issue, affected lots of linux users-not found solution unless pppd package built from source would solve it](*,)

---

