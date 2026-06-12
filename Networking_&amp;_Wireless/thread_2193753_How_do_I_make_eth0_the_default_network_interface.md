---
title: "How do I make eth0 the default network interface?"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by miceagol on 2013-12-14
I have set up VPN on a server. Whenever I start the VPN server with
```

sudo service openvpn start

```
all internet traffic is routed through the tun0 interface, which then becomes available. However, I still want the server to use eth0 when I start openvpn. How do I make it the default interface? 

I want the tun0 to be available, since I'm using this interface for one user only.

---

### Post by varunendra on 2013-12-15
I'm not familiar with VPN in Ubuntu yet, but can't you define static routes so that all but the traffic from that particular user goes through eth0?

Please see this (mostly unrelated post) if you know even lesser than I do about routing table :P : [http://ubuntuforums.org/showthread.php?p=12819114](http://ubuntuforums.org/showthread.php?p=12819114)

Accordingly, I'd like to see the output of "route -n" after tun0 interface is created, also the IP of the user for which you want to use it.

---

### Post by miceagol on 2013-12-18
> **varunendra said:**
> I'm not familiar with VPN in Ubuntu yet, but can't you define static routes so that all but the traffic from that particular user goes through eth0?

Please see this (mostly unrelated post) if you know even lesser than I do about routing table :P : [http://ubuntuforums.org/showthread.php?p=12819114](http://ubuntuforums.org/showthread.php?p=12819114)

Accordingly, I'd like to see the output of "route -n" after tun0 interface is created, also the IP of the user for which you want to use it.

The thing is that I have already created a script which runs all traffic from one specific user through the tun0 interface. This script worked flawlessly to start with, then suddenly all traffic started to use the tun0 interface whenever openvpn is running. 

So there has to be something wrong with the default routing.

route -n before starting openvpn:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.19.1    0.0.0.0         UG    0      0        0 eth0
192.168.19.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

After starting openvpn:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.104.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.19.1    0.0.0.0         UG    0      0        0 eth0
10.104.1.1      10.104.1.5      255.255.255.255 UGH   0      0        0 tun0
10.104.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
109.201.154.154 192.168.19.1    255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.104.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.19.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

---

### Post by miceagol on 2013-12-18
And with the above routing after starting openvpn, I lose my Internet connection, so there is something wrong with that table. But I need help to find the error. :-/

---

