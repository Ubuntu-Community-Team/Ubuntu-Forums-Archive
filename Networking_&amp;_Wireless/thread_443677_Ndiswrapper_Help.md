---
title: "Ndiswrapper Help"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by kilroy423 on 2007-05-14
Trying to figure out why Ubuntu has'nt recognized my wifi card after loading the driver via ndiswrapper...

```
dan@dan-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
w39n51          
driver present, hardware present
```

```
dan@dan-laptop:~$ iwconfig

lo        no wireless extensions.
sit0      no wireless extensions.
eth0      no wireless extensions.
```

```
dan@dan-laptop:~$ ifconfig
eth0      
Link encap:Ethernet  
HWaddr 00:16:D4:3F:CE:0A
          UP BROADCAST MULTICAST  MTU:1500  
Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0        
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000       
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback        
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1      
RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)
```

thx in advance for any help and if you need more info let me know

dan

---

