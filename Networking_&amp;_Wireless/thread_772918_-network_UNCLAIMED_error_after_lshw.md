---
title: "*-network UNCLAIMED error after lshw"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by johnnyboyc on 2008-04-28
sudo lshw gives:
```
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

```

I believe the "*-network UNCLAIMED" Is the problem that prevents me from detecting wireless networks. Does anyone know what this could mean? I am really having difficulty with this.

Also I noticed that there is no "logical name" given, i.e. wlan, wlan1 etc.. is this normal?


Thank you!
John

---

### Post by sebthew0lf on 2010-08-07
> **johnnyboyc said:**
> sudo lshw gives:
```
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

```

I believe the "*-network UNCLAIMED" Is the problem that prevents me from detecting wireless networks. Does anyone know what this could mean? I am really having difficulty with this.

Also I noticed that there is no "logical name" given, i.e. wlan, wlan1 etc.. is this normal?


Thank you!
John

Have you solve your problem?

---

