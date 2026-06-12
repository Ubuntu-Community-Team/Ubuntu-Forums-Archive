---
title: "Huawei E220 and internet connection (gutsy 7.10)"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Eglo on 2007-11-26
hi.
have times a HUAWEI e220 and wanted in the InterNet, have all fell tries German :
:
[http://linux.frankenberger.at/Huawei_E220.html](http://linux.frankenberger.at/Huawei_E220.html) 

completely in accordance with oh if I these **sudo /sbin/huaweiAktBbo **in terminals called naturally with root right, get I:
```
Hldam HUAWEI E220 a prepnem na modem - bbo 06
huaweiAktBbo: huaweiAktBbo.c:113: main: Assertion `dev' failed.
Aborted (core dumped)
```
what is that? if I call, get **pppd call ppp nodetach** in terminals I:
```
connect script failed
```
sometimes I get long answer and not yet in the InterNet:
```
Serial connection established.
using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x793ca7d1> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xf7a904> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xf7a904> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x793ca7d1> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x793ca7d1]
rcvd [LCP DiscReq id=0x1 magic=0xf7a904]
rcvd [CHAP Challenge id=0x1 <e683fa51169be91596ccc49bbedb5395>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <cc034786f790b0a0d5ed408aa0506c7e>, name = "USER"]
rcvd [LCP EchoRep id=0x0 magic=0xf7a904 79 3c a7 d1]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [LCP EchoReq id=0x1 magic=0x793ca7d1]
IPCP: timeout sending Config-Requests
sent [LCP TermReq id=0x2 "No network protocols running"]
sent [LCP TermReq id=0x3 "No network protocols running"]
Connection terminated.
Modem hangup
```
what does the problem lie? or which I must editing? my details:
[B]OS: Ubuntu Gutsy
Hardware: HP G5000
Huawei E220 USB Modem
internetprovider: [3.DK]("http://www.3webshop.dk/default.aspx?__link=ProductDetail&ProductGuid=848a1933-a73d-4cd9-8a53-bf94fbd8787b&InfoMenuID=19EC3788-1788-4369-92A1-9330C81079A7") [/B]
I thank for each assistance
sorry for my bad English
Best regards  Mamphp

---

