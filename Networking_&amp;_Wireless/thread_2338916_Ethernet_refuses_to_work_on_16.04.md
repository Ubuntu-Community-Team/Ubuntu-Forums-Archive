---
title: "Ethernet refuses to work on 16.04"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by jwut on 2016-10-02
I just upgraded one of my old PC's to ubuntu 16.04 and the Ethernet completely quit on me.  It will act like its connected, but won't work.
Any help would be greatly appreciated.  Thanks in advance!

Output of ifconfig
```

enp0s25   Link encap:Ethernet  HWaddr 00:1a:a0:a0:0b:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


enp0s25:avahi Link encap:Ethernet  HWaddr 00:1a:a0:a0:0b:f9  
          inet addr:169.254.9.68  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:206048 (206.0 KB)  TX bytes:206048 (206.0 KB)
```



Output of dmesg | grep "eth0"

```
[    1.800789] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1a:a0:a0:0b:f9
[    1.800794] e1000e 0000:00:19.0 eth0: Intel(R) PRO/10/100 Network Connection
[    1.800820] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[    1.952917] e1000e 0000:00:19.0 enp0s25: renamed from eth0
```

---

### Post by ajgreeny on 2016-10-03
Let's see the output of ```
cat /etc/network/interfaces
```to see if that gives us any clues.

---

