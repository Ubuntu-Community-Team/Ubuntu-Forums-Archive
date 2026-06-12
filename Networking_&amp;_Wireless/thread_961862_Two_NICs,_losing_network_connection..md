---
title: "Two NICs, losing network connection."
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by InThane on 2008-10-28
Greetings,

I'm trying to set up a CoovaChilli install on a bare bones Ubuntu Server 8.04 install. However, I have a problem that's biting me in the butt before I ever even get to the install stage.

I'm losing network connectivity over and over again.

Here's my interfaces file:

[FONT="Courier New"]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 168.156.96.170
        netmask 255.255.255.0
        network 168.156.96.0
        broadcast 168.156.96.255
        gateway 168.156.96.4
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 168.156.96.34 168.156.96.35

auto eth1
iface eth1 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        dns-nameservers 168.156.96.34 168.156.96.35[/FONT]

At some point, the machine loses network connectivity. No error messages pop up, but I can't ping anything. If I ifdown eth1, then everything starts working again. I then ifup eth1, everything works for $RANDOM_PERIOD_OF_TIME, and then it all dumps again.

Here's the output of netstat -rn:
[FONT="Courier New"]Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
168.156.96.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         168.156.96.4    0.0.0.0         UG        0 0          0 eth0[/FONT]

Any ideas what I'm doing wrong?

---

