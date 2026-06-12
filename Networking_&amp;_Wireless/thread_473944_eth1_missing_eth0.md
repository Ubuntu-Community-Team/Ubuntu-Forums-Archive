---
title: "eth1? missing eth0"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by jcpunk on 2007-06-14
I just upgraded my network card from an old ISA to a PCI card, but the new card shows up as eth1.  How on earth do I make it eth0 like the rest of my ubuntu installations?

ifconfig -a only shows eth1, lo, and sit0.

---

### Post by linux noooob on 2007-06-14
there is eth1 because the computer still thinks that the old network card is there so you can leave it (like me) or you can uninstall the last network card even though it is not there.

---

### Post by baustiech on 2007-11-28
Wow, that was the most remarkably unhelpful reply I think I've ever read anywhere.

It caused me to actually login and attempt something more helpful...

check /etc/iftab

This file manually maps MAC address to eth device names.  For whatever reasons, across several ubuntu versions, I've had it cause all kinds of problems, many more than it purports to solve.

---

### Post by cmcginty on 2008-06-06
I had a similar problem in Hardy Heron 8.04.

First look at /etc/udev/rules.d/70-persitent-net.rules. My file looked like this:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:4d:94:0a:87", ATTR{type}=="1", NAME="eth0"

# PCI device 0x1969:0x1048 (atl1)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:c6:38:53:e0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

My old device was the first one, and my new device was the second one. I just deleted the first device lines, and changed the second name to 'eth0', like so:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x1969:0x1048 (atl1)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:c6:38:53:e0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

