---
title: "Ubuntu 10.10 chrashes"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by Gr0t on 2011-05-25
I recently purchased an Acer EeePc 1001PXD with:
2Gb DDR3 RAM
Intel Atom455 motherboard

After purchasing this netbook I decided to get rid of windows and run Ubuntu 10.10.
Once I got used to Ubuntu I love it. The only complaint that I have is that after spending some time on the internet, using facebook, youtube, etc. the screen will either go black or just freeze. When this happens everything is unresponsive.

When I look through the System Logs -> syslog i notice that before my computer becomes unresponsive it logs:

May 25 16:53:30 garrett-netbook rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="727" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 25 16:53:31 garrett-netbook rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="727" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 25 16:53:55 garrett-netbook anacron[939]: Job `cron.daily' terminated
May 25 16:53:55 garrett-netbook anacron[939]: Job `cron.weekly' started
May 25 16:53:55 garrett-netbook anacron[2143]: Updated timestamp for job `cron.weekly' to 2011-05-25
May 25 16:54:01 garrett-netbook anacron[939]: Job `cron.weekly' terminated
May 25 16:54:01 garrett-netbook anacron[939]: Normal exit (2 jobs run)
May 25 17:17:01 garrett-netbook CRON[2160]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 17:30:05 garrett-netbook kernel: [ 4395.648132] Skipping EDID probe due to cached edid
May 25 18:17:01 garrett-netbook CRON[2209]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 18:55:19 garrett-netbook kernel: [ 9509.460132] Skipping EDID probe due to cached edid
May 25 19:10:34 garrett-netbook kernel: [10424.476125] Skipping EDID probe due to cached edid
May 25 19:17:01 garrett-netbook CRON[2226]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 20:13:40 garrett-netbook kernel: [14210.520153] Skipping EDID probe due to cached edid
May 25 20:17:01 garrett-netbook CRON[2326]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 20:18:40 garrett-netbook acpid: client connected from 2491[114:123]
May 25 20:18:40 garrett-netbook acpid: 1 client rule loaded
May 25 20:24:33 garrett-netbook kernel: [14864.332136] Skipping EDID probe due to cached edid
May 25 21:17:01 garrett-netbook CRON[2529]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 21:21:20 garrett-netbook dhclient: DHCPREQUEST of 192.168.2.101 on wlan0 to 192.168.2.254 port 67
May 25 21:21:20 garrett-netbook dhclient: DHCPACK of 192.168.2.101 from 192.168.2.254
May 25 21:21:20 garrett-netbook dhclient: bound to 192.168.2.101 -- renewal in 16350 seconds.
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info> (wlan0): DHCPv4 state changed bound -> renew
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info>   address 192.168.2.101
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info>   prefix 24 (255.255.255.0)
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info>   gateway 192.168.2.254
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info>   hostname 'garrett-netbook'
May 25 21:21:20 garrett-netbook NetworkManager[787]: <info>   nameserver '192.168.2.254'
May 25 21:25:25 garrett-netbook kernel: [18515.944153] Skipping EDID probe due to cached edid
May 25 21:33:20 garrett-netbook kernel: [18990.796103] Skipping EDID probe due to cached edid


I then did some research on the Internet trying to solve this issue but have no luck.
This is what is spit out by dmesg:

