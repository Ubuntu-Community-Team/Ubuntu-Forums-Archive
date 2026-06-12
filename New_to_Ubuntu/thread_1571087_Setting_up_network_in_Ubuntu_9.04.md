---
title: "Setting up network in Ubuntu 9.04"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Nikhil_07n on 2010-09-09
Well, last time I used installed ubuntu on my ancient machine networking was no problem. But this time the network applet is displaying "No network devices found".

How to fix this?

P.S. : Running ubuntu for the second time(well, you can consider it first as last time I didn't mess around).

**EDIT** : This time I'm working on a Intel DH55TC motherboard with core i5 760. Sorry for the unclear information.

---

### Post by bredman on 2010-09-09
Please post the results of the following commands...
ifconfig
lspci

Enter the following command and post anything that refers to Ethernet or Network
dmesg

In case you are wondering, what the commands do...
1. List the interface configurations
2. List the hardware plugged into the PCI bus
3. List diagnostic messages

---

### Post by Nikhil_07n on 2010-09-09
Here.

ifconfig :

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

lspci :


00:00.0 Host bridge: Intel Corporation Clarksfield/Lynnfield DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Clarksfield/Lynnfield PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Clarksfield/Lynnfield System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Clarksfield/Lynnfield Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Clarksfield/Lynnfield System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Clarksfield/Lynnfield Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation Ibex Peak HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation Ibex Peak PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation Ibex Peak KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation Device 10f0 (rev 06)
00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation Ibex Peak 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation Ibex Peak 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8
01:00.1 Audio device: ATI Technologies Inc Device aa58

dmesg :


[    0.560151] net_namespace: 776 bytes
[    0.560151] Booting paravirtualized kernel on bare hardware
[    0.560197] Time: 15:09:01  Date: 09/09/10
[    0.560197] regulator: core version 0.5
[    0.560197] NET: Registered protocol family 16
[    0.560197] EISA bus registered
[    0.560197] ACPI: bus type pci registered
[    0.560197] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.560197] PCI: MCFG area at e0000000 reserved in E820
[    0.560197] PCI: Using MMCONFIG for extended config space
[    0.560197] PCI: Using configuration type 1 for base access
[    0.560641] ACPI: EC: Look up EC in DSDT
[    0.569604] ACPI: Interpreter enabled
[    0.569607] ACPI: (supports S0 S1 S3 S4 S5)
[    0.569620] ACPI: Using IOAPIC for interrupt routing
[    0.569790] ACPI: BIOS _OSI(Linux) query ignored
[    0.576019] ACPI: No dock devices found.
[    0.576073] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.576153] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.576155] pci 0000:00:03.0: PME# disabled
[    0.576400] pci 0000:00:16.0: reg 10 64bit mmio: [0xfe729000-0xfe72900f]
[    0.576440] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.576447] pci 0000:00:16.0: PME# disabled
[    0.576488] pci 0000:00:16.2: reg 10 io port: [0xf150-0xf157]
[    0.576497] pci 0000:00:16.2: reg 14 io port: [0xf140-0xf143]
[    0.576506] pci 0000:00:16.2: reg 18 io port: [0xf130-0xf137]
[    0.576516] pci 0000:00:16.2: reg 1c io port: [0xf120-0xf123]
[    0.576526] pci 0000:00:16.2: reg 20 io port: [0xf110-0xf11f]
[    0.576587] pci 0000:00:16.3: reg 10 io port: [0xf100-0xf107]
[    0.576598] pci 0000:00:16.3: reg 14 32bit mmio: [0xfe728000-0xfe728fff]
[    0.576675] pci 0000:00:19.0: reg 10 32bit mmio: [0xfe700000-0xfe71ffff]
[    0.576684] pci 0000:00:19.0: reg 14 32bit mmio: [0xfe727000-0xfe727fff]
[    0.576693] pci 0000:00:19.0: reg 18 io port: [0xf020-0xf03f]
[    0.576719] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.576726] pci 0000:00:19.0: PME# disabled
[    0.576774] pci 0000:00:1a.0: reg 10 32bit mmio: [0xfe726000-0xfe7263ff]
[    0.576812] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.576819] pci 0000:00:1a.0: PME# disabled
[    0.576859] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe720000-0xfe723fff]
[    0.576888] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.576895] pci 0000:00:1b.0: PME# disabled
[    0.576938] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.576945] pci 0000:00:1c.0: PME# disabled
[    0.576987] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.576993] pci 0000:00:1c.4: PME# disabled
[    0.577045] pci 0000:00:1d.0: reg 10 32bit mmio: [0xfe725000-0xfe7253ff]
[    0.577082] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.577089] pci 0000:00:1d.0: PME# disabled
[    0.577227] pci 0000:00:1f.2: reg 10 io port: [0xf0f0-0xf0f7]
[    0.577236] pci 0000:00:1f.2: reg 14 io port: [0xf0e0-0xf0e3]
[    0.577244] pci 0000:00:1f.2: reg 18 io port: [0xf0d0-0xf0d7]
[    0.577253] pci 0000:00:1f.2: reg 1c io port: [0xf0c0-0xf0c3]
[    0.577258] pci 0000:00:1f.2: reg 20 io port: [0xf0b0-0xf0bf]
[    0.577267] pci 0000:00:1f.2: reg 24 io port: [0xf0a0-0xf0af]
[    0.577300] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe724000-0xfe7240ff]
[    0.577312] pci 0000:00:1f.3: reg 20 io port: [0xf000-0xf01f]
[    0.577352] pci 0000:00:1f.5: reg 10 io port: [0xf090-0xf097]
[    0.577360] pci 0000:00:1f.5: reg 14 io port: [0xf080-0xf083]
[    0.577369] pci 0000:00:1f.5: reg 18 io port: [0xf070-0xf077]
[    0.577377] pci 0000:00:1f.5: reg 1c io port: [0xf060-0xf063]
[    0.577386] pci 0000:00:1f.5: reg 20 io port: [0xf050-0xf05f]
[    0.577391] pci 0000:00:1f.5: reg 24 io port: [0xf040-0xf04f]
[    0.577433] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.577440] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe620000-0xfe63ffff]
[    0.577445] pci 0000:01:00.0: reg 20 io port: [0xe000-0xe0ff]
[    0.577452] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe600000-0xfe61ffff]
[    0.577458] pci 0000:01:00.0: supports D1 D2
[    0.577485] pci 0000:01:00.1: reg 10 64bit mmio: [0xfe640000-0xfe643fff]
[    0.577505] pci 0000:01:00.1: supports D1 D2
[    0.577530] pci 0000:00:03.0: bridge io port: [0xe000-0xefff]
[    0.577533] pci 0000:00:03.0: bridge 32bit mmio: [0xfe600000-0xfe6fffff]
[    0.577537] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.577662] pci 0000:00:1e.0: transparent bridge
[    0.577691] bus 00 -> node 0
[    0.577695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.577929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.578009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.578091] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    1.582697] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.582810] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.582923] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.583037] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.583151] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.583260] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    1.583374] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.583487] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.583612] ACPI: WMI: Mapper loaded
[    1.583635] SCSI subsystem initialized
[    1.583635] libata version 3.00 loaded.
[    1.583635] usbcore: registered new interface driver usbfs
[    1.583635] usbcore: registered new interface driver hub
[    1.583635] usbcore: registered new device driver usb
[    1.583635] PCI: Using ACPI for IRQ routing
[    1.588015] Bluetooth: Core ver 2.13
[    1.588035] NET: Registered protocol family 31
[    1.588035] Bluetooth: HCI device and connection manager initialized
[    1.588035] Bluetooth: HCI socket layer initialized
[    1.588035] NET: Registered protocol family 8
[    1.588035] NET: Registered protocol family 20
[    1.588037] NetLabel: Initializing
[    1.588038] NetLabel:  domain hash size = 128
[    1.588039] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.588046] NetLabel:  unlabeled traffic allowed by default
[    1.588065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 2302, 2301, 2300, 2299, 0
[    1.588070] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.592028] hpet: hpet2 irq 2303 for MSI
[    1.592036] hpet: hpet3 irq 2302 for MSI
[    1.596040] hpet: hpet4 irq 2301 for MSI
[    1.600041] hpet: hpet5 irq 2300 for MSI
[    1.600054] AppArmor: AppArmor Filesystem Enabled
[    1.604035] Switched to high resolution mode on CPU 0
[    1.604490] Switched to high resolution mode on CPU 2
[    1.604518] Switched to high resolution mode on CPU 3
[    1.604535] Switched to high resolution mode on CPU 1
[    1.608025] pnp: PnP ACPI init
[    1.608036] ACPI: bus type pnp registered
[    1.611080] pnp: PnP ACPI: found 13 devices
[    1.611082] ACPI: ACPI bus type pnp unregistered
[    1.611084] PnPBIOS: Disabled by ACPI PNP
[    1.611090] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.611092] system 00:01: iomem range 0xe0000000-0xe3ffffff has been reserved
[    1.611094] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    1.611095] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.611097] system 00:01: iomem range 0xfee00000-0xfee0ffff has been reserved
[    1.611103] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.611107] system 00:0b: ioport range 0x400-0x47f has been reserved
[    1.611109] system 00:0b: ioport range 0x1180-0x119f has been reserved
[    1.611110] system 00:0b: ioport range 0x500-0x57f has been reserved
[    1.611112] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.611114] system 00:0b: iomem range 0xfec00000-0xfecfffff has been reserved
[    1.611115] system 00:0b: iomem range 0xfed08000-0xfed08fff has been reserved
[    1.611117] system 00:0b: iomem range 0xff000000-0xffffffff has been reserved
[    1.645756] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    1.645759] pci 0000:00:03.0:   IO window: 0xe000-0xefff
[    1.645762] pci 0000:00:03.0:   MEM window: 0xfe600000-0xfe6fffff
[    1.645764] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.645768] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.645769] pci 0000:00:1c.0:   IO window: disabled
[    1.645777] pci 0000:00:1c.0:   MEM window: disabled
[    1.645784] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.645792] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    1.645794] pci 0000:00:1c.4:   IO window: disabled
[    1.645801] pci 0000:00:1c.4:   MEM window: disabled
[    1.645808] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.645817] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    1.645818] pci 0000:00:1e.0:   IO window: disabled
[    1.645826] pci 0000:00:1e.0:   MEM window: disabled
[    1.645832] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.645846] pci 0000:00:03.0: setting latency timer to 64
[    1.645857] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.645861] pci 0000:00:1c.0: setting latency timer to 64
[    1.645871] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.645878] pci 0000:00:1c.4: setting latency timer to 64
[    1.645886] pci 0000:00:1e.0: setting latency timer to 64
[    1.645893] bus: 00 index 0 io port: [0x00-0xffff]
[    1.645895] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.645896] bus: 01 index 0 io port: [0xe000-0xefff]
[    1.645897] bus: 01 index 1 mmio: [0xfe600000-0xfe6fffff]
[    1.645899] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    1.645900] bus: 01 index 3 mmio: [0x0-0x0]
[    1.645901] bus: 02 index 0 mmio: [0x0-0x0]
[    1.645902] bus: 02 index 1 mmio: [0x0-0x0]
[    1.645903] bus: 02 index 2 mmio: [0x0-0x0]
[    1.645904] bus: 02 index 3 mmio: [0x0-0x0]
[    1.645905] bus: 03 index 0 mmio: [0x0-0x0]
[    1.645906] bus: 03 index 1 mmio: [0x0-0x0]
[    1.645907] bus: 03 index 2 mmio: [0x0-0x0]
[    1.645908] bus: 03 index 3 mmio: [0x0-0x0]
[    1.645909] bus: 04 index 0 mmio: [0x0-0x0]
[    1.645910] bus: 04 index 1 mmio: [0x0-0x0]
[    1.645911] bus: 04 index 2 mmio: [0x0-0x0]
[    1.645912] bus: 04 index 3 io port: [0x00-0xffff]
[    1.645914] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    1.645919] NET: Registered protocol family 2
[    1.660091] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.660227] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.660525] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.660677] TCP: Hash tables configured (established 131072 bind 65536)
[    1.660679] TCP reno registered
[    1.668126] NET: Registered protocol family 1
[    1.668197] checking if image is initramfs... it is
[    2.111121] Freeing initrd memory: 7371k freed
[    2.111346] cpufreq: No nForce2 chipset.
[    2.111419] audit: initializing netlink socket (disabled)
[    2.111433] type=2000 audit(1284044942.108:1): initialized
[    2.116800] highmem bounce pool size: 64 pages
[    2.116802] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.117666] VFS: Disk quotas dquot_6.5.1
[    2.117697] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.118073] fuse init (API version 7.10)
[    2.118119] msgmni has been set to 1665
[    2.118266] alg: No test for stdrng (krng)
[    2.118272] io scheduler noop registered
[    2.118274] io scheduler anticipatory registered
[    2.118275] io scheduler deadline registered
[    2.118283] io scheduler cfq registered (default)
[    2.168051] pci 0000:01:00.0: Boot video device
[    2.171114] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.171142] pcieport-driver 0000:00:03.0: found MSI capability
[    2.171159] pcieport-driver 0000:00:03.0: irq 2298 for MSI/MSI-X
[    2.171166] pci_express 0000:00:03.0:pcie00: allocate port service
[    2.171174] pci_express 0000:00:03.0:pcie01: allocate port service
[    2.171211] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.171242] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.171265] pcieport-driver 0000:00:1c.0: irq 2297 for MSI/MSI-X
[    2.171278] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.171326] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    2.171357] pcieport-driver 0000:00:1c.4: found MSI capability
[    2.171380] pcieport-driver 0000:00:1c.4: irq 2296 for MSI/MSI-X
[    2.171393] pci_express 0000:00:1c.4:pcie00: allocate port service
[    2.173165] aer 0000:00:03.0:pcie01: service driver aer loaded
[    2.173171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.173176] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.173249] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.173250] ACPI: Power Button (FF) [PWRF]
[    2.173279] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.173281] ACPI: Power Button (CM) [PWRB]
[    2.173617] ACPI: SSDT CBE14C18, 038C (r1    AMI      IST        1 MSFT  3000001)
[    2.173831] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] - 3F, should be 1F [20080926]
[    2.173834] ACPI: SSDT CBE1DD18, 0084 (r1    AMI      CST        1 MSFT  3000001)
[    2.174315] Monitor-Mwait will be used to enter C-2 state
[    2.174317] Monitor-Mwait will be used to enter C-3 state
[    2.174325] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    2.174339] processor ACPI_CPU:00: registered as cooling_device0
[    2.174342] ACPI: Processor [P000] (supports 8 throttling states)
[    2.174808] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    2.174822] processor ACPI_CPU:01: registered as cooling_device1
[    2.174824] ACPI: Processor [P001] (supports 8 throttling states)
[    2.175301] ACPI: CPU2 (power states: C1[C1] C3[C3])
[    2.175314] processor ACPI_CPU:02: registered as cooling_device2
[    2.175316] ACPI: Processor [P002] (supports 8 throttling states)
[    2.175778] ACPI: CPU3 (power states: C1[C1] C3[C3])
[    2.175789] processor ACPI_CPU:03: registered as cooling_device3
[    2.175791] ACPI: Processor [P003] (supports 8 throttling states)
[    2.177713] isapnp: Scanning for PnP cards...
[    2.536092] isapnp: No Plug & Play device found
[    2.544575] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.544660] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.544904] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.545034] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.545099] 0000:00:16.3: ttyS1 at I/O 0xf100 (irq = 17) is a 16550A
[    2.545514] brd: module loaded
[    2.545714] loop: module loaded
[    2.545748] Fixed MDIO Bus: probed
[    2.545751] PPP generic driver version 2.4.2
[    2.545782] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.545797] Driver 'sd' needs updating - please use bus_type methods
[    2.545802] Driver 'sr' needs updating - please use bus_type methods
[    2.545841] ata_piix 0000:00:1f.2: version 2.12
[    2.545854] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.545858] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.700052] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.700149] scsi0 : ata_piix
[    2.700215] scsi1 : ata_piix
[    2.701256] ata1: SATA max UDMA/133 cmd 0xf0f0 ctl 0xf0e0 bmdma 0xf0b0 irq 19
[    2.701265] ata2: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf0b8 irq 19
[    3.496115] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.496138] ata1.01: SATA link down (SStatus 0 SControl 0)
[    3.504487] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    3.504491] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.520507] ata1.00: configured for UDMA/133
[    4.316101] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.316115] ata2.01: SATA link down (SStatus 0 SControl 0)
[    4.324266] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223C, ID01, max UDMA/100
[    4.340277] ata2.00: configured for UDMA/100
[    4.342091] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    4.342147] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.342156] sd 0:0:0:0: [sda] Write Protect is off
[    4.342157] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.342170] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.342207] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.342215] sd 0:0:0:0: [sda] Write Protect is off
[    4.342216] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.342229] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.342231]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.392164] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.392192] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.394206] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  ID01 PQ: 0 ANSI: 5
[    4.401455] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.401459] Uniform CD-ROM driver Revision: 3.20
[    4.401542] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.401562] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.401578] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.401585] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.556033] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    4.556058] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.556130] scsi2 : ata_piix
[    4.556176] scsi3 : ata_piix
[    4.557053] ata3: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf050 irq 19
[    4.557055] ata4: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf058 irq 19
[    4.895123] pata_acpi 0000:00:16.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.895141] pata_acpi 0000:00:16.2: setting latency timer to 64
[    4.895158] pata_acpi 0000:00:16.2: PCI INT C disabled
[    4.895193] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.895209] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.895225] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.895228] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    4.895256] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.899242] ehci_hcd 0000:00:1a.0: debug port 2
[    4.899251] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    4.899264] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe726000
[    4.912033] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.912106] usb usb1: configuration #1 chosen from 1 choice
[    4.912123] hub 1-0:1.0: USB hub found
[    4.912127] hub 1-0:1.0: 2 ports detected
[    4.912194] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.912206] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.912212] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    4.912233] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.916204] ehci_hcd 0000:00:1d.0: debug port 2
[    4.916213] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    4.916225] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe725000
[    4.932033] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.932105] usb usb2: configuration #1 chosen from 1 choice
[    4.932119] hub 2-0:1.0: USB hub found
[    4.932122] hub 2-0:1.0: 2 ports detected
[    4.932183] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.932192] uhci_hcd: USB Universal Host Controller Interface driver
[    4.932217] usbcore: registered new interface driver libusual
[    4.932231] usbcore: registered new interface driver usbserial
[    4.932237] USB Serial support registered for generic
[    4.932244] usbcore: registered new interface driver usbserial_generic
[    4.932245] usbserial: USB Serial Driver core
[    4.932270] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.932272] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.932657] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.936184] mice: PS/2 mouse device common for all mice
[    4.948207] rtc_cmos 00:06: RTC can wake from S4
[    4.948247] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    4.948278] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.948311] device-mapper: uevent: version 1.0.3
[    4.948371] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    4.948521] device-mapper: multipath: version 1.0.5 loaded
[    4.948523] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.948580] EISA: Probing bus 0 at eisa.0
[    4.948610] EISA: Detected 0 cards.
[    4.948784] cpuidle: using governor ladder
[    4.948871] cpuidle: using governor menu
[    4.949156] TCP cubic registered
[    4.949210] NET: Registered protocol family 10
[    4.949469] lo: Disabled Privacy Extensions
[    4.949641] NET: Registered protocol family 17
[    4.949650] Bluetooth: L2CAP ver 2.11
[    4.949651] Bluetooth: L2CAP socket layer initialized
[    4.949652] Bluetooth: SCO (Voice Link) ver 0.6
[    4.949653] Bluetooth: SCO socket layer initialized
[    4.949673] Bluetooth: RFCOMM socket layer initialized
[    4.949676] Bluetooth: RFCOMM TTY layer initialized
[    4.949677] Bluetooth: RFCOMM ver 1.10
[    4.949718] Marking TSC unstable due to TSC halts in idle
[    4.950523] Using IPI No-Shortcut mode
[    4.950559] registered taskstats version 1
[    4.950653]   Magic number: 10:899:183
[    4.950775] rtc_cmos 00:06: setting system clock to 2010-09-09 15:09:05 UTC (1284044945)
[    4.950777] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.950778] EDD information not available.
[    4.950897] Freeing unused kernel memory: 532k freed
[    4.951018] Write protecting the kernel text: 4128k
[    4.951085] Write protecting the kernel read-only data: 1532k
[    4.982663] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.224050] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    5.356624] usb 1-1: configuration #1 chosen from 1 choice
[    5.356822] hub 1-1:1.0: USB hub found
[    5.356978] hub 1-1:1.0: 6 ports detected
[    5.462704] PM: Starting manual resume from disk
[    5.462706] PM: Resume from partition 8:6
[    5.462707] PM: Checking hibernation image.
[    5.462923] PM: Resume from disk failed.
[    5.468281] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    5.488754] kjournald starting.  Commit interval 5 seconds
[    5.488761] EXT3-fs: mounted filesystem with ordered data mode.
[    5.600540] usb 2-1: configuration #1 chosen from 1 choice
[    5.600695] hub 2-1:1.0: USB hub found
[    5.600958] hub 2-1:1.0: 8 ports detected
[    5.672568] usb 1-1.5: new low speed USB device using ehci_hcd and address 3
[    5.769880] usb 1-1.5: configuration #1 chosen from 1 choice
[    8.784421] udev: starting version 141
[    8.854427] usbcore: registered new interface driver hiddev
[    8.856630] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[    8.872245] generic-usb 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1a.0-1.5/input0
[    8.872256] usbcore: registered new interface driver usbhid
[    8.872258] usbhid: v2.6:USB HID core driver
[    8.893460] parport_pc 00:04: reported by Plug and Play ACPI
[    8.893643] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.083623] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.129474] ppdev: user-space parallel port driver
[    9.527416] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.527640] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.558895] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.603607] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.603678] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.808659] lp0: using parport0 (interrupt-driven).
[    9.854616] Adding 176672k swap on /dev/sda6.  Priority:-1 extents:1 across:176672k
[   10.377905] EXT3 FS on sda5, internal journal
[   11.187314] type=1505 audit(1284025151.733:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1996
[   11.212586] type=1505 audit(1284025151.761:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2000
[   11.212630] type=1505 audit(1284025151.761:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2000
[   11.212651] type=1505 audit(1284025151.761:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2000
[   11.212670] type=1505 audit(1284025151.761:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2000
[   11.282141] type=1505 audit(1284025151.829:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2005
[   11.282204] type=1505 audit(1284025151.829:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2005
[   11.296916] type=1505 audit(1284025151.845:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2009
[   12.328393] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.328395] Bluetooth: BNEP filters: protocol multicast
[   12.334641] Bridge firewalling registered

---

### Post by bredman on 2010-09-09
It looks like your Ethernet hardware is "Ethernet controller: Intel Corporation Device 10f0 (rev 06)" but is not being recognised.

I did a quick search on the internet and found a common suggestion, see
[http://osdir.com/ml/debian-bugs-dist/2010-05/msg01317.html](http://osdir.com/ml/debian-bugs-dist/2010-05/msg01317.html)
as an example.

To summarise the possible solution...
Open a terminal (CTRL-ALT-t)
Enter the following commands
sudo modprobe e1000e
sudo dhclient

You will be asked for your password. Ignore the warnings from the modprobe command.

Then enter the command ifconfig again to see if an interface with the name eth0 (or similar) appears.

---

### Post by bredman on 2010-09-09
Apologies, I just noticed that you have ancient hardware, and the module that I recommended is for gigabit Ethernet, which may not work.

If "e1000e" does not work, try again with "e1000" and "e100".

This will step you backwards from gigabit ethernet through to 100 megabit ethernet, and hopefully something will match your hardware.

---

### Post by Nikhil_07n on 2010-09-09
Umm. Actually I mistyped that part. This machine is quite new.
core i5 760 on a Intel DH55TC.

Here's what I did. That didn't solve the problem.

nikhil@SideWinder:~$ sudo modprobe e1000e
[sudo] password for nikhil: 
nikhil@SideWinder:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/c6:7a:3c:f6:3d:8f
Sending on   LPF/pan0/c6:7a:3c:f6:3d:8f
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
nikhil@SideWinder:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr c6:7a:3c:f6:3d:8f  
          inet6 addr: fe80::c47a:3cff:fef6:3d8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5521 (5.5 KB)

pan0:avahi Link encap:Ethernet  HWaddr c6:7a:3c:f6:3d:8f  
          inet addr:169.254.7.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

Sorry, but would you mind posting some information about what am I dealing with here.

Thanks.

---

### Post by bredman on 2010-09-09
Did you try the commands
sudo modprobe e1000
sudo modprobe e100

You can forget about the dhclient command for the moment. What you are looking for is the ifconfig command to show an eth0 device or similar. At the moment it only shows "lo" which is a loopback for test purposes, and "pan0" which is your bluetooth connection.

Is there a cable plugged from your Ethernet port to a router? Are there any green/yellow lights on your Ethernet port?

---

### Post by Nikhil_07n on 2010-09-12
Sorry for no posting for a while. I tried figuring it out on my own. Looked like a driver problem to me(Network adapter unclaimed). So I searched for network drivers by intel, but didn't find any for 9.04([link](http://www.intel.com/support/motherboards/desktop/dh55tc/sb/CS-031186.htm).

So, I removed 9.04 completely and installed 10.04.1. Well, I didn't have any problems with network in it. Just click & GO!

So, for now, this case is closed. Thanks for the replies bredman.

---

