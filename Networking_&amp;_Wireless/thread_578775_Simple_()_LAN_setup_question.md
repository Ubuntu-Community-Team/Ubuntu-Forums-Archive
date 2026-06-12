---
title: "Simple (?) LAN setup question"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by juantao on 2007-10-17
Hello, 

I am able to obtain a lease from my LAN but I cannot ping out to the world from it. Probably because I do not understand the meaning of a 'gateway' or some other seemingly simple (to you) concept...

Here are my dhcpd.conf and /etc/network/interfaces files - do you see the error? 

Thanks, Jon D.

### /etc/dhcpd.conf

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.7.255;
option routers 192.168.7.1;
option domain-name-servers 69.9.129.9, 4.2.2.1, 66.241.64.10;
option domain-name "dsl.mind.net";

subnet 192.168.7.0 netmask 255.255.255.0 {
range 192.168.7.41 192.168.7.49;
}


### /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 69.9.146.99
        netmask 255.255.255.0
        network 69.9.146.0
        broadcast 69.9.146.255
        gateway 69.9.146.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 69.9.129.9 4.2.2.1 66.241.64.10
        dns-search dsl.mind.net

# The secondary network interface
auto eth0
iface eth0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0

---

### Post by mpokrywka on 2007-10-18
Two things:
1. Check if forwarding is active on your "gateway" (this server with dhcpd and two lan interfaces)
```
cat /proc/sys/net/ipv4/ip_forward
```
should be 1

If not, add line:
```
net.ipv4.ip_forward=1
```
to /etc/sysctl.conf

2. Check if IP masquerading is set on eth1 on your gateway:
```
iptables -t nat -nv -L
```
If there is nothing in POSTROUTING chain, you should add something like:
```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

You can use tcpdump to look if packets are flowing both directions, like:
**tcpdump -ni eth1**
(to check what is going on on your "internet" interface)

---

