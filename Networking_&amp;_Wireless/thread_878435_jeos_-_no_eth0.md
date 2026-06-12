---
title: "jeos - no eth0"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by prickly on 2008-08-02
I created a jeos virtual machine and moved it to ESXi and now the networking is broken. 

I had a static IP address set before the move and I have changed /etc/networking/interfaces to the following to try and get it to work:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

When I run 'ifconfig' eth0 does not exist. 

My windows virtual machine imported into ESXi fine so I know that ESXi is working, can anyone suggest things that I can do to get my jeos virtual machine working?

Many thanks.

---

### Post by prickly on 2008-08-03
I just figured this out so you can delete this if necessary.

Eth0 was not present after the virtual machine was moved to ESXi but I later found that eth1 existed and I just used that instead :D

---

