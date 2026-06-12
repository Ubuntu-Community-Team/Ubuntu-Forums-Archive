---
title: "Networking problems"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by mad_max0204 on 2008-11-16
Hi guys,
I have some networking problems. I had installed wireless card to share my internet connection on it so I can connect from my laptops but I gave up on that since it didnt work. Now I have 2 network adapters. One is eth0 which is LAN and internet connected and other one is pan0 which I dont know what is. How can I remove this pan0 interface since I got only lan card now and how can I setup my LAN card ip settings so I dont have to set it up on every startup ??


Thanks

---

### Post by gnusci on 2008-11-16
Please read this sticky

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

> How can I remove this pan0 interface since I got only lan card now and how can I setup my LAN card ip settings so I dont have to set it up on every startup ??

You can edit

/etc/network/interfaces

and remove **pan0**

---

### Post by mad_max0204 on 2008-11-16
This is in my /etc/network/interfaces

auto lo
iface lo inet loopback

What should I remove ??

---

### Post by gnusci on 2008-11-16
could you post the output of:

**$ ifconfig**

---

### Post by mad_max0204 on 2008-11-16
Here are both ifconfig and ifconfig -a

> matija@zverko:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:09:42:ec  
          inet addr:10.10.0.10  Bcast:10.10.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:97946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73660 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:50614135 (50.6 MB)  TX bytes:6111392 (6.1 MB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:379752 (379.7 KB)  TX bytes:379752 (379.7 KB)

matija@zverko:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:09:42:ec  
          inet addr:10.10.0.10  Bcast:10.10.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:97955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73669 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:50614831 (50.6 MB)  TX bytes:6112182 (6.1 MB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380376 (380.3 KB)  TX bytes:380376 (380.3 KB)

pan0      Link encap:Ethernet  HWaddr 8a:77:42:87:9d:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by gnusci on 2008-11-16
Regarding pan0 here I found this

[http://affix.sourceforge.net/affix-doc/c1051.html](http://affix.sourceforge.net/affix-doc/c1051.html)

It is about bluetooth devices. You have to go to Synaptic and search for bluetooth and remove the packages since you are notusing bluetooth.

But there is not any wlan in you output!. Please run

**$ lspci** 

An search for your wireless adapter, and then run


**$ lspci -vvnn**

and post the information about your wireless.

---

