---
title: "PPTP gives [pppd]Modem hangup Connection Terminated."
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by esdee303 on 2007-01-16
Hello,

I'm using Ubuntu 6.10.  I'm trying to connect to another network with PPTP.  On the other side there's a Lancom7111, configured with PPTP access.  When I try with a Windows PC, it's no problem to connect, with pptp (via kvpnc) Ubuntu gives the following debug info:

[I]Log session started at: Tue Jan 16 13:04:48 2007
2007-01-16 13:04:49 debug: No IP for default interface found, using "127.0.0.1".
2007-01-16 13:04:50 info: "PppdUpScript" started.
2007-01-16 13:04:50 info: "PppdUpScript" finished.
2007-01-16 13:04:50 debug: Username: steven.deferme
2007-01-16 13:04:50 debug: Trying to connect to server "XXX.XXX.XXX.XXX" with user "steven.deferme"...

2007-01-16 13:04:50 info: [pppd]Using interface ppp0
Connect: ppp0 <--> /dev/pts/1

2007-01-16 13:04:50 debug: Tunnel device: ppp0
Connect: ppp0 <--> /dev/pts/1


2007-01-16 13:04:50 info: "pppd" started.
2007-01-16 13:04:51 info: [pppd]Modem hangup
Connection terminated.

2007-01-16 13:04:51 debug: There is a reason for stop connecting, terminating "pppd" process.
2007-01-16 13:04:51 info: "pppd route process" started.
2007-01-16 13:04:51 info: File /etc/ppp/chap-secrets sucessfully removed[/I]

I tried turning on/off MPPE, tried turning off/on default gateway,... I always get a connected, immediately followed by a connection finished...

Any ideas ?

thx

---

### Post by gilgongo on 2007-01-16
For some reason, I've only been able to successfully PPTP using pptpconfig on Linux systems. Could you try that instead? I see that there's no binary for Ubuntu 6.10 though, but maybe you could try sniffing around [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

---

