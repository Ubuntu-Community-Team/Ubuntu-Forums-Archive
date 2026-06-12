---
title: "Upgraded to new router and now wired connection will not work."
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by john229 on 2014-05-23
Tried ifconfig,
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 80:ee:73:14:7d:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1968951 (1.9 MB)  TX bytes:1968951 (1.9 MB)


wlan0     Link encap:Ethernet  HWaddr e0:91:53:45:09:72  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:53ff:fe45:972/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:624301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:755811701 (755.8 MB)  TX bytes:61035064 (61.0 MB)
I have been searching this issue since I upgraded and finally decided to post.

---

### Post by cmcanulty on 2014-05-23
I upgraded my router last week and similar issue I couldn't figure it out after 12 hours called in a pro and took him 2 1/2 hours don't still know what the issue is. One thing might help go to edit under the connections icon and delete all the old connections then restart.

---

