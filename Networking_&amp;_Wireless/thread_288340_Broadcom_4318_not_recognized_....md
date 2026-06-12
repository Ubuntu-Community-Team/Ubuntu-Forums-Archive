---
title: "Broadcom 4318 not recognized ..."
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by slacker9876 on 2006-10-29
Cannot seem to get this working and the driver is not loading and I do not know why. I am using the 64-bit driver provided my Linuxant, authored by Broadcom. Here is a snapshot of the related message file.

```
[   31.576110] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   31.614987] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.796280] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[   31.797455] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   31.797793] GSI 21 sharing vector 0xB1 and IRQ 21
[   31.797797] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 177
[   31.805438] ndiswrapper (NdisWriteErrorLogEntry:241): log: 6F4C79B0, count: 1, return_address: ffffffff8822513e
[   31.805446] ndiswrapper (NdisWriteErrorLogEntry:244): code: 267
[   31.805511] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[   31.805519] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[   31.805538] ndiswrapper (miniport_halt:327): device ffff810071276500 is not initialized - not halting
[   31.805550] ndiswrapper: device eth%d removed
[   31.805559] unregister_netdevice: device eth%d/ffff810071276000 never was registered
[   31.805574] ACPI: PCI interrupt for device 0000:05:02.0 disabled
[   31.805583] ndiswrapper: probe of 0000:05:02.0 failed with error -22
```

Mods, if you feel this needs to be moved to 64-bit fourm ... feel free. I placed this here for exposure and I feel this is more of an ndis issue rather than a 64-bit issue.

---

### Post by H.E. Pennypacker on 2006-10-29
Are you sure this hasn't been covered already, because this is a widely known card?  I am sure there is something on this already on the forums.  See what you find using a search.

---

