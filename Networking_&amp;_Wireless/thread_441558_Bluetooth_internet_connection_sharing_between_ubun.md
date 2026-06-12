---
title: "Bluetooth internet connection sharing between ubuntu laptop and xp desktop"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by anthortic on 2007-05-12
i have had joy in browsing the internet on my laptop through my xp desktop when i boot xp (on the laptop). however when i boot ubuntu i have had no luck. for weeks i have searched forums and googled all manner of search terms but without any positive results. so i want to ask, are there any success storys in bluetooth communicating between ubuntu and xp for internet connection sharing??? it would be great to hear how things have gone and what worked, and what not...

---

### Post by Spleenie on 2007-06-08
*bump*

I am also interested in sharing my internet connection with a bluetooth device. I have found one resource which goes on about modifying iptables and such, but was wondering if there was a less arduous utility for enabling connection sharing through a bluetooth dongle.

Cheers, S.

---

### Post by skatc on 2007-06-14
I am also looking for information on bluetooth ics between Ubuntu and Windows XP.  Spleenie, could you post a link to the resource you mentioned?  At this point I'll try anything!

---

### Post by Spleenie on 2007-06-14
[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)

This was the one. 

S.

---

### Post by YaroMan86 on 2008-06-12
I connect to the network... at least... according to the Treo, I am.

But using the web browser gets no response. Here's the output of my DUND terminal:

```
yaro@irma:~$ dund --nodetach --listen --persist --msdun call palm
dund[7274]: Bluetooth DUN daemon version 3.26
using channel 6
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x805ccf65> <pcomp> <accomp>]
dund[7276]: New connection from 00:07:E0:1C:F3:95
rcvd [LCP ConfRej id=0x1 <magic 0x805ccf65>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
sent [LCP ConfAck id=0x2 <asyncmap 0x0> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x0]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.2.1>]
rcvd [IPCP ConfReq id=0x1 <addr 0.0.0.0> <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP ConfNak id=0x1 <addr 192.168.2.2> <ms-dns1 192.168.15.1> <ms-dns3 192.168.15.1>]
rcvd [LCP EchoRep id=0x0 magic=0x0]
rcvd [LCP ProtRej id=0x3 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 192.168.2.1>]
rcvd [IPCP ConfReq id=0x2 <addr 192.168.2.2> <compress VJ 0f 01> <ms-dns1 192.168.15.1> <ms-dns3 192.168.15.1>]
sent [IPCP ConfAck id=0x2 <addr 192.168.2.2> <compress VJ 0f 01> <ms-dns1 192.168.15.1> <ms-dns3 192.168.15.1>]
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.2.1
remote IP address 192.168.2.2
Script /etc/ppp/ip-up started (pid 7281)
Script /etc/ppp/ip-up finished (pid 7281), status = 0x0

```

---

### Post by anthortic on 2008-06-23
thank you , it took ages until i needed it again but the link you offered did the trick ;)


*difficult though!!.....!!*

---

### Post by ederic on 2008-06-24
I tried it yesterday with my Treo 650 and my updated Hardy Heron installation. Didn't work. I wonder what went wrong. :(

---

