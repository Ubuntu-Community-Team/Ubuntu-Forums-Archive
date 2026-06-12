---
title: "pppd gets SIGTERM after sending first message"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by jannewmarch on 2018-01-15
Trying to connect to my modem using pppoe. I'm seeing the modem and getting its address, but right after sending the first LCP message, pppd gets a SIGTERM and then shuts down. There was a posting on this topic back in 2010, and the workaround then seems to be in system I have now, so not applicable: Ubuntu 17.04, pppd 2.4.7. Syslog shows

[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Send PPPOE Discovery V1T1 PADI session 0x[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]0 length 4[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  dst ff:ff:ff:ff:ff:ff  src 38:4b:72:f0:2[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]6:c3[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  [service-name][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Recv PPPOE Discovery V1T1 PADO session 0x0 length 40[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  dst 38:4b:72:f0:26:c3  src 00:2a:10:c3:6f:53[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  [service-name] [AC-name dstr1.m03.au] [AC-cookie  76 95 aa ab b9 ec 1d 4e c2 f6 b6 71 e8 0b eb 70][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Send PPPOE Discovery V1T1 PADR session 0x0 length 24[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  dst 00:2a:10:c3:6f:53  src 38:4b:72:f0:26:c3[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  [service-name] [AC-cookie  76 95 aa ab b9 ec 1d 4e c2 f6 b6 71 e8 0b eb 70][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Recv PPPOE Discovery V1T1 PADS session 0x1288 length 24[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  dst 38:4b:72:f0:26:c3  src 00:2a:10:c3:6f:53[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]:  [service-name] [AC-cookie  76 95 aa ab b9 ec 1d 4e c2 f6 b6 71 e8 0b eb 70][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: PADS: Service-Name: ''[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: PPP session is 4744[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Connected to 00:2a:10:c3:6f:53 via interface eth1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: using channel 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Using interface ppp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Connect: ppp0 <--> eth1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: sent [LCP ConfReq id=0x1 <mru 1492> <magic 0x1cca8a01>][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Terminating on signal 15[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: sent [LCP TermReq id=0x2 "User request"][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: rcvd [LCP ConfReq id=0x1 <mru 1492> <auth chap MD5> <magic 0x8283b65c>][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: rcvd [LCP ConfAck id=0x1 <mru 1492> <magic 0x1cca8a01>][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: rcvd [LCP TermAck id=0x2][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Connection terminated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Jan 15 23:45:15 raspberrypi pppd[424]: Exit.[/FONT][/COLOR]

Any clues?
Thanks, Jan

---

