---
title: "Ubuntu 7.10 vs Comtrend 635"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by klapczuk on 2007-12-19
Hi,
I'm trying to get Internet connectivity from Ubuntu 7.10 via Comtrend 635 ADSL switch/router/modem. The problem is strange. Router has 4 Ethernet ports, and I connect two computers to it (one with Win XP, and the second with Ubuntu7.10). WinXP gets a perfect Internet connectivity, but Ubuntu doesn't. It looks like that:
- Ubuntu gets IP from DHCP
- I can ping hosts on LAN and on Internet
- the DNS works well - it resolves all the names I require
- Web browsing doesn't work well - some sites get opened, some not (if there are images on site, they don't load)
- apt-get update doesn't get connections
- even the telnet session to router is broken (it works perfectly from the WinXP) - it stops in half of a welcome banner

What I tried so far:
- removing IPv6, both from modprobe.d and firefox (ipv6 disable true)
- testing on Ubuntu 7.10 live cd - doesn't work 
- tried on live cd on other equipment - doesn't work
- tweaking the sysctl concerning the net buffers - without success

So - has anyone seen it so far? And how to fix it?

Best regards,

klapczuk

---

### Post by mellowd on 2007-12-19
I assume this router is an external one?

If you open a terminal and type this:

```
ifconfig
```

What do you see?

---

### Post by klapczuk on 2007-12-19
The output is following:

krzysztof@BUNTU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:7D:C7:D1
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:1821773 (1.7 MB)  TX bytes:518183 (506.0 KB)
          Base address:0x3000 Memory:ee000000-ee020000

eth1      Link encap:Ethernet  HWaddr 00:19:D2:04:46:6F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:14 dropped:36 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1605 (1.5 KB)  TX bytes:5309 (5.1 KB)
          Interrupt:21 Base address:0xa000 Memory:edf00000-edf00fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:54219 (52.9 KB)  TX bytes:54219 (52.9 KB)


eth0 is wired, eth1 is wireless. On both the connectivity is broken.

klapczuk

---

### Post by mellowd on 2007-12-19
Hmm, your wired connection is getting an IP address. Also I can see it both sending and receiving packets.

Could you do this, open a terminal and type this:

```
sudo aptitude install traceroute
```

And then in the same terminal 

```
traceroute www.google.com
```


How far do you get?

---

### Post by klapczuk on 2007-12-20
Hi,
That's my tracepath:
krzysztof@BUNTU:~$ sudo tracepath [www.google.pl](www.google.pl)
Password or swipe finger:
 1:  192.168.1.3 (192.168.1.3)                              0.182ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2  10.859ms
 2:  kra-ru2.neo.tpnet.pl (213.25.2.76)                   asymm  3  70.875ms
 3:  Bz.kra-ru2.do.kra-r2.tpnet.pl (80.50.158.9)           asymm  4  66.883ms
 4:  no reply
 5:  tengige0-3-0-2.ffttr1.FrankfurtAmMain.opentransit.net (193.251.249.229) asymm  4  92.033ms
 6:  teleglobe-2.GW.opentransit.net (193.251.249.230)     asymm  5  98.950ms
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
17:  192.168.1.3 (192.168.1.3)                            asymm  1 2004.027ms !H
     Resume: pmtu 1500
krzysztof@BUNTU:~$                              


For me this is not for sure problem of the routing. I get good IP, default GW, and can resolve DNS addresses. I can as well ping hosts in Internet. For me there is rather some problem on the Ubuntu / Comtrend router edge (maybe this is a driver in Ubuntu??). I use the T60 laptop. The problem seems difficult, because using the other router (Cisco) everything works well with Ubuntu, and using XP installed on the same T60 machine works with Comtrend router.
Regards,

klapczuk

---

### Post by mellowd on 2007-12-20
Hmm, odd.

does this router have ssh or telnet access by any chance? If so could you log on and trace or ping straight from the router itself?

---

### Post by klapczuk on 2007-12-20
Yes, this router has telnet/http access possibity. I cannot trace from it, but I can ping from it to any site in Internet.
As I think - the problem is on the UBUNTU/router edge - because when I try to telnet to router from UBUNTU - the session gets broken (this is one subnet) . Under WinXP it works normally - I can login to router and issue commands. I suspect some problems with UBUNTU gigabit ethernet driver in T60 (intel PRO/wireless), but I cannot prove it.

Regards,

klapczuk

---

### Post by mellowd on 2007-12-20
Hmm, you may be right. I'm not 100% sure as I don't have that laptop. Maybe start a new thread in the hardware section asking if anyone else is having a problem with this particular laptop. Sorry I can't give much help with this one

---

