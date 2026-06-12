---
title: "Lost network"
date: 2020-11-12
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2020-11-12
I have an old Dell Inspiron laptop that has been running Xubuntu 18.04. Suddenly could not update, so I just attempted to reinstall. Now everything works except it can't connect to my LAN. Did lshw and got this:
> *-network       description: Ethernet interface       product: 88E8040 PCI-E Fast Ethernet Controller       vendor: Marvell Technology Group Ltd.       physical id: 0       bus info: pci@0000:09:00.0       logical name: enp9s0       version: 13       serial: 00:23:ae:2e:8b:3d       capacity: 100Mbit/s       width: 64 bits       clock: 33MHz       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair       resources: irq:18 memory:f68fc000-f68fffff ioport:de00(size=256)

I have no idea what that tells me or how to connect to my network (which the previous version was able to do). I should add that the network manager shows no networks at all, other than "Ethernet."
Update: Was able to connect with Belkin adapter, then it disconnected saying I had a local domain that was incompatible with Avahi. Have no idea what that means.
Another update: Using the stickies I was able to update my Broadcom driver and connect normally without the Belkin, but I still keep getting the disconnect message. However, it is not disconnecting. What the hell? Is there any way to make that go away?

---

### Post by slickymaster on 2020-11-12
*Thread moved to **Networking & Wireless**.*

---

