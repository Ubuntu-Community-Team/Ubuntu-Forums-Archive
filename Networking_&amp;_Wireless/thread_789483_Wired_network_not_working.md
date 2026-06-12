---
title: "Wired network not working"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Nirc on 2008-05-10
I have wired networking between my windows PC and my linux one. This was working fine until this morning, now the PCs won't talk the lights on the network ports do not even come on, not even before the OS has loaded. But if I plug them into my router or my xbox 360 then network activity lights come on and the connection works.
lspci gives the correct information:

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 21)

and so does ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1C:C4:DB:B5:39  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c4ff:fedb:b539/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1131 (1.1 KiB)  TX bytes:5922 (5.7 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5312107 (5.0 MiB)  TX bytes:5312107 (5.0 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:63:28:F4  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe63:28f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:811379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:781594 errors:2 dropped:2 overruns:0 carrier:0
          collisions:46913 txqueuelen:1000 
          RX bytes:683976310 (652.2 MiB)  TX bytes:481352716 (459.0 MiB)
          Interrupt:16 Base address:0x4000 

I haven't changed anything or done any updates since last night, any ideas whats wrong?

---

### Post by superprash2003 on 2008-05-10
hmm.. some cable problem??

---

### Post by Nirc on 2008-05-11
I don't think its a cable problem as I can use the same cable to connect to my xbox 360, also I tried 2 different cables and got the same result with both.

---

