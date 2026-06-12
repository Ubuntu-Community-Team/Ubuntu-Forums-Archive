---
title: "Slow Network for One PC"
date: 2018-01-20
forum: Networking &amp; Wireless
---

### Post by boz_1812 on 2018-01-20
OS: Xubuntu 16.04 64bit
Router: ASUS DSL N55U Gigabit Router
Switch: TP-Link TL-SG1008D Gigabit switch
PCs: All have gigabit ethernet

I have 2 PC's connected directly to the router and get transfer speeds of 100Mb/s+.

I also have 2 connections from the switch going into 2 wall jacks in the den, with cable running into the ceiling then down the wall into to 2 jacks, one each in room 1 and room 2.  These rooms share a dividing wall and the outlet jacks are opposite each other, ie either side of the same wall.

For room 1 I get transfer speeds of 60Mb/s+ (older PC so that seems reasonable), but for room 2 the best speed I can get is 11Mb/s.  I use cat6 cabling throughout, including the cables run through the wall to the 2 room jacks.

If I connect a cable to the switch (using the same port) and run it across the floor to the PC in room 2 I can get 100Mb/s+.  I've swapped out all cables except the 2 that run through the wall, but no change.

For what it's worth, the "through the wall" cabling was done professionally 5 months ago.  I initially attributed the slow speed to an old PC I was using, which although it had a gigabit card, it was running at 100Mb/s and I could not force it to 1000Mb/s.  The replacement PC is a HP 8200 SFF, i5.
I'm suspicious of the cable running to room 2, but don't know how to test it.

---

### Post by TheFu on 2018-01-21
Use **iperf3** to perform the tests.  100Mb/s isn't good for a GigE network.  You should be getting 920Mbps or higher between all the systems.  Cheap GigE NICs fro 2002 would get 200Mbps.  The last 5 yrs, every GigE NIC should handle 900+Mbps. Heck, a chromebook with a USB3-to-GigE adapter here gets 920Mbps.

See: 
```
$ iperf3 -c  hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 47058 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   922 Mbits/sec    0    140 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   920 Mbits/sec    0    163 KBytes       
[  4]   2.00-3.00   sec   110 MBytes   921 Mbits/sec    0    191 KBytes       
[  4]   3.00-4.00   sec   110 MBytes   922 Mbits/sec    0    211 KBytes       
[  4]   4.00-5.00   sec   110 MBytes   919 Mbits/sec    0    246 KBytes       
[  4]   5.00-6.00   sec   109 MBytes   918 Mbits/sec    0    259 KBytes       
[  4]   6.00-7.00   sec   110 MBytes   919 Mbits/sec    0    272 KBytes       
[  4]   7.00-8.00   sec   110 MBytes   919 Mbits/sec    0    272 KBytes       
[  4]   8.00-9.00   sec   110 MBytes   923 Mbits/sec    0    420 KBytes       
[  4]   9.00-10.00  sec   110 MBytes   920 Mbits/sec    0    420 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.07 GBytes   920 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.07 GBytes   920 Mbits/sec                  receiver

iperf Done.

```  
That is a chromebook --> USB3-to-GigE --> CAT5e --> GigE Switch --> CAT5e to GigE Switch --> Core i7-920 system.
If I wanted to determine an issue with a cable, I'd use a known-good computer on the rpoblem cable to see the impact.  Also, consider the switch ports - sometimes those fail.

---

### Post by boz_1812 on 2018-01-22
Thanks, iperf3 is a great tool and I wasn't aware of it.

