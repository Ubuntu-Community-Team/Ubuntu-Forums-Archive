---
title: "Wifi: Netgear WG511 (using ndiswrapper)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by thorN on 2008-04-30
Hi,

I'm trying to get wireless card working on an old Toshiba 300CDS (with Damn Small Linux.)

The wifi card chipset is ISL3890.

I set up ndiswrapper correctly, but dmesg reports:

**dmesg**
```
...
PCI: No IRQ known for interrupt pin A of device 15:00.0. Please try using pci=biosirq.
ndiswrapper: request for irq 0 failed
...
```

From advice on another thread, I tried enabling ACPI (DSL disabled this by default) and using pci=biosirq (using GRUB.)

Does anyone have any suggestions where to go from here?

Thanks.

---

