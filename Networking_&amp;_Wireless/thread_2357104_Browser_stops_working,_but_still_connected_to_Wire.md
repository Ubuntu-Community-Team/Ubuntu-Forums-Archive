---
title: "Browser stops working, but still connected to Wireless"
date: 2017-03-30
forum: Networking &amp; Wireless
---

### Post by martimus on 2017-03-30
Hello every one!

Still very new to Ubuntu, I've recently started to have intermittent problems with web browsing. Firefox stops working and says that its lost connection to the server. I have the same problem when I fire up Chrome.
 When I check my wireless connection it's still connected. The only way I can get the browser to start working again is by restarting my computer. All other device on my network are unaffected by this problem.
 I have noticed that while running Transmission, it seems to accelerate the problem (may just be a coincidence), however, it still happens regardless if Transmission is running or not. I am suspecting that it
 may be my wireless USB adapter since its old. I've tried updating the firmware, but was unsuccessful. Its an old Netgear USB adapter (WN111v2). Ive read several other post that seemed to have similar problems,
 but nothing has worked. Here are some commands that I've run while the browser is down.

[PHP]p { margin-bottom: 0.1in; line-height: 120%; }a:link {  }   
Ping google:
 
 
 ping www.google.com
 ping: unknown host www.google.com

p { margin-bottom: 0.1in; line-height: 120%; }a:link {  }   

Ping 4.2.2.2:

 
 
 PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
 64 bytes from 4.2.2.2: icmp_seq=1 ttl=57 time=20.4 ms
 64 bytes from 4.2.2.2: icmp_seq=2 ttl=57 time=20.3 ms
 64 bytes from 4.2.2.2: icmp_seq=3 ttl=57 time=20.2 ms
 64 bytes from 4.2.2.2: icmp_seq=4 ttl=57 time=20.2 ms
 64 bytes from 4.2.2.2: icmp_seq=5 ttl=57 time=20.0 ms
 64 bytes from 4.2.2.2: icmp_seq=6 ttl=57 time=30.9 ms
 64 bytes from 4.2.2.2: icmp_seq=7 ttl=57 time=20.2 ms
 ^C
 --- 4.2.2.2 ping statistics ---
 7 packets transmitted, 7 received, 0% packet loss, time 6007ms
 rtt min/avg/max/mdev = 20.042/21.795/30.961/3.744 ms
 
 
[/PHP]
[PHP]p { margin-bottom: 0.1in; line-height: 120%; }a:link {  }   

Ifconfig:
 
 
 enp0s31f6 Link encap:Ethernet  HWaddr 34:97:f6:91:0f:ce   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:16 Memory:f7100000-f7120000  
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:16601 errors:0 dropped:0 overruns:0 frame:0
           TX packets:16601 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1  
           RX bytes:1655755 (1.6 MB)  TX bytes:1655755 (1.6 MB)

[/PHP]

---

