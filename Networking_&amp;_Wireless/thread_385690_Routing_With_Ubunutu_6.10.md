---
title: "Routing With Ubunutu 6.10"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by cycloptivity on 2007-03-16
Hi guys,
For the past 48 hours I've been trying to get my box to route my internet traffic through to my LAN without success. The local IRC channels haven't been helpful and i have a LAN starting in like 4 hours :( .

Anyway heres the go, I have tried following various tutorials which produced iptables errors, i have set ```
net.ipv4.conf.forwarding=1
``` in my **/etc/sysctl.conf**. And the results of netstat -nr are;

```

root@gateway:~# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         10.0.0.138      0.0.0.0         UG        0 0          0 eth1

```

Basicaly the setup is eth0  will run DHCP  out the LAN and eth1 will pipe in internet traffic but this has eluded me. any help would be really *really* appreciated

Cheers,

---