t pref]
[    0.252243] pci 0000:01:00.0: reg 10: [mem 0xf7fc0000-0xf7ffffff 64bit]
[    0.252260] pci 0000:01:00.0: reg 18: [io  0xec00-0xec7f]
[    0.252354] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.252366] pci 0000:01:00.0: PME# disabled
[    0.260066] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.260081] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.260093] pci 0000:00:1c.3:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    0.260107] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260217] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.260228] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.260240] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.260254] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.260264] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.260273] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.260282] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.260291] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.260300] pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xfed8ffff] (subtractive decode)
[    0.260337] pci_bus 0000:00: on NUMA node 0
[    0.260368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.260901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.261097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.261259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.297565] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.297951] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.298315] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.298690] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.299055] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.299433] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.299800] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.300214] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.300388] HEST: Table is not found!
[    0.300577] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.300607] vgaarb: loaded
[    0.301065] SCSI subsystem initialized
[    0.301293] libata version 3.00 loaded.
[    0.301452] usbcore: registered new interface driver usbfs
[    0.301492] usbcore: registered new interface driver hub
[    0.301566] usbcore: registered new device driver usb
[    0.302284] ACPI: WMI: Mapper loaded
[    0.302291] PCI: Using ACPI for IRQ routing
[    0.302359] PCI: pci_cache_line_size set to 64 bytes
[    0.302496] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.302506] reserve RAM buffer: 000000007f690000 - 000000007fffffff 
[    0.302784] NetLabel: Initializing
[    0.302791] NetLabel:  domain hash size = 128
[    0.302797] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.302827] NetLabel:  unlabeled traffic allowed by default
[    0.302918] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.302931] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.302945] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.308299] Switching to clocksource tsc
[    0.335977] AppArmor: AppArmor Filesystem Enabled
[    0.336012] pnp: PnP ACPI init
[    0.336055] ACPI: bus type pnp registered
[    0.342187] pnp: PnP ACPI: found 13 devices
[    0.342196] ACPI: ACPI bus type pnp unregistered
[    0.342206] PnPBIOS: Disabled by ACPI PNP
[    0.342244] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.342254] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.342279] system 00:07: [io  0x025c-0x025f] has been reserved
[    0.342289] system 00:07: [io  0x0380-0x0383] has been reserved
[    0.342298] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.342307] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.342317] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.342326] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.342336] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.342346] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.342356] system 00:07: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.342366] system 00:07: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.342376] system 00:07: [mem 0xfff00000-0xffffffff] has been reserved
[    0.342395] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.342405] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.342424] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.342442] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.342452] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.342462] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.342472] system 00:0c: [mem 0x00100000-0x7f6fffff] could not be reserved
[    0.342482] system 00:0c: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.382085] pci 0000:00:1c.0: BAR 14: assigned [mem 0x7f700000-0x7f8fffff]
[    0.382100] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.382112] pci 0000:00:1c.3: BAR 15: assigned [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.382123] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.382133] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.382142] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.382151] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.382163] pci 0000:00:1c.0:   bridge window [mem 0x7f700000-0x7f8fffff]
[    0.382175] pci 0000:00:1c.0:   bridge window [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.382189] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.382197] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.382209] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.382220] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.382234] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.382243] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.382255] pci 0000:00:1c.3:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    0.382266] pci 0000:00:1c.3:   bridge window [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.382280] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.382286] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.382296] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.382305] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.382332] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.382348]   alloc irq_desc for 16 on node -1
[    0.382354]   alloc kstat_irqs on node -1
[    0.382371] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.382383] pci 0000:00:1c.0: setting latency timer to 64
[    0.382402] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.382412]   alloc irq_desc for 17 on node -1
[    0.382418]   alloc kstat_irqs on node -1
[    0.382430] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.382441] pci 0000:00:1c.1: setting latency timer to 64
[    0.382460]   alloc irq_desc for 19 on node -1
[    0.382465]   alloc kstat_irqs on node -1
[    0.382477] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.382487] pci 0000:00:1c.3: setting latency timer to 64
[    0.382503] pci 0000:00:1e.0: setting latency timer to 64
[    0.382513] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.382521] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.382530] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.382538] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.382547] pci_bus 0000:00: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.382555] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.382563] pci_bus 0000:04: resource 1 [mem 0x7f700000-0x7f8fffff]
[    0.382572] pci_bus 0000:04: resource 2 [mem 0x7f900000-0x7fafffff 64bit pref]
[    0.382581] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.382589] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.382597] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.382606] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.382614] pci_bus 0000:01: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    0.382623] pci_bus 0000:01: resource 2 [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.382632] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.382639] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.382648] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.382656] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.382664] pci_bus 0000:05: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.382753] NET: Registered protocol family 2
[    0.382936] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.383538] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.384685] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.385255] TCP: Hash tables configured (established 131072 bind 65536)
[    0.385266] TCP reno registered
[    0.385283] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.385307] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.385553] NET: Registered protocol family 1
[    0.385597] pci 0000:00:02.0: Boot video device
[    0.385796] PCI: CLS 32 bytes, default 64
[    0.386305] cpufreq-nforce2: No nForce2 chipset.
[    0.386384] Scanning for low memory corruption every 60 seconds
[    0.386725] audit: initializing netlink socket (disabled)
[    0.386751] type=2000 audit(1306373909.380:1): initialized
[    0.410196] highmem bounce pool size: 64 pages
[    0.410213] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.414998] VFS: Disk quotas dquot_6.5.2
[    0.415187] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.417184] fuse init (API version 7.14)
[    0.417495] msgmni has been set to 1683
[    0.740456] Freeing initrd memory: 10520k freed
[    0.754032] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.754041] io scheduler noop registered
[    0.754046] io scheduler deadline registered
[    0.754087] io scheduler cfq registered (default)
[    0.754307] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.754358]   alloc irq_desc for 40 on node -1
[    0.754362]   alloc kstat_irqs on node -1
[    0.754380] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.754551] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.754597]   alloc irq_desc for 41 on node -1
[    0.754601]   alloc kstat_irqs on node -1
[    0.754614] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.754784] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.754830]   alloc irq_desc for 42 on node -1
[    0.754834]   alloc kstat_irqs on node -1
[    0.754846] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.755055] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.755280] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.755500] intel_idle: MWAIT substates: 0x20220
[    0.755505] intel_idle: v0.4 model 0x1C
[    0.755509] intel_idle: lapic_timer_reliable_states 0x2
[    0.755520] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.755808] ACPI: AC Adapter [AC0] (on-line)
[    0.755981] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.756219] Switching to clocksource hpet
[    0.760945] ACPI: Lid Switch [LID]
[    0.761083] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.761095] ACPI: Sleep Button [SLPB]
[    0.761196] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.761205] ACPI: Power Button [PWRB]
[    0.761316] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.761325] ACPI: Power Button [PWRF]
[    0.761814] ACPI: acpi_idle yielding to intel_idle
[    0.777814] thermal LNXTHERM:01: registered as thermal_zone0
[    0.777833] ACPI: Thermal Zone [TZ00] (64 C)
[    0.778058] ERST: Table is not found!
[    0.778492] isapnp: Scanning for PnP cards...
[    0.778661] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.783122] brd: module loaded
[    0.784948] loop: module loaded
[    0.786712] Fixed MDIO Bus: probed
[    0.786841] PPP generic driver version 2.4.2
[    0.786959] tun: Universal TUN/TAP device driver, 1.6
[    0.786965] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.787198] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.787248]   alloc irq_desc for 23 on node -1
[    0.787254]   alloc kstat_irqs on node -1
[    0.787271] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.787306] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.787315] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.787416] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.787466] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.787485] ehci_hcd 0000:00:1d.7: debug port 1
[    0.791393] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.791439] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7cf7c00
[    0.805030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.805375] hub 1-0:1.0: USB hub found
[    0.805390] hub 1-0:1.0: 8 ports detected
[    0.805586] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.805632] uhci_hcd: USB Universal Host Controller Interface driver
[    0.805703] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.805720] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.805728] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.805840] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.805882] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    0.806254] hub 2-0:1.0: USB hub found
[    0.806267] hub 2-0:1.0: 2 ports detected
[    0.806408] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.806424] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.806432] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.806537] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.806597] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    0.806940] hub 3-0:1.0: USB hub found
[    0.806953] hub 3-0:1.0: 2 ports detected
[    0.807095]   alloc irq_desc for 18 on node -1
[    0.807101]   alloc kstat_irqs on node -1
[    0.807116] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.807131] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.807139] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.807240] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.807296] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.807644] hub 4-0:1.0: USB hub found
[    0.807657] hub 4-0:1.0: 2 ports detected
[    0.807795] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.807811] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.807819] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.807925] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.807982] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    0.808339] hub 5-0:1.0: USB hub found
[    0.808352] hub 5-0:1.0: 2 ports detected
[    0.808682] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.832222] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.832239] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.832460] mice: PS/2 mouse device common for all mice
[    0.832910] rtc_cmos 00:03: RTC can wake from S4
[    0.833039] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.833080] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.833422] device-mapper: uevent: version 1.0.3
[    0.833805] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.833987] device-mapper: multipath: version 1.1.1 loaded
[    0.833995] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.834344] EISA: Probing bus 0 at eisa.0
[    0.834352] EISA: Cannot allocate resource for mainboard
[    0.834361] Cannot allocate resource for EISA slot 1
[    0.834369] Cannot allocate resource for EISA slot 2
[    0.834376] Cannot allocate resource for EISA slot 3
[    0.834384] Cannot allocate resource for EISA slot 4
[    0.834391] Cannot allocate resource for EISA slot 5
[    0.834399] Cannot allocate resource for EISA slot 6
[    0.834406] Cannot allocate resource for EISA slot 7
[    0.834414] Cannot allocate resource for EISA slot 8
[    0.834420] EISA: Detected 0 cards.
[    0.834880] cpuidle: using governor ladder
[    0.835267] cpuidle: using governor menu
[    0.836048] TCP cubic registered
[    0.836472] NET: Registered protocol family 10
[    0.837469] lo: Disabled Privacy Extensions
[    0.838063] NET: Registered protocol family 17
[    0.840212] Using IPI No-Shortcut mode
[    0.840501] PM: Resume from disk failed.
[    0.840528] registered taskstats version 1
[    0.840993]   Magic number: 11:630:610
[    0.841168] rtc_cmos 00:03: setting system clock to 2011-05-26 01:38:31 UTC (1306373911)
[    0.841177] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.841183] EDD information not available.
[    0.893593] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.912729] ACPI: Battery Slot [BAT0] (battery present)
[    1.133098] isapnp: No Plug & Play device found
[    1.133159] Freeing unused kernel memory: 688k freed
[    1.133719] Write protecting the kernel text: 4940k
[    1.133790] Write protecting the kernel read-only data: 1976k
[    1.157068] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.171936] udev[76]: starting version 163
[    1.365728] atl1c 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.365755] atl1c 0000:01:00.0: setting latency timer to 64
[    1.541696] atl1c 0000:01:00.0: version 1.0.0.2-NAPI
[    1.550112] ahci 0000:00:1f.2: version 3.0
[    1.550150]   alloc irq_desc for 21 on node -1
[    1.550157]   alloc kstat_irqs on node -1
[    1.550176] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.550249]   alloc irq_desc for 43 on node -1
[    1.550255]   alloc kstat_irqs on node -1
[    1.550275] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.550392] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.550404] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.550416] ahci 0000:00:1f.2: setting latency timer to 64
[    1.550667] scsi0 : ahci
[    1.551052] scsi1 : ahci
[    1.551322] scsi2 : ahci
[    1.551549] scsi3 : ahci
[    1.552394] ata1: SATA max UDMA/133 abar m1024@0xf7cf7800 port 0xf7cf7900 irq 43
[    1.552405] ata2: DUMMY
[    1.552411] ata3: DUMMY
[    1.552416] ata4: DUMMY
[    1.872079] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.873505] ata1.00: unexpected _GTF length (8)
[    1.927614] ata1.00: ATA-8: ST9250315AS, 0003SDM1, max UDMA/133
[    1.927627] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.930056] ata1.00: unexpected _GTF length (8)
[    1.930485] ata1.00: configured for UDMA/133
[    1.944331] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0003 PQ: 0 ANSI: 5
[    1.944791] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.944950] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.945229] sd 0:0:0:0: [sda] Write Protect is off
[    1.945238] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.945305] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.945931]  sda: sda1 sda2 < sda5 >
[    1.989378] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.249227] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.249238] EXT4-fs (sda1): write access will be enabled during recovery
[    9.018487] EXT4-fs (sda1): orphan cleanup on readonly fs
[    9.018514] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6306076
[    9.018693] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6306071
[    9.018730] EXT4-fs (sda1): 2 orphan inodes deleted
[    9.018737] EXT4-fs (sda1): recovery complete
[    9.442180] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   22.520047] udev[333]: starting version 163
[   22.559738] Adding 6142972k swap on /dev/sda5.  Priority:-1 extents:1 across:6142972k 
[   22.582776] lp: driver loaded but no devices found
[   23.183725] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.359779] Linux agpgart interface v0.103
[   23.406719] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[   23.407283] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   23.439982] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   23.553220] cfg80211: Calling CRDA to update world regulatory domain
[   23.613109] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[   23.613890] eeepc_wmi: Backlight controlled by ACPI video driver
[   23.661220] cfg80211: World regulatory domain updated:
[   23.661231]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.661242]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.661251]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.661260]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.661269]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.661278]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.713270] [drm] Initialized drm 1.1.0 20060810
[   23.722120] Linux video capture interface: v2.00
[   23.801987] uvcvideo: Found UVC 1.00 device USB2.0 UVC VGA WebCam (13d3:5702)
[   23.837063] type=1400 audit(1306373934.491:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=621 comm="apparmor_parser"
[   23.837892] type=1400 audit(1306373934.491:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=621 comm="apparmor_parser"
[   23.838395] type=1400 audit(1306373934.491:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=621 comm="apparmor_parser"
[   23.882090] input: USB2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   23.883368] usbcore: registered new interface driver uvcvideo
[   23.883378] USB Video Class driver (v0.1.0)
[   24.156367] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.156380] i915 0000:00:02.0: setting latency timer to 64
[   24.211865] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.211887] ath9k 0000:02:00.0: setting latency timer to 64
[   24.263417] ath: EEPROM regdomain: 0x60
[   24.263426] ath: EEPROM indicates we should expect a direct regpair map
[   24.263437] ath: Country alpha2 being used: 00
[   24.263443] ath: Regpair used: 0x60
[   24.295854]   alloc irq_desc for 44 on node -1
[   24.295863]   alloc kstat_irqs on node -1
[   24.295881] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   24.295903] [drm] set up 7M of stolen space
[   24.396043] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000/0xa0000
[   24.466954] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   24.467425] [drm] initialized overlay support
[   24.612526] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.681782] type=1400 audit(1306373935.335:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=775 comm="apparmor_parser"
[   24.682425] type=1400 audit(1306373935.335:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=775 comm="apparmor_parser"
[   24.682798] type=1400 audit(1306373935.335:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=775 comm="apparmor_parser"
[   24.688698] type=1400 audit(1306373935.343:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=774 comm="apparmor_parser"
[   24.743567] type=1400 audit(1306373935.395:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=778 comm="apparmor_parser"
[   24.749559] type=1400 audit(1306373935.403:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=778 comm="apparmor_parser"
[   24.769331] type=1400 audit(1306373935.423:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=776 comm="apparmor_parser"
[   24.781099] Skipping EDID probe due to cached edid
[   24.797622] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   24.799462] Registered led device: ath9k-phy0::radio
[   24.799525] Registered led device: ath9k-phy0::assoc
[   24.799585] Registered led device: ath9k-phy0::tx
[   24.799653] Registered led device: ath9k-phy0::rx
[   24.799681] phy0: Atheros AR9285 Rev:2 mem=0xf8320000, irq=17
[   25.104633] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   25.219881] Console: switching to colour frame buffer device 128x37
[   25.227557] fb0: inteldrmfb frame buffer device
[   25.227563] drm: registered panic notifier
[   25.239752] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.240347] Slow work thread pool: Starting up
[   25.243646] Slow work thread pool: Ready
[   25.254546] ACPI Warning: _BQC returned an invalid level (20100428/video-640)
[   25.270137]   alloc irq_desc for 45 on node -1
[   25.270148]   alloc kstat_irqs on node -1
[   25.270177] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   25.270973] acpi device:2b: registered as cooling_device2
[   25.271076] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.287338] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   25.289163] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.290729] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   25.290835]   alloc irq_desc for 22 on node -1
[   25.290843]   alloc kstat_irqs on node -1
[   25.290862] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.290951]   alloc irq_desc for 46 on node -1
[   25.290957]   alloc kstat_irqs on node -1
[   25.290978] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   25.291031] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.428404] hda_codec: ALC259: BIOS auto-probing.
[   25.428607] hda_codec: connection list not available for 0x24
[   25.489090] Skipping EDID probe due to cached edid
[   25.847553] ppdev: user-space parallel port driver
[   26.283085] vboxdrv: Found 2 processor cores.
[   26.283668] vboxdrv: fAsync=0 offMin=0x154 offMax=0x82a
[   26.286690] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   26.286700] vboxdrv: Successfully loaded version 4.0.6 (interface 0x00180000).
[   26.406109] Skipping EDID probe due to cached edid
[   26.440254] Skipping EDID probe due to cached edid
[   27.833890] Skipping EDID probe due to cached edid
[   27.876130] Skipping EDID probe due to cached edid
[   27.912076] Skipping EDID probe due to cached edid
[   27.945130] Skipping EDID probe due to cached edid
[   35.952899] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   38.707467] Netfilter messages via NETLINK v0.30.
[   44.661125] Skipping EDID probe due to cached edid
[   44.697126] Skipping EDID probe due to cached edid
[   44.733117] Skipping EDID probe due to cached edid
[   44.769114] Skipping EDID probe due to cached edid
[   48.173122] Skipping EDID probe due to cached edid
[   50.281946] wlan0: Selected IBSS BSSID 02:23:76:ea:61:28 based on configured SSID
[   51.981428] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   51.983684] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   51.983696] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   51.983703] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   52.109107] Skipping EDID probe due to cached edid

