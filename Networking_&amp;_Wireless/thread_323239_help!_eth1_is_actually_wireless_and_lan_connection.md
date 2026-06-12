---
title: "help! eth1 is actually wireless and lan connection not working...."
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by aznranndydraman on 2006-12-21
I had installed Edgy and had no previous Linux experience. Right now my network connection is shown as eth1, but infact it is by wireless and not the Ethernet at all (I was wondering why it was so slow so I unplugged the cable and that's how I found out). Does anyone know anything about this or do I need to give more info?

---

### Post by scrooge_74 on 2006-12-21
you need to give more info

do ifconfig and post details

do you want to conect wireless or ethernet based?

---

### Post by aznranndydraman on 2006-12-21
wow that was quick, thanx:
eth0      Link encap:Ethernet  HWaddr 00:14:22:DE:93:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:47:C7:46  
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5487697 (5.2 MiB)  TX bytes:1545450 (1.4 MiB)
          Interrupt:201 Base address:0x6000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7179 (7.0 KiB)  TX bytes:7179 (7.0 KiB)

---

### Post by aznranndydraman on 2006-12-21
the smilies is actually a :D, forgot to disable them

---

### Post by scrooge_74 on 2006-12-21
Well it seems you are connected using eth1, do you want to use eth0? connect it open terminal type sudo ifup eth0
and sudo ifdown eth1

or from the network panel enable eth0 and disable eth1

---

### Post by aznranndydraman on 2006-12-21
that's a good idea, I'll try that,but is eth1 suppose to be wireless? or is it that it can be anything you set it to?

---

### Post by scrooge_74 on 2006-12-21
> **aznranndydraman said:**
> that's a good idea, I'll try that,but is eth1 suppose to be wireless? or is it that it can be anything you set it to?

Generally the system will take care of that for you unless you want to configure that manually ;)

Your wireless card can also be something like ath0

---

### Post by aznranndydraman on 2006-12-21
i see....thanks again!

---

