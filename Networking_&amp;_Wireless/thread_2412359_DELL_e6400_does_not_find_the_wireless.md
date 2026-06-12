---
title: "DELL e6400 does not find the wireless"
date: 2019-02-11
forum: Networking &amp; Wireless
---

### Post by eddyq on 2019-02-11
I loaded Ubuntu version #11-Ubuntu SMP. I am loading it on a DELL E6400. When it finished loading Firefox can't find a connection. It never asked me about my wireless as it normally does. It should be noted that this computer was running Windows 10 with wireless moments before I inserted a new disk and loaded Ubuntu. I have run the procedure given by a search for [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html) but that just came to a dead end. Everything looked OK to me. Here are some of the results:

lshw -C network
---------------------
    description: Network controller
    product: BCM4322 802.11a/b/g/n Wireless LAN Controller
    vendor: Broadcom Inc. and subsidiaries
    physical id: 0
    bus info: pci@0000:0c:00.0
    version: 01
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list
    configuration: driver=b43-pci-bridge latency=0
    resources: irq:17 memory:f69fc000-f69fffff
    WARNING: says I should run this as super-user (I will do that if the above does not seem complete)

lspci
------
    0c:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4322 802.11a/b/g/n Wireless LAN controller (rev 01)

lspci -v
---------
    0c:00.0 Network controller: Broadcom Inc and subsidiaries BCM4322 802.11a/b/g/n Wireless LAN controller (rev 01)
    Subsystem Dell Wireless 1510 Wireless-N WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>     <------------------------------------------ is this the problem?
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

Does anyone have any ideas?

---

### Post by chili555 on 2019-02-11
> product: BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Inc. and subsidiaries
Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by eddyq on 2019-02-12
That loaded a driver but it still does not work.  So I put my windows drive back in and the wireless works perfectly there. Note that I have Ubuntu version 18.10. Could they have changed things since the link you gave me? If so what do I do?

---

