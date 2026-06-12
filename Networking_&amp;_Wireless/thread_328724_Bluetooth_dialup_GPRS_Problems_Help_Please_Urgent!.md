---
title: "Bluetooth dialup GPRS Problems Help Please Urgent!!!"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by mthakur2006 on 2006-12-31
Hi all,
I have a serious problem with bluetooth dialup .... I have a Lenovo 3000 C100 and a Motorola L6. I am running Kubuntu Dapper 6.06 (got rid of edgy) and bluetooth works alright, i.e. I can send and receive files. I tried to set it using the bluetooth guide at ubuntu wiki, and I am using Orange GPRS. When I try to connect, I get this: (excerpt from /var/log/syslog)::

Dec 31 12:53:14 localhost pppd[14009]: pppd 2.4.4b1 started by mtha, uid 1000
Dec 31 12:53:17 localhost hcid[13415]: link_key_request (sba=11:11:11:11:11:11,
dba=00:17:84:8E:E5:63)
Dec 31 12:53:18 localhost chat[14010]: timeout set to 35 seconds
Dec 31 12:53:18 localhost chat[14010]: abort on (\nBUSY\r)
Dec 31 12:53:18 localhost chat[14010]: abort on (\nERROR\r)
Dec 31 12:53:18 localhost chat[14010]: abort on (\nNO ANSWER\r)
Dec 31 12:53:18 localhost chat[14010]: abort on (\nNO CARRIER\r)
Dec 31 12:53:18 localhost chat[14010]: abort on (\nNO DIALTONE\r)
Dec 31 12:53:18 localhost chat[14010]: abort on (\nRINGING\r\n\r\nRINGING\r)
Dec 31 12:53:18 localhost chat[14010]: send (^MAT^M)
Dec 31 12:53:18 localhost chat[14010]: expect (OK)
Dec 31 12:53:18 localhost chat[14010]: ^MAT^M^M
Dec 31 12:53:18 localhost chat[14010]: OK
Dec 31 12:53:18 localhost chat[14010]:  -- got it
Dec 31 12:53:18 localhost chat[14010]: send (AT+CGDCONT=2,"IP","paygwap"^M)
Dec 31 12:53:19 localhost chat[14010]: expect (OK)
Dec 31 12:53:19 localhost chat[14010]: ^M
Dec 31 12:53:19 localhost chat[14010]: AT+CGDCONT=2,"IP","paygwap"^M^M
Dec 31 12:53:19 localhost chat[14010]: OK
Dec 31 12:53:19 localhost chat[14010]:  -- got it
Dec 31 12:53:19 localhost chat[14010]: send (ATD*99#^M)
Dec 31 12:53:20 localhost chat[14010]: expect (CONNECT)
Dec 31 12:53:20 localhost chat[14010]: ^M
Dec 31 12:53:20 localhost chat[14010]: ATD*99#^M^M
Dec 31 12:53:20 localhost chat[14010]: CONNECT
Dec 31 12:53:20 localhost chat[14010]:  -- got it
Dec 31 12:53:20 localhost chat[14010]: send (^M)
Dec 31 12:53:20 localhost pppd[14009]: Serial connection established.
Dec 31 12:53:20 localhost pppd[14009]: using channel 1
Dec 31 12:53:20 localhost pppd[14009]: Using interface ppp0
Dec 31 12:53:20 localhost pppd[14009]: Connect: ppp0 <--> /dev/rfcomm0
Dec 31 12:53:21 localhost pppd[14009]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <
magic 0x3070cc5e> <pcomp> <accomp>]
Dec 31 12:53:21 localhost pppd[14009]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <
magic 0x3070cc5e> <pcomp> <accomp>]
Dec 31 12:53:21 localhost pppd[14009]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <
auth pap> <magic 0x10748666> <pcomp> <accomp>]
Dec 31 12:53:21 localhost pppd[14009]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <
auth pap> <magic 0x10748666> <pcomp> <accomp>]
Dec 31 12:53:21 localhost pppd[14009]: sent [LCP EchoReq id=0x0 magic=0x3070cc5e
]
Dec 31 12:53:21 localhost pppd[14009]: sent [PAP AuthReq id=0x1 user="mtha-lapto
p" password=<hidden>]
Dec 31 12:53:21 localhost pppd[14009]: rcvd [LCP EchoRep id=0x0 magic=0x10748768
]
Dec 31 12:53:21 localhost pppd[14009]: rcvd [PAP AuthAck id=0x1]
Dec 31 12:53:21 localhost pppd[14009]: PAP authentication succeeded
Dec 31 12:53:22 localhost kernel: [4300015.753000] PPP BSD Compression module re                                                              gistered
Dec 31 12:53:22 localhost pppd[14009]: sent [CCP ConfReq id=0x1 <deflate 15> <de                                                              flate(old#) 15> <bsd v1 15>]
Dec 31 12:53:22 localhost pppd[14009]: sent [IPCP ConfReq id=0x1 <compress VJ 0f                                                               01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Dec 31 12:53:22 localhost kernel: [4300015.827000] PPP Deflate Compression modul                                                              e registered
Dec 31 12:53:22 localhost pppd[14009]: rcvd [LCP ProtRej id=0x1 80 fd 01 01 00 0                                                              f 1a 04 78 00 18 04 78 00 15 03 2f]
Dec 31 12:53:22 localhost pppd[14009]: Protocol-Reject for 'Compression Control                                                               Protocol' (0x80fd) received
Dec 31 12:53:22 localhost pppd[14009]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f                                                               01>]
Dec 31 12:53:22 localhost pppd[14009]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>                                                               <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Dec 31 12:53:23 localhost pppd[14009]: Hangup (SIGHUP)
Dec 31 12:53:23 localhost pppd[14009]: Modem hangup
Dec 31 12:53:23 localhost pppd[14009]: Connection terminated.
Dec 31 12:53:24 localhost pppd[14009]: Exit.


Any help,???:confused:

---

### Post by lingnoi on 2007-01-01
I am having problems as well with a motorola phone (currently having to use windows to connect to the internet).

My laptop is a Samsung R55 laptop with a Motorola A1200. I made a forum post about it as well at [http://www.ubuntuforums.org/showthread.php?t=315505](http://www.ubuntuforums.org/showthread.php?t=315505)

It seems no one can answer. I have asked on Motorola's [open source section]("http://opensource.motorola.com") but so far there has been no answer.

---

