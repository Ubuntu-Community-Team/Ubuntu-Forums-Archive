---
title: "Lot's of traffic from router...need help undestanding"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by HautingLu on 2007-10-28
Hi guys,

I've recently tweaked my network settings and gave my Feisty machine a static IP. I also reserved the IP for the machine in the router (Netgear) settings. But I'm looking in my log files and see a huge list of daily traffic between my router and the machine on port 137. 

Can anyone help me decipherer this? This is the output of a "tail" of /var/log/messages:

> 
Oct 28 18:07:09 desktop kernel: [ 5575.284000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4174 PROTO=UDP SPT=2353 DPT=137 LEN=58 
Oct 28 18:08:31 desktop kernel: [ 5656.508000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4175 PROTO=UDP SPT=2354 DPT=137 LEN=58 
Oct 28 18:08:32 desktop kernel: [ 5657.728000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4176 PROTO=UDP SPT=2354 DPT=137 LEN=58 
Oct 28 18:08:33 desktop kernel: [ 5658.932000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4177 PROTO=UDP SPT=2354 DPT=137 LEN=58 
Oct 28 18:08:36 desktop kernel: [ 5661.736000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4178 PROTO=UDP SPT=2355 DPT=137 LEN=58 
Oct 28 18:08:37 desktop kernel: [ 5662.964000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4179 PROTO=UDP SPT=2355 DPT=137 LEN=58 
Oct 28 18:08:38 desktop kernel: [ 5664.156000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4180 PROTO=UDP SPT=2355 DPT=137 LEN=58 
Oct 28 18:08:41 desktop kernel: [ 5666.964000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4181 PROTO=UDP SPT=2356 DPT=137 LEN=58 
Oct 28 18:08:42 desktop kernel: [ 5668.140000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4182 PROTO=UDP SPT=2356 DPT=137 LEN=58 
Oct 28 18:08:44 desktop kernel: [ 5669.340000] Inbound IN=eth0 OUT= MAC=00:1a:92:d1:13:d0:00:6c:80:4f:d2:8e:08:00 SRC=192.168.0.1 DST=192.168.0.49 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4183 PROTO=UDP SPT=2356 DPT=137 LEN=58 


The mac is from my router. Why all the sudden traffic on 137? In "messages" alone it shows up 461 times.

Thanks.


edit: Found an achieved thread, could this be from a Windows machine on my home network? None has been on during those times.

---

### Post by dburnett77 on 2007-10-29
Yeah, you've tapped an e-mail account, and thrown the ID port, to cover your tracks.

---

### Post by auxilum on 2007-10-29
It appears your router is opening up many connections to port 137 (NetBIOS) on your computer.  I'd recommend to check over your router's configs carefully to ensure you are not allowing unnecessary traffic into your network.

---

