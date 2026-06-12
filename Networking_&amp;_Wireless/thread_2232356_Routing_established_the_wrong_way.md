---
title: "Routing established the wrong way"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by marcelo_ni on 2014-07-01
Here follows the routing table (route -n output) from my Ubuntu 10.04 machine. 

[FONT=courier new]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.181.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.206.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0[/FONT]

All home pcs are behind a Linksys router, with a 192.168.1.0 local network. 
As can be seen, the eth0 interface has the destination set to the local network and the gateway set to 0.0.0.0; wlan0 have two routes: one is like the eth0's, but the other (last row) is correct. 
So, the eth0 interface cannot be used to access the internet. If I disable the wifi, I lost all internet access.
I cannot say when this funny thing started, but surely it was recent, because I never care regarding wifi connection.

The only thing I could possibly correlate was I had to reject two kernel updates (2.6.32-61 and 2.6.32-62) because they lost some mouse events. 

TIA 

Regards

---

### Post by clearski on 2014-07-01
According to the routing table, the only way you can forward packets  beyond your local network segment is through 192.168.1.1 on *wlan0* interface.

```
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0
```

It means that you have a gateway defined in the *wlan0* section of your /etc/network/interfaces configuration file.

You need to add a gateway to the *eth0 *section:

```
gateway 192.168.1.1
```

Eventually restart. :)

This way, when you disable wifi (your *wlan0* interface), you should be able to access Internet using the other interface (eth0).

---

