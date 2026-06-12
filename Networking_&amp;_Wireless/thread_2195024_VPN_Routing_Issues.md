---
title: "VPN Routing Issues"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by image28 on 2013-12-21
I have a home pptp vpn server running on my router. When I try connect to it it disconnects after 2 minutes every time. I worked out this is a routing issue, possibly because my local network and my home network have the same ip ranges. After playing with the routing table I managed to get the connection to stay up ( don't remember what I did though )... With the default settings my routing table looks as follows before and after the vpn connection.

Before VPN:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

after VPN:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
101.XX.XXX.XX   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
101.XX.XXX.XX   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

I want all my internet traffic to go through the vpn and also access the samba shares from my home network, But I know way to little about networking and routing.
Any help would be hugely apreciated.... 

Thanks.

---

### Post by image28 on 2013-12-22
This routing table seems to work, bit unsure if it is sending data just through the vpn or sending it through both vpn and unsecure wireless connection.... anyone see anything wrong with this routing table.... again know very little about network routing...

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
101.XX.XXX.XX   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
101.XX.XXX.XX   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0 <<< is this sending traffic through both???
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0  <<< ????

```

---

