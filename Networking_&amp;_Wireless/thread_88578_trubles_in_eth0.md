---
title: "trubles in eth0"
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by pminetti on 2005-11-10
Hi
Someone can tell me where are the config files for network when my system startup
actually my system do not start eth0, nor "lo" , I go to system adminsitration network and activate eth0, but seems not to be working, because when I boot again no eth0 active!

sorry for my English!

thanks

---

### Post by invalid on 2005-11-10
The file is /etc/network/interfaces

Just for reference, here is what mine looks like:
```
beau@willow:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface usb0 inet static
address 192.168.129.1
netmask 255.255.255.0

```

Cheers,
Cb

---

