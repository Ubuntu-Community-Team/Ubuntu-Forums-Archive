---
title: "HELP!!!! Plasma Workspace ALWAYS Crashes on Shutdown after 190 updates"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Dark7man on 2011-02-21
HELP!  I dont wanna have to back to scratch yet AGAIN!

Hey guys... this happened to me a few days ago as well...

Newly installed Kubuntu 10.10... all updates installed while the OS was being installed.

I havent done anything really..installed a few applications from the software manager - everythings fine...

I then added the "amarok" ppa via konsole - ran sudo apt-get update etc... then exit konsole and ran the "Check for software updates" and it found 190 updates... I installed them....

Now when I rebooted my desktop wallpaper was gone (blackscreen) + plasma seems to play around... for example... if I scroll up and down a web page etc... it doesnt seem to load everything... you can see it doesnt look right then when your roll the mouse over it - it seems to show it correctly!  This happens with panels or any kind of image at all on the screen....

ALSO - when I reboot or shutdown even log off - Plasma Workspace seems to crash - I try to send the crash report but it says I dont have the debug symbols installed - I go through to install them and it fails.

Any ideas anyone?
Any help is much appreciated!

---

### Post by aeiah on 2011-02-21
what do your error logs say? in a terminal:
```

cat /var/log/messages
```
or 
```

dmesg

```

---

### Post by Dark7man on 2011-02-21
I ran the 1st command in konsole and the txt it spat out was too long in konsole - so I went into KSystemLog - highlighted everything and saved it.  The file is 90kb and the limit for attachments is 19.5 kb

I'm just gonna copy and paste it in the body of my next reply...

Thanks for replying...

---

