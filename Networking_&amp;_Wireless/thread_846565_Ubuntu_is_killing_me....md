---
title: "Ubuntu is killing me..."
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by fritzjavel on 2008-07-01
Man i'm getting upset, i've been following tips after tips to fix my internet connection, and now i'm near close to giving up... so my last resort is to ask the ubuntu smart people, i'm a serios noob on ubuntu, i struggle to understand anything.. i want to use ubunt because windows just is windows but i herd ubuntu has much more to offer.... but could someone please help me connect my ubuntu online? because it's reading my modem, it detected my ip and everything, but won't connect so i took roaming mode off, and set up static ip, and then it would use sudo ifconfig, it would tell me unable to resolve host... so now i found a fix i'm going to follow, and then try at the connection again... Please help me...

---

### Post by camccall on 2008-07-01
Okay, let's start over a bit fritzjavel.  First, what exactly are you trying to do.  I think you are trying to connect to the internet using a wifi connection, is this correct?  If this is the case the second step may be to post the model of your wifi card on your computer.  If you don't know how to get this let us know and we will walk you through it.  Also, if I was correct about the problem, can you let us know if your connection is using security or not.  

I also don't want to seem rude, but when you ask a question in any forum it might be a good idea to at check out [this guide]("http://www.catb.org/~esr/faqs/smart-questions.html#asking").  If you ask questions the right way you will get responses here.

---

### Post by fritzjavel on 2008-07-01
O okay i see my fault with my topic... But no i'm not trying to set up a wifi, i'm actually trying to set my my wired LAN connection, throught an ethernet port. I have ubuntu on a 15gig HD, and windows XP on a 80gig HD, Dualboot, i did not make any partition but rather bought a dedicated HD for ubuntu... I do not have any security for my LAN...

---

### Post by Iowan on 2008-07-01
The "unable to resolve host" message sounds like a DNS issue.  Please post your **/etc/networking/interfaces** file and the results of **ifconfig**.  Depending on your setup, DHCP might work (leave "roaming" off).

---

### Post by camccall on 2008-07-01
If you are unsure of how to do this let us know and we'll give you some help.

---

### Post by fritzjavel on 2008-07-03
Sorry, about the wait, you know ubuntu will not let your mound a HD, unless you do a proper restart of windows, yeah i didn't know that, so i mounted my HD, and then opened the word Document i'm using to send info to myself on ubuntu... LOL... okay this is what i have.. :

ifconfig

eth0      Link encap:Ethernet  HWaddr 

         inet addr:74.186.143.67  Bcast:74.255.255.255  Mask:255.0.0.0

          inet6 addr: fe80::211:9ff:fe68:b944/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:258 errors:0 dropped:0 overruns:0 frame:0

          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:15712 (15.3 KB)  TX bytes:4673 (4.5 KB)

          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4232 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4232 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:211600 (206.6 KB)  TX bytes:211600 (206.6 KB)

---

### Post by fritzjavel on 2008-07-03
Interfaces
auto lo 
iface lo inet loopback 
iface eth0 inet static 
address 74.186.143.67 
netmask 255.0.0.0 
gateway 65.14.252.4 
auto eth0

---

### Post by fritzjavel on 2008-07-03
I fixed the unable to find host problem, that was because of my host name in network/ host/ no name listed...

---

### Post by fritzjavel on 2008-07-03
But i'm still not connecting to the internet... Nothing seems to be working when i try it..

---

### Post by Iowan on 2008-07-03
Now that the hostname issue is history \\:D/, it's time to start afresh... 
You might try going back to DHCP (unless your ISP gave you specific IP). I don't use roaming mode, either.  The netmask looks unusual (but that would depend on your ISP, again.)

---

### Post by fritzjavel on 2008-07-03
So could you please help me on what to do? Like whats my first step?

---

