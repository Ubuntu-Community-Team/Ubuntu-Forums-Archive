---
title: "Multiple IP on one interface"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by wjrhee77 on 2008-05-28
Hello all,

I have a server on DMZ with external static ip assigned and /etc/network/interfaces is as below :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address x.x.x.179
        netmask 255.255.255.240
        network x.x.x.176
        broadcast x.x.x.191
        gateway x.x.x.177

What i want to do is to add an internal LAN static ip (192.168.0.140) to same interface so that clients on LAN can connect to server on DMZ using MySQL ODBC connector to 192.168.0.140, not x.x.x179 <-- this is the eth0.

So what i would do is start by adding eth0:0,  
auto eth0:0
iface eth0:0 inet static
        address 192.168.0.140
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

Few things I am not sure about.  Can i add multiple ip to one interface with different subnet & gateway?  In this case, I am trying to use one external static ip & one internal LAN static ip to same network interface.

Any opinions on multiple ips on same network interface would be great.  In this case, i want to add one global static ip (x.x.x.179) & one internal ip (192.168.0.140)

Thank you.****

---

