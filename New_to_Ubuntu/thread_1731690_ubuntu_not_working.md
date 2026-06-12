---
title: "ubuntu not working"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-04-17
hey have an acer aspire AM1610-U1202 A, and i am having trouble with booting maveric 10.10. during installation it kept freezing and says too much work irq17. what does this mean? should i not have installed this version on to my aspire. this is my first run of ubuntu. i would really love to get ubuntu up and running smoothly i played around with it for about three days before all this started to happen again. thx

---

### Post by josephmills on 2011-04-17
Hi there Josh and welcome to ubuntu forums. after you downloaded ubuntu 10.10 did you check the md5sum number also where did you get it (link) well thanks and hope to hear from you soon


**EDIT:** is this a dual boot also?

---

### Post by joshcanfield on 2011-04-17
md5sum um no i dont know what that is :(...im new to linux. no this is not a dual boot. i got 10.10 from ubuntu's download screen. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download).

edit: also i did run the mem test and i booted from the cd to see if i liked it and all that came up fine with no problems

---

### Post by samvkampen on 2011-04-17
Hmm.... this PC should be perfectly capable of running Ubuntu. If it says IRQ#17 disabled (or something like that), the device connected to IRQ #17 is disabled. I do not have enough information about it to know what has happened, but try to run dmesg, then post the output here. There might be something interesting inside ;) (_Can_ you run dmesg, or does it just freeze?)

---

### Post by josephmills on 2011-04-17
can you run it as a live cd right now? this should help with the whole md5sum    
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by joshcanfield on 2011-04-17
what is dmsg? ill give it a try if i know what it is. ill try what the link to md5sum and see what is says

---

### Post by samvkampen on 2011-04-17
It's a dump of kernel output, all information on what happens with devices is in there (afaik). You can look at this example:

> ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17cnxthsf_NVM_Open: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 will retry later..
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!
cnxthsf_NVM_WriteFlushList: cannot create instance 0-PCI-8086:24c6-14f1:5422: err=-2 failed again!

This is some dmesg output from someone that had an IRQ problem too.

---

### Post by joshcanfield on 2011-04-17
ok this is what the dmesg said

                     p { margin-bottom: 0.08in; }  [    0.190295] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
 [    0.190300] pci 0000:00:03.3: PME# disabled
 [    0.190341] pci 0000:00:04.0: reg 10: [mem 0xfdffc000-0xfdffc07f]
 [    0.190350] pci 0000:00:04.0: reg 14: [io  0xfe00-0xfe7f]
 [    0.190399] pci 0000:00:04.0: supports D1 D2
 [    0.190402] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
 [    0.190407] pci 0000:00:04.0: PME# disabled
 [    0.190442] pci 0000:00:05.0: reg 10: [io  0xfd00-0xfd07]
 [    0.190451] pci 0000:00:05.0: reg 14: [io  0xfc00-0xfc03]
 [    0.190459] pci 0000:00:05.0: reg 18: [io  0xfb00-0xfb07]
 [    0.190468] pci 0000:00:05.0: reg 1c: [io  0xfa00-0xfa03]
 [    0.190476] pci 0000:00:05.0: reg 20: [io  0xf900-0xf90f]
 [    0.190512] pci 0000:00:05.0: PME# supported from D3cold
 [    0.190518] pci 0000:00:05.0: PME# disabled
 [    0.190619] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
 [    0.190625] pci 0000:00:06.0: PME# disabled
 [    0.190679] pci 0000:00:0c.0: reg 10: [mem 0xfdffb000-0xfdffb7ff]
 [    0.190688] pci 0000:00:0c.0: reg 14: [mem 0xfdff4000-0xfdff7fff]
 [    0.190741] pci 0000:00:0c.0: supports D1 D2
 [    0.190744] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot
 [    0.190750] pci 0000:00:0c.0: PME# disabled
 [    0.190789] pci 0000:00:0d.0: reg 10: [mem 0xfdffa000-0xfdffafff]
 [    0.190799] pci 0000:00:0d.0: reg 14: [io  0x0000-0x00ff]
 [    0.190852] pci 0000:00:0d.0: PME# supported from D0 D3hot D3cold
 [    0.190858] pci 0000:00:0d.0: PME# disabled
 [    0.190886] pci 0000:00:0e.0: reg 10: [mem 0xfdff8000-0xfdff9fff]
 [    0.190960] pci 0000:00:0f.0: reg 10: [mem 0xfdff0000-0xfdff3fff]
 [    0.191018] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
 [    0.191024] pci 0000:00:0f.0: PME# disabled
 [    0.191148] pci 0000:00:1f.0: PME# supported from D0 D3hot D3cold
 [    0.191154] pci 0000:00:1f.0: PME# disabled
 [    0.191212] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
 [    0.191220] pci 0000:01:00.0: reg 14: [mem 0xfdde0000-0xfddfffff]
 [    0.191227] pci 0000:01:00.0: reg 18: [io  0xef00-0xef7f]
 [    0.191266] pci 0000:01:00.0: supports D1 D2
 [    0.191311] pci 0000:00:01.0: PCI bridge to [bus 01-01]
 [    0.191317] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
 [    0.191323] pci 0000:00:01.0:   bridge window [mem 0xfdd00000-0xfddfffff]
 [    0.191329] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
 [    0.191396] pci 0000:00:06.0: PCI bridge to [bus 02-02]
 [    0.191405] pci 0000:00:06.0:   bridge window [io  0xd000-0xdfff]
 [    0.191411] pci 0000:00:06.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
 [    0.191420] pci 0000:00:06.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
 [    0.191484] pci 0000:00:1f.0: PCI bridge to [bus 03-03]
 [    0.191493] pci 0000:00:1f.0:   bridge window [io  0xc000-0xcfff]
 [    0.191499] pci 0000:00:1f.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
 [    0.191510] pci 0000:00:1f.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
 [    0.191531] pci_bus 0000:00: on NUMA node 0
 [    0.191538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
 [    0.233229] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
 [    0.233390] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
 [    0.233545] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
 [    0.233702] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
 [    0.233861] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
 [    0.234016] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
 [    0.234171] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
 [    0.234332] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
 [    0.234408] HEST: Table is not found!
 [    0.234533] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
 [    0.234538] vgaarb: loaded
 [    0.234796] SCSI subsystem initialized
 [    0.234920] libata version 3.00 loaded.
 [    0.234999] usbcore: registered new interface driver usbfs
 [    0.235019] usbcore: registered new interface driver hub
 [    0.235052] usbcore: registered new device driver usb
 [    0.235244] ACPI: WMI: Mapper loaded
 [    0.235247] PCI: Using ACPI for IRQ routing
 [    0.235251] PCI: pci_cache_line_size set to 64 bytes
 [    0.235352] reserve RAM buffer: 000000000009f400 - 000000000009ffff  
 [    0.235356] reserve RAM buffer: 0000000037ff0000 - 0000000037ffffff  
 [    0.235493] NetLabel: Initializing
 [    0.235497] NetLabel:  domain hash size = 128
 [    0.235499] NetLabel:  protocols = UNLABELED CIPSOv4
 [    0.235516] NetLabel:  unlabeled traffic allowed by default
 [    0.235560] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
 [    0.235567] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
 [    0.235574] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
 [    0.240061] Switching to clocksource tsc
 [    0.257134] AppArmor: AppArmor Filesystem Enabled
 [    0.257173] pnp: PnP ACPI init
 [    0.257210] ACPI: bus type pnp registered
 [    0.258115] pnp 00:01: disabling [io  0x0010-0x001f] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258121] pnp 00:01: disabling [io  0x0022-0x003f] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258125] pnp 00:01: disabling [io  0x0044-0x005f] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258129] pnp 00:01: disabling [io  0x0062-0x0063] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258134] pnp 00:01: disabling [io  0x0065-0x006f] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258138] pnp 00:01: disabling [io  0x0074-0x007f] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258142] pnp 00:01: disabling [io  0x0091-0x0093] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258147] pnp 00:01: disabling [io  0x00a2-0x00bf] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.258151] pnp 00:01: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:0d.0 BAR 1 [io  0x0000-0x00ff]
 [    0.262213] pnp: PnP ACPI: found 14 devices
 [    0.262217] ACPI: ACPI bus type pnp unregistered
 [    0.262223] PnPBIOS: Disabled by ACPI PNP
 [    0.262241] system 00:01: [io  0x04d0-0x04d1] has been reserved
 [    0.262245] system 00:01: [io  0x0800-0x0805] has been reserved
 [    0.262249] system 00:01: [io  0x0290-0x0297] has been reserved
 [    0.262253] system 00:01: [io  0x0880-0x088f] has been reserved
 [    0.262267] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
 [    0.262278] system 00:0d: [mem 0x000f0000-0x000fffff] could not be reserved
 [    0.262282] system 00:0d: [mem 0xfed00000-0xfed000ff] has been reserved
 [    0.262287] system 00:0d: [mem 0xfed30000-0xfed300ff] has been reserved
 [    0.262291] system 00:0d: [mem 0x37ff0000-0x37ffffff] could not be reserved
 [    0.262295] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
 [    0.262299] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
 [    0.262303] system 00:0d: [mem 0x00100000-0x37feffff] could not be reserved
 [    0.262307] system 00:0d: [mem 0xffee0000-0xffefffff] has been reserved
 [    0.262311] system 00:0d: [mem 0xfffe0000-0xfffeffff] has been reserved
 [    0.262315] system 00:0d: [mem 0xfec00000-0xfecfffff] could not be reserved
 [    0.262319] system 00:0d: [mem 0xfee00000-0xfeefffff] has been reserved
 [    0.299266] pci 0000:00:0d.0: BAR 1: assigned [io  0x1000-0x10ff]
 [    0.299275] pci 0000:00:0d.0: BAR 1: set to [io  0x1000-0x10ff] (PCI address [0x1000-0x10ff]
 [    0.299280] pci 0000:00:01.0: PCI bridge to [bus 01-01]
 [    0.299285] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
 [    0.299292] pci 0000:00:01.0:   bridge window [mem 0xfdd00000-0xfddfffff]
 [    0.299298] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
 [    0.299307] pci 0000:00:06.0: PCI bridge to [bus 02-02]
 [    0.299311] pci 0000:00:06.0:   bridge window [io  0xd000-0xdfff]
 [    0.299318] pci 0000:00:06.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
 [    0.299324] pci 0000:00:06.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
 [    0.299332] pci 0000:00:1f.0: PCI bridge to [bus 03-03]
 [    0.299338] pci 0000:00:1f.0:   bridge window [io  0xc000-0xcfff]
 [    0.299346] pci 0000:00:1f.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
 [    0.299352] pci 0000:00:1f.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
 [    0.299376] pci 0000:00:01.0: setting latency timer to 64
 [    0.299390] pci 0000:00:06.0: setting latency timer to 64
 [    0.299403] pci 0000:00:1f.0: setting latency timer to 64
 [    0.299408] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
 [    0.299412] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
 [    0.299416] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
 [    0.299419] pci_bus 0000:01: resource 1 [mem 0xfdd00000-0xfddfffff]
 [    0.299422] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
 [    0.299426] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
 [    0.299429] pci_bus 0000:02: resource 1 [mem 0xfdc00000-0xfdcfffff]
 [    0.299433] pci_bus 0000:02: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
 [    0.299436] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
 [    0.299440] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
 [    0.299443] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
 [    0.299497] NET: Registered protocol family 2
 [    0.299612] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
 [    0.300084] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
 [    0.301143] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
 [    0.301601] TCP: Hash tables configured (established 131072 bind 65536)
 [    0.301604] TCP reno registered
 [    0.301609] UDP hash table entries: 512 (order: 2, 16384 bytes)
 [    0.301624] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
 [    0.301755] NET: Registered protocol family 1
 [    0.359950] pci 0000:01:00.0: Boot video device
 [    0.359958] PCI: CLS 64 bytes, default 64
 [    0.360228] cpufreq-nforce2: No nForce2 chipset.
 [    0.360273] Scanning for low memory corruption every 60 seconds
 [    0.360441] audit: initializing netlink socket (disabled)
 [    0.360458] type=2000 audit(1136076991.356:1): initialized
 [    0.370807] highmem bounce pool size: 64 pages
 [    0.370815] HugeTLB registered 4 MB page size, pre-allocated 0 pages
 [    0.374359] VFS: Disk quotas dquot_6.5.2
 [    0.374446] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 [    0.375316] fuse init (API version 7.14)
 [    0.375444] msgmni has been set to 1712
 [    0.546871] Freeing initrd memory: 10524k freed
 [    0.562607] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
 [    0.562612] io scheduler noop registered
 [    0.562615] io scheduler deadline registered
 [    0.562636] io scheduler cfq registered (default)
 [    0.562797] pcieport 0000:00:06.0: setting latency timer to 64
 [    0.562847]   alloc irq_desc for 40 on node -1
 [    0.562849]   alloc kstat_irqs on node -1
 [    0.562865] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
 [    0.562954] pcieport 0000:00:1f.0: setting latency timer to 64
 [    0.563003]   alloc irq_desc for 41 on node -1
 [    0.563005]   alloc kstat_irqs on node -1
 [    0.563017] pcieport 0000:00:1f.0: irq 41 for MSI/MSI-X
 [    0.563130] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 [    0.563166] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
 [    0.563443] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
 [    0.563452] ACPI: Power Button [PWRB]
 [    0.563534] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
 [    0.563540] ACPI: Power Button [PWRF]
 [    0.563617] ACPI: Fan [FAN] (on)
 [    0.563918] ACPI: acpi_idle registered with cpuidle
 [    0.567895] thermal LNXTHERM:01: registered as thermal_zone0
 [    0.567910] ACPI: Thermal Zone [THRM] (55 C)
 [    0.568188] thermal LNXTHERM:02: registered as thermal_zone1
 [    0.568200] ACPI: Thermal Zone [SYST] (37 C)
 [    0.568294] ERST: Table is not found!
 [    0.568401] isapnp: Scanning for PnP cards...
 [    0.568595] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
 [    0.568707] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 [    0.568818] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 [    0.569246] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 [    0.569413] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 [    0.569559] serial 0000:00:0d.0: enabling device (0086 -> 0087)
 [    0.569568]   alloc irq_desc for 17 on node -1
 [    0.569571]   alloc kstat_irqs on node -1
 [    0.569580] serial 0000:00:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
 [    0.575559] brd: module loaded
 [    0.576347] loop: module loaded
 [    0.576654] pata_sis 0000:00:02.5: version 0.5.2
 [    0.576678]   alloc irq_desc for 16 on node -1
 [    0.576681]   alloc kstat_irqs on node -1
 [    0.576691] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 [    0.576835] scsi0 : pata_sis
 [    0.576954] scsi1 : pata_sis
 [    0.577801] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
 [    0.577805] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
 [    0.577851] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
 [    0.577886] pata_acpi 0000:00:05.0: setting latency timer to 64
 [    0.577903] pata_acpi 0000:00:05.0: PCI INT A disabled
 [    0.578363] Fixed MDIO Bus: probed
 [    0.578414] PPP generic driver version 2.4.2
 [    0.578475] tun: Universal TUN/TAP device driver, 1.6
 [    0.578478] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
 [    0.578594] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 [    0.578618]   alloc irq_desc for 22 on node -1
 [    0.578621]   alloc kstat_irqs on node -1
 [    0.578628] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
 [    0.578650] ehci_hcd 0000:00:03.3: setting latency timer to 64
 [    0.578655] ehci_hcd 0000:00:03.3: EHCI Host Controller
 [    0.578702] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
 [    0.578743] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
 [    0.578765] ehci_hcd 0000:00:03.3: irq 22, io mem 0xfdffd000
 [    0.588294] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
 [    0.588470] hub 1-0:1.0: USB hub found
 [    0.588478] hub 1-0:1.0: 8 ports detected
 [    0.588593] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 [    0.588611]   alloc irq_desc for 20 on node -1
 [    0.588614]   alloc kstat_irqs on node -1
 [    0.588621] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
 [    0.588635] ohci_hcd 0000:00:03.0: setting latency timer to 64
 [    0.588640] ohci_hcd 0000:00:03.0: OHCI Host Controller
 [    0.588692] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
 [    0.588718] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfdfff000
 [    0.646531] hub 2-0:1.0: USB hub found
 [    0.646539] hub 2-0:1.0: 4 ports detected
 [    0.646618]   alloc irq_desc for 21 on node -1
 [    0.646621]   alloc kstat_irqs on node -1
 [    0.646628] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
 [    0.646641] ohci_hcd 0000:00:03.1: setting latency timer to 64
 [    0.646645] ohci_hcd 0000:00:03.1: OHCI Host Controller
 [    0.646694] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
 [    0.646719] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfdffe000
 [    0.702637] hub 3-0:1.0: USB hub found
 [    0.702645] hub 3-0:1.0: 4 ports detected
 [    0.702732] uhci_hcd: USB Universal Host Controller Interface driver
 [    0.702858] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
 [    0.702862] PNP: PS/2 controller doesn't have KBD irq; using default 1
 [    0.703255] serio: i8042 KBD port at 0x60,0x64 irq 1
 [    0.703265] serio: i8042 AUX port at 0x60,0x64 irq 12
 [    0.703430] mice: PS/2 mouse device common for all mice
 [    0.703601] rtc_cmos 00:04: RTC can wake from S4
 [    0.703656] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
 [    0.703683] rtc0: alarms up to one year, 242 bytes nvram, hpet irqs
 [    0.703832] device-mapper: uevent: version 1.0.3
 [    0.703971] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
 [    0.704071] device-mapper: multipath: version 1.1.1 loaded
 [    0.704075] device-mapper: multipath round-robin: version 1.0.0 loaded
 [    0.704237] EISA: Probing bus 0 at eisa.0
 [    0.704245] Cannot allocate resource for EISA slot 1
 [    0.704256] Cannot allocate resource for EISA slot 4
 [    0.704274] EISA: Detected 0 cards.
 [    0.704377] cpuidle: using governor ladder
 [    0.704380] cpuidle: using governor menu
 [    0.704872] TCP cubic registered
 [    0.705059] NET: Registered protocol family 10
 [    0.705622] lo: Disabled Privacy Extensions
 [    0.705980] NET: Registered protocol family 17
 [    0.708234] Using IPI No-Shortcut mode
 [    0.708406] PM: Resume from disk failed.
 [    0.708424] registered taskstats version 1
 [    0.708727]   Magic number: 6:927:909
 [    0.708822] rtc_cmos 00:04: setting system clock to 2006-01-01 00:56:32 UTC (1136076992)
 [    0.708827] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
 [    0.708829] EDD information not available.
 [    0.740845] ata1.00: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
 [    0.756895] ata1.00: configured for UDMA/33
 [    0.922459] isapnp: No Plug & Play device found
 [    0.923457] scsi 0:0:0:0: CD-ROM            SONY     CD-RW  CRX230ED  4YS1 PQ: 0 ANSI: 5
 [    0.927016] sr0: scsi3-mmc drive: 85x/52x writer cd/rw xa/form2 cdda tray
 [    0.927021] Uniform CD-ROM driver Revision: 3.20
 [    0.927242] sr 0:0:0:0: Attached scsi CD-ROM sr0
 [    0.927350] sr 0:0:0:0: Attached scsi generic sg0 type 5
 [    0.927472] ata2: port disabled. ignoring.
 [    0.927523] Freeing unused kernel memory: 688k freed
 [    0.928411] Write protecting the kernel text: 4940k
 [    0.928474] Write protecting the kernel read-only data: 1976k
 [    0.951615] udev[78]: starting version 163
 [    1.059678] sata_sis 0000:00:05.0: version 1.0
 [    1.059704] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
 [    1.059712] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
 [    1.083237] scsi2 : sata_sis
 [    1.092072] scsi3 : sata_sis
 [    1.092968] ata3: PATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xf900 irq 17
 [    1.092973] ata4: PATA max UDMA/133 cmd 0xfb00 ctl 0xfa00 bmdma 0xf908 irq 17
 [    1.097570]   alloc irq_desc for 18 on node -1
 [    1.097574]   alloc kstat_irqs on node -1
 [    1.097585] b43-pci-bridge 0000:00:0e.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 [    1.097596] b43-pci-bridge 0000:00:0e.0: setting latency timer to 64
 [    1.103944] FDC 0 is a post-1991 82077
 [    1.116114] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
 [    1.116124] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
 [    1.116132] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
 [    1.116139] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
 [    1.156134] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0e.0
 [    1.156158] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
 [    1.156186]   alloc irq_desc for 19 on node -1
 [    1.156189]   alloc kstat_irqs on node -1
 [    1.156199] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
 [    1.156212] sis190 0000:00:04.0: setting latency timer to 64
 [    1.156226] sis190: 0000:00:04.0: Read MAC address from EEPROM
 [    1.156230] sis190: 0000:00:04.0: Error EEPROM read 0
 [    1.156234] sis190: 0000:00:04.0: Read MAC address from APC
 [    1.204015] sis190: 0000:00:04.0: unknown PHY 0x1c:0xc910 transceiver at address 1
 [    1.269700] ata3.00: ATA-8: WDC WD1600AAJS-00WAA0, 58.01D58, max UDMA/133
 [    1.269708] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
 [    1.284475] ata3.00: configured for UDMA/133
 [    1.284648] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 58.0 PQ: 0 ANSI: 5
 [    1.284877] sd 2:0:0:0: Attached scsi generic sg1 type 0
 [    1.285193] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
 [    1.285284] sd 2:0:0:0: [sda] Write Protect is off
 [    1.285288] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
 [    1.285327] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 [    1.285837]  sda: sda1 sda2 < sda5 >
 [    1.308373] sd 2:0:0:0: [sda] Attached SCSI disk
 [    1.352019] usb 2-2: new low speed USB device using ohci_hcd and address 2
 [    1.440652] ata4.01: NODEV after polling detection
 [    1.448747] ata4.00: ATAPI: HL-DT-ST DVDRAM_GSA-H60N, CA01, max UDMA/100
 [    1.464774] ata4.00: configured for UDMA/100
 [    1.470673] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM_GSA-H60N  CA01 PQ: 0 ANSI: 5
 [    1.482390] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
 [    1.482575] sr 3:0:0:0: Attached scsi CD-ROM sr1
 [    1.482670] sr 3:0:0:0: Attached scsi generic sg2 type 5
 [    1.588216] usbcore: registered new interface driver hiddev
 [    1.594210] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input2
 [    1.594412] generic-usb 0003:0461:0010.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:03.0-2/input0
 [    1.606632] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.1/input/input3
 [    1.606797] generic-usb 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:03.0-2/input1
 [    1.606893] usbcore: registered new interface driver usbhid
 [    1.606897] usbhid: USB HID core driver
 [    1.694930] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
 [    1.694938] EXT4-fs (sda1): write access will be enabled during recovery
 [    1.716520] sis190: 0000:00:04.0: Using transceiver at address 1 as default
 [    1.749322] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f80e4000 (IRQ: 19), 00:1c:25:30:d7:47
 [    1.749327] sis190 0000:00:04.0: eth0: RGMII mode.
 [    1.749335] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
 [    1.755060] EXT4-fs (sda1): recovery complete
 [    1.755320] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
 [    1.780616] firewire_ohci 0000:00:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
 [    1.780629] firewire_ohci 0000:00:0c.0: setting latency timer to 64
 [    1.840068] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
 [    1.872525] usb 3-3: new full speed USB device using ohci_hcd and address 2
 [    2.340205] firewire_core: created device fw0: GUID 00016c200045c94b, S400
 [    2.392519] usb 3-4: new full speed USB device using ohci_hcd and address 3
 [    2.626304] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:03.1/usb3/3-4/3-4:1.0/input/input4
 [    2.626407] generic-usb 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:03.1-4/input0
 [    2.637931] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:03.1/usb3/3-4/3-4:1.1/input/input5
 [    2.638051] generic-usb 0003:045E:0745.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:03.1-4/input1
 [    2.666902] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:03.1/usb3/3-4/3-4:1.2/input/input6
 [    2.667065] generic-usb 0003:045E:0745.0005: input,hiddev96,hidraw4: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:03.1-4/input2
 [   11.532323] udev[324]: starting version 163
 [   11.609629] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k  
 [   11.661035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 [   11.725295] Linux agpgart interface v0.103
 [   11.737155] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
 [   11.800536] lp: driver loaded but no devices found
 [   11.919384] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
 [   11.951950] Initializing USB Mass Storage driver...
 [   11.952144] parport_pc 00:0a: reported by Plug and Play ACPI
 [   11.952194] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
 [   11.962803] type=1400 audit(1136077003.748:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=560 comm="apparmor_parser"
 [   11.963561] type=1400 audit(1136077003.748:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
 [   11.963975] type=1400 audit(1136077003.748:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=560 comm="apparmor_parser"
 [   11.969539] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
 [   11.990062] cfg80211: Calling CRDA to update world regulatory domain
 [   11.997319] scsi4 : usb-storage 3-3:1.0
 [   11.998378] ppdev: user-space parallel port driver
 [   12.012140] usbcore: registered new interface driver usb-storage
 [   12.012147] USB Mass Storage support registered.
 [   12.025017] cfg80211: World regulatory domain updated:
 [   12.025022]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
 [   12.025027]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   12.025031]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
 [   12.025034]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
 [   12.025038]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   12.025042]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   12.040425] lp0: using parport0 (interrupt-driven).
 [   12.074831] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
 [   12.165820] phy0: Selected rate control algorithm 'minstrel'
 [   12.166806] Registered led device: b43-phy0::tx
 [   12.166835] Registered led device: b43-phy0::rx
 [   12.166863] Registered led device: b43-phy0::radio
 [   12.166979] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
 [   12.185542] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 [   12.185634] HDA Intel 0000:00:0f.0: setting latency timer to 64
 [   12.226051] hda_codec: ALC1200: BIOS auto-probing.
 [   12.226060] hda_codec: ALC1200: SKU not ready 0x598301f0
 [   12.347088] type=1400 audit(1136077004.132:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=794 comm="apparmor_parser"
 [   12.348086] type=1400 audit(1136077004.136:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=794 comm="apparmor_parser"
 [   12.394565] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   12.429614] type=1400 audit(1136077004.216:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=890 comm="apparmor_parser"
 [   12.433721] type=1400 audit(1136077004.220:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=891 comm="apparmor_parser"
 [   12.434553] type=1400 audit(1136077004.220:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=891 comm="apparmor_parser"
 [   12.434977] type=1400 audit(1136077004.220:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=891 comm="apparmor_parser"
 [   12.459474] type=1400 audit(1136077004.244:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=893 comm="apparmor_parser"
 [   13.024934] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
 [   13.031927] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
 [   13.038921] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
 [   13.046164] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
 [   13.049903] sd 4:0:0:0: Attached scsi generic sg3 type 0
 [   13.053288] sd 4:0:0:1: Attached scsi generic sg4 type 0
 [   13.054329] sd 4:0:0:2: Attached scsi generic sg5 type 0
 [   13.055531] sd 4:0:0:3: Attached scsi generic sg6 type 0
 [   13.279913] sd 4:0:0:2: [sdd] Attached SCSI removable disk
 [   13.301943] sd 4:0:0:0: [sdb] Attached SCSI removable disk
 [   13.323930] sd 4:0:0:1: [sdc] Attached SCSI removable disk
 [   13.334908] sd 4:0:0:3: [sde] Attached SCSI removable disk
 [   13.669301] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
 [   14.730571] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
 [   72.675133] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
 [   72.675138] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
 [   72.675143] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
 [   72.704532] sis190 0000:00:04.0: eth0: auto-negotiating...
 [   74.693241] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
 [  842.949795] ISO 9660 Extensions: Microsoft Joliet Level 3
 [  842.963681] ISO 9660 Extensions: RRIP_1991A

sry it took so long i couldnt find my flash drive 

Does this help at all?

---

### Post by samvkampen on 2011-04-18
Is this the on the installed ubuntu? Because I can see that some devices are connected to IRQ17, but no error. Can you post a screenshot of the error you get when it freezes? Because dmesg generates lots of output, you might have to pipe  it into gedit, because terminal has limited number of lines. Just try to run:```
dmesg | gedit
``` if it works it should open gedit and pipe the output in it. Again, i'm not sure if it works, but you can give it a try.

---

### Post by K_45 on 2011-04-18
Boot into the BIOS, disable the serial port, and if you don't use IDE disable it too. Same with floppy. That should free up some resources. Assuming that BIOS even has the options.

---

### Post by samvkampen on 2011-04-18
That always is a good idea, but that wont solve the problem right?

---

### Post by K_45 on 2011-04-18
> **samvkampen said:**
> That always is a good idea, but that wont solve the problem right?

Well, there seems to be not enough IRQ's, so if we free the interrupts, there will be more resources to go around, potentially solving the problem.

---

### Post by samvkampen on 2011-04-18
Where can you see that? It's probably a n00b question, but I kinda am.

---

### Post by K_45 on 2011-04-18
Search for IRQ 17, and you'll see. Similar with other IRQ's, but disabling options in the BIOS will free some interrupts.

---

### Post by joshcanfield on 2011-04-24
sorry i have gotten pretty busy this past week i will try what yall have said and i will see what i can do about posting the results


results... i disabled the serial and the ide and it works just fine now took me a whild to find them though in not too knowledgeable when it comes to the bios. actually in adition to it working moy my computer seems to rune a lot and i mean a lot faster and smoother. thanks a lot for the advice every body

---

### Post by Blasphemist on 2011-04-24
Do you guys think this has anything at all to do with his wireless driver errors? When those errors are seen, is there no need to go to the site it directs to and follow it? I've seen others report that error for wireless issues. Just asking to learn.

---

### Post by samacaster on 2011-04-24
A couple of things could be going haywire here.

Did you burn the iso at the slowest possible speed allowed by your burning program?

Have you checked the hash? (Md5sum) There are a ton of small programs that you can use to check the validity of a file. 

Are you installing with any peripherals attached? If you have any attached (Printers, Pendrives,etc...) remove them.

The Live environment works as you say, but sometimes there can still be corruption within the file.

As for the IRQ 17 issue, that resource is usually for one of the Standard OpenHCD USB Host Controllers.

Your running Vista/7 correct? Hit the Start button and type sys config and a system configuration window will come up. Click the tools tab and highlight System Information and then click Launch. Click to expand Hardware Resources and click IRQ. This will list all the Interrupts being used and what they are assigned to. 

Look for 17. Also check Conflicts/Sharing. You'll find a good many are shared and unless you've added things (sound/video cards, etc..) you should have no conflicts.

What your looking for is something that can be disabled in the Device Manager. Are you really going to use all your USB ports? Most people use a wireless mouse nowadays so, for instance, you could disable your mouse port, freeing up a resource. 

It would be a good idea to check your device manager anyway. Click Start and simply type device manager and it will come up. If there are any alerts you'll notice them straight away.

---

