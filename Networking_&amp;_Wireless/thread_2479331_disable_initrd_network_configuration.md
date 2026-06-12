---
title: "disable initrd network configuration?"
date: 2022-09-21
forum: Networking &amp; Wireless
---

### Post by valentijnsessink on 2022-09-21
Hi,

In short: how to tell initrd to not run dhclient during boot? I don't need the network during boot time, I'm not using any iscsi- or other network-related drives; and the dhclient that starts causes problems.

Setup: I have a machine running 22.04 (upgraded from 20.04 upgraded from -- well, might have been 18.04 or even 16.04) that has a couple of bridges over VLAN's. It has an old fashioned /etc/network/interfaces file that goes like this:
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
address something-something
[netmask, yada yada]
bridge_ports enp1s0
Another bridge, br1, is running from a vlan that is running on enp1s0, which works, because Linux filters out vlan packets before doing anything else (i.e. br0 won't notice the VLAN packets). Unfortunately, during boot, the initrdwill try to use dhclient to fetch an IP address for its' main interface, enp0s1. If it doesn't succeed, it takes a loooong time. If it does succeed, the main interface will have an IP address that clashes with it's bridge interface and the host is unreachable.

Now the only thing I would like to do is to disable dhclient in initrd - but do it the official way, i.e. how can I tell initrd to not run dhclient? I found /etc/default/networking and tried to set "CONFIGURE_INTERFACES=no", but this doesn't help (even after update-initrd -k all -u).

Best regards,

Valentijn

---

