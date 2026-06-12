---
title: "Cant connect to internet but can VNC fine"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by uMuppet on 2008-08-10
Firefox or APT cant connect to the internet but I can VNC to the machine over the internet just fine.  It uses a static wired IP address.
It all used to work fine until I tried to install a 3G wireless card a couple of weeks ago, I have uninstalled the 3G card now and removed all software.  
This is the output of my ifconfig
 
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:8f:85:dd  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe8f:85dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5013092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4152940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5784392308 (5.3 GB)  TX bytes:2627868377 (2.4 GB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:767629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:767629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:391173660 (373.0 MB)  TX bytes:391173660 (373.0 MB)

Thanks

---

