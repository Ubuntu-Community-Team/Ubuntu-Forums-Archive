---
title: "no inward via wireless (outward works fine)"
date: 2022-01-08
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2022-01-08
I finally got ubuntu-server working on my Raspberry Pi but I had to give in an wire it.
I have wireless working. :-)
BUT
I can do anything from that computer outward but it is not visible (ping, nmap) to any computer on the network.

---

### Post by bjlockie on 2022-01-08
I suspect it has something to do with routes.
This is with the wired connected.

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 eth0
default         _gateway        0.0.0.0         UG    600    0        0 wlan1
192.168.68.0    0.0.0.0         255.255.252.0   U     0      0        0 eth0
192.168.68.0    0.0.0.0         255.255.252.0   U     0      0        0 wlan1
_gateway        0.0.0.0         255.255.255.255 UH    100    0        0 eth0
_gateway        0.0.0.0         255.255.255.255 UH    600    0        0 wlan1
```

---

### Post by bjlockie on 2022-01-09
I deleted the eth0 routes and rebooted but I have no internet. :-(

```

sudo ip route del default via 192.168.68.1 dev eth0
sudo ip route del 192.168.68.0/22 dev eth0
sudo ip route del 192.168.68.1 dev eth0

```

---

### Post by bjlockie on 2022-01-09
I can ssh to the IP for the wireless only if the wired is connected.

But now it can ping out and in.

---

### Post by bjlockie on 2022-01-10
> **bjlockie said:**
> I can ssh to the IP for the wireless only if the wired is connected.

But now it can ping out and in.

Now I can ping it from one computer but not another.
So half fixed.

---

