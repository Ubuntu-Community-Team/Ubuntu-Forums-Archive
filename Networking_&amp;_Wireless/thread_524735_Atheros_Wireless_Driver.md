---
title: "Atheros Wireless Driver"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Samnsparky on 2007-08-13
:confused: This is very confusing. I have an Atheros wireless card  with ndiswrapper in my Aspire 5570z and I have this for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1B:24:2A:54:8E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:24:2A:54:8E  
          inet addr:XXXXXXXX Bcast:XXXXXXX  Mask:XXXXXX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1220 (1.1 KiB)  TX bytes:1220 (1.1 KiB)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:54100000-54110000 

wlan0:ava Link encap:Ethernet  HWaddr XXXXXXX 
          inet addr:XXXXXXXX Bcast:XXXXXXXX  Mask:XXXXXXX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:54100000-54110000 

In network settings I have a wireless device, with roaming enabled, and this is in my ndiswrapper -l:

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci).

However in the network manager there are no wireless networks listed and I can not connect to any wireless networks. Anyone know how to fix this?

Thanks,
Sam

---

### Post by Samnsparky on 2007-08-13
Just so you know I get this:

sam@sam-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

even though I am right next to my wireless router.

---

### Post by Samnsparky on 2007-08-13
I fixed it. (I am not sure how but I did)

---

