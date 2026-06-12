---
title: "How to install network if I skipped during installation?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2007-04-10
I installed Ubuntu 6.10 Server, but I skipped the whole network configuration.  Once I have Ubuntu installed and I boot into it, how do I set up the whole network stuff after the fact?

---

### Post by spd106 on 2007-04-10
You want the /etc/network/interfaces file. This is where you put the configuration settings for each interface. Try the man pages for details (man interfaces).
It will probably end up looking something like this
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.150
netmask 255.0.0.0
gateway 10.0.0.1
dns-nameserver 10.0.0.145

auto eth1
iface eth1 inet dhcp

```

You can also use *ifconfig* and *route* or *ip addr* and *ip route* to give you the current state and configure things temporarily.

---

### Post by quux on 2007-04-10
Configuration of network interfaces can be done in /etc/network/interfaces, see "man interfaces" for a description and examples. 

If you use DHCP, the config typically looks like this:
```

auto eth0
iface eth0 inet dhcp

```

---

