---
title: "Connection to the Internet - help please!!!"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by tcrabb on 2007-08-05
Cannot seem to get connection to establish - have used sudo eciadslconf.sh to bring up GUI configuration utility but fails when trying to connect - last bit of connection script output below (shows channel 40 but runs through many channels, failing on each) ...

My ISP uses these settings and I assume VC-MUX just means the normal VCM_RFC2364 ....

IP Addressing: dynamically assigned IP address
VPI: 0
VCI: 38
Connection type: PPPoA
Encapsulation: VC-MUX
Authentication method: CHAP

No idea what DNS servers are to be or if it matters if left blank. Any ideas people???

#######################################

Firmware seems to be already loaded

setting up modem (3/5)..

ECI load 2: success
synchronization successful

connecting modem (4/5)..

using channel 40
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hangup
Connection terminated.
Script /usr/bin/pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 10167), status = 0xf5
using channel 41
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Script /usr/bin/pppoeci -vpi 0 -vci 38 -vendor 0x0915 -product 0x0102 -mode VCM_RFC2364 finished (pid 10178), status = 0xf5
Modem hangup
Connection terminated.

###########################################

---

### Post by HereInOz on 2007-08-05
I am guessing that you are not using an Ethernet modem.  Is this correct?

What modem are you using?  Internal PCI?  USB?

---

### Post by tcrabb on 2007-08-05
Fujitsu fxd310 - a USB modem which comes supported in the config utility / drivers.

Had this modem working fine under Xandros. Ditched Xandros to try Ubuntu now modem not working. Not happy.

NOt shown in 1st part of post - but initial error is that it can't get channel whatever that means then starts trying random channels whatever it means by 'channel'.

---

