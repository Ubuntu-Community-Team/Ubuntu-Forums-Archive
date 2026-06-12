---
title: "Some network configuration"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by reauthor on 2007-04-11
Hy...

I use network-manager-gnome for my wireless network which have radius server for authentication,and works perfectly...Now,I need to setup a static ip address with static routes  which will works in combinatin with network-manager-gnome..I done something like this:First I connect whith network-manager-gnome than I must restart network interfaces than I can use virtual ip adress(eth1:0) and static routes...I know that is a stupid way to make things work but that is the only way for me...So if somebody can tell me a good way to make this work..Thanks a lot guys...

This is my interfaces configuration:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid MSI


auto eth1:0
iface eth1:0 inet static
address 10.52.190.11
netmask 255.255.255.0

#static routes
up /sbin/route add -net 10.52.230.0/24 gw 10.52.190.10 dev eth1
down /sbin/route del -net 10.52.230.0/24 gw 10.52.190.10 dev eth1

up /sbin/route add -net 10.52.220.0/24 gw 10.52.190.10 dev eth1
down /sbin/route del -net 10.52.220.0/24 gw 10.52.190.10 dev eth1

up /sbin/route add -net 10.52.210.0/24 gw 10.52.190.10 dev eth1
down /sbin/route del -net 10.52.210.0/24 gw 10.52.190.10 dev eth1

up /sbin/route add -net 10.52.200.0/24 gw 10.52.190.10 dev eth1
down /sbin/route del -net 10.52.200.0/24 gw 10.52.190.10 dev eth1

---

