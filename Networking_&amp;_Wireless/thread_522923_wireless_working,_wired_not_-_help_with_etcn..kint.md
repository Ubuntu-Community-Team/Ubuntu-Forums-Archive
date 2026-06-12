---
title: "wireless working, wired not - help with /etc/n..k/interfaces"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by theolster on 2007-08-11
I'm trying to re-install Ubuntu Server 6.06 LTS after a harddisk failure, and I can't for the life of me work out how I had my /etc/network/interfaces set up!

I configured my wireless networking through the install cd, and all works fine, I can ping and ssh.  But on the CD there was no option for configuring the wired network, only one or the other.

Although I want to set up port-forwarding and so on, at the moment I'd be happy for a ping!

Your help would be appreciated - my interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
face lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.26
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        wireless-key1 **********
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search home

auto eth0
iface eth0 static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
```

---

### Post by lloyd_b on 2007-08-11
I'm assuming that "eth0" is the wired network interface.  I see one definite problem and one possible problem with the "interfaces" section for eth0:

1.  Definite problem:
```
iface eth0 static
```
should be
```
iface eth0 inet static
```

2. Possible problem:  You don't have any gateway defined for this interface.  This is acceptable if there genuinely isn't a gateway on that subnet (for instance, if your gateway to the internet is via the wireless).

Lloyd B.

---