```
I first tested 2 PCs connected directly to the router,
bob@krt0169:~$ iperf3 -c 192.168.1.85
Connecting to host 192.168.1.85, port 5201
[  4] local 192.168.1.102 port 45704 connected to 192.168.1.85 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   113 MBytes   952 Mbits/sec    0    375 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   936 Mbits/sec    0    375 KBytes       
[  4]   2.00-3.00   sec   111 MBytes   935 Mbits/sec    0    375 KBytes       
[  4]   3.00-4.00   sec   112 MBytes   937 Mbits/sec    0    375 KBytes       
[  4]   4.00-5.00   sec   112 MBytes   936 Mbits/sec    0    375 KBytes       
[  4]   5.00-6.00   sec   112 MBytes   942 Mbits/sec    0    375 KBytes       
[  4]   6.00-7.00   sec   111 MBytes   933 Mbits/sec    0    375 KBytes       
[  4]   7.00-8.00   sec   112 MBytes   939 Mbits/sec    0    375 KBytes       
[  4]   8.00-9.00   sec   111 MBytes   934 Mbits/sec    0    375 KBytes       
[  4]   9.00-10.00  sec   112 MBytes   937 Mbits/sec    0    375 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.09 GBytes   938 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.09 GBytes   937 Mbits/sec                  receiver

iperf Done.
bob@krt0169:~$ 

For the next 2 tests I used the same laptop for consistency.  
Laptop connected in room 1
bob@krt0169:~$ iperf3 -c 192.168.1.125
Connecting to host 192.168.1.125, port 5201
[  4] local 192.168.1.102 port 45272 connected to 192.168.1.125 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   954 Mbits/sec    0    413 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   938 Mbits/sec    0    413 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   937 Mbits/sec    0    436 KBytes       
[  4]   3.00-4.00   sec   112 MBytes   936 Mbits/sec    0    436 KBytes       
[  4]   4.00-5.00   sec   111 MBytes   935 Mbits/sec    0    436 KBytes       
[  4]   5.00-6.00   sec   112 MBytes   937 Mbits/sec    0    436 KBytes       
[  4]   6.00-7.00   sec   111 MBytes   933 Mbits/sec    0    457 KBytes       
[  4]   7.00-8.00   sec   112 MBytes   944 Mbits/sec    0    457 KBytes       
[  4]   8.00-9.00   sec   111 MBytes   934 Mbits/sec    0    457 KBytes       
[  4]   9.00-10.00  sec   112 MBytes   938 Mbits/sec    0    457 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.09 GBytes   939 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.09 GBytes   937 Mbits/sec                  receiver

iperf Done.
bob@krt0169:~$ 

Laptop connected in room 2 (where I suspect the cabling is faulty)
bob@krt0169:~$ iperf3 -c 192.168.1.125
Connecting to host 192.168.1.125, port 5201
[  4] local 192.168.1.102 port 46364 connected to 192.168.1.125 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  12.9 MBytes   108 Mbits/sec    0    293 KBytes       
[  4]   1.00-2.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   2.00-3.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   3.00-4.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   4.00-5.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   5.00-6.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   6.00-7.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   7.00-8.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   8.00-9.00   sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
[  4]   9.00-10.00  sec  11.2 MBytes  93.8 Mbits/sec    0    293 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   114 MBytes  95.3 Mbits/sec    0             sender
[  4]   0.00-10.00  sec   112 MBytes  94.3 Mbits/sec                  receiver

iperf Done.
bob@krt0169:~$ 
```

So it looks like the cabling to room 2 is the problem.

---

### Post by TheFu on 2018-01-22
Best to use code tags here for any terminal output. Easier to read when things line up - Adv Reply (#).

Yep. Looks like you found the issue, assuming you've swapped the switch ports around. Sometimes the cable is fine and the switch port is the issue.  

Does the switch show GigE or 100 base-tx lights?  
Does ifconfig show a GigE connection or just 10/100?

Are you certain it is using CAT5e or better cable?  BTW, CAT5e is 2x better than needed for GigE at 500m distances, but CAT5 can't.  CAT6 tp is significantly thicker and kinda a dead end cable.  I bought some thinking that 10Gbps network would use it and for short distances it can, but not for longer runs.  

The 93 Mbps is pretty close to 100Mbps, so something seems off.

---

