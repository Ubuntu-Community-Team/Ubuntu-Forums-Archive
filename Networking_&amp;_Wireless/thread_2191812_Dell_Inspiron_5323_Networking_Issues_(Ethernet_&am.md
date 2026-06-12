---
title: "Dell Inspiron 5323 Networking Issues (Ethernet &amp; Wifi)"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by azelma on 2013-12-04
Hi all,

So I've had some issues with the ethernet and wireless on my computer. I'm running Ubuntu 12.04.

The issue with the ethernet I believe stems from the fact that there is no driver:

sudo lshw -C network returns the following:
```
 *-network                      description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.9.0-030900-generic firmware=18.168.6.1 ip=192.168.0.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:43 memory:d0500000-d0501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d043ffff ioport:2000(size=128)
```

I tried this, which I found in another thread:
```
wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2)
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make

```

But got this out, among other things (this seemed like the relevant bit, but I can post the full output if needed):
```
cc1: some warnings being treated as errorsmake[4]: *** [/home/valerie/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx/alx_main.o] Error 1
make[3]: *** [/home/valerie/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros/alx] Error 2
make[2]: *** [/home/valerie/compat-wireless-3.5.1-1-snpc/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/home/valerie/compat-wireless-3.5.1-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.9.0-030900-generic'
make: *** [modules] Error 2

```

The issue with wireless is far trickier, and much more of an issue, as far as I'm concerned. (I can also make a separate thread for it, if that's preferable.)
It's very slow. The slowness varies, and it's usually <1 Mbps, when another computer on the same wireless network is 10+ Mbps. The faster the network is, the faster it seems to go, but I'm not sure I've ever seen it break 6 Mbps.
A friend of mine has had similar issues on Windows with the same model computer, so I think it might be related to the Intel Centrino Wireless-N 2230 card. Anyone have ideas on how to troubleshoot that?

---

### Post by azelma on 2013-12-04
So I think I've got the ethernet issue fixed, following instructions here: [http://askubuntu.com/questions/105607/how-do-i-get-an-atheros-ar8131-ethernet-card-working](http://askubuntu.com/questions/105607/how-do-i-get-an-atheros-ar8131-ethernet-card-working)

Anyone have ideas on the wireless slowness issue?

---

