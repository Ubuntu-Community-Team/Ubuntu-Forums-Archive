---
title: "VPNC routes"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Muflon on 2008-11-11
Hi 

I am trying to use VPNC with Intrepid.  This used to work under Hardy.

My routing table goes from

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

```

to this when VPNC is connected

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
86.13.88.3      192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 tun0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

```

However I am unable to ping any of the servers on the VPN.

Does anyone know if the routes look correct?

Thanks

Muflon

---

