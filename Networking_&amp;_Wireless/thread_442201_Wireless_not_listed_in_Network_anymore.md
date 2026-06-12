---
title: "Wireless not listed in Network anymore"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by PCE_Moose on 2007-05-13
Wireless has always worked well, no problems, no driver issues, ran straight from Ubuntu Edgy default install with Network Manager. :) 

Recently (on **Fiesty**) my HDD had a few errors on it, I ran **fsck** and ans YES to all questions (b/c I thought I was fixing errors).  

My wireless connection is no longer listed in Network, the Connections tab only shows "Wired Connection" + "Modem Connection".

Running **lshw** :
[INDENT] *-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@02:02.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=128 maxlatency=34 mingnt=2
                resources: iomemory:90000000-90000fff irq:11
[/INDENT]
I believe this means that a driver is loaded, so how do I go from here to using the card again?
Any help will be appreciated.

---

### Post by x64Jimbo on 2007-05-13
If the interface is listed at all in the /etc/network/interfaces file, NetworkManager will ignore it. Comment out any references to that interface in that file and that should probably fix it.

---

### Post by gborzi on 2007-05-13
That output means that there is no kernel module (i.e. driver) loaded for your wireless device. I checked on my laptop, unloading the wireless driver (in my case ipw3945) makes the UNCLAIMED word appear, loading it I get > *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                .....
have you tried to manually load the driver ?

---

