---
title: "OpenVPN client and nginx"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by Confused_Cheese on 2015-09-27
Hiya,

I have a headless linux box that currently runs a few sites through nginx. I want to also use the box to redirect a specific users traffic through an OpenVPN connection that I don't have server control over (I believe this is possible via iptables forcing a user to use the tun0 interface?).

The problem I have is that when I connect to OpenVPN, it auto routes all traffic over the VPN which kills incoming requests to sites hosted through nginx.

I currently have no iptable rules.

My routes before:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 p2p1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p2p1

```

After connecting:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.111.1.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 p2p1
10.111.1.1      10.111.1.5      255.255.255.255 UGH   0      0        0 tun0
10.111.1.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
104.238.169.26  192.168.1.1     255.255.255.255 UGH   0      0        0 p2p1
128.0.0.0       10.111.1.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p2p1



```

Can anyone help? :(

---

