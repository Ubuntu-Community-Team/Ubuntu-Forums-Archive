---
title: "Strange iptables behaviour"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by milen243 on 2007-07-05
Hi, I am sharing my Inet connection at home and have been experienceg issues with p2p traffic for some time now. I share the connection using iptables rules which always seem to cause trouble. The only way I have been able to share it without the p2p issues is using ipmasq (if I remember right) which does not support forwarding ports.

So the problem is that I need to use iptables but every possible ruleset has been more trouble than help so far. I have tried a simple two line script just to make the NAT and everything is ok but p2p traffic. I recently tried a longer ruleset generated from a website but the result is the same. I will quote both of them here and I hope you can tell me how I could resolve the p2p that I have.

Basically everything but p2p works fine. When I have p2p traffic my connection slows down and then almost stops working. From time to time the speed normalises for a few seconds and then it drops dead again. The problem exists both from Windows and Linux computers using p2p.

```
sudo iptables -A FORWARD -s 192.168.0.0/16 -o ppp0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.0.0/16 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT
```


Edit: I found something that might help:
tail from kern.log

```
0x00 SYN URGP=0 
Jul  6 02:11:01 milen243 kernel: [  326.007542] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:01 milen243 kernel: [  326.007552] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:01 milen243 kernel: [  326.007555]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:01 milen243 kernel: [  326.007568]   Tx ring dfe53000:  80000000 80000000 80000000 0000 80000000 80000000
Jul  6 02:11:03 milen243 kernel: [  328.777958] INPUT packet died: IN=ppp0 OUT= MAC= SRC=87.120.0.108 DST=87.120.222.243 LEN=48 TOS=0x00 PREC=0x60 TTL=123 ID=3903 DF PROTO=TCP SPT=4770 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0 
Jul  6 02:11:05 milen243 kernel: [  330.001076] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:05 milen243 kernel: [  330.001086] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:05 milen243 kernel: [  330.001089]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:05 milen243 kernel: [  330.001102]   Tx ring dfe53000:  80000000 80000000 0000 80000000 80000000 80000000
Jul  6 02:11:09 milen243 kernel: [  333.994609] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:09 milen243 kernel: [  333.994619] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:09 milen243 kernel: [  333.994623]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:09 milen243 kernel: [  333.994635]   Tx ring dfe53000:  80000000 80000000 0000 80000000 80000000 80000000
Jul  6 02:11:09 milen243 kernel: [  334.788151] INPUT packet died: IN=ppp0 OUT= MAC= SRC=87.120.0.108 DST=87.120.222.243 LEN=48 TOS=0x00 PREC=0x60 TTL=123 ID=3938 DF PROTO=TCP SPT=4770 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0 
Jul  6 02:11:13 milen243 kernel: [  337.988143] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:13 milen243 kernel: [  337.988153] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:13 milen243 kernel: [  337.988156]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:13 milen243 kernel: [  337.988168]   Tx ring dfe53000:  80000000 0000 80000000 80000000 80000000 80000000
Jul  6 02:11:14 milen243 kernel: [  339.475024] Invalid packet: IN=ppp0 OUT= MAC= SRC=87.121.11.209 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0x20 TTL=120 ID=6540 PROTO=TCP SPT=3502 DPT=9090 WINDOW=65340 RES=0x00 ACK FIN URGP=0 
Jul  6 02:11:17 milen243 kernel: [  341.981679] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:17 milen243 kernel: [  341.981688] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:17 milen243 kernel: [  341.981691]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:17 milen243 kernel: [  341.981704]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 80000000 0000
Jul  6 02:11:19 milen243 kernel: [  344.247468] New not syn: IN=ppp0 OUT= MAC= SRC=64.12.201.42 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0xE0 TTL=107 ID=15953 DF PROTO=TCP SPT=5190 DPT=51879 WINDOW=16384 RES=0x00 ACK URGP=0 
Jul  6 02:11:21 milen243 kernel: [  345.975211] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:21 milen243 kernel: [  345.975221] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:21 milen243 kernel: [  345.975224]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:21 milen243 kernel: [  345.975237]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 80000000 0000
Jul  6 02:11:23 milen243 kernel: [  348.217702] New not syn: IN=ppp0 OUT=eth1 SRC=87.116.112.231 DST=192.168.0.4 LEN=576 TOS=0x10 PREC=0x40 TTL=120 ID=10856 PROTO=TCP SPT=64295 DPT=9090 WINDOW=65287 RES=0x00 ACK URGP=0 
Jul  6 02:11:25 milen243 kernel: [  349.968746] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:25 milen243 kernel: [  349.968756] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:25 milen243 kernel: [  349.968759]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:25 milen243 kernel: [  349.968772]   Tx ring dfe53000:  0000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:26 milen243 kernel: [  351.349161] Invalid packet: IN=ppp0 OUT= MAC= SRC=80.72.88.123 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0x00 TTL=122 ID=18107 DF PROTO=TCP SPT=2085 DPT=9090 WINDOW=65535 RES=0x00 ACK FIN URGP=0 
Jul  6 02:11:29 milen243 kernel: [  353.962277] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:11:29 milen243 kernel: [  353.962288] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:11:29 milen243 kernel: [  353.962291]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:29 milen243 kernel: [  353.962303]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 0000 80000000

```

