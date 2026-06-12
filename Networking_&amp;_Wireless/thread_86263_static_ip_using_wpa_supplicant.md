---
title: "static ip using wpa_supplicant"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by juicybananahead on 2005-11-04
Hi there,

After much toil and trouble I managed to get my Netgear wg511v2 (Marvell chipset) working using ndiswrapper. However, I'm connecting to my ap using wpa_supplicant. DHCP works fine but has anyone had any success setting up a static ip while using wpa_supplicant? My /etc/network/interfaces looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

# auto eth0

iface wlan0 inet static
        address 192.168.1.7
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 81.1.113.10 81.1.113.11

auto wlan0

```

Any comments will be greatly appreciated!

/juicy

---

### Post by juicybananahead on 2005-11-05
For future reference, I managed to get it working with the following /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

#iface eth0 inet dhcp

# auto eth0

#iface wlan0 inet dhcp

iface wlan0 inet static
	address 192.168.1.7
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
#	dns-nameservers 81.1.113.10 81.1.113.11

auto wlan0

```

---

