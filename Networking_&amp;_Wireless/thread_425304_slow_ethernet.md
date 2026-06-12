---
title: "slow ethernet"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by stonerrob420 on 2007-04-27
Hello! I have a strange problem I have a windows xp computer sharing its internet connection with a ubuntu dapper computer through a 25 foot ethernet crossover cable. Both the computers have 3COM 3c905C-TX/TX-M [Tornado] fast ethernet cards in them. the Windows XPcomputer says the the connection is 100 MBPS. On the ubuntu computer the connection is 10 MBPS. How do it I increase the speed of the connection from the ubuntu computer to 100 MBPS?

Here is all the ifconfig information from the terminal.

rob@rob-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:73:CC:DF
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe73:ccdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211287 errors:12 dropped:0 overruns:8 frame:12
          TX packets:278319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35972626 (34.3 MiB)  TX bytes:297422914 (283.6 MiB)
          Interrupt:3 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:113642 (110.9 KiB)  TX bytes:113642 (110.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.163.1  Bcast:172.16.163.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.141.1  Bcast:172.16.141.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by stonerrob420 on 2007-04-30
Does anybody know how to reset the ethernet connection in ubuntu dapper back to default?  now I cant share file anymore but I can still surf off of the shared internet connection.:confused:

---

### Post by visorjoe on 2007-05-01
i have same problem,still can't find any answer,in feisty:(

---

### Post by stonerrob420 on 2007-05-06
I really wish I could transfer files back and forth from the two computers at full speed. Its so much easier to do it that way than to burn them to a DVD-RW. The windows computer is the one that is sharing the internet connection with the ubuntu computer so the problem is not there it has to be the ubuntu computer and the way the ethernet is configured.

---

