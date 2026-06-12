---
title: "Network Bridge; ICS?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by louman on 2007-07-10
My box has two network cards, eth0 and eth1. eth0 is connected to a 4-port router via DHCP, and eth1 isn't connected to anything (yet).

What I want is to be able to plug a device into eth1 (in this case a wifi access point) and automatically obtain an address through the router's DHCP. This would require some sort of connection between eth0 and eth1.

Essentially, I'd like the connection to eth1 behave transparently the same as if I were to plug in to a port on the router and lease an address via DHCP. 
Here's a rough sketch of what I mean:
[IMG]http://img367.imageshack.us/img367/8576/blahqv7.png[/IMG]

I have tried to use brctl to bridge eth0 to eth1, but the documentation I've found on it is unclear and I'm not sure it's what I should be using.

I have looked at the ubuntu community documentation for InternetConnectionSharing and NetworkConnectionBridge but they haven't helped me.
Here's what my /etc/network/interfaces configuration looks like (which doesn't work):
```
# The primary network interface
auto eth0
iface eth0 inet dhcp


iface br0 inet dhcp
bridge_ports eth0 eth1
auto br0
```

Anyone with networking (specifically with Ubuntu/Linux) experience please point me in the right direction. Thanks!

---

