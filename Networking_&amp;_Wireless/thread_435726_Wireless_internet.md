---
title: "Wireless internet?"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by cgbier on 2007-05-07
I'm trying to go with my Compaq Pressario over my wireless network on the internet.
The Broadcom card works perfectly (thanks to this forum!). I connect via a Linksys WAP54G access point and Linksys BEFSR41 router to my modem. While I can see the other (Windows) computers and files on the net, I cannot connect to the www from my laptop.
On other locations (college, bars) it works fine.
For the moment, I have thrown out any security meassures, but still can't connect.

Any clues?

---

### Post by chili555 on 2007-05-07
It seems clear that if you can see other computers on the local network, you are reaching the access point and router. I assume the router/access point setup is correct and that other computers reach the internet.

May we please see the output of:```
ifconfig
ping -c3 www.google.com
ping -c3 72.14.209.104
```Thanks.

---

### Post by cgbier on 2007-05-08
This is the output of ifconfig. What&#347; that weird thing with the 2 eth1?

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F2:B3:BF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1532296 (1.4 MiB)  TX bytes:367796 (359.1 KiB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:23:B3:79  
          inet6 addr: fe80::214:a5ff:fe23:b379/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:16 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7745 (7.5 KiB)  TX bytes:25619 (25.0 KiB)
          Interrupt:3 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:23:B3:79  
          inet addr:169.254.6.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x8000 

I have upgraded now to Feisty and gut the fwcutter from the synaptics. The antenna LCD is working, it talks to the access point, but I can't ping out - don even see my shared puters on the net anymore.

---

### Post by cgbier on 2007-05-08
It works like a breeze now!

There was some driver bug .... an answer is somewhere around in another thread. Tim Gardener had a solution.
Sorry that I didn't bookmark it, but it's in the other meanwhile countless other threads today about a non-working internet.

---

