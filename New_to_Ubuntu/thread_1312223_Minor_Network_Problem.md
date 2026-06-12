---
title: "Minor Network Problem"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by travmanx on 2009-11-03
I currently upgraded to 9.10 the day it came out. A few days before I installed 'Wicd Network Manager'. It worked fine, I connected via a static IP. 
When I reboot my computer the Network Manager says 'Connected to wired network (IP: 1.1.1.1) and I have no network connection at all. All I have to do is click disconnect and connect, then it auto obtains an IP, rather than static. (Doesn't matter to me whether it's static or auto).

I noticed when I click Scripts everything is blank, I'm sure something is supposed to be there to auto obtain my IP.

I've reinstalled Wicd, thinking it was a problem whilst upgrading. No luck. If I unistall WICD, will the default Ubuntu Network still be set up? Or is there a quick fix to this problem.

I did do a 'Test Hardware', but whats the point when I couldn't connect to the Internet to send in the bug while it reads my IP as 1.1.1.1 :P.

Thanks
Travis

Edit:
Figured I'd restart and post ifconfig -a results before and after:

> eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:b3:2b  
          inet addr:1.1.1.1  Bcast:1.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:a0ff:fe8a:b32b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:499 (499.0 B)  TX bytes:4094 (4.0 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8a:b3:2b  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe8a:b32b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:243633 (243.6 KB)  TX bytes:34135 (34.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



---

### Post by zvacet on 2009-11-03
Did you tried 

```
sudo pppoeconf
```

---

### Post by travmanx on 2009-11-03
> **zvacet said:**
> Did you tried 

```
sudo pppoeconf
```

 Sorry, I scanned 1 interface, but the Access              
 Concentrator of your provider did not respond. Please     
 check your network and modem cables. Another reason       
 for the scan failure may also be another running pppoe    
 process which controls the modem.      

Thanks for attempt tho :)

Hmmm should I just reinstall the default network manager?

---

### Post by zvacet on 2009-11-03
I´m not an expert but it look like wicd is still running.Yuo can try to uninstall it and then run above command.If that doesn´t work reinstall network manager.

---

