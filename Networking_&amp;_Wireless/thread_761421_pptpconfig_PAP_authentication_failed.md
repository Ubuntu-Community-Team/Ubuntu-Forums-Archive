---
title: "pptpconfig: PAP authentication failed"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by glederfein on 2008-04-21
Hey all!
I connect to the internet through a router by DHCP.
I am trying to connect to a PPTP VPN server (ip=132.68.254.109) using "pptpconfig" but I am unsuccessful. Here is the output:
```
using channel 47
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x29523a6a>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth pap> <magic 0x353dd3d2>]
sent [LCP ConfAck id=0x1 <mru 1400> <auth pap> <magic 0x353dd3d2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x29523a6a>]
sent [PAP AuthReq id=0x1 user="ccdis3.technion.ac.il\\sgdled" password=<hidden>]
rcvd [PAP AuthNak id=0x1 "Request Denied"]
Remote message: Request Denied
PAP authentication failed
sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
rcvd [LCP TermReq id=0x2]
sent [LCP TermAck id=0x2]
rcvd [LCP TermAck id=0x2]
Connection terminated.
Script pptp technion_vpn --nolaunchpppd  finished (pid 14247), status = 0x0
pptpconfig: pppd process terminated by signal 19 (failed)
pptpconfig: SIGSTOP
```
It seems there is a problem with the PAP authentication. I tried all kinds of options in the "Encryption" tab however this doesn't seem to help.

Please help me!

---

### Post by glederfein on 2008-04-23
Does anyone have any idea why I can't connect??

---

