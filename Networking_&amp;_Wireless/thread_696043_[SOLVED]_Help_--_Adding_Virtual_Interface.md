---
title: "[SOLVED] Help -- Adding Virtual Interface"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by sgardne on 2008-02-13
Sorry for the double post, I didn't see this networking category. Mods, please delete the other one.

I am attempting to do this on a server I have. Here is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.x
netmask 255.255.255.248
gateway xxx.xxx.xxx.y
hwaddress ether 00:14:22:1b:58:c0

iface eth1:2000 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.2.2
hwaddress ether 00:14:22:1B:58:C1
```

Whenever i issue sudo ifup eth1:2000 i get the following:
```
$ sudo ifup eth1:2000
SIOCADDRT: No such process
Failed to bring up eth1:2000.
```

I have found that if I comment out the gateway entry of the interfaces file, I can get eth1:2000 to come up, but that's not enough. How do I make a route to 192.168.2.2?

---

### Post by sgardne on 2008-02-13
Okay, I don't know what changed, but now when I have the gateway line commented out and I issue the ifup command, i get this:

```
$ sudo ifup eth1:2000
SIOCSIFFLAGS: Cannot assign requested address
```

Any ideas?

---

### Post by sgardne on 2008-02-15
Solved: [http://ubuntuforums.org/showthread.php?t=696013](http://ubuntuforums.org/showthread.php?t=696013)

---

