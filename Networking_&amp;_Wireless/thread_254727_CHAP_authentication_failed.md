---
title: "CHAP authentication failed"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by lopi on 2006-09-10
I have installed ubuntu 6.06 on my PC. I have a PPPoE conection with username and password. I make the conection with 'pppoeconf' command and I recive the follow error:

root@ubuntu:~# plog
Sep  4 16:23:45 ubuntu pppd[5022]: Plugin rp-pppoe.so loaded.
Sep  4 16:23:45 ubuntu pppd[5024]: pppd 2.4.4b1 started by root, uid 0
Sep  4 16:23:45 ubuntu pppd[5024]: PPP session is 915
Sep  4 16:23:45 ubuntu pppd[5024]: Using interface ppp1
Sep  4 16:23:45 ubuntu pppd[5024]: Connect: ppp1 <--> eth0
Sep  4 16:23:48 ubuntu pppd[5024]: CHAP authentication failed: ^H
Sep  4 16:23:48 ubuntu pppd[5024]: CHAP authentication failed
Sep  4 16:23:48 ubuntu pppd[5024]: Connection terminated.

Thanks.

---

### Post by tbonius on 2006-09-11
Did you setup a /etc/ppp/chap-secrets file witht he correct syntax for username and password?

T

---

