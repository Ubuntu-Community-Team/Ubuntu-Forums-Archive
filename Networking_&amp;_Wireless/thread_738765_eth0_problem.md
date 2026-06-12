---
title: "eth0 problem"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by DeVonne on 2008-03-29
Hello, I have recently downloaded firestarter to do internet connection sharing

I connect with ppp0 just fine, used it to make this post

However my wired connection eth0 seems to have no IP or anything
and firestarter says it cant start because eth0 is not ready

Thanks

root@visionary-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:6E:44:FD  
          inet6 addr: fe80::240:caff:fe6e:44fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207634 (202.7 KB)  TX bytes:2136 (2.0 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8833 (8.6 KB)  TX bytes:8833 (8.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:98.134.139.188  P-t-P:209.97.109.74  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:12804287 (12.2 MB)  TX bytes:608876 (594.6 KB)

root@visionary-desktop:~#

---

### Post by fmartinez on 2008-03-29
You try giving it a static ip address. That's what I had to do when Network Manager wouldn't recognize my network. It worked great. 
System => Administration =>Network

---

### Post by DeVonne on 2008-03-29
Did not help me, then firestarter messed up my connection to the internet, had to remove it

Still need help with internet connection sharing :(

---

### Post by superprash2003 on 2008-03-29
take a look at this [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Iowan on 2008-03-30
You might post your **/etc/network/interfaces** file - or at least verify the existence of **auto eth0** therein.

---

