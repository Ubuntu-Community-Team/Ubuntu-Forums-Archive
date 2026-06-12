---
title: "Modem working ,but no internet??"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by paulgir on 2006-10-22
seems to dial out ok,but no internet
I've got as far as dialing out and making a connection to my ISP,but can't get any response when I try to get on any sites.I just get failed to "connect to server" messages.

This is the output when I use plog:

paul@paul-desktop:~$ plog
Oct 19 16:02:35 localhost pppd[12602]: rcvd [IPCP ConfReq id=0x81 <addr 222.152.43.xxx>]
Oct 19 16:02:35 localhost pppd[12602]: sent [IPCP ConfAck id=0x81 <addr 222.152.43.xxx>]
Oct 19 16:02:35 localhost pppd[12602]: rcvd [IPCP ConfNak id=0x2 <addr 202.150.118.xxx>]
Oct 19 16:02:35 localhost pppd[12602]: sent [IPCP ConfReq id=0x3 <addr 202.150.118.xxx>]
Oct 19 16:02:36 localhost pppd[12602]: rcvd [IPCP ConfAck id=0x3 <addr 202.150.118.xxx>]
Oct 19 16:02:36 localhost pppd[12602]: Cannot determine ethernet address for proxy ARP
Oct 19 16:02:36 localhost pppd[12602]: local IP address 202.150.118.xxx
Oct 19 16:02:36 localhost pppd[12602]: remote IP address 222.152.43.xxx
Oct 19 16:02:36 localhost pppd[12602]: Script /etc/ppp/ip-up started (pid 12631)
Oct 19 16:02:36 localhost pppd[12602]: Script /etc/ppp/ip-up finished (pid 12631), status = 0x0
paul@paul-desktop:~$ poff
paul@paul-desktop:~$ plog
Oct 19 16:03:20 localhost pppd[12602]: Sent 516 bytes, received 412 bytes.
Oct 19 16:03:20 localhost pppd[12602]: Script /etc/ppp/ip-down started (pid 12681)
Oct 19 16:03:20 localhost pppd[12602]: sent [LCP TermReq id=0x2 "User request"]
Oct 19 16:03:21 localhost pppd[12602]: Script /etc/ppp/ip-down finished (pid 12681), status = 0x0
Oct 19 16:03:21 localhost pppd[12602]: rcvd [LCP TermAck id=0x2]
Oct 19 16:03:21 localhost pppd[12602]: Connection terminated.
Oct 19 16:03:22 localhost pppd[12602]: Exit.

It looks like I'm sending and receiving something but I can't see any results from this.

Any help would be appreciated

---

