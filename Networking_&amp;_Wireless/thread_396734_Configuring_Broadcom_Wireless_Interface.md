---
title: "Configuring Broadcom Wireless Interface"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by shadyzay on 2007-03-29
Hello, I was trying to configure a Broadcom BC4311 wireless card on a laptop ( Dell Inspiron 6400 ).

This is what I did:
1. Blacklist bcm43xx
2. Installed the latest ndiswrapper ( from sourceforge )
3. Brought the driver files from the windows installation ( they're called: oem14.inf, bcm4sbxp.sys )
4. Installed the driver in ndiswrapper the output looked fine:
```
oem14 : driver installed
                     device (14E4:170C) present (alternate driver: b44)

```
5. modprobe ndiswrapper, everything looks fine as described by wiki's and other forum posts.

Now the problem is:
I open 'network settings', there's no eth0, only eth1 ( for the lan ).
trying to ifup eth0 gives a 'ERROR while getting interface flags: No such device' error

dmesg shows no problems at all.

here are some related files:
file: /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
	address 172.16.1.10
	netmask 255.255.0.0
	network 172.16.0.0
	broadcast 172.16.255.255
	gateway 172.16.1.1
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid NETGEAR
	wireless-key1 77777777777777777777777777
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.2.9 192.168.2.14

iface eth1 inet dhcp

auto eth1

```

file: /etc/iftab
```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:18:f3:32:54:e4 arp 1
eth1 mac 00:15:c5:b8:95:af arp 1

```

file: /etc/modprobe.d/ndiswrapper
```

alias wlan0 ndiswrapper

```

Any Ideas??

---

### Post by Floppyjoe on 2007-03-29
When you use ndiswrapper on a Broadcom card the usual network interface created for it is eth1. Your wireless settings in /etc/network/interfaces should be under the eth1 interface not the eth0. eth0 is the wired ethernet connection.

---

### Post by shadyzay on 2007-03-29
So I should replace eth0 with eth1 in /etc/network/interfaces and vice versa ??

---

### Post by Floppyjoe on 2007-03-29
Just make sure there is no wireless stuff in the eth0 interface stuff

---

