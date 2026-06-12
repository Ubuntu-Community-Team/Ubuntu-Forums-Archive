---
title: "cant connect to internet in clean ubuntu server 14.04.3"
date: 2016-01-23
forum: Networking &amp; Wireless
---

### Post by ishay on 2016-01-23
hello :)
i just installed a ubuntu server 14.04.3 on a vm and i am unable to connect to the internet.
ping google.com gives the output:
 ping: unknown host google.com

/etc/network/interfaces looks like this:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

ifconfig -a does not show an ipaddress for eth0

thank you very much in advance for your help :)

---

### Post by Harvey_Artz on 2016-01-25
Shut down your vm and go into settings, change your network interface to bridged.

You don't say what virtualization software you're using, but most are easy to find the settings.

---

