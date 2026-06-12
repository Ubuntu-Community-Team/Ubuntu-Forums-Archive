---
title: "Can Connect to the Internet but No Network :("
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by afzalnaj on 2007-08-28
Hello...i have been extremely active and have discovered a way to connect to the internet
when connection is the following

Server Type : PPTP
Authentication : MSCHAP V2
Compression : MPPC

i connected via pptpconfig

but before connecting through the tunnel...i was able to access my LAN sites but not the internet...now i can access the internet but not the LAN sites...as soon as i stop the tunnel...i can access LAN sites...i think this is a routing problem...plz help me solve this 

thanks

here are the result of route -n before and after starting the tunnel

Before Starting Tunnel


```
[FONT="System"]afzal@ProStreet:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.104.128.0    0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         10.104.128.3    0.0.0.0         UG    0      0        0 eth0
afzal@ProStreet:~$[/FONT]
```

After Starting Tunnel

```
[FONT="System"]afzal@ProStreet:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.101.10.1     10.104.128.3    255.255.255.255 UGH   0      0        0 eth0
125.209.120.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.104.128.0    0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
afzal@ProStreet:~$[/FONT]
```

---

