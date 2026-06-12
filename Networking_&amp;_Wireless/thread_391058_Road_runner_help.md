---
title: "Road runner help"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Ezhax on 2007-03-22
Hello all I need some help I have been trying to connect to the internet using my comp which has a fresh installation of ubuntu 6.10 Edgy.  I have tried everything, the comp is a laptop (Compaq M2000) and is connected straight into the roadrunner modem via ethernet.  It seems to be recieving packets but not sending and nothing shows up when address typed in.  I have tried many things and would welcome any ideas.

---

### Post by esaym on 2007-03-22
hmm.  Are you using wireless?  Usually wired ethernet connections are no problem.  Open up the console and type in ```
lspci
``` and post us the output.  ALso give us the output of ```
ifconfig
```

---

### Post by Ezhax on 2007-03-22
Well the thing is that if i type all the crap from ifconfig id be here for a while but i am using a wired connection and the ethernet "card" from lspci is Realtek semiconductor
it works when i am connected to a dsl connection at my college but not at my friends roadrunner.

ifconfig is
eth0 
Link encap: Ethernet HWaddr 00:16:36:06:c4:27
inet6 addr: fe80::216:36ff:fe06:c427/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:436 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 drpped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RX bytes 26160 (25.5 KiB) TX bytes:2520 (2.4 KiB)
Interrupt:209 Base address:0x2000

---

### Post by esaym on 2007-03-22
> **Ezhax said:**
> Well the thing is that if i type all the crap from ifconfig id be here for a while but i am using a wired connection and the ethernet "card" from lspci is Realtek semiconductor
it works when i am connected to a dsl connection at my college but not at my friends roadrunner.

ifconfig is
eth0 
Link encap: Ethernet HWaddr 00:16:36:06:c4:27
inet6 addr: fe80::216:36ff:fe06:c427/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:436 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 drpped:0 overruns:0 carrier:0
collisions:0 txqueulen:1000
RX bytes 26160 (25.5 KiB) TX bytes:2520 (2.4 KiB)
Interrupt:209 Base address:0x2000

Oh so it works on a wired connection at your college but not on a wired connection at your friends?  So I guess the problem is not ubuntu then.  Does your friend have any other computers connected to the RR connection?  It sounds like dhcp might be turned off on the router if he has one.  What does the road runner cable modem plug into?  Does it run into some kind of router?  If so, model number?  Does your friend know anything about computers?

---

