---
title: "Problem connecting with a static IP through PPPoE"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by gaelfx on 2008-07-04
I work in China at a University and their network is setup such that I must use a Static IP address (probably because of the switch I'm connected to) and then connect by dialing up the PPPoE connection. This works great in Windows, which is not surprising in China, but I can't get it to work in Ubuntu 8.04. I haven't tried any other version of Linux, but I'm guessing I would have the same problem with any other distro. I asked the student that helps me with computer problems if he knew why I can't connect with Linux and he told me that he has never used Linux (he's a computer major in China, it's really a shame). Does anyone have any experience with trying to make such a connection in Linux? Could you guide me through the process of fixing it? If you need any other information, just post a reply and I will get back to you as soon as possible. Thank you.

---

### Post by gaelfx on 2008-07-05
Hate to bump something, but I could really use some help on this one.

---

### Post by superprash2003 on 2008-07-05
just to make sure you have an ip.. go to the terminal and type ifconfig and post output here.. if you are sure you have an ip then type sudo pppoeconf in the terminal and create a dialer

---

### Post by gaelfx on 2008-07-05
Here's the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:1c:28:a4  
          inet addr:210.31.212.178  Bcast:210.31.212.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe1c:28a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9060 (8.8 KB)  TX bytes:7749 (7.5 KB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98864 (96.5 KB)  TX bytes:98864 (96.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.8.255.93  P-t-P:10.8.255.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:30 (30.0 B)  TX bytes:30 (30.0 B)

```

I hope that helps, but I don't see anything that looks all that useful there. Then again, networking is not really my strong point.

---

### Post by gaelfx on 2008-07-05
Well, as is usually the case in any of my ventures, the solution was so remarkably simple that I wish I had never asked the question. Turns out, I had to change my wired connection to "enable roaming mode", which to me makes no sense, but it works. Whoopee.

---

