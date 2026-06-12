---
title: "Boot time"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Aitashan on 2011-07-28
how to reduce the boot of Ubuntu 11.04 it takes about 2 and a half minute to boot up completely is this normal or is there is fix for this

---

### Post by beew on 2011-07-28
> **Aitashan said:**
> how to reduce the boot of Ubuntu 11.04 it takes about 2 and a half minute to boot up completely is this normal or is there is fix for this

It is not normal. It takes a bit longer than 10.10 and 10.04 (to load Unity) but shouldn't take more than 30 -40s (my 10.10 installations boot in about 10s -25s depending on the computer)

What are your computer's specs? How did you install 11.04? (ie a fresh install or an upgrade?)

---

### Post by Gone fishing on 2011-07-28
I had a problem with EDID errors slowing the boot process with Natty. I wonder what dmesg will show you?

---

### Post by redbikemaster on 2011-07-28
Sorry, but I'd like to know what EDID errors are. Also, what is dmesg?

---

### Post by Aitashan on 2011-07-28
> **beew said:**
> It is not normal. It takes a bit longer than 10.10 and 10.04 (to load Unity) but shouldn't take more than 30 -40s (my 10.10 installations boot in about 10s -25s depending on the computer)

What are your computer's specs? How did you install 11.04? (ie a fresh install or an upgrade?)

i did a fresh install using a usb and i am running pentium 4 2.80ghz 1 gb ram and unity 2d cuz i have the native intel built in VGA graphics card

---

### Post by konsolelover on 2011-07-28
P4+ 1 gb+ Unity can slow down your system but not that much. Install bootchart

---

### Post by Aitashan on 2011-07-28
> **konsolelover said:**
> P4+ 1 gb+ Unity can slow down your system but not that much. Install bootchart

how do i use the boot chart

---

### Post by robgraves on 2011-07-28
open a terminal and type in:
```
sudo apt-get install bootchart
```
then reboot the machine

---

### Post by konsolelover on 2011-07-28
for installing bootchart
```
sudo apt-get install bootchart
```
After you computer boots, you will find the boot charts in this folder:
```
/var/log/bootchart
```

---

### Post by Gone fishing on 2011-07-28
Sorry open a terminal and type dmesg.

This will display any kernel messages including errors