This freezing does not only occur when i am surfing websites like youtube but i have noticed that this is when it occurs the most. I do not know if any of this means anything to anybody but if you know how to solve my problem please help as it is very annoying.

Thanks in advance,
Garrett

---

### Post by jtarin on 2011-05-25
Browser and version?

---

### Post by Gr0t on 2011-05-25
I am using Firefox 3.6.17
I would like to continue using firefox if possible

---

### Post by jtarin on 2011-05-26
Try turning off Compiz if it's on.It's off? Then.......
Let's check your graphics chip and also what module(s)/driver(s) are loaded for it.Open a terminal and type "lspci" (without quotes)post results here. Next open a terminal and type the command "lsmod" (without quotes) post results here.

---

### Post by jtarin on 2011-05-26
Where did you get your flash install from?

---

### Post by Gr0t on 2011-05-26
i am using Ubuntu 10.10 32-bit

as for compiz i am not sure...
under system -> preferences -> appearance -> visual effects i have "Normal" selected

lscpi returns:

garrett@garrett-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

and lsmod returns:

garrett@garrett-netbook:~$ lsmod
Module                  Size  Used by
xt_tcpudp               1927  4 
nf_conntrack_ipv4      10783  3 
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
xt_state                1014  3 
nf_conntrack           63258  2 nf_conntrack_ipv4,xt_state
xt_mark                  935  6 
xt_NFQUEUE              1743  3 
ipt_REJECT              2004  2 
nfnetlink_queue         6704  3 
nfnetlink               3691  4 nfnetlink_queue
binfmt_misc             6599  1 
vboxnetadp              6936  0 
vboxnetflt             18657  0 
vboxdrv               229899  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
joydev                  8767  0 
arc4                    1165  2 
iptable_filter          1302  1 
ip_tables              10460  1 iptable_filter
x_tables               15921  7 xt_tcpudp,xt_state,xt_mark,xt_NFQUEUE,ipt_REJECT,iptable_filter,ip_tables
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
ath9k                  88884  0 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  295435  5 
snd_seq_midi            4588  0 
ath9k_common            5982  1 ath9k
snd_rawmidi            17783  1 snd_seq_midi
ath9k_hw              292329  2 ath9k,ath9k_common
uvcvideo               55847  0 
ath                     8153  2 ath9k,ath9k_hw
drm_kms_helper         30200  1 i915
videodev               43098  1 uvcvideo
mac80211              231959  2 ath9k,ath9k_common
snd_seq_midi_event      6047  1 snd_seq_midi
v4l1_compat            13359  2 uvcvideo,videodev
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168060  5 i915,drm_kms_helper
eeepc_wmi               2963  0 
sparse_keymap           3145  1 eeepc_wmi
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
intel_agp              26566  2 i915
psmouse                59033  0 
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  1 i915
led_class               2633  1 ath9k
soundcore                880  1 snd
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21728  1 ahci
atl1c                  29949  0

