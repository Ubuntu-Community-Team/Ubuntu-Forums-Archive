---
title: "Networking fails to come up at boot, comes up fine later"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by bradtem on 2007-01-21
I'm running Edgy on an ASUS  P5NSLI which has the Marvell 88E8001 controller.

When I boot edgy, networking does not come up -- both eth0 and lo0 fail to come up but I can't find any diagnostics about it.   I am configured for a static IP in /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.123.14
netmask 255.255.255.0
gateway 192.168.123.254


Anyway, after booting, if I do ifup -a it does nothing as though all interfaces are up, but none show in ifconfig.  However, if I do ifdown -a, I get a SIOCDELRT: No such process diagnostic.

Then if I do ifup -a, the interfaces come up just fine.

The device is detected fine as shown by log messages in dmesg: 

[17179581.696000] skge 1.5 addr 0xd6000000 irq 74 chip Yukon-Lite rev 9
[17179581.696000] skge eth0: addr 00:18:f3:6b:69:b1


And it shows up fine in lspci.  The fact that lo0 isn't coming up either makes me wonder if something else is the culprit.  Of course, this problem means the system is unreachable after things like a reboot or a WOL boot.     (Long term goal is to be able to get this thing to hibernate or ram suspend and WOL but with the proprietary nvidia driver I know that's going to be a challenge.)

Any thoughts?

---

