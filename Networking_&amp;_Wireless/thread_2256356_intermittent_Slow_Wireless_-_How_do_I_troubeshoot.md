---
title: "intermittent Slow Wireless - How do I troubeshoot"
date: 2014-12-11
forum: Networking &amp; Wireless
---

### Post by randyklein on 2014-12-11
I've installed two different variants of Ubuntu on my laptop - Elemental OS, and Peppermint OS.  Both have had the exact same issue.  Normally browsing the internet is blazing fast.  Usually a few times an hour, the internet would slow to a crawl.  No web pages will load.  They wont time out though.  The pages just show as loading.  This will last about 30 seconds, and then everything I had open will load and be as fast as ever.  I know its this device, and not my internet because other devices on the network are fast at that exact time.  There are plenty of free resources on the laptop.

Where do I even begin to troubleshoot?  I'm thinking that it's the driver for the wireless NIC, since it's happening on two different variants.  Here are the NIC results from an LSHW...

```
description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 2c:27:d7:a8:bf:0a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:52 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```

---

### Post by randyklein on 2014-12-11
I can see it happening in the ping.  This was actually a quick one, but you get the point.
[img]http://i.imgur.com/Pf0FF3Y.png[/img]

---

