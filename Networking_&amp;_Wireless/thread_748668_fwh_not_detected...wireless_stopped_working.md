---
title: "fwh not detected...wireless stopped working"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by prem1er on 2008-04-07
I haven't made any changes to the system recently and the other day I noticed that my boot was taking longer than usual.  When it finally booted my wireless network was no longer working.  It is almost as if I have no wireless card.  'ifconfig' returns a result for my wired connection, but not for wireless.  This is the new error I have been receiving during boot, the first and last lines of this output are the problem.  Any help much appreciated.

```

[   18.308250] intel_rng: FWH not detected
[   20.427735] ACPI: AC Adapter [AC] (off-line)
[   18.486533] ACPI: Battery Slot [BAT0] (battery present)
[   18.524135] input: Lid Switch as /devices/virtual/input/input3
[   18.524560] ACPI: Lid Switch [LID]
[   18.524602] input: Power Button (CM) as /devices/virtual/input/input4
[   18.554894] ACPI: Power Button (CM) [PBTN]
[   18.554964] input: Sleep Button (CM) as /devices/virtual/input/input5
[   18.582837] ACPI: Sleep Button (CM) [SBTN]
[   18.625761] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input6
[   18.642753] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.643240] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   18.674731] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   18.674879] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input8
[   18.702665] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   19.107510] nvidia: module license 'NVIDIA' taints kernel.
[   19.591291] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.591300] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   19.591407] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   19.786542] sdhci: Secure Digital Host Controller Interface driver
[   19.786546] sdhci: Copyright(c) Pierre Ossman
[   19.786585] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   19.786609] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   19.786679] mmc0: SDHCI at 0xdcbfd500 irq 23 DMA
[   19.811569] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   19.811573] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   19.811708] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.811723] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   19.811742] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.830858] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   19.830878] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.159448] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   20.195376] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   20.260523] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.631365] iwl3945: Radio Frequency Kill Switch is On:
[   20.631367] Kill switch must be turned off for wireless networking to work.

```

---

### Post by prem1er on 2008-04-07
bump....any thoughts?

---

### Post by prem1er on 2008-04-08
rebump

---