[http://www.linfo.org/dmesg.html](http://www.linfo.org/dmesg.html)

My EDID errors were due to my screen not being properly supported and it did make the boot process very, very slow.

---

### Post by Aitashan on 2011-07-28
> **Gone fishing said:**
> Sorry open a terminal and type dmesg.

This will display any kernel messages including errors

[http://www.linfo.org/dmesg.html](http://www.linfo.org/dmesg.html)

My EDID errors were due to my screen not being properly supported and it did make the boot process very, very slow.

this is what i got
```

([    0.200909] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.200917] pci_root PNP0A03:00: host bridge window [mem 0x3f000000-0xffffffff] (ignored)
[    0.200941] pci 0000:00:00.0: [8086:2570] type 0 class 0x000600
[    0.200950] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.200965] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.201038] pci 0000:00:02.0: [8086:2572] type 0 class 0x000300
[    0.201060] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.201074] pci 0000:00:02.0: reg 14: [mem 0xffa80000-0xffafffff]
[    0.201088] pci 0000:00:02.0: reg 18: [io  0xec00-0xec07]
[    0.201153] pci 0000:00:03.0: [8086:2573] type 1 class 0x000604
[    0.201204] pci 0000:00:06.0: [8086:2576] type 0 class 0x000880
[    0.201221] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.201335] pci 0000:00:1d.0: [8086:24d2] type 0 class 0x000c03
[    0.201392] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.201438] pci 0000:00:1d.1: [8086:24d4] type 0 class 0x000c03
[    0.201495] pci 0000:00:1d.1: reg 20: [io  0xc800-0xc81f]
[    0.201541] pci 0000:00:1d.2: [8086:24d7] type 0 class 0x000c03
[    0.201598] pci 0000:00:1d.2: reg 20: [io  0xcc00-0xcc1f]
[    0.201644] pci 0000:00:1d.3: [8086:24de] type 0 class 0x000c03
[    0.201702] pci 0000:00:1d.3: reg 20: [io  0xd000-0xd01f]
[    0.201761] pci 0000:00:1d.7: [8086:24dd] type 0 class 0x000c03
[    0.201791] pci 0000:00:1d.7: reg 10: [mem 0xffa7f400-0xffa7f7ff]
[    0.201904] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.201913] pci 0000:00:1d.7: PME# disabled
[    0.201939] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.201997] pci 0000:00:1f.0: [8086:24d0] type 0 class 0x000601
[    0.202079] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.202108] pci 0000:00:1f.1: [8086:24db] type 0 class 0x000101
[    0.202128] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.202144] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.202159] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.202175] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.202191] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.202206] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.202244] pci 0000:00:1f.2: [8086:24d1] type 0 class 0x000101
[    0.202263] pci 0000:00:1f.2: reg 10: [io  0xe800-0xe807]
[    0.202278] pci 0000:00:1f.2: reg 14: [io  0xe400-0xe403]
[    0.202292] pci 0000:00:1f.2: reg 18: [io  0xe000-0xe007]
[    0.202307] pci 0000:00:1f.2: reg 1c: [io  0xdc00-0xdc03]
[    0.202321] pci 0000:00:1f.2: reg 20: [io  0xd800-0xd80f]
[    0.202370] pci 0000:00:1f.3: [8086:24d3] type 0 class 0x000c05
[    0.202431] pci 0000:00:1f.3: reg 20: [io  0xd400-0xd41f]
[    0.202489] pci 0000:00:1f.5: [8086:24d5] type 0 class 0x000401
[    0.202542] pci 0000:00:1f.5: reg 18: [mem 0xffa7fc00-0xffa7fdff]
[    0.202558] pci 0000:00:1f.5: reg 1c: [mem 0xffa7f800-0xffa7f8ff]
[    0.202609] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.202618] pci 0000:00:1f.5: PME# disabled
[    0.202657] pci 0000:02:01.0: [8086:1019] type 0 class 0x000200
[    0.202680] pci 0000:02:01.0: reg 10: [mem 0xff8e0000-0xff8fffff]
[    0.202702] pci 0000:02:01.0: reg 18: [io  0xbc00-0xbc1f]
[    0.202758] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.202766] pci 0000:02:01.0: PME# disabled
[    0.202816] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.202825] pci 0000:00:03.0:   bridge window [io  0xb000-0xbfff]
[    0.202833] pci 0000:00:03.0:   bridge window [mem 0xff800000-0xff8fffff]
[    0.202842] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202910] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.202920] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.202936] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.202951] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202964] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.202973] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.202992] pci_bus 0000:00: on NUMA node 0
[    0.203004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.203158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.203225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.209850] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.209991] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.210129] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.210275] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.210410] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.210546] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.210694] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.210831] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.211109] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.211140] vgaarb: loaded
[    0.211653] SCSI subsystem initialized
[    0.211851] libata version 3.00 loaded.
[    0.211985] usbcore: registered new interface driver usbfs
[    0.212048] usbcore: registered new interface driver hub
[    0.212121] usbcore: registered new device driver usb
[    0.212438] wmi: Mapper loaded
[    0.212443] PCI: Using ACPI for IRQ routing
[    0.212453] PCI: pci_cache_line_size set to 64 bytes
[    0.212575] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.212582] reserve RAM buffer: 000000003ef30000 - 000000003fffffff 
[    0.212845] NetLabel: Initializing
[    0.212850] NetLabel:  domain hash size = 128
[    0.212855] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212879] NetLabel:  unlabeled traffic allowed by default
[    0.213084] hpet clockevent registered
[    0.213091] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.213100] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.213112] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.216774] Switching to clocksource hpet
[    0.219067] Switched to NOHz mode on CPU #0
[    0.219170] Switched to NOHz mode on CPU #1
[    0.236336] AppArmor: AppArmor Filesystem Enabled
[    0.236399] pnp: PnP ACPI init
[    0.236449] ACPI: bus type pnp registered
[    0.236652] pnp 00:00: [bus 00-ff]
[    0.236663] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.236674] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.236681] pnp 00:00: [io  0x0d00-0xffff window]
[    0.236688] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.236696] pnp 00:00: [mem 0x00000000 window]
[    0.236704] pnp 00:00: [mem 0x3f000000-0xffffffff window]
[    0.236841] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.236955] pnp 00:01: [dma 4]
[    0.236960] pnp 00:01: [io  0x0000-0x000f]
[    0.236966] pnp 00:01: [io  0x0081-0x0083]
[    0.236971] pnp 00:01: [io  0x0087]
[    0.236976] pnp 00:01: [io  0x0089-0x008b]
[    0.236981] pnp 00:01: [io  0x008f]
[    0.236986] pnp 00:01: [io  0x00c0-0x00df]
[    0.237060] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.237088] pnp 00:02: [io  0x0070-0x0071]
[    0.237109] pnp 00:02: [irq 8]
[    0.237208] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.237287] pnp 00:03: [io  0x0060]
[    0.237292] pnp 00:03: [io  0x0064]
[    0.237304] pnp 00:03: [irq 1]
[    0.237389] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.237674] pnp 00:04: [io  0x0061]
[    0.237779] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.237804] pnp 00:05: [io  0x00f0-0x00ff]
[    0.237821] pnp 00:05: [irq 13]
[    0.237900] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.238062] pnp 00:06: [io  0x03f0-0x03f1]
[    0.238068] pnp 00:06: [io  0x03f2-0x03f3]
[    0.238074] pnp 00:06: [io  0x03f4-0x03f5]
[    0.238078] pnp 00:06: [io  0x03f7]
[    0.238090] pnp 00:06: [irq 6]
[    0.238095] pnp 00:06: [dma 2]
[    0.238242] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.238608] pnp 00:07: [io  0x03f8-0x03ff]
[    0.238622] pnp 00:07: [irq 4]
[    0.238810] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.239441] pnp 00:08: [io  0x0378-0x037f]
[    0.239447] pnp 00:08: [io  0x0778-0x077f]
[    0.239461] pnp 00:08: [irq 7]
[    0.239467] pnp 00:08: [dma 3]
[    0.239721] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.239753] pnp 00:09: [io  0x0010-0x001f]
[    0.239759] pnp 00:09: [io  0x0022-0x003f]
[    0.239764] pnp 00:09: [io  0x0044-0x005f]
[    0.239769] pnp 00:09: [io  0x0062-0x0063]
[    0.239775] pnp 00:09: [io  0x0065-0x006f]
[    0.239780] pnp 00:09: [io  0x0072-0x007f]
[    0.239784] pnp 00:09: [io  0x0080]
[    0.239789] pnp 00:09: [io  0x0084-0x0086]
[    0.239794] pnp 00:09: [io  0x0088]
[    0.239799] pnp 00:09: [io  0x008c-0x008e]
[    0.239805] pnp 00:09: [io  0x0090-0x009f]
[    0.239814] pnp 00:09: [io  0x00a2-0x00bf]
[    0.239820] pnp 00:09: [io  0x00e0-0x00ef]
[    0.239825] pnp 00:09: [io  0x04d0-0x04d1]
[    0.239990] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.240040] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.240187] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.240196] pnp 00:0a: [mem 0xfff80000-0xffffffff]
[    0.240326] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.240680] pnp 00:0b: [io  0x0400-0x047f]
[    0.240689] pnp 00:0b: [io  0x0000-0xffffffff disabled]
[    0.240698] pnp 00:0b: [io  0x0680-0x06ff]
[    0.240708] pnp 00:0b: [io  0x0500-0x053f]
[    0.240715] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.240724] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.240731] pnp 00:0b: [mem 0xfed20000-0xfed9ffff]
[    0.240885] system 00:0b: [io  0x0400-0x047f] has been reserved
[    0.240892] system 00:0b: [io  0x0680-0x06ff] has been reserved
[    0.240899] system 00:0b: [io  0x0500-0x053f] has been reserved
[    0.240908] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.240915] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.240922] system 00:0b: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.240931] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241401] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.241407] pnp 00:0c: [mem 0x000c0000-0x000dffff]
[    0.241413] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.241419] pnp 00:0c: [mem 0x00100000-0x3effffff]
[    0.241425] pnp 00:0c: [mem 0x00000000-0xffffffff disabled]
[    0.241577] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.241586] system 00:0c: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.241593] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.241600] system 00:0c: [mem 0x00100000-0x3effffff] could not be reserved
[    0.241609] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.242016] pnp: PnP ACPI: found 13 devices
[    0.242022] ACPI: ACPI bus type pnp unregistered
[    0.242030] PnPBIOS: Disabled by ACPI PNP
[    0.281308] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40000000-0x400003ff]
[    0.281322] pci 0000:00:1f.1: BAR 5: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff])
[    0.281331] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.281339] pci 0000:00:03.0:   bridge window [io  0xb000-0xbfff]
[    0.281349] pci 0000:00:03.0:   bridge window [mem 0xff800000-0xff8fffff]
[    0.281357] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    0.281368] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.281373] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.281382] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.281390] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.281420] pci 0000:00:1e.0: setting latency timer to 64
[    0.281428] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.281434] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.281441] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.281447] pci_bus 0000:02: resource 1 [mem 0xff800000-0xff8fffff]
[    0.281454] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.281460] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.281541] NET: Registered protocol family 2
[    0.281697] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.282303] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.283408] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.283987] TCP: Hash tables configured (established 131072 bind 65536)
[    0.284067] TCP reno registered
[    0.284087] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.284126] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.284431] NET: Registered protocol family 1
[    0.284474] pci 0000:00:02.0: Boot video device
[    0.284632] PCI: CLS 64 bytes, default 64
[    0.284946] cpufreq-nforce2: No nForce2 chipset.
[    0.285266] audit: initializing netlink socket (disabled)
[    0.285289] type=2000 audit(1311849330.284:1): initialized
[    0.298788] highmem bounce pool size: 64 pages
[    0.298801] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.303273] VFS: Disk quotas dquot_6.5.2
[    0.303434] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.305180] fuse init (API version 7.16)
[    0.305446] msgmni has been set to 1704
[    0.306098] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.306170] io scheduler noop registered
[    0.306174] io scheduler deadline registered
[    0.306212] io scheduler cfq registered (default)
[    0.306570] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.306628] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.307010] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.368091] ACPI: Sleep Button [SLPB]
[    0.368259] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.368272] ACPI: Power Button [PWRF]
[    0.368577] ACPI: acpi_idle registered with cpuidle
[    0.370766] ERST: Table is not found!
[    0.370871] isapnp: Scanning for PnP cards...
[    0.370938] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.391291] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.616580] Freeing initrd memory: 12556k freed
[    0.725117] isapnp: No Plug & Play device found
[    0.751459] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.751898] Linux agpgart interface v0.103
[    0.752043] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    0.752078] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.752279] agpgart-intel 0000:00:00.0: detected 16384K stolen memory
[    0.752453] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    0.754558] brd: module loaded
[    0.755527] loop: module loaded
[    0.755709] i2c-core: driver [adp5520] using legacy suspend method
[    0.755712] i2c-core: driver [adp5520] using legacy resume method
[    0.755903] ata_piix 0000:00:1f.1: version 2.13
[    0.755922] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.755949] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.756051] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.756671] scsi0 : ata_piix
[    0.756847] scsi1 : ata_piix
[    0.758284] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.758289] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.758338] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.758352] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.758439] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.758919] scsi2 : ata_piix
[    0.759047] scsi3 : ata_piix
[    0.760088] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 18
[    0.760093] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 18
[    0.760881] Fixed MDIO Bus: probed
[    0.760952] PPP generic driver version 2.4.2
[    0.761066] tun: Universal TUN/TAP device driver, 1.6
[    0.761070] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.761250] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.761306] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.761332] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.761338] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.761409] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.761508] ehci_hcd 0000:00:1d.7: debug port 1
[    0.765389] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.765416] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7f400
[    0.780021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.780246] hub 1-0:1.0: USB hub found
[    0.780254] hub 1-0:1.0: 8 ports detected
[    0.780421] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.780450] uhci_hcd: USB Universal Host Controller Interface driver
[    0.780528] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.780540] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.780546] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.780624] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.780709] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c400
[    0.780928] hub 2-0:1.0: USB hub found
[    0.780936] hub 2-0:1.0: 2 ports detected
[    0.781055] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.781066] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.781071] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.781143] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.781221] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.781430] hub 3-0:1.0: USB hub found
[    0.781438] hub 3-0:1.0: 2 ports detected
[    0.781546] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.781556] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.781561] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.781634] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.784070] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cc00
[    0.784299] hub 4-0:1.0: USB hub found
[    0.784307] hub 4-0:1.0: 2 ports detected
[    0.784418] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784428] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.784433] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.784501] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.784568] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d000
[    0.784783] hub 5-0:1.0: USB hub found
[    0.784790] hub 5-0:1.0: 2 ports detected
[    0.784992] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.784996] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.785814] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.786010] mousedev: PS/2 mouse device common for all mice
[    0.786238] rtc_cmos 00:02: RTC can wake from S4
[    0.786376] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.786405] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.786556] device-mapper: uevent: version 1.0.3
[    0.786692] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.786840] device-mapper: multipath: version 1.2.0 loaded
[    0.786847] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.786979] EISA: Probing bus 0 at eisa.0
[    0.787022] EISA: Detected 0 cards.
[    0.787125] cpuidle: using governor ladder
[    0.787131] cpuidle: using governor menu
[    0.787668] TCP cubic registered
[    0.787882] NET: Registered protocol family 10
[    0.788964] NET: Registered protocol family 17
[    0.788999] Registering the dns_resolver key type
[    0.789090] Using IPI No-Shortcut mode
[    0.789273] PM: Hibernation image not present or could not be loaded.
[    0.789294] registered taskstats version 1
[    0.789542]   Magic number: 3:200:579
[    0.789609] pci_bus 0000:00: hash matches
[    0.789663] rtc_cmos 00:02: setting system clock to 2011-07-28 10:35:31 UTC (1311849331)
[    0.789669] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.789671] EDD information not available.
[    0.807191] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.912547] ata2.00: ATAPI: CREATIVE DVD-ROM DVD1620E, VER .20Q, max UDMA/33
[    0.937734] ata1.00: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[    0.937741] ata1.00: 240121728 sectors, multi 16: LBA 
[    0.944202] ata2.00: configured for UDMA/33
[    0.952329] ata1.00: configured for UDMA/100
[    0.952530] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[    0.952860] sd 0:0:0:0: [sda] 240121728 512-byte logical blocks: (122 GB/114 GiB)
[    0.952891] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.953003] sd 0:0:0:0: [sda] Write Protect is off
[    0.953010] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.953079] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.953384] scsi 1:0:0:0: CD-ROM            CREATIVE DVD-ROM DVD1620E .20Q PQ: 0 ANSI: 5
[    0.954311] sr0: scsi3-mmc drive: 0x/1x cd/rw xa/form2 cdda tray
[    0.954317] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.954520] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.954642] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.020122]  sda: sda1 sda2 < sda5 >
[    1.020698] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.020760] Freeing unused kernel memory: 700k freed
[    1.021512] Write protecting the kernel text: 5192k
[    1.021605] Write protecting the kernel read-only data: 2148k
[    1.098518] <30>udev[86]: starting version 167
[    1.276061] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.284109] Refined TSC clocksource calibration: 2792.999 MHz.
[    1.284122] Switching to clocksource tsc
[    1.355346] Floppy drive(s): fd0 is 1.44M
[    1.365445] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.365454] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.365550] e1000 0000:02:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.365569] e1000 0000:02:01.0: setting latency timer to 64
[    1.371292] FDC 0 is a National Semiconductor PC87306
[    1.483736] input: HID 04b3:3108 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[    1.484505] generic-usb 0003:04B3:3108.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:3108] on usb-0000:00:1d.2-1/input0
[    1.484562] usbcore: registered new interface driver usbhid
[    1.484568] usbhid: USB HID core driver
[    1.589704] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.589710] EXT4-fs (sda1): write access will be enabled during recovery
[    1.795141] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:11:11:84:04:dc
[    1.795155] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.402956] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.402979] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3014731
[    5.403081] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3014730
[    5.403158] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2884524
[    5.403190] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2884617
[    5.403217] EXT4-fs (sda1): 4 orphan inodes deleted
[    5.403221] EXT4-fs (sda1): recovery complete
[    6.020388] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.125618] Adding 1028092k swap on /dev/sda5.  Priority:-1 extents:1 across:1028092k 
[    8.164324] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.001571] <30>udev[308]: starting version 167
[   10.742721] type=1400 audit(1311849341.447:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=491 comm="apparmor_parser"
[   10.743848] type=1400 audit(1311849341.447:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[   10.744481] type=1400 audit(1311849341.451:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[   11.457299] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.551136] lp: driver loaded but no devices found
[   11.596812] parport_pc 00:08: reported by Plug and Play ACPI
[   11.596892] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.632336] intel_rng: Firmware space is locked read-only. If you can't or
[   11.632340] intel_rng: don't want to disable this in firmware setup, and if
[   11.632344] intel_rng: you are certain that your system has a functional
[   11.632348] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   11.645381] ppdev: user-space parallel port driver
[   11.695442] lp0: using parport0 (interrupt-driven).
[   12.176621] [drm] Initialized drm 1.1.0 20060810
[   12.735507] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.735520] i915 0000:00:02.0: setting latency timer to 64
[   12.757204] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.757211] [drm] Driver supports precise vblank timestamp query.
[   12.770411] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.770811] [drm] initialized overlay support
[   12.903392] fbcon: inteldrmfb (fb0) is primary device
[   12.903642] Console: switching to colour frame buffer device 160x64
[   12.903711] fb0: inteldrmfb frame buffer device
[   12.903717] drm: registered panic notifier
[   12.904231] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.036965] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.037018] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   13.472050] intel8x0_measure_ac97_clock: measured 54568 usecs (2629 samples)
[   13.472055] intel8x0: clocking to 48000
[   16.625688] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.628449] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   16.628670] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.788572] type=1400 audit(1311849347.495:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=784 comm="apparmor_parser"
[   16.789562] type=1400 audit(1311849347.495:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=784 comm="apparmor_parser"
[   23.758898] type=1400 audit(1311849354.463:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
[   23.759742] type=1400 audit(1311849354.463:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
[   23.760686] type=1400 audit(1311849354.467:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
[   23.847407] type=1400 audit(1311849354.551:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=857 comm="apparmor_parser"
[   23.861885] type=1400 audit(1311849354.567:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=863 comm="apparmor_parser"
[   23.863116] type=1400 audit(1311849354.567:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=863 comm="apparmor_parser"
[   23.896727] type=1400 audit(1311849354.603:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=864 comm="apparmor_parser"
[   24.175707] type=1400 audit(1311849354.879:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=859 comm="apparmor_parser"
[   24.187104] type=1400 audit(1311849354.891:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=859 comm="apparmor_parser"
[   24.193785] type=1400 audit(1311849354.899:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=859 comm="apparmor_parser"
[   27.496022] eth0: no IPv6 routers present
[   28.090120] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   40.675180] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  668.436027] end_request: I/O error, dev fd0, sector 0
[  678.480027] end_request: I/O error, dev fd0, sector 0
[  679.696035] end_request: I/O error, dev fd0, sector 0
[  680.960043] end_request: I/O error, dev fd0, sector 0)

```

---

### Post by Aitashan on 2011-07-28
> **konsolelover said:**
> for installing bootchart
```
sudo apt-get install bootchart
```After you computer boots, you will find the boot charts in this folder:
```
/var/log/bootchart
```

this is what i got

---

### Post by Aitashan on 2011-07-28
now what guyz how do i make my boot faster

---

### Post by Gone fishing on 2011-07-28
the final error > end_request: I/O error, dev fd0, sector 0) is something to do with a floppy drive. I,m not sure, but do you have a floppy drive? it is possible that the boot process is being slowed down by trying to access a floppy drive. If you have a floppy drive can you disable it in BIOS?

---

### Post by Gone fishing on 2011-07-28
I found this:

>  **Common kernel problems** [....]

**Boot pauses probing floppy device**

On some machines (mostly laptops with removable floppy drives), boot will pause while the (non-existant) floppy device is probed. A series of the following messages will appear:

end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0

[http://fedoraproject.org/wiki/Common_kernel_problems#Boot_pauses_probing_floppy_device](http://fedoraproject.org/wiki/Common_kernel_problems#Boot_pauses_probing_floppy_device)

Disable the floppy in BIOS if you don't have a floppy then the kernel can be prevented from trying to access the non existent floppy by adding to the boot options floppy.allowed_drive_mask=0

---

### Post by Aitashan on 2011-07-29
> **Gone fishing said:**
> I found this:



[http://fedoraproject.org/wiki/Common_kernel_problems#Boot_pauses_probing_floppy_device](http://fedoraproject.org/wiki/Common_kernel_problems#Boot_pauses_probing_floppy_device)

Disable the floppy in BIOS if you don't have a floppy then the kernel can be prevented from trying to access the non existent floppy by adding to the boot options floppy.allowed_drive_mask=0

thank you for your replies but can you please simplify your solution given

---

### Post by Aitashan on 2011-07-29
i don't know on how to get into bios or the line you said

---

### Post by Gone fishing on 2011-07-29
The BIOs is the firmware on the PC usually if you press del or F3 or F11 (depending on the PC) when the PC is starting up this will allow you to get into the BIOs setup. The instructions should be in your PCs instruction book.

Try changing the setting in BIOs before thinking about changing the boot options.

---

### Post by Aitashan on 2011-07-29
> **Gone fishing said:**
> The BIOs is the firmware on the PC usually if you press del or F3 or F11 (depending on the PC) when the PC is starting up this will allow you to get into the BIOs setup. The instructions should be in your PCs instruction book.

Try changing the setting in BIOs before thinking about changing the boot options.
 
i am sorry but i dont think changing from the bios is a help could you please help me edit the boot options

---

### Post by Gone fishing on 2011-07-29
Edit the /etc/default/grub file and add the kernel parameter to the 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line

Open a terminal and paste the following command

```
gksu gedit /etc/default/grub
```

make the line look like

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash floppy.allowed_drive_mask=0" 

Then run in a terminal ```
sudo update-grub
```

---

### Post by konsolelover on 2011-07-29
+1 to GoneFishing
n also u can check boot order ,may be your system goes for the other options before getting the right one..ain't a Linux expert n had this problem too..my system used to boot in 50-55 seconds..u can speed up booting up process in any OS by avoiding unnecessary services at startup..using Ubuntu-Classic instead of Unity can also help u out ...

---

### Post by Aitashan on 2011-07-31
thank you guyz for all your help especially to you gone fishing

---

### Post by Aitashan on 2011-07-31
how can i delete boot chart files it says i am not owner and my boot time increased to more 15 sec i think i did something wrong with the grub boot menu is it possible to restore the previous grub

---

### Post by Gone fishing on 2011-07-31
OK is it now booting as it should?

You can delete something that you don't own by getting root privileges this is done using the sudo or gksu command. Open a terminal and type > gksu nautilus   go to the file you want to delete and delete it.

To update grub simply run ```
sudo update-grub
``` this fill rebuild grub depending on what is needed and in your /etc/default/grub file.

---

### Post by Aitashan on 2011-07-31
thank you real zippy you really did the trick got my boot back to 36 sec thanks a lot

---

### Post by Gone fishing on 2011-07-31
Your /etc/default/grub should look as below to edit it ```
sudo gedit /etc/default/grub
```

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash floppy.allowed_drive_mask=0"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

for you the important line is > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash floppy.allowed_drive_mask=0"

then ```
sudo update-grub
```  

This should work and remove the floppy boot errors it wont make it boot slower - I checked it on my box.

---

### Post by Gone fishing on 2011-07-31
Ignore my last post and mark as solved 

Thanks

---

