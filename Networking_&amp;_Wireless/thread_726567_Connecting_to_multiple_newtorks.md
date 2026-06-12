---
title: "Connecting to multiple newtorks"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by rstuart on 2008-03-16
Hi All,

I have a need to connect to a wired and wireless network simultaneously. The wired network is eth0 and the wireless eth1. Unfortunately NetworkManager doesn't support this (well, 0.7 does but not sure if it is released and only version 0.6.6 is listed in the packages for the upcoming hardy).

Is there an alternate GUI tool i can use to do this or will i have to follow kevdog's sticky post about manual network connections?

Cheers

---

### Post by Suparious on 2008-03-17
Of course there are always tools like [webmin]("http://prdownloads.sourceforge.net/webadmin/webmin_1.400_all.deb") that can GUI-ify all your ubuntu configurations with the simple install of a .deb package. 

The only alternative that I know of would be to familiarize yourself with /etc/network/interfaces. Here is a simple example:

```
[CODE]suparious@kronikus:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth5
iface lo inet loopback

# The primary network interface
iface eth5 inet static
        address         216.40.103.200
        netmask         255.255.255.240
        broadcast       216.40.103.207
        network         216.40.103.192
        gateway         216.40.103.206

```

here is what I think you are asking:

```
suparious@kronikus:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address         207.40.103.200
        netmask         255.255.255.240
        broadcast       207.40.103.207
        network         207.40.103.192
        gateway         207.40.103.206

# The secondary network interface
iface eth1 inet static
        address         192.168.0.33
        netmask         255.255.255.0
        broadcast       192.168.0.255
        network         192.168.0.0
        gateway         192.168.0.1

```

or for dual DHCP:
```
suparious@kronikus:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet dhcp

```

---