and tail from /var/log/debug

```


Jul  6 02:11:41 milen243 kernel: [  365.942903]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:41 milen243 kernel: [  365.942916]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 0000 80000000
Jul  6 02:11:45 milen243 kernel: [  369.936426]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:45 milen243 kernel: [  369.936438]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 0000 80000000
Jul  6 02:11:49 milen243 kernel: [  373.929960]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:49 milen243 kernel: [  373.929972]   Tx ring dfe53000:  0000 80000000 80000000 80000000 0000 80000000
Jul  6 02:11:53 milen243 kernel: [  377.923492]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:53 milen243 kernel: [  377.923505]   Tx ring dfe53000:  0000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:57 milen243 kernel: [  381.917026]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:11:57 milen243 kernel: [  381.917039]   Tx ring dfe53000:  80000000 80000000 0000 80000000 80000000 80000000
Jul  6 02:12:01 milen243 kernel: [  385.910561]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:01 milen243 kernel: [  385.910574]   Tx ring dfe53000:  80000000 0000 80000000 80000000 80000000 80000000
Jul  6 02:12:05 milen243 kernel: [  389.904094]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:05 milen243 kernel: [  389.904106]   Tx ring dfe53000:  0000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:09 milen243 kernel: [  393.897628]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:09 milen243 kernel: [  393.897640]   Tx ring dfe53000:  80000000 0000 80000000 80000000 80000000 80000000
Jul  6 02:12:13 milen243 kernel: [  397.891162]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:13 milen243 kernel: [  397.891175]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 0000 80000000
Jul  6 02:12:17 milen243 kernel: [  401.884697]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:17 milen243 kernel: [  401.884710]   Tx ring dfe53000:  0000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:21 milen243 kernel: [  405.878230]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:21 milen243 kernel: [  405.878242]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 0000 80000000
Jul  6 02:12:25 milen243 kernel: [  409.871763]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:25 milen243 kernel: [  409.871775]   Tx ring dfe53000:  80000000 80000000 80000000 0000 80000000 80000000
Jul  6 02:12:29 milen243 kernel: [  413.865296]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:29 milen243 kernel: [  413.865308]   Tx ring dfe53000:  0000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:33 milen243 kernel: [  417.858829]   Rx ring dfa04000:  80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000 80000000
Jul  6 02:12:33 milen243 kernel: [  417.858842]   Tx ring dfe53000:  80000000 80000000 80000000 80000000 80000000 0000


```

