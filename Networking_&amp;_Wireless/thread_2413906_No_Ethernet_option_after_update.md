---
title: "No Ethernet option after update"
date: 2019-03-03
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2019-03-03
[COLOR=#242729][FONT=Arial]I am running ubuntu 18.04.2 LTS. After latest update, I do not have internet. I even have no ethernet option in Network Manager. Ifconfig -a gives me just lo interface. Between updating and restarting computer I changed kernel from linux-image-4.15.0-43-generic to linux-image-4.15.0-45-generic.[/FONT][/COLOR]
lspci -v

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 10, NUMA node 0
    I/O ports at de00 [size=256]
    Memory at fdbff000 (64-bit, prefetchable) [size=4K]
    Memory at fdbe0000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at fde00000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 12-34-56-78-12-34-56-78

lshw -C network

 *-network UNCLAIMED       
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbe0000-fdbeffff memory:fde00000-fde0ffff

---

### Post by Chesslover on 2019-03-04
I solved it by booting to previous kernel (Advanced options)

---

