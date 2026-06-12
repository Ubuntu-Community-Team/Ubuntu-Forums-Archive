---
title: "Lost Network"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by timjohn7 on 2008-04-04
After installing Gutsy 2 months ago, I've had no network problems. Wireless connection from my Atheros card on my laptop to my router and wireless network access from my laptop to desktop shared folders (still got XP on Desktop).

Yesterday I ran Update manager and installed the available updates (about 8).

Today I still have full internet connection through the router, but I have no access to my Desktop.  When clicking Places-Network I get an error message saying "File Doesnt Exist"


here's the output of ifconfig

Please help... As a newbie, this is puzzling and I don't know what to do to restore my previously perfectly-working network.

tim@tim-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:03:2F:16:CE:AF  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:2fff:fe16:ceaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3469009 (3.3 MB)  TX bytes:428977 (418.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:03:0D:0D:59:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vbox0     Link encap:Ethernet  HWaddr 00:FF:F5:9F:81:2C  
          inet6 addr: fe80::2ff:f5ff:fe9f:812c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-03-2F-16-CE-AF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27920 errors:0 dropped:0 overruns:0 frame:276
          TX packets:3737 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6546620 (6.2 MB)  TX bytes:593999 (580.0 KB)
          Interrupt:16

---

