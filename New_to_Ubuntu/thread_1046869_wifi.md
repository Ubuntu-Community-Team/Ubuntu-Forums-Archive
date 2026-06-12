---
title: "wifi"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by evrkusd on 2009-01-21
basic question about wifi in 8.10 (compaq presario f700, tried to install mad-wifi but apparently failed or don't know how to work it)

is there supposed to be a simple way to check out the SSIDs in the area? 

in control i have network tools and network configuration, neither of which display any sort of wifi options. 

thanks for your help.

---

### Post by yobird42 on 2009-01-21
type in sudo ifconfig in terminal and post results

---

### Post by evrkusd on 2009-01-21
ath0      Link encap:Ethernet  HWaddr 00:1f:3a:86:92:a2  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      
Link encap:Ethernet  HWaddr 00:1e:68:43:0e:65  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:220 

lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:7738 (7.7 KB)  TX bytes:7738 (7.7 KB)

wifi0     L
ink encap:UNSPEC  HWaddr 00-1F-3A-86-92-A2-30-30-00-00-00-00-00-00-00-00  
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:1143 errors:0 dropped:0 overruns:0 frame:7
          
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:280 
          
RX bytes:128254 (128.2 KB)  
TX bytes:1231 (1.2 KB)
          
Interrupt:19

---

### Post by yobird42 on 2009-01-21
ok your wireless card is recognized so that's not a problem 

sudo iwlist scan will list them for you.

---

### Post by evrkusd on 2009-01-21
ah, you are wonderful. just got it. thanks thanks thanks.

---

