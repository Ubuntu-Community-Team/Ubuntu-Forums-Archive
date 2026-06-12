---
title: "[SOLVED] all of my interfaces have moved :-("
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2008-11-28
Hi

Today (Nov 28th) I updated the kernel as requested by ubuntu. Upon reboot, my network interfaces have moved; internet was eth0 and now is eth5; lan was, and still is eth1.

```
ip link set dev eth5 name eth0
```Will rename it, but on reboot, it reverts to eth5

Although I have made it work, for historical graphs (mrtg) and stats (vnstat) I would prefer the internet to stay as eth0.

I see this in the logs:

```
Nov 28 08:52:31 6cw-server kernel: [   34.766500] eth0: RTL8168b/8111b at 0xf8842000, 00:0a:5e:53:80:f1, XID 38000000 IRQ 221
Nov 28 08:52:31 6cw-server kernel: [   42.190096] udev: renamed network interface eth0 to eth5
```Any help appreciated in this, or even an explanation as to why this has happened after a few years.

Steve

---

### Post by Ayuthia on 2008-11-28
Does ifconfig show any other devices?

---

### Post by sparky-steve on 2008-11-28
Yes; I have five network cards in the server (one single NIC, and a quad NIC); they were eth0 and eth1-4 respectively.  They are now eth1-4 (no change) and eth5 - there is no eth0.

As previously stated:

```
ip link set dev eth5 name eth0
```

Will rename eth5 to eth0 until the next reboot; The problem is, this server is my gateway to the world, and more importantly, back in again - I dont want to be in some other country, and a power-cut & UPS shutdown happen, and not be able to get back in again.

So, I need to either find out how to fix it at boot, or run that code above as soon as the system comes up.

Cheers for playing

---

### Post by Ayuthia on 2008-11-28
Have you checked /etc/udev/rules.d/70-persistent-net.rules?  It might be defined in there.

---

### Post by sparky-steve on 2008-11-28
Superb - it was in there twice; once for the hard-coded MAC and once for the user-defined MAC (required by ISP).

All fixed & tested.

Thanks!

---

