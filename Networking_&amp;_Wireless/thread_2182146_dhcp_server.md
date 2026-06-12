---
title: "dhcp server"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Bondar_Mircea on 2013-10-20
I have two network card on my server (eth0 and eth1). On eth0 i plugged the internet cable. I have static ip from my isp and add to /etc/network/interfaces: ip, gateway, mask, broadcast...I have ping with google.com. I install isc dhcp with this conf:

```

authoritaive;
subnet 192.168.50.0 netmask 255.255.255.0{
range 192.168.50.100 192.168.50.150;
option broadcast-address 192.168.50.255;
option routers 192.168.50.1;
default-lease-time 600;
max-lease-time 7200;
}

```

on eth1(where dhcp server listening)

```

iface eth1 inet static
address 192.168.50.1
netmask 255.255.255.0
broadcast 192.168.50.255

```

on eth0 (internet)

```

iface eth0 inet static
address 86.120.135.9
netmask 255.255.255.128
gateway 255.255.255.128

```

in resolv.conf
```

nameserver 213.154.124.1    nameserver 193.231.252.1


```
I have enabled ipv4 forwarding (net.ipv4.ip_forward=1)
I have added this in iptables:

```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
. The problem after this is: The internet on server work (ping for google.ro work). I connect another computer to server and the ip for that computer is 192.168.50.102, netmask 255.255.255.0, gateway 192.168.50.1, dns server 192.168.50.1....but the internet not work (i have limited or no conectivity). I need help

---

### Post by tenmoi on 2013-10-20
Your config

on eth0 (internet)

Code:

iface eth0 inet static
address 86.120.135.9
[B]netmask 255.255.255.128
gateway 255.255.255.128[/B]

Take a close look at the lines in bold, please.

---

### Post by Bondar_Mircea on 2013-10-20
I type wrong in forum gateway is 86.120.135.1

---

### Post by Doug S on 2013-10-20
Please post the output for these commands: "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L", after you have tried accessing internet from 192.168.50.102.

---

