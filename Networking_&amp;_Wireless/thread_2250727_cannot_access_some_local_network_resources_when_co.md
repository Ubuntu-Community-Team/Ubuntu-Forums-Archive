---
title: "cannot access some local network resources when connected to vpn."
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by cybercity@localhost on 2014-10-30
My isp has configured a VPN (PPTP) server in order to connect to the internet and a basic DHCP server to assign ip to the clients everything is ok but i cannot access some network destinations when i am connected to a vpn server. i guess there has to be some routing table modifications in ethernet or vpn connection to resolve that issue.
here is my routing config before connecting to vpn.
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.87.8.1              0.0.0.0         UG       0      0        0 eth0
10.87.8.0       0.0.0.0            255.255.254.0   U         1      0        0 eth0

```
in this configuration i can access all network resources but cannot access internet because i have to establish a vpn connection.

and this is how my routing table looks like when i am connected to a vpn server.
```

Destination     Gateway         Genmask         Flags   Metric Ref    Use Iface
0.0.0.0           0.0.0.0              0.0.0.0             U         0      0        0 ppp0
10.87.8.0        0.0.0.0            255.255.254.0    U         1      0        0 eth0
172.17.1.10    10.87.8.1       255.255.255.255   UGH    0      0        0 eth0
172.17.1.10    10.87.8.1       255.255.255.255  UGH     0      0        0 eth0
172.17.1.10    0.0.0.0           255.255.255.255  UH       0      0        0 ppp0

```
i need your help to fix this issue.

---

