---
title: "Network start only with network-admin's help"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by dronord on 2006-11-16
OS 6.10, KDE, under VMWare.

File /etc/network/interfaces is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp
```

```
sudo ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
```
and on boot system network start failure.

Folder /var/run/network/ not exist.

After upgrade from Breeze(gnome), have network-admin, use him.

---

### Post by dronord on 2006-11-16
```
sudo dhclient
``` helped me.
Why it not work automatically? (when booting OS)

---

