---
title: "Can't connect to internet - new to linux, fresh install"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by NutooLinux on 2008-11-30
Hello all

I'm new to linux - have recently acquired a used lap top from a friend that was previously infested with multiple viruses, have always wanted to try out linux - saw this as my opportunity.

-Laptop
-Dell inspiron 630m
-Ubuntu 8.10 - intrepid ibex

Did a complete install, removing the previous OS and replacing it with Ubuntu.

- the problem - I have been experiencing is that I cannot get a hard wire connection to work at all.  I have scoured the forums, the ubuntu website, have done searches, but have been unable to resolve this issue.

- it does recognize available **wireless** networks in the area
- it does recognize available **wired networks** labeled as: auto eth0

- I'm not running a router, I'm putting the DSL cable directly from the modem to the labtop and using the automatic DHCP settings

> Sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:22:8f:d8:21  
          inet6 addr: fe80::214:22ff:fe8f:d821/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:29524 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1946433 (1.9 MB)  TX bytes:10218 (10.2 KB) 
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:bd:2d:68  
          inet6 addr: fe80::213:ceff:febd:2d68/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:82 errors:0 dropped:12 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 Base address:0x8000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:16528 (16.5 KB)  TX bytes:16528 (16.5 KB) 

pan0      Link encap:Ethernet  HWaddr be:18:b9:9a:e7:78  
          inet6 addr: fe80::bc18:b9ff:fe9a:e778/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B) 



I'd appreciate any help I can get!:(

---

### Post by Hydrohs on 2008-11-30
You should be able to access the internet with a direct connection without playing with any settings O_o

As for wireless, try installing ndiswrapper, after that you should be able to connect wirelessly.

---

### Post by NutooLinux on 2008-11-30
When I try to connect to "Auto eth0" under my "Wired Network" it gives me the following text:
[I]
"Requesting a network address from the wired network..."[/I]

then it stops with the following message box: *Disconnected - the network connection has been disconnected.*

---

### Post by Iowan on 2008-11-30
Modems (external cable modems, anyway)  sometimes "lock onto" an attached MAC address - ignoring all others.  Sometimes resetting the modem (cycling power) will allow it to "lock onto" the new computer.

---

### Post by NutooLinux on 2008-11-30
> **Iowan said:**
> Modems (external cable modems, anyway)  sometimes "lock onto" an attached MAC address - ignoring all others.  Sometimes resetting the modem (cycling power) will allow it to "lock onto" the new computer.

ugh! unbelievable

I had considered this - but deemed it too simple a fix, I'm now replying from my laptop, with full wired connection on unbuntu

haha - im a nub

thanks for the reply

---

### Post by Iowan on 2008-11-30
Glad it worked! If you have more than one computer you plan to connect to internet, you may be ahead to install a router as "front man".  Then, you wouldn't need to reset modem each time you connect a computer.  Otherwise, if you believe problem is fixed, mark thread [SOLVED] (Under Thread Tools).

---

