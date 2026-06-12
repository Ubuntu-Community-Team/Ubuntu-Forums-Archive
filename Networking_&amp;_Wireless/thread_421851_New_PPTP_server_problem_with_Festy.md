---
title: "New PPTP server problem with Festy"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by ezacon on 2007-04-24
I have just installed a new router based on Ubuntu Festy. The router is only a PPTP VPN endpoint.
I have similar routers running with Damper and Debian 4 running.
In the last router (The Festy one), i have problems with the pop-top server.
The VPN conection fail most of the times. When it works, i can disconnect and reconnect the link for some hours, but when suddenly the the link fails to start during some hours or a day.
When the link is failing, i can restart router or pptpd service but the link still fail.
I  am realy lost with this one.
I include the relevant part of syslog with a successful connection a failed connection.
The debug option is enabled:

Successfull connection:
Apr 23 22:30:21 abt pptpd[3690]: CTRL: Client x.x.x.x control connection started
Apr 23 22:30:21 abt pptpd[3690]: CTRL: Starting call (launching pppd, opening GRE)
Apr 23 22:30:22 abt pppd[3691]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr 23 22:30:22 abt pppd[3691]: pptpd-logwtmp: $Version$
Apr 23 22:30:22 abt kernel: [  834.370722] PPP generic driver version 2.4.2
Apr 23 22:30:22 abt pppd[3691]: pppd 2.4.4 started by root, uid 0
Apr 23 22:30:22 abt pppd[3691]: using channel 1
Apr 23 22:30:22 abt pppd[3691]: Using interface ppp0
Apr 23 22:30:22 abt pppd[3691]: Connect: ppp0 <--> /dev/pts/1
Apr 23 22:30:22 abt pppd[3691]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x753c07ce> <pcomp> <accomp>]
Apr 23 22:30:22 abt pptpd[3690]: GRE: Bad checksum from pppd.
Apr 23 22:30:22 abt pppd[3691]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x753c07ce> <pcomp> <accomp>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x31f907e0> <pcomp> <accomp> <callback CBCP>]
Apr 23 22:30:24 abt pppd[3691]: sent [LCP ConfRej id=0x1 <callback CBCP>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0x31f907e0> <pcomp> <accomp>]
Apr 23 22:30:24 abt pppd[3691]: sent [LCP ConfAck id=0x2 <mru 1400> <magic 0x31f907e0> <pcomp> <accomp>]
Apr 23 22:30:24 abt pppd[3691]: sent [LCP EchoReq id=0x0 magic=0x753c07ce]
Apr 23 22:30:24 abt pppd[3691]: sent [CHAP Challenge id=0xf8 <900043a4ba07040250623bed6d0dcc33>, name = "pptpd"]
Apr 23 22:30:24 abt pptpd[3690]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Apr 23 22:30:24 abt pppd[3691]: rcvd [LCP Ident id=0x3 magic=0x31f907e0 "MSRASV5.10"]
Apr 23 22:30:24 abt pppd[3691]: rcvd [LCP Ident id=0x4 magic=0x31f907e0 "MSRAS-0-MNARZZ5"]
Apr 23 22:30:24 abt pppd[3691]: rcvd [LCP EchoRep id=0x0 magic=0x31f907e0]
Apr 23 22:30:24 abt pppd[3691]: rcvd [CHAP Response id=0xf8 <a54f20052db5d0bd6362bf4258a14967000000000000000000331b7fd7544e84598bbfb05fefc86c31065ec4b7c9200400>, name = "client"]
Apr 23 22:30:24 abt pppd[3691]: sent [CHAP Success id=0xf8 "S=28E14E05C68A31FA0ED3760C2FD4765ECC435CCE M=Access granted"]
Apr 23 22:30:24 abt pppd[3691]: sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
Apr 23 22:30:24 abt kernel: [  836.797049] PPP MPPE Compression module registered
Apr 23 22:30:24 abt pppd[3691]: rcvd [CCP ConfReq id=0x5 <mppe +H +M +S +L -D +C>]
Apr 23 22:30:24 abt pppd[3691]: sent [CCP ConfNak id=0x5 <mppe +H -M +S -L -D -C>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [IPCP ConfReq id=0x6 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns3 0.0.0.0> <ms-wins 0.0.0.0>]
Apr 23 22:30:24 abt pppd[3691]: sent [IPCP TermAck id=0x6]
Apr 23 22:30:24 abt pppd[3691]: rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [CCP ConfReq id=0x7 <mppe +H -M +S -L -D -C>]
Apr 23 22:30:24 abt pppd[3691]: sent [CCP ConfAck id=0x7 <mppe +H -M +S -L -D -C>]
Apr 23 22:30:24 abt pppd[3691]: MPPE 128-bit stateless compression enabled
Apr 23 22:30:24 abt pppd[3691]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.100.80>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Apr 23 22:30:24 abt pppd[3691]: sent [IPCP ConfReq id=0x2 <addr 192.168.100.80>]
Apr 23 22:30:24 abt pppd[3691]: rcvd [IPCP ConfAck id=0x2 <addr 192.168.100.80>]
Apr 23 22:30:27 abt pppd[3691]: rcvd [IPCP ConfReq id=0x8 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns3 0.0.0.0> <ms-wins 0.0.0.0>]
Apr 23 22:30:27 abt pppd[3691]: sent [IPCP ConfRej id=0x8 <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns3 0.0.0.0> <ms-wins 0.0.0.0>]
Apr 23 22:30:27 abt pppd[3691]: rcvd [IPCP ConfReq id=0x9 <addr 0.0.0.0>]
Apr 23 22:30:27 abt pppd[3691]: sent [IPCP ConfNak id=0x9 <addr 192.168.100.90>]
Apr 23 22:30:27 abt pppd[3691]: rcvd [IPCP ConfReq id=0xa <addr 192.168.100.90>]
Apr 23 22:30:27 abt pppd[3691]: sent [IPCP ConfAck id=0xa <addr 192.168.100.90>]
Apr 23 22:30:27 abt pppd[3691]: found interface eth0 for proxy arp
Apr 23 22:30:27 abt pppd[3691]: local  IP address 192.168.100.80
Apr 23 22:30:27 abt pppd[3691]: remote IP address 192.168.100.90
Apr 23 22:30:27 abt pppd[3691]: pptpd-logwtmp.so ip-up ppp0 acopen x.x.x.x
Apr 23 22:30:27 abt pppd[3691]: Script /etc/ppp/ip-up started (pid 3735)
Apr 23 22:30:27 abt pppd[3691]: Script /etc/ppp/ip-up finished (pid 3735), status = 0x0

Failed connection:
Apr 24 07:34:00 abt pptpd[4160]: CTRL: Client x.x.x.x control connection started
Apr 24 07:34:00 abt pptpd[4160]: CTRL: Starting call (launching pppd, opening GRE)
Apr 24 07:34:00 abt pppd[4161]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr 24 07:34:00 abt pppd[4161]: pptpd-logwtmp: $Version$
Apr 24 07:34:00 abt pppd[4161]: pppd 2.4.4 started by root, uid 0
Apr 24 07:34:00 abt pppd[4161]: using channel 2
Apr 24 07:34:00 abt pppd[4161]: Using interface ppp0
Apr 24 07:34:00 abt pppd[4161]: Connect: ppp0 <--> /dev/pts/0
Apr 24 07:34:00 abt pppd[4161]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x8d42e076> <pcomp> <accomp>]
Apr 24 07:34:00 abt pptpd[4160]: GRE: Bad checksum from pppd.
Apr 24 07:34:03 abt pppd[4161]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x8d42e076> <pcomp> <accomp>]
Apr 24 07:34:28 abt last message repeated 8 times
Apr 24 07:34:31 abt pppd[4161]: LCP: timeout sending Config-Requests 
Apr 24 07:34:31 abt pppd[4161]: Connection terminated.
Apr 24 07:34:31 abt pppd[4161]: Modem hangup
Apr 24 07:34:31 abt pppd[4161]: Exit.
Apr 24 07:34:31 abt pptpd[4160]: GRE: read(fd=6,buffer=8058660,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Apr 24 07:34:31 abt pptpd[4160]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Apr 24 07:34:31 abt pptpd[4160]: CTRL: Reaping child PPP[4161]
Apr 24 07:34:31 abt pptpd[4160]: CTRL: Client x.x.x.x control connection finished


Any idea?

---

### Post by ezacon on 2007-04-24
It must be some bug with the poptop version included with festy.
I have copied:
/usr/sbin/pptpctrl
/usr/sbin/pptpd
/usr/lib/pptpd/pptp-logwtmp.so
From a Damper based router to Festy failing router and now ir works.
These files was manually recompiled when i installed the Damper router to solve 2 problems:
-pptpd-logwtmp.so version reported at pptpd start is wrong
-Syslog gets flooded by GRE log messages.

I will report tomorrow if the solution is stable in time for reference for people dealing with same problem.

---

### Post by ezacon on 2007-04-25
Fails again this morning.
I have uninstaled pptpd, ppp and bcrelay, then installed the debian 4 ppp package and festy pptpd and bcrelay and still failing. I'm out of ideas.
This afternoon i will format and install debian 4

---

