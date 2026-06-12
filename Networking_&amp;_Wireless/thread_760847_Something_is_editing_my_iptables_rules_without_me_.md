---
title: "Something is editing my iptables rules without me asking!"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by fbuchele on 2008-04-20
Hi everyone;

I had a bit of a problem a while back, for some reason my iptables rules got really messed up. I was trying to set up a local network with a vista computer, but couldn't get it to work so eventually I gave up. After that i realized that I couldn't connect to the internet anymore. I did a little bit of research, and realized that my iptables had been set up to Policy:DROP instead of Policy:Accept, so I changed them all to accept.

Now the problem is that randomly in some pattern I can't figure out, my IP tables are being set to Policy:DROP again. For some reason, I don't know, it does this, sometimes while I'm actively connected to the internet. I created a little desktop script containing: 

```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

to fix it anytime it happens, but it would be better if it didn't happen at all. Anyone have any ideas on what could be causing this?

---

### Post by fbuchele on 2008-04-23
Bump, seriously, this is kind of annoying.

---

### Post by fbuchele on 2008-04-29
Bump

Anyone out there?

---

### Post by fbuchele on 2008-05-17
Bump

Some more information: Whenever I can't access internet, lines like this start showing up in the syslog. It looks like I have some sort of firewall installed that is changing my rules.
```

May 17 09:38:49 fox-laptop kernel: [  232.889323] IN= OUT=eth0 SRC=169.254.6.118 DST=224.0.0.251 LEN=217 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=197 
May 17 09:38:52 fox-laptop kernel: [  235.747410] IN= OUT=eth0 SRC=169.254.6.118 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
May 17 09:39:05 fox-laptop kernel: [  239.152218] IN= OUT=ppp0 SRC=10.211.37.15 DST=124.217.198.74 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15521 DF PROTO=TCP SPT=45673 DPT=80 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.152536] IN= OUT=ppp0 SRC=10.211.37.15 DST=206.55.74.0 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18099 DF PROTO=TCP SPT=42529 DPT=9091 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.152799] IN= OUT=ppp0 SRC=10.211.37.15 DST=88.191.80.227 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=51493 DF PROTO=TCP SPT=33609 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.153060] IN= OUT=ppp0 SRC=10.211.37.15 DST=80.237.173.67 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15744 DF PROTO=TCP SPT=39654 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.153328] IN= OUT=ppp0 SRC=10.211.37.15 DST=72.20.14.134 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=33988 DF PROTO=TCP SPT=43695 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.153583] IN= OUT=ppp0 SRC=10.211.37.15 DST=212.187.66.3 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=50896 DF PROTO=TCP SPT=52516 DPT=37132 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:05 fox-laptop kernel: [  239.706503] IN= OUT=eth0 SRC=169.254.6.118 DST=169.254.255.255 LEN=262 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=242 
May 17 09:39:07 fox-laptop kernel: [  242.148213] IN= OUT=ppp0 SRC=10.211.37.15 DST=124.217.198.74 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15522 DF PROTO=TCP SPT=45673 DPT=80 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  242.148262] IN= OUT=ppp0 SRC=10.211.37.15 DST=206.55.74.0 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18100 DF PROTO=TCP SPT=42529 DPT=9091 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  242.148292] IN= OUT=ppp0 SRC=10.211.37.15 DST=88.191.80.227 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=51494 DF PROTO=TCP SPT=33609 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  242.148323] IN= OUT=ppp0 SRC=10.211.37.15 DST=80.237.173.67 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15745 DF PROTO=TCP SPT=39654 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  242.148353] IN= OUT=ppp0 SRC=10.211.37.15 DST=72.20.14.134 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=33989 DF PROTO=TCP SPT=43695 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  242.148383] IN= OUT=ppp0 SRC=10.211.37.15 DST=212.187.66.3 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=50897 DF PROTO=TCP SPT=52516 DPT=37132 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  243.738715] IN= OUT=eth0 SRC=169.254.6.118 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
May 17 09:39:07 fox-laptop kernel: [  247.185342] IN= OUT=ppp0 SRC=10.211.37.15 DST=89.149.242.226 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38040 DF PROTO=TCP SPT=46562 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141225] IN= OUT=ppp0 SRC=10.211.37.15 DST=124.217.198.74 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15523 DF PROTO=TCP SPT=45673 DPT=80 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141270] IN= OUT=ppp0 SRC=10.211.37.15 DST=206.55.74.0 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=18101 DF PROTO=TCP SPT=42529 DPT=9091 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141302] IN= OUT=ppp0 SRC=10.211.37.15 DST=88.191.80.227 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=51495 DF PROTO=TCP SPT=33609 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141332] IN= OUT=ppp0 SRC=10.211.37.15 DST=80.237.173.67 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15746 DF PROTO=TCP SPT=39654 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141362] IN= OUT=ppp0 SRC=10.211.37.15 DST=72.20.14.134 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=33990 DF PROTO=TCP SPT=43695 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  248.141391] IN= OUT=ppp0 SRC=10.211.37.15 DST=212.187.66.3 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=50898 DF PROTO=TCP SPT=52516 DPT=37132 WINDOW=5248 RES=0x00 SYN URGP=0 
May 17 09:39:07 fox-laptop kernel: [  250.179642] IN= OUT=ppp0 SRC=10.211.37.15 DST=89.149.242.226 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=38041 DF PROTO=TCP SPT=46562 DPT=9030 WINDOW=5248 RES=0x00 SYN URGP=0 
```

A while ago, I was trying to set up a wireless network thing so a friend could connect to me wirelessly using vista and connect to the internet through my computer. I just searched the Repos for 'firewall' and it looks like i still have ipmasq installed. This could be whats editing my stuff. I'm removing it and i will report back on if it solves the problem.

---

