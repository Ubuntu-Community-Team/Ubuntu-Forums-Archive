---
title: "Edgy Server DHCP-&gt;Static IP??"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by jboehm on 2006-12-15
This is probably a very simple question but I can't seem to find the answer.  How do I change Edgy Server from DHCP->Static IP?  Remember server does not have a GUI, terminal only. (Unless I did something horribly wrong.) 

Thanks,
Jon

---

### Post by geek_Man on 2006-12-15
I guess you could install a GUI ```
sudo aptitude install ubuntu-desktop
``` although it takes a lot of space on your HD. I'm also guessing there's a file somewhere that you can change to make your IP static.

---

### Post by Iowan on 2006-12-15
**/etc/network/interfaces**
It may also be necessary to disable the dhclient - but I don't know the clean way to do it.

---

### Post by tturrisi on 2006-12-15
~#editor /etc/network/interfaces
example
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
allow-hotplug eth0
#STATIC
iface eth0 inet static
address 192.168.1.10
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
#DYNAMIC
#iface eth0 inet dhcp
auto eth0

```

This file initiates at boot and the system will determine whether or not to start dhcp based on the contents of this file.

---