### Post by Dark7man on 2011-02-21
21/02/2011 09:25:26	D7-K	kernel	[    0.012685] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.013679] Mount-cache hash table entries: 256
21/02/2011 09:25:26	D7-K	kernel	[    0.013837] Initializing cgroup subsys ns
21/02/2011 09:25:26	D7-K	kernel	[    0.013843] Initializing cgroup subsys cpuacct
21/02/2011 09:25:26	D7-K	kernel	[    0.013847] Initializing cgroup subsys memory
21/02/2011 09:25:26	D7-K	kernel	[    0.013856] Initializing cgroup subsys devices
21/02/2011 09:25:26	D7-K	kernel	[    0.013858] Initializing cgroup subsys freezer
21/02/2011 09:25:26	D7-K	kernel	[    0.013861] Initializing cgroup subsys net_cls
21/02/2011 09:25:26	D7-K	kernel	[    0.013891] CPU: Physical Processor ID: 0
21/02/2011 09:25:26	D7-K	kernel	[    0.013893] CPU: Processor Core ID: 0
21/02/2011 09:25:26	D7-K	kernel	[    0.013896] mce: CPU supports 6 MCE banks
21/02/2011 09:25:26	D7-K	kernel	[    0.013904] CPU0: Thermal monitoring enabled (TM2)
21/02/2011 09:25:26	D7-K	kernel	[    0.013909] using mwait in idle threads.
21/02/2011 09:25:26	D7-K	kernel	[    0.013911] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
21/02/2011 09:25:26	D7-K	kernel	[    0.013919] ... version:                2
21/02/2011 09:25:26	D7-K	kernel	[    0.013921] ... bit width:              40
21/02/2011 09:25:26	D7-K	kernel	[    0.013922] ... generic registers:      2
21/02/2011 09:25:26	D7-K	kernel	[    0.013924] ... value mask:             000000ffffffffff
21/02/2011 09:25:26	D7-K	kernel	[    0.013926] ... max period:             000000007fffffff
21/02/2011 09:25:26	D7-K	kernel	[    0.013927] ... fixed-purpose events:   3
21/02/2011 09:25:26	D7-K	kernel	[    0.013929] ... event mask:             0000000700000003
21/02/2011 09:25:26	D7-K	kernel	[    0.016561] ACPI: Core revision 20100428
21/02/2011 09:25:26	D7-K	kernel	[    0.040011] ftrace: converting mcount calls to 0f 1f 44 00 00
21/02/2011 09:25:26	D7-K	kernel	[    0.040017] ftrace: allocating 22681 entries in 89 pages
21/02/2011 09:25:26	D7-K	kernel	[    0.050085] DMAR: Host address width 36
21/02/2011 09:25:26	D7-K	kernel	[    0.050088] DMAR: DRHD base: 0x00000000000000 flags: 0x1
21/02/2011 09:25:26	D7-K	kernel	[    0.050091] DMAR: parse DMAR table failure.
21/02/2011 09:25:26	D7-K	kernel	[    0.050093] Setting APIC routing to flat
21/02/2011 09:25:26	D7-K	kernel	[    0.050413] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
21/02/2011 09:25:26	D7-K	kernel	[    0.154381] CPU0: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz stepping 0a
21/02/2011 09:25:26	D7-K	kernel	[    0.160000] Booting Node   0, Processors  #1
21/02/2011 09:25:26	D7-K	kernel	[    0.320017] Brought up 2 CPUs
21/02/2011 09:25:26	D7-K	kernel	[    0.320021] Total of 2 processors activated (8778.17 BogoMIPS).
21/02/2011 09:25:26	D7-K	kernel	[    0.320542] devtmpfs: initialized
21/02/2011 09:25:26	D7-K	kernel	[    0.320668] regulator: core version 0.5
21/02/2011 09:25:26	D7-K	kernel	[    0.320698] Time:  9:25:10  Date: 02/21/11
21/02/2011 09:25:26	D7-K	kernel	[    0.320736] NET: Registered protocol family 16
21/02/2011 09:25:26	D7-K	kernel	[    0.320757] Trying to unpack rootfs image as initramfs...
21/02/2011 09:25:26	D7-K	kernel	[    0.320866] ACPI: bus type pci registered
21/02/2011 09:25:26	D7-K	kernel	[    0.320941] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
21/02/2011 09:25:26	D7-K	kernel	[    0.320944] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
21/02/2011 09:25:26	D7-K	kernel	[    0.335057] PCI: Using configuration type 1 for base access
21/02/2011 09:25:26	D7-K	kernel	[    0.340120] bio: create slab <bio-0> at 0
21/02/2011 09:25:26	D7-K	kernel	[    0.342411] ACPI: EC: Look up EC in DSDT
21/02/2011 09:25:26	D7-K	kernel	[    0.347159] ACPI: BIOS _OSI(Linux) query ignored
21/02/2011 09:25:26	D7-K	kernel	[    0.451399] ACPI: SSDT 00000000b9eb4c98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.451989] ACPI: Dynamic OEM Table Load:
21/02/2011 09:25:26	D7-K	kernel	[    0.451993] ACPI: SSDT (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.452310] ACPI: SSDT 00000000b9eb2618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.452878] ACPI: Dynamic OEM Table Load:
21/02/2011 09:25:26	D7-K	kernel	[    0.452881] ACPI: SSDT (null) 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.453448] ACPI: SSDT 00000000b9eb3e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.454049] ACPI: Dynamic OEM Table Load:
21/02/2011 09:25:26	D7-K	kernel	[    0.454052] ACPI: SSDT (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.454247] ACPI: SSDT 00000000b9eb4f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.454826] ACPI: Dynamic OEM Table Load:
21/02/2011 09:25:26	D7-K	kernel	[    0.454829] ACPI: SSDT (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
21/02/2011 09:25:26	D7-K	kernel	[    0.461051] ACPI: Interpreter enabled
21/02/2011 09:25:26	D7-K	kernel	[    0.461051] ACPI: (supports S0 S3 S4 S5)
21/02/2011 09:25:26	D7-K	kernel	[    0.461051] ACPI: Using IOAPIC for interrupt routing
21/02/2011 09:25:26	D7-K	kernel	[    0.472797] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
21/02/2011 09:25:26	D7-K	kernel	[    0.473075] ACPI: No dock devices found.
21/02/2011 09:25:26	D7-K	kernel	[    0.473080] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
21/02/2011 09:25:26	D7-K	kernel	[    0.473728] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
21/02/2011 09:25:26	D7-K	kernel	[    0.474742] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
21/02/2011 09:25:26	D7-K	kernel	[    0.474746] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.474749] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.474753] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.474816] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.474823] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.474828] pci 0000:00:02.0: reg 20: [io  0x7110-0x7117]
21/02/2011 09:25:26	D7-K	kernel	[    0.474871] pci 0000:00:02.1: reg 10: [mem 0xd5400000-0xd54fffff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.474979] pci 0000:00:1a.0: reg 20: [io  0x70e0-0x70ff]
21/02/2011 09:25:26	D7-K	kernel	[    0.475063] pci 0000:00:1a.1: reg 20: [io  0x70c0-0x70df]
21/02/2011 09:25:26	D7-K	kernel	[    0.475145] pci 0000:00:1a.7: reg 10: [mem 0xda505c00-0xda505fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.475214] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475219] pci 0000:00:1a.7: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475263] pci 0000:00:1b.0: reg 10: [mem 0xda500000-0xda503fff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.475317] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475322] pci 0000:00:1b.0: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475408] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475413] pci 0000:00:1c.0: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475502] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475506] pci 0000:00:1c.1: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475595] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475600] pci 0000:00:1c.3: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475691] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475695] pci 0000:00:1c.4: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475782] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.475787] pci 0000:00:1c.5: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.475851] pci 0000:00:1d.0: reg 20: [io  0x70a0-0x70bf]
21/02/2011 09:25:26	D7-K	kernel	[    0.475936] pci 0000:00:1d.1: reg 20: [io  0x7080-0x709f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476019] pci 0000:00:1d.2: reg 20: [io  0x7060-0x707f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476101] pci 0000:00:1d.3: reg 20: [io  0x7040-0x705f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476183] pci 0000:00:1d.7: reg 10: [mem 0xda505800-0xda505bff]
21/02/2011 09:25:26	D7-K	kernel	[    0.476251] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.476256] pci 0000:00:1d.7: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.476464] pci 0000:00:1f.2: reg 10: [io  0x7108-0x710f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476472] pci 0000:00:1f.2: reg 14: [io  0x711c-0x711f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476479] pci 0000:00:1f.2: reg 18: [io  0x7100-0x7107]
21/02/2011 09:25:26	D7-K	kernel	[    0.476486] pci 0000:00:1f.2: reg 1c: [io  0x7118-0x711b]
21/02/2011 09:25:26	D7-K	kernel	[    0.476492] pci 0000:00:1f.2: reg 20: [io  0x7020-0x703f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476499] pci 0000:00:1f.2: reg 24: [mem 0xda505000-0xda5057ff]
21/02/2011 09:25:26	D7-K	kernel	[    0.476541] pci 0000:00:1f.2: PME# supported from D3hot
21/02/2011 09:25:26	D7-K	kernel	[    0.476545] pci 0000:00:1f.2: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.476580] pci 0000:00:1f.3: reg 10: [mem 0xda506000-0xda5060ff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.476597] pci 0000:00:1f.3: reg 20: [io  0x7000-0x701f]
21/02/2011 09:25:26	D7-K	kernel	[    0.476655] pci 0000:00:1f.6: reg 10: [mem 0xda504000-0xda504fff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.477068] pci 0000:02:00.0: reg 10: [mem 0xd9500000-0xd9503fff 64bit]
21/02/2011 09:25:26	D7-K	kernel	[    0.477275] pci 0000:02:00.0: supports D1 D2
21/02/2011 09:25:26	D7-K	kernel	[    0.477437] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
21/02/2011 09:25:26	D7-K	kernel	[    0.477442] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.477446] pci 0000:00:1c.0:   bridge window [mem 0xd9500000-0xda4fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.477454] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.477608] pci 0000:03:00.0: reg 10: [io  0x5000-0x50ff]
21/02/2011 09:25:26	D7-K	kernel	[    0.477678] pci 0000:03:00.0: reg 18: [mem 0xd1410000-0xd1410fff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.477723] pci 0000:03:00.0: reg 20: [mem 0xd1400000-0xd140ffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.477741] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.477885] pci 0000:03:00.0: supports D1 D2
21/02/2011 09:25:26	D7-K	kernel	[    0.477887] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
21/02/2011 09:25:26	D7-K	kernel	[    0.477897] pci 0000:03:00.0: PME# disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.478045] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
21/02/2011 09:25:26	D7-K	kernel	[    0.478050] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478054] pci 0000:00:1c.1:   bridge window [mem 0xd8500000-0xd94fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478062] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.478115] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
21/02/2011 09:25:26	D7-K	kernel	[    0.478120] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478125] pci 0000:00:1c.3:   bridge window [mem 0xd7500000-0xd84fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478132] pci 0000:00:1c.3:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.478185] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
21/02/2011 09:25:26	D7-K	kernel	[    0.478190] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478195] pci 0000:00:1c.4:   bridge window [mem 0xd6500000-0xd74fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478202] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.478254] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
21/02/2011 09:25:26	D7-K	kernel	[    0.478259] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478264] pci 0000:00:1c.5:   bridge window [mem 0xd5500000-0xd64fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.478271] pci 0000:00:1c.5:   bridge window [mem 0xd4400000-0xd53fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.478351] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a] (subtractive decode)
21/02/2011 09:25:26	D7-K	kernel	[    0.478356] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
21/02/2011 09:25:26	D7-K	kernel	[    0.478361] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
21/02/2011 09:25:26	D7-K	kernel	[    0.478368] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
21/02/2011 09:25:26	D7-K	kernel	[    0.478371] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
21/02/2011 09:25:26	D7-K	kernel	[    0.478373] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
21/02/2011 09:25:26	D7-K	kernel	[    0.478376] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
21/02/2011 09:25:26	D7-K	kernel	[    0.478378] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
21/02/2011 09:25:26	D7-K	kernel	[    0.478422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.478709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.478885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.478982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.479097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.479192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.479333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
21/02/2011 09:25:26	D7-K	kernel	[    0.490727] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.490877] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491022] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491166] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491310] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491455] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491599] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
21/02/2011 09:25:26	D7-K	kernel	[    0.491746] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
21/02/2011 09:25:26	D7-K	kernel	[    0.491819] HEST: Table is not found!
21/02/2011 09:25:26	D7-K	kernel	[    0.491900] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
21/02/2011 09:25:26	D7-K	kernel	[    0.491915] vgaarb: loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.492058] SCSI subsystem initialized
21/02/2011 09:25:26	D7-K	kernel	[    0.492151] libata version 3.00 loaded.
21/02/2011 09:25:26	D7-K	kernel	[    0.492198] usbcore: registered new interface driver usbfs
21/02/2011 09:25:26	D7-K	kernel	[    0.492211] usbcore: registered new interface driver hub
21/02/2011 09:25:26	D7-K	kernel	[    0.492234] usbcore: registered new device driver usb
21/02/2011 09:25:26	D7-K	kernel	[    0.492461] ACPI: WMI: Mapper loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.492463] PCI: Using ACPI for IRQ routing
21/02/2011 09:25:26	D7-K	kernel	[    0.492466] PCI: pci_cache_line_size set to 64 bytes
21/02/2011 09:25:26	D7-K	kernel	[    0.492961] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
21/02/2011 09:25:26	D7-K	kernel	[    0.492964] reserve RAM buffer: 00000000b9ea8000 - 00000000bbffffff 
21/02/2011 09:25:26	D7-K	kernel	[    0.492966] reserve RAM buffer: 00000000b9f81000 - 00000000bbffffff 
21/02/2011 09:25:26	D7-K	kernel	[    0.492969] reserve RAM buffer: 00000000b9fdf000 - 00000000bbffffff 
21/02/2011 09:25:26	D7-K	kernel	[    0.492971] reserve RAM buffer: 00000000ba000000 - 00000000bbffffff 
21/02/2011 09:25:26	D7-K	kernel	[    0.493057] NetLabel: Initializing
21/02/2011 09:25:26	D7-K	kernel	[    0.493059] NetLabel:  domain hash size = 128
21/02/2011 09:25:26	D7-K	kernel	[    0.493060] NetLabel:  protocols = UNLABELED CIPSOv4
21/02/2011 09:25:26	D7-K	kernel	[    0.493073] NetLabel:  unlabeled traffic allowed by default
21/02/2011 09:25:26	D7-K	kernel	[    0.493108] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
21/02/2011 09:25:26	D7-K	kernel	[    0.493114] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
21/02/2011 09:25:26	D7-K	kernel	[    0.493119] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
21/02/2011 09:25:26	D7-K	kernel	[    0.510042] Switching to clocksource tsc
21/02/2011 09:25:26	D7-K	kernel	[    0.519769] AppArmor: AppArmor Filesystem Enabled
21/02/2011 09:25:26	D7-K	kernel	[    0.519788] pnp: PnP ACPI init
21/02/2011 09:25:26	D7-K	kernel	[    0.519811] ACPI: bus type pnp registered
21/02/2011 09:25:26	D7-K	kernel	[    0.522508]   alloc irq_desc for 23 on node 0
21/02/2011 09:25:26	D7-K	kernel	[    0.522511]   alloc kstat_irqs on node 0
21/02/2011 09:25:26	D7-K	kernel	[    0.522805] pnp: PnP ACPI: found 12 devices
21/02/2011 09:25:26	D7-K	kernel	[    0.522807] ACPI: ACPI bus type pnp unregistered
21/02/2011 09:25:26	D7-K	kernel	[    0.522822] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522828] system 00:02: [io  0x164e-0x164f] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522832] system 00:02: [io  0x0600-0x060f] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522834] system 00:02: [io  0x0610] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522837] system 00:02: [io  0x0800-0x080f] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522839] system 00:02: [io  0x0810-0x0817] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522842] system 00:02: [io  0x0820-0x0823] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522845] system 00:02: [io  0x0400-0x047f] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522848] system 00:02: [io  0x0500-0x053f] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522850] system 00:02: [io  0x0380-0x038e] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522853] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522856] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522859] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522862] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522864] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522867] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522870] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522873] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522876] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.522879] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
21/02/2011 09:25:26	D7-K	kernel	[    0.528809] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528874] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
21/02/2011 09:25:26	D7-K	kernel	[    0.528877] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528883] pci 0000:00:1c.0:   bridge window [mem 0xd9500000-0xda4fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528888] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528898] pci 0000:03:00.0: BAR 6: assigned [mem 0xd1420000-0xd142ffff pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528901] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
21/02/2011 09:25:26	D7-K	kernel	[    0.528905] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528911] pci 0000:00:1c.1:   bridge window [mem 0xd8500000-0xd94fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528916] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528923] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
21/02/2011 09:25:26	D7-K	kernel	[    0.528926] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528932] pci 0000:00:1c.3:   bridge window [mem 0xd7500000-0xd84fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528937] pci 0000:00:1c.3:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528945] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
21/02/2011 09:25:26	D7-K	kernel	[    0.528948] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528954] pci 0000:00:1c.4:   bridge window [mem 0xd6500000-0xd74fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528959] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528966] pci 0000:00:1c.5: PCI bridge to [bus 07-09]
21/02/2011 09:25:26	D7-K	kernel	[    0.528969] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528975] pci 0000:00:1c.5:   bridge window [mem 0xd5500000-0xd64fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.528979] pci 0000:00:1c.5:   bridge window [mem 0xd4400000-0xd53fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.528987] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
21/02/2011 09:25:26	D7-K	kernel	[    0.528988] pci 0000:00:1e.0:   bridge window [io  disabled]
21/02/2011 09:25:26	D7-K	kernel	[    0.528994] pci 0000:00:1e.0:   bridge window [mem disabled]
21/02/2011 09:25:26	D7-K	kernel	[    0.528998] pci 0000:00:1e.0:   bridge window [mem pref disabled]
21/02/2011 09:25:26	D7-K	kernel	[    0.529018]   alloc irq_desc for 17 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529020]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529028] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
21/02/2011 09:25:26	D7-K	kernel	[    0.529033] pci 0000:00:1c.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529042]   alloc irq_desc for 16 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529044]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529047] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[    0.529052] pci 0000:00:1c.1: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529061]   alloc irq_desc for 19 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529063]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.529066] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
21/02/2011 09:25:26	D7-K	kernel	[    0.529071] pci 0000:00:1c.3: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529080] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
21/02/2011 09:25:26	D7-K	kernel	[    0.529085] pci 0000:00:1c.4: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529094] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[    0.529099] pci 0000:00:1c.5: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529107] pci 0000:00:1e.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.529111] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
21/02/2011 09:25:26	D7-K	kernel	[    0.529114] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529116] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529119] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529121] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529124] pci_bus 0000:02: resource 1 [mem 0xd9500000-0xda4fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529126] pci_bus 0000:02: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.529129] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529131] pci_bus 0000:03: resource 1 [mem 0xd8500000-0xd94fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529133] pci_bus 0000:03: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.529136] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529138] pci_bus 0000:05: resource 1 [mem 0xd7500000-0xd84fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529140] pci_bus 0000:05: resource 2 [mem 0xd2400000-0xd33fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.529143] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529145] pci_bus 0000:06: resource 1 [mem 0xd6500000-0xd74fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529147] pci_bus 0000:06: resource 2 [mem 0xd3400000-0xd43fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.529149] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529151] pci_bus 0000:07: resource 1 [mem 0xd5500000-0xd64fffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529154] pci_bus 0000:07: resource 2 [mem 0xd4400000-0xd53fffff 64bit pref]
21/02/2011 09:25:26	D7-K	kernel	[    0.529156] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
21/02/2011 09:25:26	D7-K	kernel	[    0.529158] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529160] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529163] pci_bus 0000:0a: resource 7 [mem 0xc0000000-0xfebfffff]
21/02/2011 09:25:26	D7-K	kernel	[    0.529205] NET: Registered protocol family 2
21/02/2011 09:25:26	D7-K	kernel	[    0.529360] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.530639] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.535105] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.535701] TCP: Hash tables configured (established 524288 bind 65536)
21/02/2011 09:25:26	D7-K	kernel	[    0.535704] TCP reno registered
21/02/2011 09:25:26	D7-K	kernel	[    0.535713] UDP hash table entries: 2048 (order: 4, 65536 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.535756] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.535911] NET: Registered protocol family 1
21/02/2011 09:25:26	D7-K	kernel	[    0.535936] pci 0000:00:02.0: Boot video device
21/02/2011 09:25:26	D7-K	kernel	[    0.536523] PCI: CLS 64 bytes, default 64
21/02/2011 09:25:26	D7-K	kernel	[    0.536525] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
21/02/2011 09:25:26	D7-K	kernel	[    0.536528] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
21/02/2011 09:25:26	D7-K	kernel	[    0.536530] software IO TLB at phys 0x1f9e000 - 0x5f9e000
21/02/2011 09:25:26	D7-K	kernel	[    0.536573] Simple Boot Flag at 0x44 set to 0x1
21/02/2011 09:25:26	D7-K	kernel	[    0.536751] Scanning for low memory corruption every 60 seconds
21/02/2011 09:25:26	D7-K	kernel	[    0.536924] audit: initializing netlink socket (disabled)
21/02/2011 09:25:26	D7-K	kernel	[    0.536937] type=2000 audit(1298280309.520:1): initialized
21/02/2011 09:25:26	D7-K	kernel	[    0.551194] HugeTLB registered 2 MB page size, pre-allocated 0 pages
21/02/2011 09:25:26	D7-K	kernel	[    0.552553] VFS: Disk quotas dquot_6.5.2
21/02/2011 09:25:26	D7-K	kernel	[    0.552609] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
21/02/2011 09:25:26	D7-K	kernel	[    0.553129] fuse init (API version 7.14)
21/02/2011 09:25:26	D7-K	kernel	[    0.553210] msgmni has been set to 7697
21/02/2011 09:25:26	D7-K	kernel	[    0.553542] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
21/02/2011 09:25:26	D7-K	kernel	[    0.553545] io scheduler noop registered
21/02/2011 09:25:26	D7-K	kernel	[    0.553547] io scheduler deadline registered
21/02/2011 09:25:26	D7-K	kernel	[    0.553580] io scheduler cfq registered (default)
21/02/2011 09:25:26	D7-K	kernel	[    0.553688] pcieport 0000:00:1c.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.553733]   alloc irq_desc for 40 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.553735]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.553748] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.553837] pcieport 0000:00:1c.1: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.553877]   alloc irq_desc for 41 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.553878]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.553886] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.553980] pcieport 0000:00:1c.3: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.554020]   alloc irq_desc for 42 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554022]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554030] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.554119] pcieport 0000:00:1c.4: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.554158]   alloc irq_desc for 43 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554160]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554168] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.554259] pcieport 0000:00:1c.5: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.554298]   alloc irq_desc for 44 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554300]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.554307] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.554411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
21/02/2011 09:25:26	D7-K	kernel	[    0.554436] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554446] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554455] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554464] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554473] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554495] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554504] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554513] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554522] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554531] Firmware did not grant requested _OSC control
21/02/2011 09:25:26	D7-K	kernel	[    0.554538] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
21/02/2011 09:25:26	D7-K	kernel	[    0.554611] intel_idle: MWAIT substates: 0x22220
21/02/2011 09:25:26	D7-K	kernel	[    0.554613] intel_idle: does not run on family 6 model 23
21/02/2011 09:25:26	D7-K	kernel	[    0.554994] ACPI: AC Adapter [ACAD] (on-line)
21/02/2011 09:25:26	D7-K	kernel	[    0.555088] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
21/02/2011 09:25:26	D7-K	kernel	[    0.555093] ACPI: Power Button [PWRB]
21/02/2011 09:25:26	D7-K	kernel	[    0.555132] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
21/02/2011 09:25:26	D7-K	kernel	[    0.555452] ACPI: Lid Switch [LID0]
21/02/2011 09:25:26	D7-K	kernel	[    0.555491] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
21/02/2011 09:25:26	D7-K	kernel	[    0.555495] ACPI: Sleep Button [SLPB]
21/02/2011 09:25:26	D7-K	kernel	[    0.555547] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
21/02/2011 09:25:26	D7-K	kernel	[    0.555550] ACPI: Power Button [PWRF]
21/02/2011 09:25:26	D7-K	kernel	[    0.556021] ACPI: acpi_idle registered with cpuidle
21/02/2011 09:25:26	D7-K	kernel	[    0.579948] Monitor-Mwait will be used to enter C-1 state
21/02/2011 09:25:26	D7-K	kernel	[    0.580010] Monitor-Mwait will be used to enter C-2 state
21/02/2011 09:25:26	D7-K	kernel	[    0.580036] Monitor-Mwait will be used to enter C-3 state
21/02/2011 09:25:26	D7-K	kernel	[    0.580043] Marking TSC unstable due to TSC halts in idle
21/02/2011 09:25:26	D7-K	kernel	[    0.590076] Switching to clocksource hpet
21/02/2011 09:25:26	D7-K	kernel	[    0.595547] [Firmware Bug]: Invalid critical threshold (0)
21/02/2011 09:25:26	D7-K	kernel	[    0.596828] thermal LNXTHERM:01: registered as thermal_zone0
21/02/2011 09:25:26	D7-K	kernel	[    0.596836] ACPI: Thermal Zone [TZ01] (48 C)
21/02/2011 09:25:26	D7-K	kernel	[    0.596942] ERST: Table is not found!
21/02/2011 09:25:26	D7-K	kernel	[    0.597243] Linux agpgart interface v0.103
21/02/2011 09:25:26	D7-K	kernel	[    0.597272] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
21/02/2011 09:25:26	D7-K	kernel	[    0.598665] brd: module loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.599221] loop: module loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.599728] Fixed MDIO Bus: probed
21/02/2011 09:25:26	D7-K	kernel	[    0.599793] PPP generic driver version 2.4.2
21/02/2011 09:25:26	D7-K	kernel	[    0.599829] tun: Universal TUN/TAP device driver, 1.6
21/02/2011 09:25:26	D7-K	kernel	[    0.599831] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
21/02/2011 09:25:26	D7-K	kernel	[    0.599898] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
21/02/2011 09:25:26	D7-K	kernel	[    0.599922] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
21/02/2011 09:25:26	D7-K	kernel	[    0.599946] ehci_hcd 0000:00:1a.7: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.599950] ehci_hcd 0000:00:1a.7: EHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.600013] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
21/02/2011 09:25:26	D7-K	kernel	[    0.600050] ehci_hcd 0000:00:1a.7: debug port 1
21/02/2011 09:25:26	D7-K	kernel	[    0.603925] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
21/02/2011 09:25:26	D7-K	kernel	[    0.603945] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xda505c00
21/02/2011 09:25:26	D7-K	kernel	[    0.633280] ACPI: Battery Slot [BAT0] (battery present)
21/02/2011 09:25:26	D7-K	kernel	[    0.640023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
21/02/2011 09:25:26	D7-K	kernel	[    0.640163] hub 1-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.640168] hub 1-0:1.0: 4 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.640257]   alloc irq_desc for 20 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.640260]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.640268] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
21/02/2011 09:25:26	D7-K	kernel	[    0.640295] ehci_hcd 0000:00:1d.7: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.640298] ehci_hcd 0000:00:1d.7: EHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.640339] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
21/02/2011 09:25:26	D7-K	kernel	[    0.640370] ehci_hcd 0000:00:1d.7: debug port 1
21/02/2011 09:25:26	D7-K	kernel	[    0.644241] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
21/02/2011 09:25:26	D7-K	kernel	[    0.644263] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda505800
21/02/2011 09:25:26	D7-K	kernel	[    0.670021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
21/02/2011 09:25:26	D7-K	kernel	[    0.670177] hub 2-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.670182] hub 2-0:1.0: 8 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.670268] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
21/02/2011 09:25:26	D7-K	kernel	[    0.670285] uhci_hcd: USB Universal Host Controller Interface driver
21/02/2011 09:25:26	D7-K	kernel	[    0.670364] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[    0.670376] uhci_hcd 0000:00:1a.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.670380] uhci_hcd 0000:00:1a.0: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.670419] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
21/02/2011 09:25:26	D7-K	kernel	[    0.670461] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070e0
21/02/2011 09:25:26	D7-K	kernel	[    0.670568] hub 3-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.670572] hub 3-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.670628]   alloc irq_desc for 21 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.670630]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.670637] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
21/02/2011 09:25:26	D7-K	kernel	[    0.670643] uhci_hcd 0000:00:1a.1: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.670646] uhci_hcd 0000:00:1a.1: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.670680] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
21/02/2011 09:25:26	D7-K	kernel	[    0.670714] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000070c0
21/02/2011 09:25:26	D7-K	kernel	[    0.670825] hub 4-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.670833] hub 4-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.670892] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
21/02/2011 09:25:26	D7-K	kernel	[    0.670898] uhci_hcd 0000:00:1d.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.670901] uhci_hcd 0000:00:1d.0: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.670939] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
21/02/2011 09:25:26	D7-K	kernel	[    0.670964] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000070a0
21/02/2011 09:25:26	D7-K	kernel	[    0.671066] hub 5-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.671070] hub 5-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.671127] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
21/02/2011 09:25:26	D7-K	kernel	[    0.671135] uhci_hcd 0000:00:1d.1: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.671138] uhci_hcd 0000:00:1d.1: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.671167] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
21/02/2011 09:25:26	D7-K	kernel	[    0.671193] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00007080
21/02/2011 09:25:26	D7-K	kernel	[    0.671299] hub 6-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.671303] hub 6-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.671356] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[    0.671362] uhci_hcd 0000:00:1d.2: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.671366] uhci_hcd 0000:00:1d.2: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.671409] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
21/02/2011 09:25:26	D7-K	kernel	[    0.671434] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00007060
21/02/2011 09:25:26	D7-K	kernel	[    0.671546] hub 7-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.671551] hub 7-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.671605]   alloc irq_desc for 18 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.671607]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.671612] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
21/02/2011 09:25:26	D7-K	kernel	[    0.671618] uhci_hcd 0000:00:1d.3: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.671621] uhci_hcd 0000:00:1d.3: UHCI Host Controller
21/02/2011 09:25:26	D7-K	kernel	[    0.671654] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
21/02/2011 09:25:26	D7-K	kernel	[    0.671688] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00007040
21/02/2011 09:25:26	D7-K	kernel	[    0.671791] hub 8-0:1.0: USB hub found
21/02/2011 09:25:26	D7-K	kernel	[    0.671795] hub 8-0:1.0: 2 ports detected
21/02/2011 09:25:26	D7-K	kernel	[    0.671906] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
21/02/2011 09:25:26	D7-K	kernel	[    0.685157] Freeing initrd memory: 16320k freed
21/02/2011 09:25:26	D7-K	kernel	[    0.694216] serio: i8042 KBD port at 0x60,0x64 irq 1
21/02/2011 09:25:26	D7-K	kernel	[    0.694231] serio: i8042 AUX port at 0x60,0x64 irq 12
21/02/2011 09:25:26	D7-K	kernel	[    0.694385] mice: PS/2 mouse device common for all mice
21/02/2011 09:25:26	D7-K	kernel	[    0.694538] rtc_cmos 00:04: RTC can wake from S4
21/02/2011 09:25:26	D7-K	kernel	[    0.694585] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
21/02/2011 09:25:26	D7-K	kernel	[    0.694620] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
21/02/2011 09:25:26	D7-K	kernel	[    0.694734] device-mapper: uevent: version 1.0.3
21/02/2011 09:25:26	D7-K	kernel	[    0.694828] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
21/02/2011 09:25:26	D7-K	kernel	[    0.694897] device-mapper: multipath: version 1.1.1 loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.694899] device-mapper: multipath round-robin: version 1.0.0 loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.695098] cpuidle: using governor ladder
21/02/2011 09:25:26	D7-K	kernel	[    0.695842] cpuidle: using governor menu
21/02/2011 09:25:26	D7-K	kernel	[    0.696116] TCP cubic registered
21/02/2011 09:25:26	D7-K	kernel	[    0.696229] NET: Registered protocol family 10
21/02/2011 09:25:26	D7-K	kernel	[    0.696581] lo: Disabled Privacy Extensions
21/02/2011 09:25:26	D7-K	kernel	[    0.696759] NET: Registered protocol family 17
21/02/2011 09:25:26	D7-K	kernel	[    0.697418] PM: Resume from disk failed.
21/02/2011 09:25:26	D7-K	kernel	[    0.697432] registered taskstats version 1
21/02/2011 09:25:26	D7-K	kernel	[    0.698025]   Magic number: 15:878:424
21/02/2011 09:25:26	D7-K	kernel	[    0.698163] rtc_cmos 00:04: setting system clock to 2011-02-21 09:25:10 UTC (1298280310)
21/02/2011 09:25:26	D7-K	kernel	[    0.698165] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
21/02/2011 09:25:26	D7-K	kernel	[    0.698167] EDD information not available.
21/02/2011 09:25:26	D7-K	kernel	[    0.698262] Freeing unused kernel memory: 908k freed
21/02/2011 09:25:26	D7-K	kernel	[    0.698608] Write protecting the kernel read-only data: 10240k
21/02/2011 09:25:26	D7-K	kernel	[    0.698810] Freeing unused kernel memory: 412k freed
21/02/2011 09:25:26	D7-K	kernel	[    0.699085] Freeing unused kernel memory: 1644k freed
21/02/2011 09:25:26	D7-K	kernel	[    0.715471] udev[84]: starting version 163
21/02/2011 09:25:26	D7-K	kernel	[    0.715588] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
21/02/2011 09:25:26	D7-K	kernel	[    0.763011] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
21/02/2011 09:25:26	D7-K	kernel	[    0.764383] agpgart-intel 0000:00:00.0: detected 65532K stolen memory, trimming to 32768K
21/02/2011 09:25:26	D7-K	kernel	[    0.861122] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
21/02/2011 09:25:26	D7-K	kernel	[    0.861151] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
21/02/2011 09:25:26	D7-K	kernel	[    0.861213] r8169 0000:03:00.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.861393]   alloc irq_desc for 45 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.861395]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.861412] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.861876] r8169 0000:03:00.0: eth0: RTL8102e at 0xffffc900050d4000, 00:26:9e:33:a1:13, XID 04d00000 IRQ 45
21/02/2011 09:25:26	D7-K	kernel	[    0.886739] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
21/02/2011 09:25:26	D7-K	kernel	[    0.886778] ahci 0000:00:1f.2: version 3.0
21/02/2011 09:25:26	D7-K	kernel	[    0.886800] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
21/02/2011 09:25:26	D7-K	kernel	[    0.886847]   alloc irq_desc for 46 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.886849]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    0.886862] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    0.886917] ahci: SSS flag set, parallel bus scan disabled
21/02/2011 09:25:26	D7-K	kernel	[    0.886950] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
21/02/2011 09:25:26	D7-K	kernel	[    0.886954] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
21/02/2011 09:25:26	D7-K	kernel	[    0.886959] ahci 0000:00:1f.2: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.905363] [drm] Initialized drm 1.1.0 20060810
21/02/2011 09:25:26	D7-K	kernel	[    0.941444] scsi0 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.941620] scsi1 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.941726] scsi2 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.941798] scsi3 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.941870] scsi4 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.941943] scsi5 : ahci
21/02/2011 09:25:26	D7-K	kernel	[    0.942145] ata1: SATA max UDMA/133 abar m2048@0xda505000 port 0xda505100 irq 46
21/02/2011 09:25:26	D7-K	kernel	[    0.942149] ata2: SATA max UDMA/133 abar m2048@0xda505000 port 0xda505180 irq 46
21/02/2011 09:25:26	D7-K	kernel	[    0.942151] ata3: DUMMY
21/02/2011 09:25:26	D7-K	kernel	[    0.942153] ata4: DUMMY
21/02/2011 09:25:26	D7-K	kernel	[    0.942155] ata5: SATA max UDMA/133 abar m2048@0xda505000 port 0xda505300 irq 46
21/02/2011 09:25:26	D7-K	kernel	[    0.942158] ata6: SATA max UDMA/133 abar m2048@0xda505000 port 0xda505380 irq 46
21/02/2011 09:25:26	D7-K	kernel	[    0.942211] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[    0.942216] i915 0000:00:02.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[    0.990035] usb 2-4: new high speed USB device using ehci_hcd and address 2
21/02/2011 09:25:26	D7-K	kernel	[    1.016148] [drm] detected 63M stolen memory, trimming to 32M
21/02/2011 09:25:26	D7-K	kernel	[    1.016256]   alloc irq_desc for 47 on node -1
21/02/2011 09:25:26	D7-K	kernel	[    1.016258]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[    1.016268] i915 0000:00:02.0: irq 47 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[    1.016283] [drm] set up 32M of stolen space
21/02/2011 09:25:26	D7-K	kernel	[    1.016437] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
21/02/2011 09:25:26	D7-K	kernel	[    1.016442] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
21/02/2011 09:25:26	D7-K	kernel	[    1.133692] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
21/02/2011 09:25:26	D7-K	kernel	[    1.491286] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
21/02/2011 09:25:26	D7-K	kernel	[    1.493507] ata1.00: ATA-8: WDC WD3200BEKT-60F3T1, 12.01A12, max UDMA/100
21/02/2011 09:25:26	D7-K	kernel	[    1.493510] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
21/02/2011 09:25:26	D7-K	kernel	[    1.495810] ata1.00: configured for UDMA/100
21/02/2011 09:25:26	D7-K	kernel	[    1.511386] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
21/02/2011 09:25:26	D7-K	kernel	[    1.511531] sd 0:0:0:0: Attached scsi generic sg0 type 0
21/02/2011 09:25:26	D7-K	kernel	[    1.511712] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
21/02/2011 09:25:26	D7-K	kernel	[    1.511764] sd 0:0:0:0: [sda] Write Protect is off
21/02/2011 09:25:26	D7-K	kernel	[    1.511767] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
21/02/2011 09:25:26	D7-K	kernel	[    1.511789] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
21/02/2011 09:25:26	D7-K	kernel	[    1.512119]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
21/02/2011 09:25:26	D7-K	kernel	[    1.576303] sd 0:0:0:0: [sda] Attached SCSI disk
21/02/2011 09:25:26	D7-K	kernel	[    1.680054] Skipping EDID probe due to cached edid
21/02/2011 09:25:26	D7-K	kernel	[    2.213689] Console: switching to colour frame buffer device 170x48
21/02/2011 09:25:26	D7-K	kernel	[    2.216331] fb0: inteldrmfb frame buffer device
21/02/2011 09:25:26	D7-K	kernel	[    2.216333] drm: registered panic notifier
21/02/2011 09:25:26	D7-K	kernel	[    2.216335] Slow work thread pool: Starting up
21/02/2011 09:25:26	D7-K	kernel	[    2.216444] Slow work thread pool: Ready
21/02/2011 09:25:26	D7-K	kernel	[    2.221457] ACPI Error (dswload-0802): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
21/02/2011 09:25:26	D7-K	kernel	[    2.221463] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20100428/psloop-231)
21/02/2011 09:25:26	D7-K	kernel	[    2.221468] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03.GBQC] (Node ffff88013b63c640), AE_ALREADY_EXISTS
21/02/2011 09:25:26	D7-K	kernel	[    2.221481] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
21/02/2011 09:25:26	D7-K	kernel	[    2.221515] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03._BQC] (Node ffff88013b63c620), AE_ALREADY_EXISTS
21/02/2011 09:25:26	D7-K	kernel	[    2.221527] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
21/02/2011 09:25:26	D7-K	kernel	[    2.221567] ACPI Warning: Evaluating _BQC failed (20100428/video-651)
21/02/2011 09:25:26	D7-K	kernel	[    2.223403] acpi device:02: registered as cooling_device2
21/02/2011 09:25:26	D7-K	kernel	[    2.223802] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
21/02/2011 09:25:26	D7-K	kernel	[    2.223842] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
21/02/2011 09:25:26	D7-K	kernel	[    2.223898] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
21/02/2011 09:25:26	D7-K	kernel	[    2.461347] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
21/02/2011 09:25:26	D7-K	kernel	[    2.478761] ata2.00: ATAPI: hp       CDDVDW TS-L633M, 0301, max UDMA/100
21/02/2011 09:25:26	D7-K	kernel	[    2.496835] ata2.00: configured for UDMA/100
21/02/2011 09:25:26	D7-K	kernel	[    2.512463] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633M  0301 PQ: 0 ANSI: 5
21/02/2011 09:25:26	D7-K	kernel	[    2.522336] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
21/02/2011 09:25:26	D7-K	kernel	[    2.522341] Uniform CD-ROM driver Revision: 3.20
21/02/2011 09:25:26	D7-K	kernel	[    2.522519] sr 1:0:0:0: Attached scsi CD-ROM sr0
21/02/2011 09:25:26	D7-K	kernel	[    2.522578] sr 1:0:0:0: Attached scsi generic sg1 type 5
21/02/2011 09:25:26	D7-K	kernel	[    2.870128] ata5: SATA link down (SStatus 0 SControl 300)
21/02/2011 09:25:26	D7-K	kernel	[    3.240101] ata6: SATA link down (SStatus 0 SControl 300)
21/02/2011 09:25:26	D7-K	kernel	[    3.940093] Skipping EDID probe due to cached edid
21/02/2011 09:25:26	D7-K	kernel	[    4.069398] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
21/02/2011 09:25:26	D7-K	kernel	[   16.172864] udev[487]: starting version 163
21/02/2011 09:25:26	D7-K	kernel	[   16.212924] Adding 7842812k swap on /dev/sda6.  Priority:-1 extents:1 across:7842812k 
21/02/2011 09:25:26	D7-K	kernel	[   16.241775] lp: driver loaded but no devices found
21/02/2011 09:25:26	D7-K	kernel	[   16.289960] lis3lv02d: laptop model unknown, using default axes configuration
21/02/2011 09:25:26	D7-K	kernel	[   16.351362] lib80211: common routines for IEEE802.11 drivers
21/02/2011 09:25:26	D7-K	kernel	[   16.351366] lib80211_crypt: registered algorithm 'NULL'
21/02/2011 09:25:26	D7-K	kernel	[   16.356880] wl: module license 'MIXED/Proprietary' taints kernel.
21/02/2011 09:25:26	D7-K	kernel	[   16.429742] lis3lv02d: 8 bits sensor found
21/02/2011 09:25:26	D7-K	kernel	[   16.433902] lirc_dev: IR Remote Control driver registered, major 251 
21/02/2011 09:25:26	D7-K	kernel	[   16.434012] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
21/02/2011 09:25:26	D7-K	kernel	[   16.434604] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
21/02/2011 09:25:26	D7-K	kernel	[   16.434667] enecir: unknown ENE chip detected, assuming KB3926D
21/02/2011 09:25:26	D7-K	kernel	[   16.434669] enecir: driver support incomplete
21/02/2011 09:25:26	D7-K	kernel	[   16.434671] enecir: chip is 0x3926 - 0x00, 0xd2
21/02/2011 09:25:26	D7-K	kernel	[   16.434678] enecir: hardware features:
21/02/2011 09:25:26	D7-K	kernel	[   16.434680] enecir: learning and tx off, gpio40_learn off, fan_in off
21/02/2011 09:25:26	D7-K	kernel	[   16.434682] enecir: driver has been succesfully loaded
21/02/2011 09:25:26	D7-K	kernel	[   16.505451] Linux video capture interface: v2.00
21/02/2011 09:25:26	D7-K	kernel	[   16.508424] uvcvideo: Found UVC 1.00 device HP Webcam (0408:03f1)
21/02/2011 09:25:26	D7-K	kernel	[   16.510119] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
21/02/2011 09:25:26	D7-K	kernel	[   16.510132] wl 0000:02:00.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[   16.522426] input: HP WMI hotkeys as /devices/virtual/input/input6
21/02/2011 09:25:26	D7-K	kernel	[   16.535659] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
21/02/2011 09:25:26	D7-K	kernel	[   16.535712] usbcore: registered new interface driver uvcvideo
21/02/2011 09:25:26	D7-K	kernel	[   16.535715] USB Video Class driver (v0.1.0)
21/02/2011 09:25:26	D7-K	kernel	[   16.543796] type=1400 audit(1298280326.338:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=797 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.544449] type=1400 audit(1298280326.338:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=797 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.544801] type=1400 audit(1298280326.338:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=797 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.545402] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
21/02/2011 09:25:26	D7-K	kernel	[   16.547410] type=1400 audit(1298280326.338:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=807 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.548269] type=1400 audit(1298280326.338:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.548620] type=1400 audit(1298280326.338:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.588716] lib80211_crypt: registered algorithm 'TKIP'
21/02/2011 09:25:26	D7-K	kernel	[   16.589026] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
21/02/2011 09:25:26	D7-K	kernel	[   16.600151] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
21/02/2011 09:25:26	D7-K	kernel	[   16.600296] Registered led device: hp::hddprotect
21/02/2011 09:25:26	D7-K	kernel	[   16.600317] lis3lv02d driver loaded.
21/02/2011 09:25:26	D7-K	kernel	[   16.662872]   alloc irq_desc for 22 on node -1
21/02/2011 09:25:26	D7-K	kernel	[   16.662876]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[   16.662884] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
21/02/2011 09:25:26	D7-K	kernel	[   16.662962]   alloc irq_desc for 48 on node -1
21/02/2011 09:25:26	D7-K	kernel	[   16.662963]   alloc kstat_irqs on node -1
21/02/2011 09:25:26	D7-K	kernel	[   16.662974] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
21/02/2011 09:25:26	D7-K	kernel	[   16.663005] HDA Intel 0000:00:1b.0: setting latency timer to 64
21/02/2011 09:25:26	D7-K	kernel	[   16.800432] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
21/02/2011 09:25:26	D7-K	kernel	[   16.800517] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Found user 'avahi' (UID 105) and group 'avahi' (GID 110).
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Successfully dropped root privileges.
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	avahi-daemon 0.6.27 starting up.
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Successfully called chroot().
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Successfully dropped remaining capabilities.
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	No service file found in /etc/avahi/services.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> NetworkManager (version 0.8.1) is starting...
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> Read config file /etc/NetworkManager/nm-system-settings.conf
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> trying to start the modem manager...
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Network interface enumeration completed.
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Registering HINFO record with values 'X86_64'/'LINUX'.
21/02/2011 09:25:26	D7-K	avahi-daemon[1016]	Server startup complete. Host name is D7-K.local. Local service cookie is 740329644.
21/02/2011 09:25:26	D7-K	modem-manager	ModemManager (version 0.4) starting...
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Ericsson MBM
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin ZTE
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Generic
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Gobi
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Huawei
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Longcheer
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin SimTech
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Sierra
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Novatel
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin AnyData
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin MotoC
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Option
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Option High-Speed
21/02/2011 09:25:26	D7-K	modem-manager	Loaded plugin Nokia
21/02/2011 09:25:26	D7-K	modem-manager	(tty/ttyS0): port's parent platform driver is not whitelisted
21/02/2011 09:25:26	D7-K	modem-manager	(tty/ttyS1): port's parent platform driver is not whitelisted
21/02/2011 09:25:26	D7-K	modem-manager	(tty/ttyS2): port's parent platform driver is not whitelisted
21/02/2011 09:25:26	D7-K	modem-manager	(tty/ttyS3): port's parent platform driver is not whitelisted
21/02/2011 09:25:26	D7-K	kernel	[   16.893266] type=1400 audit(1298280326.688:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1040 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.893918] type=1400 audit(1298280326.688:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1040 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.894271] type=1400 audit(1298280326.688:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1040 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	kernel	[   16.896482] type=1400 audit(1298280326.688:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1042 comm="apparmor_parser"
21/02/2011 09:25:26	D7-K	polkitd[1027]	started daemon version 0.99 using authority implementation `local' version `0.99'
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> monitoring kernel firmware directory '/lib/firmware'.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: init!
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: update_system_hostname
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPluginIfupdown: management mode: unmanaged
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth1, iface: eth1)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: end _init.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   Ifupdown: get unmanaged devices count: 0
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: (27319968) ... get_connections.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   SCPlugin-Ifupdown: (27319968) ... get_connections (managed=false): return empty list.
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	   Ifupdown: get unmanaged devices count: 0
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/hp-wmi/rfkill/rfkill0) (driver hp-wmi)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> WiFi enabled by radio killswitch; enabled by state file
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> WWAN enabled by radio killswitch; enabled by state file
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> WiMAX enabled by radio killswitch; enabled by state file
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> Networking is enabled by state file
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<error> [1298280326.743776] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): driver supports SSID scans (scan_capa 0x01).
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): now managed
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 1 -> 2 (reason 2)
21/02/2011 09:25:26	D7-K	NetworkManager[1018]	<info> (eth1): bringing up device.
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth1): preparing device.
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth1): deactivating device (reason: 2).
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): carrier is OFF
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): now managed
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): device state change: 1 -> 2 (reason 2)
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): bringing up device.
21/02/2011 09:25:27	D7-K	kernel	[   17.255766] r8169 0000:03:00.0: eth0: link down
21/02/2011 09:25:27	D7-K	kernel	[   17.256327] ADDRCONF(NETDEV_UP): eth0: link is not ready
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): preparing device.
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth0): deactivating device (reason: 2).
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> modem-manager is now available
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> Trying to start the supplicant...
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth1): supplicant manager state:  down -> idle
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 2 -> 3 (reason 0)
21/02/2011 09:25:27	D7-K	NetworkManager[1018]	<info> (eth1): supplicant interface state:  starting -> ready
21/02/2011 09:25:27	D7-K	cron[1105]	(CRON) INFO (pidfile fd = 3)
21/02/2011 09:25:27	D7-K	init	apport pre-start process (1085) terminated with status 1
21/02/2011 09:25:27	D7-K	acpid	starting up with proc fs
21/02/2011 09:25:27	D7-K	acpid	36 rules loaded
21/02/2011 09:25:27	D7-K	acpid	waiting for events: event logging is off
21/02/2011 09:25:27	D7-K	init	apport post-stop process (1117) terminated with status 1
21/02/2011 09:25:27	D7-K	anacron[1127]	Anacron 2.3 started on 2011-02-21
21/02/2011 09:25:27	D7-K	cron[1133]	(CRON) STARTUP (fork ok)
21/02/2011 09:25:27	D7-K	cron[1133]	(CRON) INFO (Running @reboot jobs)
21/02/2011 09:25:27	D7-K	anacron[1127]	Normal exit (0 jobs run)
21/02/2011 09:25:27	D7-K	acpid	client connected from 1082[0:0]
21/02/2011 09:25:27	D7-K	acpid	1 client rule loaded
21/02/2011 09:25:27	D7-K	kernel	[   17.470481] Skipping EDID probe due to cached edid
21/02/2011 09:25:27	D7-K	kernel	[   17.476470] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
21/02/2011 09:25:27	D7-K	kernel	[   17.520097] Skipping EDID probe due to cached edid
21/02/2011 09:25:27	D7-K	kernel	[   17.560810] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
21/02/2011 09:25:27	D7-K	anacron[1238]	Anacron 2.3 started on 2011-02-21
21/02/2011 09:25:27	D7-K	anacron[1238]	Normal exit (0 jobs run)
21/02/2011 09:25:27	D7-K	kernel	[   18.095245] ppdev: user-space parallel port driver
21/02/2011 09:25:28	D7-K	kernel	[   18.717091] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
21/02/2011 09:25:28	D7-K	init	plymouth-stop pre-start process (1354) terminated with status 1
21/02/2011 09:25:28	D7-K	pulseaudio[1356]	core-util.c: Home directory /etc/timidity not ours.
21/02/2011 09:25:28	D7-K	pulseaudio[1356]	lock-autospawn.c: Cannot access autospawn lock.
21/02/2011 09:25:28	D7-K	pulseaudio[1356]	main.c: Failed to acquire autospawn lock
21/02/2011 09:25:28	D7-K	kdm_greet[1285]	Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
21/02/2011 09:25:28	D7-K	avahi-daemon[1016]	Joining mDNS multicast group on interface eth1.IPv6 with address fe80::226:5eff:fe8f:f833.
21/02/2011 09:25:28	D7-K	avahi-daemon[1016]	New relevant interface eth1.IPv6 for mDNS.
21/02/2011 09:25:28	D7-K	avahi-daemon[1016]	Registering new address record for fe80::226:5eff:fe8f:f833 on eth1.*.
21/02/2011 09:25:37	D7-K	kernel	[   28.130086] eth1: no IPv6 routers present
21/02/2011 09:31:49	D7-K	kdm	:0[1284]: pam_sm_authenticate: Called
21/02/2011 09:31:49	D7-K	kdm	:0[1284]: pam_sm_authenticate: username = [dark7man]
21/02/2011 09:31:49	D7-K	kdm	:0[1372]: Passphrase file wrapped
21/02/2011 09:31:50	D7-K	kernel	[  400.651311] Intel AES-NI instructions are not detected.
21/02/2011 09:31:50	D7-K	kernel	[  400.683177] padlock: VIA PadLock not detected.
21/02/2011 09:31:51	D7-K	NetworkManager[1018]	<error> [1298280711.1960] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
21/02/2011 09:31:52	D7-K	anacron[1661]	Anacron 2.3 started on 2011-02-21
21/02/2011 09:31:52	D7-K	anacron[1661]	Normal exit (0 jobs run)
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) starting connection 'KLinkSys'
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 3 -> 4 (reason 0)
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 4 -> 5 (reason 0)
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless): access point 'KLinkSys' has security, but secrets are required.
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 5 -> 6 (reason 0)
21/02/2011 09:31:52	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
21/02/2011 09:31:52	D7-K	kernel	[  402.899057] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
21/02/2011 09:31:52	D7-K	kernel	[  402.940095] Skipping EDID probe due to cached edid
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Successfully called chroot.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Successfully dropped privileges.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Successfully limited resources.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Running.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Watchdog thread running.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Canary thread running.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Successfully made thread 1822 of process 1822 (n/a) owned by '1000' high priority at nice level -11.
21/02/2011 09:32:01	D7-K	rtkit-daemon[1824]	Supervising 1 threads of 1 processes of 1 users.
21/02/2011 09:32:02	D7-K	rtkit-daemon[1824]	Successfully made thread 1845 of process 1822 (n/a) owned by '1000' RT at priority 5.
21/02/2011 09:32:02	D7-K	rtkit-daemon[1824]	Supervising 2 threads of 1 processes of 1 users.
21/02/2011 09:32:02	D7-K	rtkit-daemon[1824]	Successfully made thread 1848 of process 1822 (n/a) owned by '1000' RT at priority 5.
21/02/2011 09:32:02	D7-K	rtkit-daemon[1824]	Supervising 3 threads of 1 processes of 1 users.
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 40.
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: snd_pcm_dump():
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Soft volume PCM
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Control: PCM Playback Volume
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: min_dB: -51
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: max_dB: 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: resolution: 256
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Its setup is:
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   stream       : CAPTURE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   access       : MMAP_INTERLEAVED
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   format       : S16_LE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   subformat    : STD
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   channels     : 2
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   rate         : 44100
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   exact rate   : 44100 (44100/1)
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   msbits       : 16
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   buffer_size  : 88192
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_size  : 44096
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_time  : 999909
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   tstamp_mode  : ENABLE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_step  : 1
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   avail_min    : 87310
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_event : 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   start_threshold  : -1
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   stop_threshold   : 6205960286516543488
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   silence_threshold: 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   silence_size : 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   boundary     : 6205960286516543488
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c: Its setup is:
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   stream       : CAPTURE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   access       : MMAP_INTERLEAVED
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   format       : S16_LE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   subformat    : STD
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   channels     : 2
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   rate         : 44100
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   exact rate   : 44100 (44100/1)
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   msbits       : 16
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   buffer_size  : 88192
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_size  : 44096
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_time  : 999909
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   tstamp_mode  : ENABLE
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_step  : 1
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   avail_min    : 87310
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   period_event : 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   start_threshold  : -1
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   stop_threshold   : 6205960286516543488
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   silence_threshold: 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   silence_size : 0
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   boundary     : 6205960286516543488
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   appl_ptr     : 50248
21/02/2011 09:32:03	D7-K	pulseaudio[1822]	alsa-util.c:   hw_ptr       : 50248
21/02/2011 09:32:04	D7-K	kernel	[  414.391320] Skipping EDID probe due to cached edid
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<warn> Failed to update connection secrets: 1 802-1x
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 6 -> 4 (reason 0)
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 4 -> 5 (reason 0)
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless): connection 'KLinkSys' has security, and secrets exist.  No new secrets needed.
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Config: added 'ssid' value 'KLinkSys'
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Config: added 'scan_ssid' value '1'
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Config: added 'key_mgmt' value 'WPA-PSK'
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Config: added 'psk' value '<omitted>'
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> Config: set interface ap_scan to 1
21/02/2011 09:32:15	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  inactive -> scanning
21/02/2011 09:32:20	D7-K	wpa_supplicant[1079]	Trying to associate with 00:16:b6:41:60:12 (SSID='KLinkSys' freq=2467 MHz)
21/02/2011 09:32:20	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  scanning -> associating
21/02/2011 09:32:20	D7-K	wpa_supplicant[1079]	Association request to the driver failed
21/02/2011 09:32:21	D7-K	wpa_supplicant[1079]	Associated with 00:16:b6:41:60:12
21/02/2011 09:32:21	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  associating -> associated
21/02/2011 09:32:21	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  associated -> 4-way handshake
21/02/2011 09:32:22	D7-K	wpa_supplicant[1079]	WPA: Key negotiation completed with 00:16:b6:41:60:12 [PTK=CCMP GTK=CCMP]
21/02/2011 09:32:22	D7-K	wpa_supplicant[1079]	CTRL-EVENT-CONNECTED - Connection to 00:16:b6:41:60:12 completed (auth) [id=0 id_str=]
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  4-way handshake -> group handshake
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  group handshake -> completed
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KLinkSys'.
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 5 -> 7 (reason 0)
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> dhclient started with pid 1960
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
21/02/2011 09:32:22	D7-K	dhclient	Internet Systems Consortium DHCP Client V3.1.3
21/02/2011 09:32:22	D7-K	dhclient	Copyright 2004-2009 Internet Systems Consortium.
21/02/2011 09:32:22	D7-K	dhclient	All rights reserved.
21/02/2011 09:32:22	D7-K	dhclient	For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
21/02/2011 09:32:22	D7-K	dhclient	
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> (eth1): DHCPv4 state changed nbi -> preinit
21/02/2011 09:32:22	D7-K	dhclient	Listening on LPF/eth1/00:26:5e:8f:f8:33
21/02/2011 09:32:22	D7-K	dhclient	Sending on   LPF/eth1/00:26:5e:8f:f8:33
21/02/2011 09:32:22	D7-K	dhclient	Sending on   Socket/fallback
21/02/2011 09:32:22	D7-K	dhclient	DHCPREQUEST of 192.168.7.103 on eth1 to 255.255.255.255 port 67
21/02/2011 09:32:22	D7-K	dhclient	DHCPACK of 192.168.7.103 from 192.168.7.1
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> (eth1): DHCPv4 state changed preinit -> reboot
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   address 192.168.7.103
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   prefix 24 (255.255.255.0)
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   gateway 192.168.7.1
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   hostname 'D7-K'
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   nameserver '194.168.4.100'
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   nameserver '194.168.8.100'
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info>   domain name 'cable.virginmedia.net'
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
21/02/2011 09:32:22	D7-K	dhclient	bound to 192.168.7.103 -- renewal in 38270 seconds.
21/02/2011 09:32:22	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
21/02/2011 09:32:22	D7-K	avahi-daemon[1016]	Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.7.103.
21/02/2011 09:32:22	D7-K	avahi-daemon[1016]	New relevant interface eth1.IPv4 for mDNS.
21/02/2011 09:32:22	D7-K	avahi-daemon[1016]	Registering new address record for 192.168.7.103 on eth1.IPv4.
21/02/2011 09:32:23	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 7 -> 8 (reason 0)
21/02/2011 09:32:23	D7-K	NetworkManager[1018]	<info> Policy set 'KLinkSys' (eth1) as default for IPv4 routing and DNS.
21/02/2011 09:32:23	D7-K	NetworkManager[1018]	<info> Updating /etc/hosts with new system hostname
21/02/2011 09:32:23	D7-K	NetworkManager[1018]	<info> Activation (eth1) successful, device activated.
21/02/2011 09:32:23	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
21/02/2011 09:32:23	D7-K	nm-dispatcher.action	nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
21/02/2011 09:32:23	D7-K	nm-dispatcher.action	Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
21/02/2011 09:32:24	D7-K	ntpdate[2012]	adjust time server 91.189.94.4 offset -0.082041 sec
21/02/2011 09:32:43	D7-K	kernel	[  453.850035] CE: hpet increased min_delta_ns to 7500 nsec
21/02/2011 09:35:56	D7-K	sudo	pam_sm_authenticate: Called
21/02/2011 09:35:56	D7-K	sudo	pam_sm_authenticate: username = [dark7man]
21/02/2011 09:35:56	D7-K	sudo	pam_sm_authenticate: /home/dark7man is already mounted
21/02/2011 09:36:49	D7-K	kernel	[  699.444032] lo: Disabled Privacy Extensions
21/02/2011 09:39:06	D7-K	kernel	[  836.222835] show_signal_msg: 15 callbacks suppressed
21/02/2011 09:39:06	D7-K	kernel	[  836.222840] npviewer.bin[2436]: segfault at 0 ip 00000000f61c88c1 sp 00000000ff926f70 error 4 in libflashplayer.so[f5e00000+b5f000]
21/02/2011 09:39:39	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 8 -> 3 (reason 38)
21/02/2011 09:39:39	D7-K	NetworkManager[1018]	<info> (eth1): deactivating device (reason: 38).
21/02/2011 09:39:39	D7-K	NetworkManager[1018]	<info> (eth1): canceled DHCP transaction, DHCP client pid 1960
21/02/2011 09:39:39	D7-K	avahi-daemon[1016]	Withdrawing address record for 192.168.7.103 on eth1.
21/02/2011 09:39:39	D7-K	avahi-daemon[1016]	Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.7.103.
21/02/2011 09:39:39	D7-K	avahi-daemon[1016]	Interface eth1.IPv4 no longer relevant for mDNS.
21/02/2011 09:39:39	D7-K	wpa_supplicant[1079]	CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
21/02/2011 09:39:39	D7-K	acpid	client 1082[0:0] has disconnected
21/02/2011 09:39:39	D7-K	acpid	client connected from 1082[0:0]
21/02/2011 09:39:39	D7-K	acpid	1 client rule loaded
21/02/2011 09:39:40	D7-K	kernel	[  870.196401] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
21/02/2011 09:39:40	D7-K	NetworkManager[1018]	<error> [1298281180.534489] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
21/02/2011 09:39:40	D7-K	NetworkManager[1018]	<error> [1298281180.536259] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
21/02/2011 09:39:40	D7-K	NetworkManager[1018]	<error> [1298281180.536716] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
21/02/2011 09:39:41	D7-K	kdm_greet[2563]	Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
21/02/2011 09:39:45	D7-K	kernel	[  875.605773] type=1400 audit(1298281185.395:17): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:45	D7-K	kernel	[  875.626265] type=1400 audit(1298281185.415:18): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:45	D7-K	kernel	[  875.626286] type=1400 audit(1298281185.415:19): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:47	D7-K	kernel	[  877.939663] type=1400 audit(1298281187.725:20): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:47	D7-K	kernel	[  877.939678] type=1400 audit(1298281187.725:21): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:47	D7-K	kernel	[  877.939929] type=1400 audit(1298281187.725:22): apparmor="DENIED" operation="file_perm" info="Failed name lookup - disconnected path" error=-116 parent=1706 profile="/usr/sbin/mysqld-akonadi" name=".local/share/akonadi/db_data/mysql.err" pid=2578 comm="mysqld-akonadi" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
21/02/2011 09:39:47	D7-K	kdm	:0[2546]: pam_sm_authenticate: Called
21/02/2011 09:39:47	D7-K	kdm	:0[2546]: pam_sm_authenticate: username = [dark7man]
21/02/2011 09:39:47	D7-K	kdm	:0[2579]: Passphrase file wrapped
21/02/2011 09:39:48	D7-K	kdm	:0[2579]: Error attempting to add filename encryption key to user session keyring; rc = [1]
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) starting connection 'KLinkSys'
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 3 -> 4 (reason 0)
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 4 -> 5 (reason 0)
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless): access point 'KLinkSys' has security, but secrets are required.
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 5 -> 6 (reason 0)
21/02/2011 09:39:49	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
21/02/2011 09:39:50	D7-K	kernel	[  880.251386] Skipping EDID probe due to cached edid
21/02/2011 09:39:57	D7-K	pulseaudio[1822]	module.c: Module "module-device-manager" should be loaded once at most. Refusing to load.
21/02/2011 09:39:57	D7-K	kernel	[  887.400133] Skipping EDID probe due to cached edid
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<warn> Failed to update connection secrets: 1 802-1x
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 6 -> 4 (reason 0)
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 4 -> 5 (reason 0)
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless): connection 'KLinkSys' has security, and secrets exist.  No new secrets needed.
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Config: added 'ssid' value 'KLinkSys'
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Config: added 'scan_ssid' value '1'
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Config: added 'key_mgmt' value 'WPA-PSK'
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Config: added 'psk' value '<omitted>'
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
21/02/2011 09:40:05	D7-K	NetworkManager[1018]	<info> Config: set interface ap_scan to 1
21/02/2011 09:40:06	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  disconnected -> scanning
21/02/2011 09:40:11	D7-K	wpa_supplicant[1079]	Trying to associate with 00:16:b6:41:60:12 (SSID='KLinkSys' freq=2467 MHz)
21/02/2011 09:40:11	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  scanning -> associating
21/02/2011 09:40:11	D7-K	wpa_supplicant[1079]	Association request to the driver failed
21/02/2011 09:40:11	D7-K	wpa_supplicant[1079]	Associated with 00:16:b6:41:60:12
21/02/2011 09:40:11	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  associating -> associated
21/02/2011 09:40:11	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  associated -> 4-way handshake
21/02/2011 09:40:12	D7-K	wpa_supplicant[1079]	WPA: Key negotiation completed with 00:16:b6:41:60:12 [PTK=CCMP GTK=CCMP]
21/02/2011 09:40:12	D7-K	wpa_supplicant[1079]	CTRL-EVENT-CONNECTED - Connection to 00:16:b6:41:60:12 completed (reauth) [id=0 id_str=]
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  4-way handshake -> group handshake
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  group handshake -> completed
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'KLinkSys'.
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 5 -> 7 (reason 0)
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> dhclient started with pid 2971
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
21/02/2011 09:40:12	D7-K	dhclient	Internet Systems Consortium DHCP Client V3.1.3
21/02/2011 09:40:12	D7-K	dhclient	Copyright 2004-2009 Internet Systems Consortium.
21/02/2011 09:40:12	D7-K	dhclient	All rights reserved.
21/02/2011 09:40:12	D7-K	dhclient	For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
21/02/2011 09:40:12	D7-K	dhclient	
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> (eth1): DHCPv4 state changed nbi -> preinit
21/02/2011 09:40:12	D7-K	dhclient	Listening on LPF/eth1/00:26:5e:8f:f8:33
21/02/2011 09:40:12	D7-K	dhclient	Sending on   LPF/eth1/00:26:5e:8f:f8:33
21/02/2011 09:40:12	D7-K	dhclient	Sending on   Socket/fallback
21/02/2011 09:40:12	D7-K	dhclient	DHCPREQUEST of 192.168.7.103 on eth1 to 255.255.255.255 port 67
21/02/2011 09:40:12	D7-K	dhclient	DHCPACK of 192.168.7.103 from 192.168.7.1
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> (eth1): DHCPv4 state changed preinit -> reboot
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   address 192.168.7.103
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   prefix 24 (255.255.255.0)
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   gateway 192.168.7.1
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   hostname 'D7-K'
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   nameserver '194.168.4.100'
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   nameserver '194.168.8.100'
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info>   domain name 'cable.virginmedia.net'
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
21/02/2011 09:40:12	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
21/02/2011 09:40:12	D7-K	dhclient	bound to 192.168.7.103 -- renewal in 42444 seconds.
21/02/2011 09:40:12	D7-K	avahi-daemon[1016]	Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.7.103.
21/02/2011 09:40:12	D7-K	avahi-daemon[1016]	New relevant interface eth1.IPv4 for mDNS.
21/02/2011 09:40:12	D7-K	avahi-daemon[1016]	Registering new address record for 192.168.7.103 on eth1.IPv4.
21/02/2011 09:40:13	D7-K	NetworkManager[1018]	<info> (eth1): device state change: 7 -> 8 (reason 0)
21/02/2011 09:40:13	D7-K	NetworkManager[1018]	<info> Policy set 'KLinkSys' (eth1) as default for IPv4 routing and DNS.
21/02/2011 09:40:13	D7-K	NetworkManager[1018]	<info> Activation (eth1) successful, device activated.
21/02/2011 09:40:13	D7-K	NetworkManager[1018]	<info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
21/02/2011 09:40:14	D7-K	ntpdate[3013]	adjust time server 91.189.94.4 offset 0.015981 sec
21/02/2011 09:41:27	D7-K	kernel	[  977.352830] lo: Disabled Privacy Extensions
21/02/2011 10:00:28	D7-K	sudo	pam_sm_authenticate: Called
21/02/2011 10:00:28	D7-K	sudo	pam_sm_authenticate: username = [dark7man]
21/02/2011 10:00:28	D7-K	sudo	pam_sm_authenticate: /home/dark7man is already mounted
21/02/2011 10:05:38	D7-K	ntfs-3g[3503]	Version 2010.8.8 external FUSE 28
21/02/2011 10:05:38	D7-K	ntfs-3g[3503]	Mounted /dev/sda1 (Read-Write, label "SYSTEM", NTFS 3.1)
21/02/2011 10:05:38	D7-K	ntfs-3g[3503]	Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=0,gid=0,dmask=0077,fmask=0177
21/02/2011 10:05:38	D7-K	ntfs-3g[3503]	Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sda1,blkdev,blksize=4096,default_permissions
21/02/2011 10:05:38	D7-K	ntfs-3g[3503]	Global ownership and permissions enforced, configuration type 1
21/02/2011 10:05:40	D7-K	ntfs-3g[3511]	Version 2010.8.8 external FUSE 28
21/02/2011 10:05:40	D7-K	ntfs-3g[3511]	Mounted /dev/sda2 (Read-Write, label "Windows7", NTFS 3.1)
21/02/2011 10:05:40	D7-K	ntfs-3g[3511]	Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=0,gid=0,dmask=0077,fmask=0177
21/02/2011 10:05:40	D7-K	ntfs-3g[3511]	Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096,default_permissions
21/02/2011 10:05:40	D7-K	ntfs-3g[3511]	Global ownership and permissions enforced, configuration type 1
21/02/2011 10:13:10	D7-K	wpa_supplicant[1079]	WPA: Group rekeying completed with 00:16:b6:41:60:12 [GTK=CCMP]
21/02/2011 10:13:10	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  completed -> group handshake
21/02/2011 10:13:10	D7-K	NetworkManager[1018]	<info> (eth1): supplicant connection state:  group handshake -> completed

---

### Post by Dark7man on 2011-02-21
I pasted the thread above twice somehow... deleted the duplicate

---

### Post by inobe on 2011-02-21
what version of kde is that sporting?

sounds like you grabbed some updates from that ppa, maybe it upgraded kde to testing packages!

---

### Post by inobe on 2011-02-21
i have to go, just encase, you may be able to fix it upgrading to stable version.

[http://www.kubuntu.org/news/kde-sc-4.6](http://www.kubuntu.org/news/kde-sc-4.6)

---

