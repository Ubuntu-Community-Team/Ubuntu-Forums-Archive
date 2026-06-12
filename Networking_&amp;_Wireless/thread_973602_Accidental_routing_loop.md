---
title: "Accidental routing loop"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-11-06
I'm on a network with one gateway and one windows pc on the lan.  I wanted to test OpenVPN so I VPNed to the gateway, using default server.conf.  This works fine.

Then I configured server.conf to push the LAN subnet to the client.  After vpning in a second time I couldn't ping either the VPN subnet or LAN subnet.  Routing loop.

  (LAN)         (VPN)     (loopback)    (LAN)
10.11.12.0 -> 10.8.0.6 -> 127.0.0.0 -> 10.11.12.0

What I don't understand is how the loopback interface, 127.0.0.0/8 points to the LAN interface.  

I know the loopback gets to the LAN interface somehow because the first time I connected and 10.8.0.6 pointed to 127.0.0.1 my gateway was receiving pings.

windows route print:
```

Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       10.11.12.1    10.11.12.254       10
         10.8.0.1  255.255.255.255         10.8.0.5        10.8.0.6       1
         10.8.0.4  255.255.255.252         10.8.0.6        10.8.0.6       30
         **10.8.0.6  255.255.255.255        127.0.0.1       127.0.0.1       30**
       10.11.12.0    255.255.255.0     10.11.12.254    10.11.12.254       10
       **10.11.12.0    255.255.255.0         10.8.0.5        10.8.0.6       1**
     10.11.12.254  255.255.255.255        127.0.0.1       127.0.0.1       10
   10.255.255.255  255.255.255.255         10.8.0.6        10.8.0.6       30
   10.255.255.255  255.255.255.255     10.11.12.254    10.11.12.254       10
        **127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1**
    189.25.78.113  255.255.255.255       10.11.12.1    10.11.12.254       10
        224.0.0.0        240.0.0.0         10.8.0.6        10.8.0.6       30
        224.0.0.0        240.0.0.0     10.11.12.254    10.11.12.254       10
  255.255.255.255  255.255.255.255         10.8.0.6        10.8.0.6       1
  255.255.255.255  255.255.255.255     10.11.12.254    10.11.12.254       1
Default Gateway:        10.11.12.1

```

To fix the routing loop I can just push a separate subnet.

---

