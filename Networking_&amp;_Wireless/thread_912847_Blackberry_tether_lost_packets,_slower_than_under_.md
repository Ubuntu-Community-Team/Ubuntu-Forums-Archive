---
title: "Blackberry tether lost packets, slower than under xp"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by nulix on 2008-09-07
Hi, sorry if this has been solved but I searched for hours and haven't found something similar.  I am using my blackberry tethered to a fresh ubuntu installation (eee pc 1000h).  The ppp connection starts up just fine with the following log:

sent [IPCP ConfReq id=0x3 <addr 10.36.26.205> <ms-dns1 149.254.201.126>]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15>]
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0c 1a 04 78 00 18 04 78 00]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
sent [IPCP ConfReq id=0x3 <addr 10.36.26.205> <ms-dns1 149.254.201.126>]
rcvd [IPCP ConfAck id=0x3 <addr 10.36.26.205> <ms-dns1 149.254.201.126>]
replacing old default route to ra0 [192.168.1.1]
Cannot determine ethernet address for proxy ARP
local  IP address 10.36.26.205
remote IP address 169.254.1.1
primary   DNS address 149.254.201.126
Script /etc/ppp/ip-up started (pid 7063)
Script /etc/ppp/ip-up finished (pid 7063), status = 0x0

and my route table looks as it should afterwards:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.1.1     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0


However when I ping google the dns lookup is instantaneous but the actual pings have massive packet loss, close to 100% but not always 100%.

PING google.co.uk (216.239.59.104) 56(84) bytes of data.

--- google.co.uk ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18024ms


I have tested the exact same APN settings etc under xp and I get a good connections with 100kbps download bandwidth (dslreports test).

This is on t-mobile uk with a blackberry curve.  Has anyone experienced anything similar? Anyone have a fix?  Any ideas would be appreciated.  Thanks

---

