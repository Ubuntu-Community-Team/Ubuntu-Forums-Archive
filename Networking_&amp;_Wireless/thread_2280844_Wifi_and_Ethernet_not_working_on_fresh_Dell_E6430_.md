---
title: "Wifi and Ethernet not working on fresh Dell E6430 install."
date: 2015-06-02
forum: Networking &amp; Wireless
---

### Post by wastelandgunner on 2015-06-02
I've tried a bunch. Originally was on the 15.04 OS but went to the 14.02 LTS hoping it would make a difference.

When I tried plugging an ethernet cable in earlier it connected and gave me momentary access to internet before disconnecting.

Wifi shows no networks at all.

What should I do?

---

### Post by cariboo on 2015-06-02
If you could post the output of:

```
sudo lshw -C network
```

in your next post.

---

### Post by wastelandgunner on 2015-06-03
> **cariboo said:**
> If you could post the output of:

```
sudo lshw -C network
```

in your next post.

Alright, here you go.

>   *-network                      description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: d4:be:d9:59:39:0a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7700000-f771ffff memory:f7739000-f7739fff ioport:f040(size=32)
  *-network
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f7600000-f7603fff




---

### Post by slickymaster on 2015-06-03
*Moved to the ***Networking & Wireless*** sub-forum.*

---

### Post by wastelandgunner on 2015-06-03
Can anyone help me out?

---

