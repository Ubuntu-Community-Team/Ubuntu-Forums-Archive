---
title: "Need help how to use Zadacom GPRS USB modem with Feisty"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by svetlisashkov on 2007-04-26
I can't manage how to use this modem with Ubuntu 7.04. When I plug my modem and run *lsusb* command i get following output:

***
Bus 002 Device 005: ID 0403:6001 Future Technology Devices International, Ltd 8-bit FIFO
***

I followed the steps from the manufacturer's site [http://www.zadako.sk/upload/pages/Navody_ZadaCOM6/linux.pdf]("http://www.zadako.sk/upload/pages/Navody_ZadaCOM6/linux.pdf")

First I create /etc/ppp/peers/edge with the following content:

/dev/ttyUSB0 230400
crtscts
user ""
debug
noauth
connect '/usr/sbin/chat -v -f /etc/ppp/chatscripts/edge'
nodetach
noipx
usepeerdns
ipcp-accept-local
local
novj
novjccomp
nobsdcomp
disconnect '/usr/sbin/chat -v -f /etc/ppp/chatscripts/edge-hang'
defaultroute
usepeerdns

The I create /etc/ppp/chatscripts/edge with th following content:

TIMEOUT 20
ABORT BUSY
ABORT "NO CARRIER"
ABORT VOICE
ABORT "NO DIALTONE"
""
ATZ OK
at+cgdcont=1,"IP","inet-gprs.mtel.bg" OK
"ATD*99#" CONNECT

The string *inet-gprs.mtel.bg* i needed by my provider MTEL in Bulgaria.

And finally make these files with the following options:

/etc/ppp/chatscripts/edge-hang
"" "+++ath"

/etc/ppp/chap-secret /etc/ppp/pap-secret
*[tab]*[tab]""

Now, after all steps above when I run *pppd call edge* i get the following output:

svetli@ubuntu-laptop:~$ pppd call edge
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x78dd650f> <pcomp> <accomp>]
rcvd [LCP ConfRej id=0x1 <magic 0x78dd650f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
sent [LCP EchoReq id=0x0 magic=0x0]
sent [PAP AuthReq id=0x1 user="ubuntu-laptop" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x0]
sent [PAP AuthReq id=0x2 user="ubuntu-laptop" password=<hidden>]
rcvd [PAP AuthAck id=0x2 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15>]
sent [IPCP ConfReq id=0x1 <addr 10.248.12.98> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0c 1a 04 78 00 18 04 78 00]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [LCP TermReq id=0x1]
LCP terminated by peer
sent [LCP TermAck id=0x1]
Connection terminated.
Serial link disconnected.
Modem hangup


Where is my mistake? Any help is highly appreciated! Thanks in advance!

P.S.: I know my English is not perfect... Excuse me!

---

### Post by ihristov on 2007-07-19
I am no expert, but maybe the problem is in
  "Protocol-Reject for 'Compression Control Protocol' (0x80fd) received"

Try removing the novjccomp and/or the nobsdcomp options in /etc/ppp/peers/edge

Also, are you able to connect with the same modem from a Windows box? If so maybe you can take a look at the advanced settings in the RAS dialup connection there and see if there is something peculiar about the compression settings.

---

