---
title: "LCP: timeout sending Config-Requests"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by knallekra on 2007-02-16
Hi!

I'm trying to sync my Palm Treo 680 to a Ubuntu laptop via bluetooth.

I have followed a lot of instructions forhow to do this, and I think Iæm almost there. Now I get , in syslog on the laptop, this message when I press "Connect" on the Treo:

Feb 16 15:09:42 localhost pppd[17569]: Connect: ppp0 <--> /dev/rfcomm1
Feb 16 15:09:42 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:42 localhost dund[17567]: New connection from 00:07:E0:C7:C8:3C
Feb 16 15:09:45 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:46 localhost pppd[17569]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:46 localhost pppd[17569]: sent [LCP ConfAck id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:48 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:50 localhost pppd[17569]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:50 localhost pppd[17569]: sent [LCP ConfAck id=0x3 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:51 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:54 localhost pppd[17569]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:54 localhost pppd[17569]: sent [LCP ConfAck id=0x4 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:54 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:57 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:09:58 localhost pppd[17569]: rcvd [LCP ConfReq id=0x5 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:09:58 localhost pppd[17569]: sent [LCP ConfAck id=0x5 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:00 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:10:02 localhost pppd[17569]: rcvd [LCP ConfReq id=0x6 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:02 localhost pppd[17569]: sent [LCP ConfAck id=0x6 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:03 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:10:06 localhost pppd[17569]: rcvd [LCP ConfReq id=0x7 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:06 localhost pppd[17569]: sent [LCP ConfAck id=0x7 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:06 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:10:09 localhost pppd[17569]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb252c0a3> <pcomp> <accomp>]
Feb 16 15:10:10 localhost pppd[17569]: rcvd [LCP ConfReq id=0x8 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:10 localhost pppd[17569]: sent [LCP ConfAck id=0x8 <asyncmap 0x0> <pcomp> <accomp>]
Feb 16 15:10:12 localhost pppd[17569]: LCP: timeout sending Config-Requests
Feb 16 15:10:12 localhost pppd[17569]: Connection terminated.
Feb 16 15:10:12 localhost pppd[17569]: Modem hangup
Feb 16 15:10:12 localhost pppd[17569]: Exit.

Can anyone help me out of this?

---