---

### Post by Gr0t on 2011-05-26
i downloaded ubuntu 10.10 from ubuntu's website when it originally came out and have since updated it hoping this issue would be resolved. I installed it using a usb

---

### Post by jtarin on 2011-05-26
> as for compiz i am not sure...
under system -> preferences -> appearance -> visual effects i have "Normal" selected
Select none...then reboot. Browse for awhile and report back.You might consider some kind of extension to block flash/ads for regular browsing if Compiz switch doesn't work.

---

### Post by jtarin on 2011-05-26
> **Gr0t said:**
> i downloaded ubuntu 10.10 from ubuntu's website when it originally came out and have since updated it hoping this issue would be resolved. I installed it using a usbI asked about "Flash Installation" as in Adobe or ?????

---

### Post by 3rdalbum on 2011-05-26
> **Gr0t said:**
> i downloaded ubuntu 10.10 from ubuntu's website when it originally came out and have since updated it hoping this issue would be resolved. I installed it using a usb

More often than not, an issue will be resolved in a new version of Ubuntu, not within the same version. Ubuntu 11.04 is out - why not try that and see if the problem still occurs?

A lot of unexplained crashes are due to faulty RAM, but I'd probably hope that it's not the case with yours because laptops are a bit harder to get into than desktop computers.

