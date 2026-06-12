---
title: "Ubuntu 16.04.2 periodical link down with two network dapter"
date: 2017-03-02
forum: Networking &amp; Wireless
---

### Post by 6-dmitry on 2017-03-02
Hello.

Tomorrow I'm reinstall on my home server Ubuntu 16.04.2 and now have a problem: periodical in random time two network adapters down link. Before reinstalling everything worked fine.

This is /etc/network/interfaces:```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


#source /etc/network/interfaces.d/*


auto lo br0 enp0s16 enp0s17


# The loopback network interface
iface lo inet loopback


# The primary network interface
iface enp0s16 inet dhcp


# The second network interface
iface enp0s17 inet manual


# Virtual bridge
iface br0 inet dhcp
        bridge_ports enp0s17

```
I'm need br0 for virtual machines network access.

What may be incorrect? Or need find issue in another place?

---

