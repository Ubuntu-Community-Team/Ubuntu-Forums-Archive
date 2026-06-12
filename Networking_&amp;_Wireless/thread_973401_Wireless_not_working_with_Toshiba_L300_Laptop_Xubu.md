---
title: "Wireless not working with Toshiba L300 Laptop Xubuntu 8.10??"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by shgadwa on 2008-11-06
I cannot seem to get wireless working properly on my laptop here. Its a toshiba L300, that I bought new a few days ago. My first problem was that it was acting like I did not have wireless internet. It was not seeing my card or something. I read some forums and a guy said to install linux-backports-modules-intrepid-generic. I did that. Then it works for about 20 minutes. After that, it starts to act funny and does not work as well... then after a while, especially if it is far from the router, it does not work at all. It might be able to connect to the internet, and it might even say its a strong signal but it does not work online. Sometimes it works very slowly but often it does not work at all.

Here is the outcome of ifconfig:

shawn@atlantis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:54:3d:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3383441092 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7044 (7.0 KB)  TX bytes:7044 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:28:99:c3  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fe28:99c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33653 (33.6 KB)  TX bytes:57990 (57.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-28-99-C3-39-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The wireless card is the wlan0 card.

Any help would be appreciated.

Thanks!
~Shawn

---

### Post by wgjhstt247 on 2008-11-06
[http://ubuntuforums.org/showthread.php?t=973400](http://ubuntuforums.org/showthread.php?t=973400)

---

### Post by shgadwa on 2008-11-06
Sorry, when I typed in ifconfig, I was plugged into a ethernet cable, I just hooked up wireless internet, unplugged the ethernet cable and I got different results.

shawn@atlantis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:54:3d:86  
          inet6 addr: fe80::21e:33ff:fe54:3d86/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5898 errors:0 dropped:3128778468 overruns:0 frame:0
          TX packets:5786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3393133 (3.3 MB)  TX bytes:1042845 (1.0 MB)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:129895 (129.8 KB)  TX bytes:129895 (129.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:28:99:c3  
          inet6 addr: fe80::221:63ff:fe28:99c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247967 (247.9 KB)  TX bytes:345324 (345.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-28-99-C3-39-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by shgadwa on 2008-11-08
That did not help. I cannot understand why it would. I tried it twice, however and it makes my system unbootable.

I read up on this quite a bit and installed new wireless drivers... that made it to work, though it was slow... after a while it did not work at all even though it said "connected to speedtouch...." and showed 3-4 bars at times.

So, its not like its not connecting to the router, it says it is... however the result of a ping is 'unkown host [www.google.is](www.google.is)'. And, I know it is not a problem with my wireless router, my computer or my wireless card as we have other computers on the network that work fine. Also, wireless used to work good on Vista... now it does not work at all.

Any help would be appreciated.

~Shawn Gadwa
From Iceland.

---

