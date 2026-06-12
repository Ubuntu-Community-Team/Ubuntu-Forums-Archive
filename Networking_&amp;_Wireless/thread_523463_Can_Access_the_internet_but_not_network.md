---
title: "Can Access the internet but not network"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by cetol on 2007-08-11
It seems that after changing from dhcp to statis ip's on all my computers I can no longer access my network storage device. I can access the internet but can not ping any of my network resources or router. Neither can I access my router. Any ideas are appreciated.

Thanks in advance

---

### Post by Kralizec on 2007-08-12
Sort of wondering why you would use a static IP instead of DHCP...but thats not my call. And it may or may not be the problem but the most obvious thing I can think of is that the subnets aren't the same on all the network devices.

---

### Post by cetol on 2007-08-12
All my windows boxes work fine, its only my fiesty laptop. All configs are the same otherwise.

---

### Post by Kralizec on 2007-08-12
Well I'm sorry to say that I'm not very familiar with networking with Ubuntu either, so I can't be of much help... Good luck, though.

---

### Post by cetol on 2007-08-12
New Information.

This lap top is dual boot. It is only ubuntu that can't access my network resources. When I boot in windows everything works fine.

The configurations are the same for the network. Anyone else have this issue???

Here is the output from ifconfig wlan0

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:6C:03:4C  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe6c:34c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1922933 (1.8 MiB)  TX bytes:148645 (145.1 KiB)
          Interrupt:5 Memory:faff6000-faff8000

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by thoffland on 2007-12-13
I'm having the same problem. I just put this hard drive in for dual booting Vista and Ubuntu and while I can surf the net, I can't access my network. I can't even ping my router, which is weird. 

I'm on the same Windows network (configured Samba) and have a static IP address so my router will allow certain protocols through for Windows and Ubuntu. This is really irritating, but I'm sure it's something simple... if I find it out I'll post back.

---

### Post by Lostincyberspace on 2007-12-13
@If you are not on the internet can you ping any thing? and can any of your other boxes ping the router?

---

### Post by thoffland on 2007-12-13
I cant ping the router or laptop from my desktop, and my laptop cannot ping the desktop, but it can ping the router just fine.

---

### Post by thoffland on 2007-12-13
Ok, I got it fixed. I have 2 ethernet controllers on this PC and eth0 was set for DHCP and eth1 was my static... however, the PC was using eth0 for a connection. I still dont know why I couldn't ping my router, but I disabled eth1 and set eth0 to static, and I'm able to ping and use NXServer now. 

Hope this helps someone else.

---

