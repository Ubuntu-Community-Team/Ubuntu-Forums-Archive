---
title: "ssh connection drops once in a while"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by alxlabs on 2008-07-29
There are 3 machines in my home network, running WinXP, Ubuntu 8.04.01, PCLinuxOS..lets call them win, ubuntu, pclinux. All of them can access internet flawlessly except one case when I'm trying to access my office machine (lets call it office) running Fedora thru ssh - connection works, but couple of "ls -la" and connection hangs up - just freezes. Here is the set of tests I've done:

1. "PCLinux" can ssh to "office" with no issue
2. "Win" can ssh thru putty to "office" with no issue
3. "Ubuntu" can ssh but connection **dies once in a while**
4. I tried Ubuntu live CD at home -> same problem
5. I tried Ubuntu live CD in the office - works flawlessly

Here is the result of "uname -a" for Ubuntu machine
```

alxlabs@alxlabs-desktop:~$ uname -a
Linux alxlabs-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```
Here is the results of "ifconfig" for Ubuntu machine
```

alxlabs@alxlabs-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0e:0c:9b:e3:03  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe9b:e303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57743848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67933535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4032463599 (3.7 GB)  TX bytes:3768227628 (3.5 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5573203 (5.3 MB)  TX bytes:5573203 (5.3 MB)

```


Here is "uname -a" for PCLinux machine
```

Linux localhost 2.6.18.8.tex5 #1 SMP Thu May 10 11:36:58 WST 2007 i686 Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz GNU/Linux

```
Here is "ifconfig" from mPCLinux machine
```

eth0      Link encap:Ethernet  HWaddr 00:19:B9:81:F5:D1
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe81:f5d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18233 (17.8 KiB)  TX bytes:17323 (16.9 KiB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Additional observations:

1. tracert from "Ubuntu" to "office" never finds the route
2. tracert from "PCLinux" to "office" never finds the route
```

alxlabs@alxlabs-desktop:/root$ sudo tracert mail.frescomicrochip.com -m 255
traceroute to mail.frescomicrochip.com (216.234.32.26), 255 hops max, 40 byte packets
 1  192.168.2.1 (192.168.2.1)  0.421 ms  0.410 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * GE0-2.WANB-TOROONXN.IP.GROUPTELECOM.NET (66.59.191.37)  59.000 ms  61.596 ms
 7  POS2-0.PEERA-TOROONXN.IP.GROUPTELECOM.NET (66.59.191.150)  78.341 ms  78.520 ms  80.368 ms
 8  if-14-2.core1.TNK-Toronto.teleglobe.net (216.6.112.41)  85.114 ms  88.153 ms  92.979 ms
 9  if-0-0.ihar1.TGS-Toronto.teleglobe.net (216.6.122.50)  108.075 ms  109.801 ms  109.809 ms
10  ix-0-3.ihar1.TGS-Toronto.teleglobe.net (209.58.16.18)  111.164 ms  113.659 ms  125.534 ms
11  e0-2.nc-frt-bas1.rtr.connection.ca (216.234.47.214)  127.013 ms  127.258 ms  96.280 ms
12  39.167.207.205.rev.connection.ca (205.207.167.39)  98.006 ms  81.851 ms  82.726 ms
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
......
......

```

2. tracert from "office" to "Ubuntu" cannot make even a single hop
```

traceroute to alxlabs.27south.com (216.99.99.169), 30 hops max, 38 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *

```

From all of the machines internet access is OK.

Just to recap: problem is that I can ssh from Win, PCLinux to office machine and cannot do the same from Ubuntu. Any ideas?

---

### Post by alxlabs on 2008-07-30
Some additional debugging revealed that 
1. "office" machine is not pingable from both "ubuntu" and "win" machines (as well as PCLinux) which may lead to MTU-related issues
1. Changing an MTU size on "Ubuntu" does not help.

---

