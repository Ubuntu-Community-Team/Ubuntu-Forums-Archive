---
title: "Lost network when moving drive to another systerm"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Schleproque on 2008-06-23
Good Day,

I have a system set up with a software mirror in which drives are bootable. I take one of the drives to another system with exactly the same hardware and the system appears to boot normally but when I check the ip address I get the following message:

Error Fetching interface information: device not found. 

When I check for the device files it is not there.

Any suggestions?

Thank You,
Rodney Holmes

---

### Post by dmizer on 2008-06-24
even though the specs are the same (linux doesn't really care if they are or not), the network adapter is different.  every NIC has a unique MAC address, and because of this, your system will assign it a new logical name.

you can find out what your card's logical name is by looking at the following command:
```
lshw -C network
```
it will be listed next to "logical name" like so:
```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED
       description: Ethernet interface
       product: 82801DB PRO/100 VM (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       [COLOR="Red"]logical name: eth2[/COLOR]
       version: 81
       serial: 00:0b:cd:4a:41:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=eepro100 multicast=yes
       resources: iomemory:fc500000-fc500fff ioport:1400-143f irq:193
```

then you can edit /etc/network/interfaces:
```
gksudo gedit /etc/network/interfaces
```
and change your current settings to your new logical name:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto [COLOR="Red"]eth0[/COLOR]
iface [COLOR="Red"]eth0[/COLOR] inet dhcp
```
in my case, i have to edit "eth0" so it reads "eth2" instead.

---

