---
title: "Ubuntu server - network not started on bootup"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Oblong_Cheese on 2007-12-18
Hi all, 

I have a slight problem with Ubuntu server; during the install process I opted to setup networking at a later time. Now, it seems as though eth0, my only network interface, is not configured to be brought up during the init process.

I understand this is handled by Upstart now, but I'm having trouble understanding the structure of this system.

I have configured my network interfaces as such:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# this hotplug thing needed for some reason?
#
mapping hotplug
        script grep
        map eth0
iface eth0 inet static
        address 192.168.1.53
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254

```

In older versions of Ubuntu, in order to reset the network config to new values, I would have tried
```

sudo /etc/init.d/networking restart

```
which in this case, doesn't appear to do anything.

In any case, the above config isn't read at all during init, and I have to physically logon at the machine (a headless server), run dhclient manually, and start network-dependent services manually.

Does anyone have any ideas?

Thanks in advance!

---

