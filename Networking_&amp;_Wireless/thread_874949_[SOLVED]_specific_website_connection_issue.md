---
title: "[SOLVED] specific website connection issue"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by imaginate on 2008-07-30
For several weeks I have been trying to connect to 76.12.87.108 with no success in ubuntu hardy.  Was having the same problem in windows xp until I ran a utility winsockxpfix.  Has anyone run into a similar problem in ubuntu and been able to fix it.  Have noted connection attempts in ubuntu causes a firewall alert on my modem. Ubuntu sees my ethernet connection as r8169. Have redetected hardware and reset network to no avail. 

Running a dual boot system windows xp/ubuntu 8.04
Realtek 8111b ethernet
Siemens Gigaset SE567 dsl modem

All assistance greatly appreciated.

Here is what I get in ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8f:df:da:f5  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fedf:daf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1285716 (1.2 MB)  TX bytes:167837 (163.9 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4424 (4.3 KB)  TX bytes:4424 (4.3 KB)


Further investigation into the firewall alert on my dsl modem indicated a tcp fragmentation error at 1470. Solution to accessing the website was to lower the mtu to 1470 using the following command,

sudo ifconfig eth0 mtu 1470

Hope this helps anyone else having a similar time-out problem on a website

---

