---
title: "Problem with network bridge"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by andyesten on 2008-05-01
I installed Ubuntu 8.04 and configured a network bridge by adding these lines to /etc/network/interfaces:

auto br0
iface br0 inet dhcp
    bridge_ports eth0

After a fresh reboot the network is not working. The routing tabel look after the reboot like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         outpost         0.0.0.0         UG    0      0        0 eth0
default         outpost         0.0.0.0         UG    100    0        0 br0

When I stop and start the network everything is fine and the routing table looks like:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         outpost         0.0.0.0         UG    100    0        0 br0

Is this a known problem? Anyone knows how to solve this problem?

Andy

---

### Post by nixscripter on 2008-05-01
It looks like it's bringing up the ethernet, setting up the routing for that, then bringing up the bridge, creating a conflict.

What else is in /etc/network interfaces? Make sure that the eth0 interface isn't configured automatically with an IP.

---

### Post by andyesten on 2008-05-02
Thanks for the reply. This is the contents of the entire /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
    bridge_ports eth0

How and where can I check if the eth0 is configured automatically with an IP? 

With Ubuntu 7 and the same setup (I think) everything was working.

Andy

---

### Post by nixscripter on 2008-05-03
Try adding something like this before the **auto br0** section:
```

auto eth0
iface eth0 inet manual
    up ifconfig eth0 up

```

Hopefully, this will make the interface not get an IP address, letting the bridge get one instead, and not cause fighting.

By the way, what other interfaces do you intend to bridge? They need to be brought up without an IP as well before the bridge interface is brought up.

---

### Post by andyesten on 2008-05-03
I added the lines and rebooted the PC. Everything is working now! Thanks! I am using this bridge for one of the VirtualBox instances.

I restored my previous /etc directory and check the old /etc/network/intercaes file but this configuration was not there. (Wanted to make sure I was not at fault here)

Thanks again!

Andy

---

