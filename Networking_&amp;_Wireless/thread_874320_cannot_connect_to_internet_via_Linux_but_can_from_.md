---
title: "cannot connect to internet via Linux but can from within xVM"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by asharma_in on 2008-07-29
Problem: I cannot connect to the internet via my Linux connection.

Some information:
I have installed Sun xVM and installed WIN XP over br0 and setup the bridge to the eth0.

I am able to connect to the internet from within the VM but cannot get past the DNS on Linux. 

Any things to check for ?

Thanks,
Anupam

---

### Post by jimv on 2008-07-30
Can you post the output of:

ifconfig
route -n

---

### Post by asharma_in on 2008-07-30
Output of ifconfig
anupam@anupam-laptop:~$ ifconfig
br0 Link encap:Ethernet HWaddr 00:18:8b:dc:09:ea
inet addr:10.187.68.225 Bcast:10.187.69.255 Mask:255.255.254.0
inet6 addr: fe80::218:8bff:fedc:9ea/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:45765 errors:0 dropped:0 overruns:0 frame:0
TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4148574 (3.9 MB) TX bytes:67863 (66.2 KB)

eth0 Link encap:Ethernet HWaddr 00:18:8b:dc:09:ea
inet addr:10.187.68.225 Bcast:10.187.69.255 Mask:255.255.254.0
inet6 addr: fe80::218:8bff:fedc:9ea/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:58586 errors:0 dropped:0 overruns:0 frame:0
TX packets:9339 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:16512526 (15.7 MB) TX bytes:1713725 (1.6 MB)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2021 errors:0 dropped:0 overruns:0 frame:0
TX packets:2021 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:133340 (130.2 KB) TX bytes:133340 (130.2 KB)

vbox0 Link encap:Ethernet HWaddr 00:ff:00:11:fc:d1
inet6 addr: fe80::2ff:ff:fe11:fcd1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8051 errors:0 dropped:0 overruns:0 frame:0
TX packets:55619 errors:0 dropped:2042 overruns:1 carrier:0
collisions:0 txqueuelen:500
RX bytes:1541692 (1.4 MB) TX bytes:15997934 (15.2 MB)

wlan0 Link encap:Ethernet HWaddr 00:19:7e:88:5d:90
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-19-7E-88-5D-90-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Output of /etc/hosts

127.0.0.1 anupam-laptop


NOTE: I cannot connect via wireless also. 

BUT 

I can connect to the internet from home though - whether it is wireless or Network. 
A bit puzzling ...

---

