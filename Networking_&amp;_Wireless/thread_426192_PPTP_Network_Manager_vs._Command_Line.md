---
title: "PPTP: Network Manager vs. Command Line"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by cokhavim on 2007-04-28
PPTP VPN works great when I use the command line.  This is the command I use:

```

sudo route del -net 0.0.0.0
sudo pptp 10.1.0.1 debug user "jo%ra" remotename "my-uni-connection-name" defaultroute mtu 1452 mru 1452 noauth
```

These were the instructions given by my uni, which also included putting my username and password in the pap-secrets and chap-secrets files, and the uni's DNS server addresses in resolv.conf.  These instructions work great.  

However, when I try the pptp plugin for NetworkManager, no matter what kind of combinations of options ticked or unticked, I can't connect.  I don't mind the command line VPN, but I'd really like to understand why the pptp NetworkManager plugin won't work.  Can anyone help me with this?  Below I post the /var/log/debug messages for both the successful command line connection, and the failed NetworkManager connection.

Successful command line connection:
```
Apr 28 16:04:14 cokhavim pppd[6699]: using channel 11
Apr 28 16:04:14 cokhavim pppd[6699]: sent [LCP ConfReq id=0x1 <mru 1452> <asyncmap 0x0> <magic 0x61c881c9> <pcomp> <accomp>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth pap> <magic 0xde284739>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [LCP ConfAck id=0x1 <mru 1400> <auth pap> <magic 0xde284739>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [LCP ConfAck id=0x1 <mru 1452> <asyncmap 0x0> <magic 0x61c881c9> <pcomp> <accomp>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [PAP AuthReq id=0x1 user="jo%ra" password=<hidden>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [PAP AuthAck id=0x1 ""]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [IPCP ConfReq id=0x1 <addr 132.64.140.2>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [IPCP ConfAck id=0x1 <addr 132.64.140.2>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Apr 28 16:04:16 cokhavim pppd[6699]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [IPCP ConfNak id=0x2 <addr 132.64.140.192>]
Apr 28 16:04:16 cokhavim pppd[6699]: sent [IPCP ConfReq id=0x3 <addr 132.64.140.192>]
Apr 28 16:04:16 cokhavim pppd[6699]: rcvd [IPCP ConfAck id=0x3 <addr 132.64.140.192>]
Apr 28 16:04:16 cokhavim pppd[6699]: Script /etc/ppp/ip-up started (pid 6702)
Apr 28 16:04:16 cokhavim pppd[6699]: Script /etc/ppp/ip-up finished (pid 6702), status = 0x0

```

Failed NetworkManager connection (pretty much the same for any combination of ticked or unticked options):
```
Apr 28 16:39:26 cokhavim pppd[7469]: using channel 16
Apr 28 16:39:27 cokhavim pppd[7469]: sent [LCP ConfReq id=0x1 <mru 1452> <asyncmap 0x0> <magic 0x7fc61c5b> <pcomp> <accomp>]
Apr 28 16:39:29 cokhavim pppd[7469]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth pap> <magic 0xde4883e2>]
Apr 28 16:39:29 cokhavim pppd[7469]: sent [LCP ConfNak id=0x1 <auth chap MD5>]
Apr 28 16:39:29 cokhavim pppd[7469]: rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MD5> <magic 0xde4883e2>]
Apr 28 16:39:29 cokhavim pppd[7469]: sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MD5> <magic 0xde4883e2>]
Apr 28 16:39:30 cokhavim pppd[7469]: sent [LCP ConfReq id=0x1 <mru 1452> <asyncmap 0x0> <magic 0x7fc61c5b> <pcomp> <accomp>]
Apr 28 16:39:30 cokhavim pppd[7469]: rcvd [LCP ConfAck id=0x1 <mru 1452> <asyncmap 0x0> <magic 0x7fc61c5b> <pcomp> <accomp>]
Apr 28 16:39:30 cokhavim pppd[7469]: sent [LCP EchoReq id=0x0 magic=0x7fc61c5b]
Apr 28 16:39:30 cokhavim pppd[7469]: rcvd [CHAP Challenge id=0x1 <991cdbe3e1cf359f6ac059e77056f4cd>, name = "Cisco107"]
Apr 28 16:39:30 cokhavim pppd[7469]: sent [CHAP Response id=0x1 <2ed81cdb6f9251ad345d7d64ab9b7a52>, name = "jo%ra"]
Apr 28 16:39:30 cokhavim pppd[7469]: rcvd [LCP EchoRep id=0x0 magic=0xde4883e2]
Apr 28 16:39:30 cokhavim pppd[7469]: rcvd [CHAP Failure id=0x1 "Request Denied"]
Apr 28 16:39:30 cokhavim pppd[7469]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
Apr 28 16:39:30 cokhavim pppd[7469]: rcvd [LCP TermReq id=0x3]
Apr 28 16:39:30 cokhavim pppd[7469]: sent [LCP TermAck id=0x3]
Apr 28 16:39:30 cokhavim pppd[7469]: Script /usr/sbin/pptp 10.1.0.1 --nolaunchpppd finished (pid 7470), status = 0x0

```

Thanks!

---

