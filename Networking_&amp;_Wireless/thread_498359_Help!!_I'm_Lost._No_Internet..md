---
title: "Help!! I'm Lost. No Internet."
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Dockdog on 2007-07-11
I don't know what to do. I have been reading posts for 2 days, reading everything I can find and I am still confused. I can't figure oyt how to configure my connection to the internet.

I am running a dual-boot system Windows XP and Feisty 7.04 

AMD AthlonXP 1800+
1.5 Ghz
256 RAM

I have two ways to choose from:

VIA Rhine II Fast Ethernet Adapter.
D-Link Air DWL - 250 Wireless PCI Adapter.

I have used terminal to get some data.

Results from ifconfig -a
[PHP]eth0      Link encap:Ethernet  HWaddr 00:50:2C:A6:5B:0E  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:17 Base address:0xd400 


eth0:avah Link encap:Ethernet  HWaddr 00:50:2C:A6:5B:0E  

          inet addr:169.254.4.77  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:17 Base address:0xd400 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:36 errors:0 dropped:0 overruns:0 frame:0

          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB)[/PHP]


Results from cat/etc/resolv.conf 
[PHP]bash: cat/etc/resolv.conf: No such file or directory [/PHP]

Results from netstat -rn
[PHP]Kernel IP routing table

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0

0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0[/PHP]

I'm not sure which way will be the best way to connect. I'll take anything at this point. I really want to learn Linux. This is all very new to me. I have been a Windows user since 3.1.

I am will to do as much work as needed. I don't want to just get it working, I want to learn how to get it working.

If anyone can help, I thank you. 

Dockdog.

---

### Post by Dockdog on 2007-07-11
I can't believe it!!!!!!!!!! I found a post from adampyre "How to install Ubuntu and configure wireless - Ubuntu 7.04 on a Dell C610 Laptop.

I started with the instructions and when I got to the point of " install Build-essential" I got a message that I had 90 updates, do you want to download now? I clicked Yes and I now have internet.:)

Thanks to anyone who has read this and was willing to help.

I guess I got lucky.

---

