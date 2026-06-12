---
title: "Bonded BCM5709 (BNX2) flaps after reboot, but works on cold boot (ESXi)"
date: 2021-10-31
forum: Networking &amp; Wireless
---

### Post by kickit2 on 2021-10-31
I have an issues where my two bonded ports on NetXtreme II BCN5709s flap after hot reboot, but work perfectly fine on a full shutdown and reboot.
This system is running under ESXi 6.7 with the NICs being hardware pass thoughed. On a fresh cold boot, it seems to work, however I do seem to have times where the this device becomes unresponsive for a few seconds on the network (although theres nothing in syslog).
Everything worked great under 18.04 until a dist-upgrade, after which this began. Booting the older kernel left everything happy again. Thinking that perhaps 20.04 might resolve the issue, I upgraded the system and still have the same. Switch config (Cisco 3650G) has not changed.


Networking is unable to push any data, and this posts over and over the standard out (this is copied from syslog) [https://paste.ubuntu.com/p/RQgJMcJCZw/](https://paste.ubuntu.com/p/RQgJMcJCZw/)


Heres a full log from syslog [https://paste.ubuntu.com/p/7SNWjN2S9y/](https://paste.ubuntu.com/p/7SNWjN2S9y/)

...hopefully that enough - it goes on for ages.

Heres the interfaces config file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


auto ens192f0
iface ens192f0 inet manual
        bond-master bond0


auto ens192f1
iface ens192f1 inet manual
        bond-master bond0


auto bond0
iface bond0 inet static
        address 192.168.0.5
        gateway 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.255


        bond-mode 4
        bond-miimon 100
        bond-lacp-rate 1
        bond-slaves ens192f0 ens192f1


        dns-search local.lan
        dns-nameservers 192.168.0.1

```

---

