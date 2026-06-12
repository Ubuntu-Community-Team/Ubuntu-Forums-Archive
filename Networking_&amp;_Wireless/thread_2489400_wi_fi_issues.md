---
title: "wi fi issues"
date: 2023-07-28
forum: Networking &amp; Wireless
---

### Post by raarkil on 2023-07-28
hello people!
bought a new laptop, installed ubuntu as my first OS but no wi fi working inside(got usb wi fi adapter working at least)
but i think would be better to set my own, I am new to linux but already tried to use linux mint and more, but they dont see a my own wifi adapter
lshw _C Network show it:

*-network UNCLAIMED
       description: Network controller
       product: MEDIATEK Corp.
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm cap_list
       configuration: latency=0
       resources: iomemory:600-5ff memory:6000000000-60000fffff memory:84000000-84007fff
I have red that I must claim it by set some driver, but what driver and where i can find repository to do it?
got ubuntu 22.04LTS
help me please...............trying to fix it for month already.............:((((

---

### Post by jeremy31 on 2023-07-28
Post results from terminal for  ```
lspci -nnk|grep -iA3 net
```

---

### Post by raarkil on 2023-07-28
0000:02:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7902]
    DeviceName: WLAN
    Subsystem: AzureWave Device [1a3b:5520]
10000:e0:06.0 PCI bridge [0604]: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 [8086:464d] (rev 04)

---

### Post by raarkil on 2023-07-28
maybe it is a hardware issue?

---

### Post by jeremy31 on 2023-07-28
As far as I know there is no support in linux for that chipset yet

---

