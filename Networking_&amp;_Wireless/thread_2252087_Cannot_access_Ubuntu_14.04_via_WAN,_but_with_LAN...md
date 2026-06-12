---
title: "Cannot access Ubuntu 14.04 via WAN, but with LAN..."
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by Singular on 2014-11-08
Running Ubuntu 14.04

Turned off the default firewall.

I also did the port-forwarding thing, and I know its working (I think) because when I run tshark, and perform an external port scan, I get:


```
1   0.000000 107.20.89.142 -> 192.168.0.14 TCP 76 40943 > http [SYN] Seq=0 Win=14600 Len=0 MSS=1452 SACK_PERM=1 TSval=1239877045 TSecr=0 WS=32
1   2   0.000048 192.168.0.14 -> 107.20.89.142 TCP 76 http > 40943 [SYN, ACK] Seq=0 Ack=1 Win=28960 Len=0 MSS=1460 SACK_PERM=1 TSval=3112352 TSecr=1239877045 WS=128
  3   0.078255 107.20.89.142 -> 192.168.0.14 TCP 68 40943 > http [ACK] Seq=1 Ack=1 Win=14624 Len=0 TSval=1239877065 TSecr=3112352
  4   0.078303 107.20.89.142 -> 192.168.0.14 TCP 68 40943 > http [FIN, ACK] Seq=1 Ack=1 Win=14624 Len=0 TSval=1239877065 TSecr=3112352
  5   0.078548 192.168.0.14 -> 107.20.89.142 TCP 68 http > 40943 [FIN, ACK] Seq=1 Ack=2 Win=29056 Len=0 TSval=3112371 TSecr=1239877065
  6   0.156254 107.20.89.142 -> 192.168.0.14 TCP 68 40943 > http [ACK] Seq=2 Ack=2 Win=14624 Len=0 TSval=1239877084 TSecr=3112371
```


On the LAN, everything works fine...looks like the router is forwarding correctly.

Ive port-forwarded port 80 and 22...port scanners say both are open but apache2 and open-ssh-server are not responding.

Anyone have any ideas what could be wrong?

Thanks!

---

### Post by steeldriver on 2014-11-08
From where are you trying to access it? if you are trying to use the WAN IP from inside the LAN, it may simply be that your router does not support that kind of NAT loopback

---

### Post by Singular on 2014-11-08
Man, you are right...just tried it from my cell phone, and it worked fine.


What's the work-around to access uniformly from the LAN?

---

### Post by wildmanne39 on 2014-11-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

