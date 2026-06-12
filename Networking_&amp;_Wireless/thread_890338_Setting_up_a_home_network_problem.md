---
title: "Setting up a home network problem"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-08-14
I have two interfaces on my ubuntu 8.04 machine, eth0 and eth1.  eth0 is for internet(working) and eth1 uses dhcp with a static ip(not working) for my other computers on the network.  

 My windows machine can't ping domain names or ips when connected to eth1.  It acquires an ip address from my dhcp3 server and can ping the static ip, but nothing on the internet.  I also tried disabling ufw.

-----------------------
/etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
auto eth1
-----------------------
/etc/dhcp3/dhcpd.conf

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 64.71.255.198;
option domain-name "shwick.mydomain";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.100;
} 
-----------------------
/etc/default/dhcp3-server

INTERFACES="eth1"
-----------------------
/etc/resolv.conf

search phub.net.cable.rogers.com
nameserver 64.71.255.198


I'm thinking this has something to do with the gateway.  When I enter a gateway in interfaces for eth1, interface eth0 can't connect/ping the internet.

I read through the ubuntu server guide but I'm really confused right now, any help is welcome.

---

### Post by insineratehymn on 2008-08-14
I can help with the logic...

Basically what you need to do is assing all the computers connected to your server on a different subnet and let your server act as a router. So you would have 2 subnets, one for all of the computers that are internet accessible, then all of the ones that see your server as their default gateway.

So.

Router goes to Laptop (hypothetical) on subnet 1.
Router goes to Ubuntu server on subnet 1.
Laptop (hypothetical) goes to Ubuntu server on subnet 2.
Xbox (hypothetical) goes to Ubuntu server on subnet 2.

---

### Post by ilrudie on 2008-08-15
If I understand what you are trying to do correctly you will need to configure your Ubuntu server as a NAT masquerading router for this to work.

[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

Also eth1 probably isnt its own gateway (because that doesn't make any sense) so you can take that out of the eth1 stanza and most likely the netmask is not needed either.

---

### Post by Shwick2 on 2008-09-23
Sorry for the long time before reply.

 The problem was that I didn't have port forwarding enabled.  I disabled ufw because it was going to cause problems moving forward with other services.  I used this as a guide to enable port forwarding with iptables: [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

---