and from /car/log/messages
```


Jul  6 02:11:57 milen243 kernel: [  381.917023] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:01 milen243 kernel: [  385.910549] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:01 milen243 kernel: [  385.910558] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:05 milen243 kernel: [  389.904081] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:05 milen243 kernel: [  389.904091] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:09 milen243 kernel: [  393.897614] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:09 milen243 kernel: [  393.897624] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:13 milen243 kernel: [  397.891149] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:13 milen243 kernel: [  397.891159] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:17 milen243 kernel: [  401.884684] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:17 milen243 kernel: [  401.884694] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:19 milen243 kernel: [  404.040115] New not syn: IN=ppp0 OUT=eth1 SRC=217.9.238.198 DST=192.168.0.4 LEN=1480 TOS=0x00 PREC=0x00 TTL=118 ID=16847 DF PROTO=TCP SPT=1813 DPT=9090 WINDOW=64844 RES=0x00 ACK PSH URGP=0 
Jul  6 02:12:19 milen243 kernel: [  404.166369] New not syn: IN=ppp0 OUT= MAC= SRC=64.12.201.42 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0xE0 TTL=107 ID=32692 DF PROTO=TCP SPT=5190 DPT=51879 WINDOW=16384 RES=0x00 ACK URGP=0 
Jul  6 02:12:21 milen243 kernel: [  405.878217] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:21 milen243 kernel: [  405.878226] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:25 milen243 kernel: [  409.871750] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:25 milen243 kernel: [  409.871759] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:28 milen243 kernel: [  412.855089] Invalid packet: IN=ppp0 OUT= MAC= SRC=87.121.11.209 DST=87.120.222.243 LEN=108 TOS=0x00 PREC=0x20 TTL=120 ID=11186 PROTO=TCP SPT=3502 DPT=9090 WINDOW=65340 RES=0x00 ACK PSH FIN URGP=0 
Jul  6 02:12:29 milen243 kernel: [  413.865283] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:29 milen243 kernel: [  413.865292] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:12:33 milen243 kernel: [  417.858817] NETDEV WATCHDOG: eth0: transmit timed out
Jul  6 02:12:33 milen243 kernel: [  417.858826] eth0: Transmit timed out, status 00000000, resetting...
Jul  6 02:13:19 milen243 kernel: [  464.086541] Invalid packet: IN=ppp0 OUT= MAC= SRC=64.12.201.42 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0xE0 TTL=107 ID=49437 DF PROTO=TCP SPT=5190 DPT=51879 WINDOW=16384 RES=0x00 ACK RST URGP=0 
Jul  6 02:13:46 milen243 kernel: [  491.184346] Invalid packet: IN=ppp0 OUT= MAC= SRC=193.151.80.201 DST=87.120.222.243 LEN=40 TOS=0x00 PREC=0x00 TTL=117 ID=16464 PROTO=TCP SPT=2048 DPT=9090 WINDOW=0 RES=0x00 RST URGP=0 
Jul  6 02:14:28 milen243 kernel: [  532.801212] Invalid packet: IN=ppp0 OUT= MAC= SRC=87.121.11.209 DST=87.120.222.243 LEN=108 TOS=0x00 PREC=0x20 TTL=120 ID=18272 PROTO=TCP SPT=3502 DPT=9090 WINDOW=65340 RES=0x00 ACK PSH FIN URGP=0 
Jul  6 02:15:21 milen243 kernel: [  586.296742] INPUT packet died: IN=ppp0 OUT= MAC= SRC=87.120.112.173 DST=87.120.222.243 LEN=64 TOS=0x00 PREC=0x00 TTL=43 ID=12132 DF PROTO=TCP SPT=2826 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Jul  6 02:15:22 milen243 kernel: [  586.921846] INPUT packet died: IN=ppp0 OUT= MAC= SRC=218.27.16.155 DST=87.120.222.243 LEN=925 TOS=0x00 PREC=0xE0 TTL=40 ID=0 DF PROTO=UDP SPT=45125 DPT=1026 LEN=905 
Jul  6 02:15:22 milen243 kernel: [  586.922063] INPUT packet died: IN=ppp0 OUT= MAC= SRC=218.27.16.155 DST=87.120.222.243 LEN=925 TOS=0x00 PREC=0xE0 TTL=40 ID=0 DF PROTO=UDP SPT=45127 DPT=1027 LEN=905 

```

---

### Post by milen243 on 2007-07-06
I think I found where the problem was coming from. I replaced the ethernet adapter and everything seems to be running fine for now. 7-8 Megabytes per second is a good indication of that ;)

---