---

### Post by jtarin on 2011-05-26
I wouldn't put 11.04 on that PC......but you do what you want.
I would do something a little more conservative.

---

### Post by Gr0t on 2011-05-26
as of right now simply turning off compiz off has worked.
i do not want to speak too soon as it has not been that long yet. i will post back if there is any changes.

and for my flash i have shockwave

---

### Post by jtarin on 2011-05-26
> **Gr0t said:**
> as of right now simply turning off compiz off has worked.
i do not want to speak too soon as it has not been that long yet. i will post back if there is any changes.

and for my flash i have shockwaveGood!10.10 is a good stable version of Ubuntu. You just need to fine tune it for your hardware. You want Compiz???? Gotta get some horsepower. :)))
Post back if you have any problems related to this topic. Different topic.....place under a different post.

---

### Post by Gr0t on 2011-05-26
unfortunately i spoke too soon. i let my computer stay on as i was sleeping and it was even disconnected from the internet and it still crashed. i looked through the logs and everything remains the same.
i realise that my eeePc is by no means a powerful machine. personally i do not care if i dont have all of the flashiness that compiz offers. i simply want it to run as intended as this is not my only computer.

---

### Post by jtarin on 2011-05-26
It sounds like a hardware problem at this point. I've run out of ideas.

---

