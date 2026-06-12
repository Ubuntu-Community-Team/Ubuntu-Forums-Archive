---
title: "[Help] Seeting up the routes for pptp"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by arsham on 2008-10-16
Hi there,
I managed to make a pptp connection with kvpnc.
I get connected , but I have problems with routing.
After connection stablished, I have no access to the internet.

Here is my settings :
```
eth2 : inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
```

The route table before vpn : 
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth2
```

The route table after vpn : 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     255.255.255.255 UGH   0      0        0 ppp0
10.10.10.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
64.22.72.121    192.168.1.1     255.255.255.255 UGH   0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         10.10.10.1      0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth2


```

Regards

---

### Post by fwre01 on 2008-10-17
> **arsham said:**
> Hi there,
I managed to make a pptp connection with kvpnc.
I get connected , but I have problems with routing.
After connection stablished, I have no access to the internet.

Here is my settings :
```
eth2 : inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
```

The route table before vpn : 
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth2
```

The route table after vpn : 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     255.255.255.255 UGH   0      0        0 ppp0
10.10.10.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
64.22.72.121    192.168.1.1     255.255.255.255 UGH   0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         10.10.10.1      0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth2


```

Regards

You have multiple default routes with the same metrics, (im not sure which one it will pick during a metric tie) however, one of them shouldnt really be there, what are the subnets you are trying to reach at the end of the vpn tunnel?

you should have something which looks more like this....

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
10.10.10.0      255.255.255.0   255.255.255.255 UH    0      0        0 ppp0
64.22.72.121    192.168.1.1     255.255.255.255 UGH   0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2

```

---

