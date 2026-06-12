---
title: "pptp to windows 2003 server"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by mparker on 2006-08-02
Hi,

I'm having trouble connecting to windows pptp servers, I know I have the names and passwords correct because connections work fine with xp pro.
Can anyone provide me help?


Thanks in advance, 

==========================================================================
nodeflate               # (from /etc/ppp/options.pptp)
                # (from /etc/ppp/peers/hosting)
                # (from /etc/ppp/peers/hosting)
require-mppe-128                # (from /etc/ppp/options.pptp)
nomppe-128              # (from /etc/ppp/peers/hosting)
mppe-stateful           # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 32
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4d124b2> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x38791e5f> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:03.69.58.2f.95.55.4f.5b.aa.f1.e5.09.2a.c5.11.09.00.00.00.00]> < 17 04 00 29>]
sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 00 29>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4d124b2> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x38791e5f> <pcomp> <accomp> <endpoint [local:03.69.58.2f.95.55.4f.5b.aa.f1.e5.09.2a.c5.11.09.00.00.00.00]>]
sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x38791e5f> <pcomp> <accomp> <endpoint [local:03.69.58.2f.95.55.4f.5b.aa.f1.e5.09.2a.c5.11.09.00.00.00.00]>]
sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x38791e5f> <pcomp> <accomp> <endpoint [local:03.69.58.2f.95.55.4f.5b.aa.f1.e5.09.2a.c5.11.09.00.00.00.00]>]
sent [LCP EchoReq id=0x0 magic=0x4d124b2]
rcvd [CHAP Challenge id=0x0 <1f8f2a4f2ba6c7451bcba3aa73d43780>, name = "SPOCK"]
sent [CHAP Response id=0x0 <6b6c241539e01eeb8709e2107ad0d6e60000000000000000038e7e8e1b22bb6ad7721b762c500ba78f39c0935f8c14c800>, name = "sumtech"]
rcvd [LCP EchoRep id=0x0 magic=0x38791e5f]
rcvd [CHAP Failure id=0x0 "E=691 R=1 C=6058043D9A0E697DB9D67AE111B929CB V=3"]
Unknown MS-CHAP authentication failure: E=691 R=1 C=6058043D9A0E697DB9D67AE111B929CB V=3
CHAP authentication failed
sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
rcvd [LCP TermAck id=0x2 "Failed to authenticate ourselves to peer"]
Connection terminated.
Waiting for 1 child processes...
  script pptp spock.sumtech.com --nolaunchpppd , pid 18846
Script pptp spock.sumtech.com --nolaunchpppd  finished (pid 18846), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.204.0   0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.204.1   0.0.0.0         UG    0      0        0 eth2
pptpconfig: pppd process terminated by signal 19 (failed)
pptpconfig: SIGSTOP
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.204.0   0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.204.1   0.0.0.0         UG    0      0        0 eth2

---

