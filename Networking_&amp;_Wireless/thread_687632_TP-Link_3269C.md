---
title: "TP-Link 3269C"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by snafle on 2008-02-04
This is a cheapass Gigabit card I nabbed off ebay to use in my first file-server- a windows based machine. It worked fine, got decent speeds and all was well.

In ubuntu (7.10) it doesn't work- not only that, but the steps for installing the chipset it's based on (R8169SC) don't appear to work- I make install, insmod and such, all to no avail. The card included on my mobo works great, but I'd like to have the whole gigabit thing going on.

This is the ouput of ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:19:E0:76:D5:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x4000 

eth3      Link encap:Ethernet  HWaddr 00:17:31:36:66:0F  
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe36:660f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:832 (832.0 b)  TX bytes:5202 (5.0 KB)
          Interrupt:19 Base address:0xc000 

eth0 being the gigabit and eth3 being the motherboard one. I know that r8169 modules is installed, since it shows up in lsmod, and I've tried r8169-6.005.00 and r8169-5.004.00 from realtek but no worky.

Help would be lovely ;)

---

