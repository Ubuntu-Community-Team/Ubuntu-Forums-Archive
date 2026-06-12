---
title: "Add static route to 14.04 server"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by Jamesss on 2015-11-23
Hi,

I have installed Ubuntu 14.04.2 LTS and configured my interfaces file in /etc/network as follows

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
	address 10.0.2.251
	netmask 255.255.255.0
	gateway 10.0.2.1
	dns-nameservers 8.8.8.8 8.8.4.4

auto em1:0
iface em1:0 inet static
	address 172.16.1.6
	netmask 255.255.0.0
	gateway 172.16.0.1
	dns-nameservers 8.8.8.8 8.8.4.4
	
post-up route add -net XXX.XXX.XXX.XXX netmask 255.255.255.255 gw 172.16.0.1

```

However the static route does not work on reboot. It does work if I enter the command manually (pre-faced with sudo) though.

The IP address is a public address on the internet

can anyone help?

thanks
James

---