### Post by MSPdwalt on 2011-05-26
Definatly sounds like a hardware problem.  run a few pases of [memtest86+]("http://www.memtest.org/") on it and see what happends.

Also how old is this machine, sometimes problems like this can be heat related and are solved by putting new thermal paste on the CPU and GPU.

---

### Post by wildmanne39 on 2011-05-26
> **Gr0t said:**
> unfortunately i spoke too soon. i let my computer stay on as i was sleeping and it was even disconnected from the internet and it still crashed. i looked through the logs and everything remains the same.
i realise that my eeePc is by no means a powerful machine. personally i do not care if i dont have all of the flashiness that compiz offers. i simply want it to run as intended as this is not my only computer.
Hi, you might check and see if it is getting hot, that is a problem with laptops, I used a pad with fans to keep mine cool.

---

### Post by jramshu on 2011-05-26
Have you checked system monitor to see what % the cpu is running when firefox is running, and with it running video or flash? I've seen them freeze when the cpu is taxed at 100%, for some reason some processors run high with the browser. Some dual cores aren't running both cores sometimes. 

Maybe lower the freq of the cpu in bios, if it isn't locked, if it's overheating.

EDIT: Also, cpu's that act like this, freezing up with relatively no load on them, are the one's that have a high cpu loads with firefox. Haven't tried with chrome yet. The Adobe Flash player will tax it in it's own box too.

