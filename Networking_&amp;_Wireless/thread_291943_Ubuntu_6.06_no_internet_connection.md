---
title: "Ubuntu 6.06: no internet connection"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by mastarna on 2006-11-03
Hi everyone,

I'm getting crazy to solve this problem ](*,) . I'm not new to linux & ubuntu. I just finished installing my brand new 6.06 and noticed internet connection was impossible. Now some info. I'm in a Uni LAN. The eth0 is normally detected and here's the ifconfig >

eth0      Link encap:Ethernet  HWaddr 00:04:0B:80:80:80  
          inet addr:172.16.40.210  Bcast:172.16.43.255  Mask:255.255.252.0
          inet6 addr: fe80::204:bff:fe80:8080/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221106 (215.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

if I ping my gw, after a few seconds, I got: "sendmsg: No buffer space available". I can ping 127.0.0.1

if I try to look for ip via browser I get "connection timed out" (for my gw, [http://gw_ip](http://gw_ip)) or "unable to connect" (for my own 127.0.0.1)

Waht's going on? Please give me an hand.

---

### Post by Ymmit on 2006-11-03
Hi there,

I have a similar problem with Ubtu: 6.06.
Occasionally my internet does not work.  Works every time in WindowsXP.  Works about 50/50 when logging onto Ubuntu.  If it works in the first few seconds, it never drops out.  If it doesn't, it never comes back online.  Perhaps we have a similar problem?  My ipconfig below:

eth0      Link encap:Ethernet  HWaddr 00:14:85:22:4B:E9
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe22:4be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8907710 (8.4 MiB)  TX bytes:2191036 (2.0 MiB)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

thanks to any that can help us.

-Ymmit

---

### Post by Gyme on 2006-11-03
Looks like I'm having the same problem.  I really have to struggle to get onto the internet at the moment after booting up.  Disabling the network card and reenabling it several times finally seems to work.  This is becoming really tiresome.

The really odd thing is that if I try to ping the router, it won't recognise it.  Although it recognises it now????????????

Help, anyone!!

ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:07:E9:83:E0:3D
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4087891 (3.8 MiB)  TX bytes:497722 (486.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:988495 (965.3 KiB)  TX bytes:988495 (965.3 KiB)

---

### Post by mastarna on 2006-11-03
...well, it looks like this is a common problem, maybe someone's the answer...

---

### Post by SunnyRabbiera on 2006-11-03
Hmm, it might be your router or modem...
some routers/modems cough up when they spot linux.

---

### Post by Gyme on 2006-11-03
lspci|grep Ether

0000:02:0c.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 10)

The router is from sky broadband using netgear.

---

### Post by Tittah on 2006-11-14
@mastarna

I have the same problem with an asus barebone in winXP. The freaky part is that we have the exact same MAC-address! I think that shouldn't be possible.

The trick for me was to change the MAC-address to something else (I changed the 2 last numbers). You could give it a try.

Anyone an explanation how it is possible that we have the same MAC-address?

---

