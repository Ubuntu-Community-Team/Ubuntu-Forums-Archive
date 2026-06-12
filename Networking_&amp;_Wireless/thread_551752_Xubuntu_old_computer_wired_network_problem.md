---
title: "Xubuntu: old computer wired network problem"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Prosis on 2007-09-15
Hello

I have a wired network on an old IBM thinkpad with Xubuntu on it.  But when I log in, I get a weird IP address.  So I have to go into the network manager, uncheck my wired  connection and recheck it so it works.

How can I get rid of this problem?

Here's my /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp





auto eth0

```

Thank You

---

