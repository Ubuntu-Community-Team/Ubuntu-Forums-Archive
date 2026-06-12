---
title: "Dell Inspiron 2330 with Ubuntu 10.10 not reading Wireless Card"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by sandino1 on 2014-04-02
Just did a fresh install of Ubuntu 10.10, 64-bit, on my Dell Inspiron One 2330. Unfortunately it's not recognizing the wireless or even the ethernet cable! The computer has no internet access so it needs either a local solution or some package (like new driver) I can put on the computer with a USB. lshw -C network is coming up with "network UNCLAIMED", which looks suspicious but I'm too much of a newb to know what to do with this information.

Here is the results of lshw -C network:

```
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e7ffff memory:f7e80000-f7e8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)
```

Here's rfkill list all:

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Here's iwconfig:

```
lo        no wireless extensions.
```

And here's lspci -nn | grep 0280:

```
01:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)
```

Thanks very much in advance!

---

### Post by wildmanne39 on 2014-04-02
10.10 has not been supported for a long time, it is very likely to have security issues since there are no longer updates for that release, you need to upgrade to a supported version then post back if you still need help with your wireless.
Thanks

---

### Post by sandino1 on 2014-04-06
OK I gave in and installed ubuntu 12.04, and everything works great right out of the box! I guess it's time for me to embrace the new LTS of ubuntu. I'm relieved that the classic gnome desktop is still available in 12.04!

---

