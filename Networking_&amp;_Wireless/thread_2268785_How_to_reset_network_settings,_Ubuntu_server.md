---
title: "How to reset network settings, Ubuntu server?"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by ouassim95 on 2015-03-11
I have a HP Proliant server with Ubuntu installed on it. Someone before me has set up a static IP and i want to set it back to a IP appointed by the DHCP. Could somebody tell me how i can reset the network settings to default or set the static ip back to DHCP?

---

### Post by SeijiSensei on 2015-03-11
Find the file /etc/network/interfaces and edit it (as root with sudo) so it looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Then reboot.

For more details read [https://help.ubuntu.com/14.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/14.04/serverguide/network-configuration.html#ip-addressing).

---

### Post by ouassim95 on 2015-03-12
I still have no internet connection.

---

### Post by SeijiSensei on 2015-03-12
Reboot, then post the results of the commands
```

ifconfig
route -n

```
in [noparse]```

```[/noparse] tags.

In particular, when you run "route -n" do you see a line like this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```
The gateway address will depend on your computer's network subnet.  If you don't have a gateway entry, then that is the problem.  Your DHCP server may not be providing the gateway correctly.

---

