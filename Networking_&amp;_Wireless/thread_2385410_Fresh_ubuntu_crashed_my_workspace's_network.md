---
title: "Fresh ubuntu crashed my workspace's network"
date: 2018-02-20
forum: Networking &amp; Wireless
---

### Post by jinziqiao88 on 2018-02-20
Hello,
I did a fresh install of ubuntu 16.04 at work, when trying to set static ip for it, I made a mistake and the loopback device started broadcasting fake ips to the network. This happened after I set the proxy server and it broke 40+ people's Internet.  Problem was solved as I turned off the loopback device.

Can you help me understand how is this possible?

/etc/network interfaces is the only file I changed.

auto lo
iface lo inet static
address 10.37.67.191
netmask 255.255.252.0
gateway 10.37.67.254
dns-nameservers 10.37.4.1 10.37.4.3

As you can guess from address and mask this broadcasts  10.37.64.* to 10.37.67.* . Clients with those ip can not access the Internet because their ips were reseted. I can also ping this ips on my ubuntu machine, unpluged.

I understand that "lo" should be "eth0", but how is a loopback device visible from outside?
Is the network set properly if it allows this to happen?
I am a noob sorry. 
Thank you for you help.

---

### Post by wyliecoyoteuk on 2018-02-20
you have set the lo interface to a network visible IP.
It should be 127.0.0.1:
or
auto lo
iface lo inet loopback


You should create a new stanza like:

iface eth0 inet static
address 10.37.67.191
netmask 255.255.252.0
gateway 10.37.67.254
dns-nameservers 10.37.4.1 10.37.4.3

BUT: depending on your version of Ubuntu, this will be managed by network manager or netmap, so you shouldn't really be editing the interfaces file.

---

### Post by chili555 on 2018-02-20
```
auto lo
iface lo inet loopback

[COLOR="#FF0000"]auto eth0[/COLOR]
iface eth0 inet static
address 10.37.67.191
netmask 255.255.252.0
gateway 10.37.67.254
dns-nameservers 10.37.4.1 10.37.4.3

```Of course, verify what the interface name is from:```
ifconfig
```It may be eth1 or enp3s0 or some other depending on your exact Ubuntu version and hardware details.

---

