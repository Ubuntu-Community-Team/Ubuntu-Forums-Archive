---
title: "ndiswrapper (ndiswrapper_add_pci_device:218): Windows driver couldn't initialize the"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by slava on 2005-07-06
hi 
i get this when i sudo modprobe ndiswrapper, dmesg

```
ndiswrapper version 1.2 loaded (preempt=yes,smp=no)
ndiswrapper: driver net5211 (,05/31/2003,2.4.0.71) loaded
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 11 (level, low) -> IRQ 11
ndiswrapper (NdisWriteErrorLogEntry:314): log: C0001389, count: 4 (e1839400), return address: f8fa50c1
ndiswrapper (ndiswrapper_add_pci_device:218): Windows 
driver couldn't initialize the device (C000009A)
ndiswrapper: probe of 0000:00:09.0 failed with error -22
```

 ```
ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present

```

i tried with ndiswrapper 1.1 and 1.2 with no luck

thanks for help
slava

---

