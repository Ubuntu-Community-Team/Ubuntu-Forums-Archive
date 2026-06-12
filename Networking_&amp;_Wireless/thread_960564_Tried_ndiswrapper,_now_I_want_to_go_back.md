---
title: "Tried ndiswrapper, now I want to go back"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Deten on 2008-10-27
I tried ndiswrapper, but it gave me more trouble then the current wireless... now how do I go back?

Info
8.10 Intrepid
Intel Corporation PRO/Wireless 3945ABG

I installed through repositories and followed the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Then to remove it, I uninstalled it through repositories, unblacklisted modprobe.p but I now have NO wireless.

Can someone help me activate the initial ubuntu drivers for wireless?

Thanks

---

### Post by Deten on 2008-10-27
hrmm, I tried making sure I removed ndiswrapper from modprobe but that didnt fix it either.

---

### Post by Deten on 2008-10-27
Anyone know how to get the original install drivers into ubuntu?

---

### Post by Deten on 2008-10-28
unashamed bump

---

### Post by Deten on 2008-10-28
my ifconfig doesnt even show wlan0 anymore

```
eth0      Link encap:Ethernet  HWaddr 00:13:a9:47:72:1c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe47:721c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27357 (27.3 KB)  TX bytes:12570 (12.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

```

---

### Post by Deten on 2008-10-28
the solution:

I had to 

```
locate ndiswrapper
```

and either rm or rmdir to get rid off every instance of ndiswrapper

after I restarted wireless is working again

---

