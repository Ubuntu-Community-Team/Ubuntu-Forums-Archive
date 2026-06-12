---
title: "Networking issue - unable to ping 8.8.8.8 etc"
date: 2019-07-07
forum: Networking &amp; Wireless
---

### Post by katoiam2 on 2019-07-07
Hello,

Thank you in advance to anyone who can help me.

I am currently able to connect to a router (tried in 3 different locations) and ping it, but unable to connect beyond in any way, be it:
ping [www.google.com](www.google.com)
ping 8.8.8.8
Normal web browsing
apt update
Torrents
Selektor to the tor network
Nor PeerGuardian.

I'm using Kubuntu 16.04.

I've searched high and low through many different forums and can't find anything that makes a difference.

I feel like I'm going crazy!

---

### Post by wildmanne39 on 2019-07-07
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by katoiam2 on 2019-07-07
mtr 8.8.8.8 gives me no information at all but doing it for my routers ip (mtr 192.168.43.199) gives me information for that step. 
Which is confusing as I would have thought mtr 8.8.8.8 would at least give me the step to the router as well.

---

### Post by katoiam2 on 2019-07-07
The only thing I have done network wise recently was :
dpkg-reconfigure resolveconf

When I was trying to get a hotel Internet connection working, though it didn't help!

---

### Post by The Cog on 2019-07-08
You are right expecting mtr to at least show your next-hop router. That makes me wonder if you actually have a default route via that next-hop router. Can you try the command "ip route" and post the response. I expect to see

---

### Post by katoiam2 on 2019-07-08
Well things have gotten even more worse/stuck!
Now I can't even see let alone connect to wifi!
                                                                                                                                                              
katoiam@katoiam-lovetop:~$ ip route                                                                                                                                                                                                                
default dev wlp8s0  scope link  metric 1003 linkdown                                                                                                                                                                                               
169.254.0.0/16 dev wlp8s0  proto kernel  scope link  src 169.254.5.222 linkdown                                                                                                                                                                    
169.254.0.0/16 dev anbox0  scope link  metric 1000                                                                                                                                                                                                 
192.168.250.0/24 dev anbox0  proto kernel  scope link  src 192.168.250.1                                                                                                                                                                           


katoiam@katoiam-lovetop:~$ sudo ifdown wlp8s0
[sudo] password for katoiam: 
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlp8s0/c4:85:08:05:f4:15
Sending on   LPF/wlp8s0/c4:85:08:05:f4:15
Sending on   Socket/fallback
DHCPRELEASE on wlp8s0 to 192.168.43.199 port 67 (xid=0x74c5b2dc)

katoiam@katoiam-lovetop:~$ sudo ifup wlp8s0
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlp8s0/c4:85:08:05:f4:15
Sending on   LPF/wlp8s0/c4:85:08:05:f4:15
Sending on   Socket/fallback
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 3 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 7 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 9 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 21 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 15 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 13 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 19 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 15 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 16 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 15 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 8 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 20 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 14 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 11 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 12 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 17 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 8 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 15 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 7 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 12 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 20 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 21 (xid=0x6177e456)
DHCPDISCOVER on wlp8s0 to 255.255.255.255 port 67 interval 3 (xid=0x6177e456)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


katoiam@katoiam-lovetop:~$ ifconfig 
anbox0    Link encap:Ethernet  HWaddr d6:88:4d:d5:e3:13  
          inet addr:192.168.250.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::d488:4dff:fed5:e313/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3613 (3.6 KB)

enp7s0    Link encap:Ethernet  HWaddr d4:be:d9:34:63:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0                                                                                                                                                                                                      
          inet6 addr: ::1/128 Scope:Host                                                                                                                                                                                                           
          UP LOOPBACK RUNNING  MTU:65536  Metric:1                                                                                                                                                                                                 
          RX packets:1792 errors:0 dropped:0 overruns:0 frame:0                                                                                                                                                                                    
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                                                                                  
          collisions:0 txqueuelen:1                                                                                                                                                                                                                
          RX bytes:135872 (135.8 KB)  TX bytes:135872 (135.8 KB)                                                                                                                                                                                   
                                                                                                                                                                                                                                                   
wlp8s0    Link encap:Ethernet  HWaddr c4:85:08:05:f4:15                                                                                                                                                                                            
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                                                                                                               
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                                                                                                                                                       
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                                                                                     
          collisions:0 txqueuelen:1000                                                                                                                                                                                                             
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                                                                                                                                                   
                                                                                                                                                                                                                                                   
wlp8s0:avahi Link encap:Ethernet  HWaddr c4:85:08:05:f4:15                                                                                                                                                                                         
          inet addr:169.254.5.222  Bcast:169.254.255.255  Mask:255.255.0.0                                                                                                                                                                         
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     

katoiam@katoiam-lovetop:~$ ping  8.8.8.8                                                                                                                                                                                                             
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of  data.                                                                                                                                                                                                        
^C                                                                                                                                                                                                                                                  
--- 8.8.8.8 ping statistics  ---                                                                                                                                                                                                                     
4 packets transmitted, 0 received, 100% packet loss, time  2999ms

---

### Post by chili555 on 2019-07-09
If you can use ifup/down, that suggests that you have populated /etc/network/interfaces in preference to Network Manager. The fact that you cannot connect, suggests that the settings in /etc/network/interfaces are faulty. May we have a look?

```
cat /etc/network/interfaces
```Doesn't the usual reliable Network Manager do the job perfectly well?

---