---

### Post by jramshu on 2011-05-28
Been digging around on this whole intel and freezing and crashing systems. I'm going to probably try intels microcode update for Linux OS's, see if that helps. Thought about trying to overclock it, but since the laptop is my Mom's, I wouldn't want to fry it out. She's going to be dissapointed when I tell her no modern version of Ubuntu, Mint, etc. would run on her box without freezing, reverted back to Windows for her.

I hadn't had no problems with any distro until I installed them to a pentium 4m, the processor runs very high and eventually freezes the system, especially when running a browser w/ flash or video. Looks like this happens on random machines, so I'm not blaming it on Linux. (been thinking about dropping back to 8.04 since it seemed to be the most stable on this chip)

I have tried to find answers for a while on here and have yet to find an "actual fix" for many of the problems intel users are having with various versions/distros of Linux freezing/crashing. Always the same answers and most time, no resolution.

---

### Post by alfred@klandestino.se on 2011-06-24
Hi! I have the exact same hardware and the same problem, but only when surfing the wifi. The ethernet port works fine. I made som tests and it seems to be some network buffer that fails, but I haven't digged deep into it yet.

---

### Post by Windwoodtrader on 2011-06-28
> **jtarin said:**
> It sounds like a hardware problem at this point. I've run out of ideas.
I have a similar problem with Natty 11.04 using an AMD Opteron 64 running a 32bit install. When I came to my computer this am my screensaver was frozen and I needed a hard kill since I couldn't invoke anything including the terminal. 

