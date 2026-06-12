---
title: "Routing table configuration lost after reboot"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2015-01-23
Hello everyone,

On Ubuntu 14.10, I've removed one static route and added 2 new ones into the ipv4 routing table:

```
root@MSI-GE60-Ubuntu-14:/home/actionmystique# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         box             0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        *               255.0.0.0       U     0      0        0 tap0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0
192.168.56.0    *               255.255.255.0   U     0      0        0 virbr2
192.168.100.0   *               255.255.255.0   U     0      0        0 virbr0
192.168.110.0   *               255.255.255.0   U     0      0        0 virbr1
192.168.127.0   *               255.255.255.0   U     0      0        0 tap1
192.168.137.0   *               255.255.255.0   U     0      0        0 tap0
root@MSI-GE60-Ubuntu-14:/home/actionmystique# route del -net 10.0.0.0 netmask 255.0.0.0
root@MSI-GE60-Ubuntu-14:/home/actionmystique# route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.137.122
root@MSI-GE60-Ubuntu-14:/home/actionmystique# route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.137.112
root@MSI-GE60-Ubuntu-14:/home/actionmystique# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         box             0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        192.168.137.112 255.0.0.0       UG    0      0        0 tap0
10.0.0.0        192.168.137.122 255.0.0.0       UG    0      0        0 tap0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0
192.168.56.0    *               255.255.255.0   U     0      0        0 virbr2
192.168.100.0   *               255.255.255.0   U     0      0        0 virbr0
192.168.110.0   *               255.255.255.0   U     0      0        0 virbr1
192.168.127.0   *               255.255.255.0   U     0      0        0 tap1
192.168.137.0   *               255.255.255.0   U     0      0        0 tap0
```

After reboot, the first routing table is back: any hint or is this just another bug?

BTW, does anyone know a GUI app for manipulating the routing table?

---

### Post by actionmystique on 2015-01-23
Apparently, it is necessary to edit /etc/network/interfaces to make changes permanent across reboots.

---

### Post by actionmystique on 2015-01-24
Webmin is a nice GUI for manipulating all host configuration, including routing.

---

### Post by actionmystique on 2015-01-24
However, **neither** webmin **nor** the configuration in **/etc/network/interfaces** have any impact on the routing table after reboot and I have just found the reason:
my static routes point towards addresses accessible on a loopback tap1 interface, which is created in **/etc/rc.local** probably loaded after /etc/network/interfaces.

The following setting works in /etc/rc.local where my tap interfaces are created:
sudo route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.127.111
sudo route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.127.112

---

### Post by SeijiSensei on 2015-01-24
The commands in /etc/rc.local are run with root privileges.  You don't need to include "sudo" on the command lines.

---

