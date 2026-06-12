---
title: "Marvell Libertas 88w8335 (rev 43) problems on laptop"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by Dred_furst on 2007-12-06
I am having some problems getting my wireless card to install on ubuntu 7.10. I have a Marvell Libertas 88w8335 (rev 43) chipset and have followed several set of instructions to try and use ndiswrapper to get the device working. unfortunatley, the device seems to refuse to load up. I have tried several sets of drives (including two sets of XP drivers) to no avail. This is what is at the end of my /var/log/messages file when I try to modprobe ndiswrapper:

```
Dec  6 11:29:38 Remasters kernel: [  977.276000] ndiswrapper: driver mrv8000c (M
arvell,02/22/2005,3.1.1.7) loaded
Dec  6 11:29:38 Remasters kernel: [  977.276000] ACPI: PCI Interrupt 0000:05:01.
0[A] -> GSI 18 (level, low) -> IRQ 23
Dec  6 11:29:38 Remasters kernel: [  977.276000] ndiswrapper: using IRQ 23
Dec  6 11:29:38 Remasters kernel: [  977.628000] ndiswrapper (mp_init:263): coul
dn't initialize device: C0000001
Dec  6 11:29:38 Remasters kernel: [  977.628000] ndiswrapper (pnp_start_device:4
40): Windows driver couldn't initialize the device (C0000001)
Dec  6 11:29:38 Remasters kernel: [  977.628000] ndiswrapper (mp_halt:305): devi
ce f04bb500 is not initialized - not halting
Dec  6 11:29:38 Remasters kernel: [  977.628000] ndiswrapper: device eth%%d remo
ved
Dec  6 11:29:38 Remasters kernel: [  977.628000] ACPI: PCI interrupt for device
0000:05:01.0 disabled
Dec  6 11:29:38 Remasters kernel: [  977.628000] ndiswrapper: probe of 0000:05:0
1.0 failed with error -22
Dec  6 11:29:38 Remasters kernel: [  977.628000] usbcore: registered new interfa
ce driver ndiswrapper

```

---

### Post by Dred_furst on 2007-12-06
Any Ideas?

---

### Post by zorgzorg2 on 2007-12-21
Hi,

I have exactly the same problem with a bluestork wifi card. It has the same chip.

Did you find a solution ?

Zorg

---