I had loaded Shockwave from the Ubuntu software application source early on the 27th (yesterday) and it works fine.

I suspect one of the following:
  Scripts in websites causing a jam-up- I have a couple of automatic update sites.
  Screen-saver is causing a freezeup after a delay(overnight?)
  The Shockwave install is getting into the mix somehow.

I am providing the same data runs you requested from the other poster-

john@john-GS221AV-ABA-s3200z:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7500 LE] (rev a1)

And:

john@john-GS221AV-ABA-s3200z:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  0 
udf                    83795  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
nouveau               621970  2 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 nouveau
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt73usb                26854  0 
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
drm                   180037  4 nouveau,ttm,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 rt2x00usb,rt2x00lib
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 rt2x00lib,mac80211
i2c_algo_bit           13184  1 nouveau
soundcore              12600  1 snd
psmouse                73312  0 
serio_raw              12990  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
usb_storage            43946  0 
firewire_core          56138  1 firewire_ohci
uas                    17676  0 
forcedeth              58190  0 
crc_itu_t              12627  3 udf,rt73usb,firewire_core
sata_nv                23176  2 
pata_amd               13762  0 
john@john-GS221AV-ABA-s3200z:~$ 

This is the log stream from last night (no log-off) and then this am when I had to do the hard kill/Start.

Jun 27 12:20:44 john-GS221AV-ABA-s3200z kernel: [   56.976011] wlan0: no IPv6 routers present
Jun 27 16:14:57 john-GS221AV-ABA-s3200z kernel: [14109.896313] audit_printk_skb: 15 callbacks suppressed
Jun 27 16:14:57 john-GS221AV-ABA-s3200z kernel: [14109.896318] type=1400 audit(1309205697.067:17): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/dev/.udev/data/b8:1" pid=3869 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 27 16:14:57 john-GS221AV-ABA-s3200z kernel: [14109.897423] type=1400 audit(1309205697.067:18): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/dev/.udev/data/b8:1" pid=3869 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 27 17:26:17 john-GS221AV-ABA-s3200z kernel: [18390.341942] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on tmds encoder (output 1)
Jun 27 17:35:01 john-GS221AV-ABA-s3200z kernel: [18914.249474] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on tmds encoder (output 1)
Jun 27 18:01:41 john-GS221AV-ABA-s3200z kernel: [20514.601678] sctp: Hash tables configured (established 65536 bind 65536)
Jun 27 19:45:03 john-GS221AV-ABA-s3200z kernel: [26716.164641] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on tmds encoder (output 1)
Jun 27 20:36:10 john-GS221AV-ABA-s3200z kernel: [29783.684681] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on tmds encoder (output 1)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] DMI present.
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] DMI: HP-Pavilion GS221AV-ABA s3200z/Acacia, BIOS  5.07 10/11/2007
Jun 28 08:45:23 john-GS221AV-ABA-s3200z kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)

Possibly something will jump out but I see no anomaly in the logs.

Thanks in advance

---

