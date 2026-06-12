---
title: "[Help] Client can't get internet from server ubuntu 14.0"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2015-01-15
Hi Master,

Modem <-- eth0(192.168.100.10) - Server Ubuntu 14.04 - >eth1 (192.168.11.0/26) -- switch --client

Modem is setting to bridge and have configure it all with pppoeconf via terminal and was modified also to /etc/sysctl.conf (net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1,net.ipv4.ip_forward=1), and the last -- > iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE.

After it, I do to ping from client,can't ping smoothly. where is the problem for this case?reach of document of setting adslpppoe in google, all nothing make solve for this server 14



this is my configuration full,

/etc/network/interfaces
```

#WAN-from ADSL INternet
auto eth0
iface eth0 inet static
address 192.168.100.10
netmask	255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255
gateway 192.168.100.3
dns-nameservers 192.168.100.3

#LAN
auto eth1
iface eth1 inet static
address 192.168.11.1
netmask	255.255.255.192
network 192.168.11.0
broadcast 192.168.11.63
dns-nameservers 192.168.11.1
dns-search mylab.local


auto dsl-provider
iface dsl-provider inet ppp
pre-up /bin/ip link set eth0 up # line maintained by pppoeconf
provider dsl-provider

```

on rc.local
```



killall pppd
ifconfig eth0 up
pon dsl-provider
ifconfig eth1 up


```

NAT and stored on ip_table files so when boot first the configurate success loaded
```

iptables -t nat -A POSTROUTING -O eth0 -j MASQUERADE

```

for sysctl.conf
```

net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.ip_forward=1

```

and the last point, my modem adsl to set on bridge and restart modem and also restart server. and still cant ping from client

please help me :(

thanks

---

