---
title: "Running both wired and wifi simultaneously"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by crusty_collins on 2006-09-16
Ok, so with LOTS of help from the forums I have my BCM card running.  I am wondering if anyone knows why I must ifdown my eth0 for the wifi to work.
When I have both interfaces running the routing gets screwed up.

```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2

```
Normally I would see a gateway of 102.158.2.1 and a default interface.

Any ideas?

---

### Post by lupine_nickt on 2006-09-17
You've got both interfaces pointing to the same subnet - that's bad practice, and it's no surprise that the routing is breaking.

You have two choices - first, you can separate the two networks out (as they should be, really) and give your wireless LAN a different subnet to the wired LAN. You'll still have to choose the default gateway yourself (unless you set up multi-homed routing, or something), but it's essentially two shell scripts on your desktop, so not a big deal.

Or, you can keep it as is and unplug your wired net every time you want use the wireless. Setting the gateway "might" work, but as I said - it's bad practice.

xF,

...Nick

---

