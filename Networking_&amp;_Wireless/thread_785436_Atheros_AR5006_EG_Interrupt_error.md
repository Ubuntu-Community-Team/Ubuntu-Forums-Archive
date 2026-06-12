---
title: "Atheros AR5006 EG Interrupt error"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by combiths on 2008-05-07
After installing the driver using ndiswrapper for my wireless card (Atheros ar 5006eg) I ran the command "tail /var/log/messages" and this is what came out...

May  7 10:42:22 daniel-laptop kernel: [  134.824000] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper (ZwClose:2247): closing handle 0xe507c528 not implemented
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper (mp_init:263): couldn't initialize device: C000009A
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper (mp_halt:305): device e351f500 is not initialized - not halting
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper: device eth%%d removed
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
May  7 10:42:22 daniel-laptop kernel: [  134.824000] ndiswrapper: probe of 0000:05:00.0 failed with error -22
May  7 10:42:22 daniel-laptop kernel: [  134.824000] usbcore: registered new interface driver ndiswrapper

...any help would be much appreciated

---

