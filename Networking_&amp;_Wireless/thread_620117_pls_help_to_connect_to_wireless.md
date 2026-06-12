---
title: "pls help to connect to wireless"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by hi100 on 2007-11-22
hi 

I have  belkin wireless usb but unable to install it.it is belkin f5d7050 version 3001uk 

I was able to successfully install rt73 driver but was not able to connect to internet.

when i type  

 sudo lshw -C network 

  *-network                
       description: Wireless interface 
       physical id: 2 
       logical name: rausb0 
              capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN 

when i type 

 iwconfig

output
 
lo        no wireless extensions. 
 
rausb0    RT73 WLAN  ESSID:off/any   
          Mode:Auto  Channel=1  Bit Rate=54 Mb/s    
          RTS thr:off   Fragment thr:off 

when i type ifconfig

output           


 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:513 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:42004 (41.0 KB)  TX bytes:42004 (41.0 KB) 
 

can any one pls suggest me where i am going wrong.

---

