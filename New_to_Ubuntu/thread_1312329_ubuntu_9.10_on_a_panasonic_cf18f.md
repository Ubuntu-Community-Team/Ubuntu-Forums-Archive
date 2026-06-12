---
title: "ubuntu 9.10 on a panasonic cf18f"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Bondy29 on 2009-11-03
I have recently picked up a Panasonic toughbook cf-18 with a blank hard drive and I have installed ubuntu 9.10. so far I can get it working like a normal laptop however I the two main features that I want/ need do not work.  

These two features are the touchscreen and the wireless, I know that the toughbook has both but still can not get them working. 

If any one can help it would be much appreseated.

---

### Post by lavinog on 2009-11-03
First thing that would be needed is to find out what hardware is installed.
Do the following in the terminal:
```

lshw > lshw.txt
lspci > lspci.txt
lsusb > lsusb.txt
dmesg > dmesg.txt
tar cvvzf hwreports.tar.gz lshw.txt lspci.txt lsusb.txt dmesg.txt

```
then attach the hwreports.tar.gz

Also did you install the 32bit or 64bit ubuntu?

---

### Post by Bondy29 on 2009-11-03
I installed the 64bit ubuntu.

lshw =

description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 600MHz
          capacity: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:9 memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:9 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:2000(size=4096) memory:e0200000-e02fffff memory:20000000-27ffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 8a
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00202010-b0020200f irq:9 memory:e0201000-e0201fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff(prefetchable) memory:2c000000-2fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 8a
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603010-b0060300f irq:9 memory:e0202000-e0202fff ioport:2c00(size=256) ioport:1400(size=256) memory:24000000-27ffffff(prefetchable) memory:30000000-33ffffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:01:02.0
                logical name: eth0
                version: 10
                serial: 00:0b:97:30:f5:34
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=32 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:9 ioport:2000(size=256) memory:e0200000-e02000ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:28000000-280003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

lspci =
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8a)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8a)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


lsusb = 

Bus 001 Device 002: ID 059f:0643 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg =

[    0.144388] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.144392] ACPI: EC: driver started in interrupt mode
[    0.144666] ACPI: No dock devices found.
[    0.145564] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.145753] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.145761] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.145769] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.145794] pci 0000:00:02.0: supports D1
[    0.145819] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.145827] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.145854] pci 0000:00:02.1: supports D1
[    0.145933] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.145992] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.146050] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.146114] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.146174] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.146181] pci 0000:00:1d.7: PME# disabled
[    0.146274] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.146281] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.146309] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.146318] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.146327] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.146337] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.146346] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.146356] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.146411] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.146459] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.146468] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.146477] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.146486] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.146518] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.146524] pci 0000:00:1f.5: PME# disabled
[    0.146569] pci 0000:01:00.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.146589] pci 0000:01:00.0: supports D1 D2
[    0.146594] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.146600] pci 0000:01:00.0: PME# disabled
[    0.146634] pci 0000:01:00.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.146654] pci 0000:01:00.1: supports D1 D2
[    0.146658] pci 0000:01:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.146665] pci 0000:01:00.1: PME# disabled
[    0.146707] pci 0000:01:02.0: reg 10 io port: [0x2000-0x20ff]
[    0.146717] pci 0000:01:02.0: reg 14 32bit mmio: [0xe0200000-0xe02000ff]
[    0.146759] pci 0000:01:02.0: supports D1 D2
[    0.146763] pci 0000:01:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.146769] pci 0000:01:02.0: PME# disabled
[    0.146810] pci 0000:00:1e.0: transparent bridge
[    0.146818] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.146824] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe02fffff]
[    0.146868] pci_bus 0000:00: on NUMA node 0
[    0.146875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.147008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.150271] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    0.150491] ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
[    0.150708] ACPI: PCI Interrupt Link [LNKC] (IRQs *9)
[    0.150924] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[    0.151138] ACPI: PCI Interrupt Link [LNKE] (IRQs *9)
[    0.151351] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.151568] ACPI: PCI Interrupt Link [LNKG] (IRQs 9) *0, disabled.
[    0.151784] ACPI: PCI Interrupt Link [LNKH] (IRQs *9)
[    0.152089] SCSI subsystem initialized
[    0.152151] libata version 3.00 loaded.
[    0.152265] usbcore: registered new interface driver usbfs
[    0.152292] usbcore: registered new interface driver hub
[    0.152336] usbcore: registered new device driver usb
[    0.152547] ACPI: WMI: Mapper loaded
[    0.152550] PCI: Using ACPI for IRQ routing
[    0.152752] Bluetooth: Core ver 2.15
[    0.152795] NET: Registered protocol family 31
[    0.152798] Bluetooth: HCI device and connection manager initialized
[    0.152803] Bluetooth: HCI socket layer initialized
[    0.152806] NetLabel: Initializing
[    0.152810] NetLabel:  domain hash size = 128
[    0.152813] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.152836] NetLabel:  unlabeled traffic allowed by default
[    0.155642] pnp: PnP ACPI init
[    0.155662] ACPI: bus type pnp registered
[    0.215245] pnp: PnP ACPI: found 11 devices
[    0.215250] ACPI: ACPI bus type pnp unregistered
[    0.215258] PnPBIOS: Disabled by ACPI PNP
[    0.215277] system 00:01: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.215283] system 00:01: iomem range 0xcd800-0xcffff could not be reserved
[    0.215295] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.215301] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.215307] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.215313] system 00:02: ioport range 0x600-0x61f has been reserved
[    0.215318] system 00:02: ioport range 0x362-0x362 has been reserved
[    0.215324] system 00:02: ioport range 0x366-0x366 has been reserved
[    0.215330] system 00:02: ioport range 0xfe00-0xfe01 has been reserved
[    0.215335] system 00:02: ioport range 0x580-0x587 has been reserved
[    0.215342] system 00:02: iomem range 0xff800000-0xffffffff could not be reserved
[    0.250099] AppArmor: AppArmor Filesystem Enabled
[    0.250151] pci 0000:01:00.0: CardBus bridge, secondary bus 0000:02
[    0.250157] pci 0000:01:00.0:   IO window: 0x002400-0x0024ff
[    0.250164] pci 0000:01:00.0:   IO window: 0x002800-0x0028ff
[    0.250171] pci 0000:01:00.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.250178] pci 0000:01:00.0:   MEM window: 0x2c000000-0x2fffffff
[    0.250185] pci 0000:01:00.1: CardBus bridge, secondary bus 0000:03
[    0.250190] pci 0000:01:00.1:   IO window: 0x002c00-0x002cff
[    0.250196] pci 0000:01:00.1:   IO window: 0x001400-0x0014ff
[    0.250203] pci 0000:01:00.1:   PREFETCH window: 0x24000000-0x27ffffff
[    0.250210] pci 0000:01:00.1:   MEM window: 0x30000000-0x33ffffff
[    0.250217] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.250223] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.250231] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    0.250238] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x27ffffff
[    0.250256] pci 0000:00:1e.0: setting latency timer to 64
[    0.250497] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    0.250501] PCI: setting IRQ 9 as level-triggered
[    0.250508] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.250725] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[    0.250732] pci 0000:01:00.1: PCI INT B -> Link[LNKE] -> GSI 9 (level, low) -> IRQ 9
[    0.250742] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.250747] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.250753] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.250758] pci_bus 0000:01: resource 1 mem: [0xe0200000-0xe02fffff]
[    0.250763] pci_bus 0000:01: resource 2 pref mem [0x20000000-0x27ffffff]
[    0.250768] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.250773] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.250779] pci_bus 0000:02: resource 0 io:  [0x2400-0x24ff]
[    0.250783] pci_bus 0000:02: resource 1 io:  [0x2800-0x28ff]
[    0.250789] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.250794] pci_bus 0000:02: resource 3 mem: [0x2c000000-0x2fffffff]
[    0.250799] pci_bus 0000:03: resource 0 io:  [0x2c00-0x2cff]
[    0.250804] pci_bus 0000:03: resource 1 io:  [0x1400-0x14ff]
[    0.250809] pci_bus 0000:03: resource 2 pref mem [0x24000000-0x27ffffff]
[    0.250814] pci_bus 0000:03: resource 3 mem: [0x30000000-0x33ffffff]
[    0.250869] NET: Registered protocol family 2
[    0.251020] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.251460] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.251622] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.251783] TCP: Hash tables configured (established 16384 bind 16384)
[    0.251788] TCP reno registered
[    0.251897] NET: Registered protocol family 1
[    0.252011] Trying to unpack rootfs image as initramfs...
[    0.626188] Freeing initrd memory: 7464k freed
[    0.634492] Simple Boot Flag at 0x41 set to 0x1
[    0.634641] cpufreq-nforce2: No nForce2 chipset.
[    0.634687] Scanning for low memory corruption every 60 seconds
[    0.634934] audit: initializing netlink socket (disabled)
[    0.634986] type=2000 audit(1257237124.631:1): initialized
[    0.650957] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.653563] VFS: Disk quotas dquot_6.5.2
[    0.653662] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.654623] fuse init (API version 7.12)
[    0.654774] msgmni has been set to 975
[    0.655120] alg: No test for stdrng (krng)
[    0.655141] io scheduler noop registered
[    0.655145] io scheduler anticipatory registered
[    0.655149] io scheduler deadline registered
[    0.655227] io scheduler cfq registered (default)
[    0.655254] pci 0000:00:02.0: Boot video device
[    0.655477] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.655519] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.658558] ACPI: AC Adapter [AC] (on-line)
[    0.658661] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.658668] ACPI: Power Button [PWRF]
[    0.658766] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.658774] ACPI: Power Button [PWRB]
[    0.658859] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.666407] ACPI: Lid Switch [LID]
[    0.666926] Marking TSC unstable due to TSC halts in idle
[    0.666953] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.666994] processor LNXCPU:00: registered as cooling_device0
[    0.667001] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.668106] Switched to high resolution mode on CPU 0
[    0.718038] thermal LNXTHERM:01: registered as thermal_zone0
[    0.718053] ACPI: Thermal Zone [TZC] (40 C)
[    0.718127] isapnp: Scanning for PnP cards...
[    1.072558] isapnp: No Plug & Play device found
[    1.074489] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.074628] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.074731] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.075254] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.075414] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.077108] brd: module loaded
[    1.077897] loop: module loaded
[    1.078024] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.078199] ata_piix 0000:00:1f.1: version 2.13
[    1.078263] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    1.078272] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.078504] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[    1.078513] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[    1.078569] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.078666] scsi0 : ata_piix
[    1.078827] scsi1 : ata_piix
[    1.080280] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.080286] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.081689] Fixed MDIO Bus: probed
[    1.081750] PPP generic driver version 2.4.2
[    1.081889] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.082135] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[    1.082143] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 9 (level, low) -> IRQ 9
[    1.082158] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.082164] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.082248] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.086181] ehci_hcd 0000:00:1d.7: debug port 1
[    1.086189] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.086834] ata2: port disabled. ignoring.
[    1.086860] ehci_hcd 0000:00:1d.7: irq 9, io mem 0xe0100000
[    1.100030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.100172] usb usb1: configuration #1 chosen from 1 choice
[    1.100224] hub 1-0:1.0: USB hub found
[    1.100239] hub 1-0:1.0: 6 ports detected
[    1.100339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100366] uhci_hcd: USB Universal Host Controller Interface driver
[    1.100403] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    1.100412] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.100418] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.100475] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.100500] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001820
[    1.100634] usb usb2: configuration #1 chosen from 1 choice
[    1.100681] hub 2-0:1.0: USB hub found
[    1.100692] hub 2-0:1.0: 2 ports detected
[    1.100975] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    1.100982] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    1.100991] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.100996] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.101053] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.101078] uhci_hcd 0000:00:1d.1: irq 9, io base 0x00001840
[    1.101207] usb usb3: configuration #1 chosen from 1 choice
[    1.101253] hub 3-0:1.0: USB hub found
[    1.101264] hub 3-0:1.0: 2 ports detected
[    1.101329] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[    1.101338] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.101344] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.101396] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.101421] uhci_hcd 0000:00:1d.2: irq 9, io base 0x00001860
[    1.101546] usb usb4: configuration #1 chosen from 1 choice
[    1.101592] hub 4-0:1.0: USB hub found
[    1.101602] hub 4-0:1.0: 2 ports detected
[    1.101748] PNP: PS/2 Controller [PNP0303:K101,FJC6000:MOU2] at 0x60,0x64 irq 1,12
[    1.110783] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.115496] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.115505] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.115510] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.115516] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.115521] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.115618] mice: PS/2 mouse device common for all mice
[    1.115806] rtc_cmos 00:05: RTC can wake from S4
[    1.115862] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.115887] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.116126] device-mapper: uevent: version 1.0.3
[    1.116255] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.116410] device-mapper: multipath: version 1.1.0 loaded
[    1.116415] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.116625] EISA: Probing bus 0 at eisa.0
[    1.116634] Cannot allocate resource for EISA slot 1
[    1.116638] Cannot allocate resource for EISA slot 2
[    1.116668] EISA: Detected 0 cards.
[    1.117408] cpuidle: using governor ladder
[    1.117511] cpuidle: using governor menu
[    1.118306] TCP cubic registered
[    1.118582] NET: Registered protocol family 10
[    1.119296] lo: Disabled Privacy Extensions
[    1.119829] NET: Registered protocol family 17
[    1.119878] Bluetooth: L2CAP ver 2.13
[    1.119882] Bluetooth: L2CAP socket layer initialized
[    1.119887] Bluetooth: SCO (Voice Link) ver 0.6
[    1.119890] Bluetooth: SCO socket layer initialized
[    1.119932] Bluetooth: RFCOMM TTY layer initialized
[    1.119937] Bluetooth: RFCOMM socket layer initialized
[    1.119940] Bluetooth: RFCOMM ver 1.11
[    1.120233] Using IPI No-Shortcut mode
[    1.120336] PM: Resume from disk failed.
[    1.120361] registered taskstats version 1
[    1.120517]   Magic number: 1:579:522
[    1.120616] rtc_cmos 00:05: setting system clock to 2009-11-03 08:32:06 UTC (1257237126)
[    1.120622] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.120625] EDD information not available.
[    1.148899] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.248562] ata1.00: ATA-6: HTS548080M9AT00, MG4OA53A, max UDMA/100
[    1.248568] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.264482] ata1.00: configured for UDMA/100
[    1.412045] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.452292] ACPI: Battery Slot [BATA] (battery present)
[    1.452716] scsi 0:0:0:0: Direct-Access     ATA      HTS548080M9AT00  MG4O PQ: 0 ANSI: 5
[    1.452916] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.452984] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.453065] sd 0:0:0:0: [sda] Write Protect is off
[    1.453070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.453112] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.453317]  sda: sda1 sda2 < sda5 >
[    1.493392] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.493416] Freeing unused kernel memory: 540k freed
[    1.493895] Write protecting the kernel text: 4568k
[    1.493960] Write protecting the kernel read-only data: 1836k
[    1.612671] usb 1-2: configuration #1 chosen from 1 choice
[    1.768377] Linux agpgart interface v0.103
[    1.798987] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    1.800135] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[    1.802012] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    1.883648] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input5
[    1.883722] ACPI: Video Device [GRFX] (multi-head: yes  rom: no  post: no)
[    1.947663] [drm] Initialized drm 1.1.0 20060810
[    1.973813] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    1.973824] i915 0000:00:02.0: setting latency timer to 64
[    1.996335] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.996376] 8139cp 0000:01:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.001853] 8139too Fast Ethernet driver 0.9.28
[    2.001897] 8139too 0000:01:02.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    2.003178] eth0: RealTek RTL8139 at 0x2000, 00:0b:97:30:f5:34, IRQ 9
[    2.026313] Initializing USB Mass Storage driver...
[    2.026443] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.026567] usbcore: registered new interface driver usb-storage
[    2.026573] USB Mass Storage support registered.
[    2.027596] usb-storage: device found at 2
[    2.027600] usb-storage: waiting for device to settle before scanning
[    2.051394] i2c-adapter i2c-1: unable to read EDID block.
[    2.051401] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.385593] [drm] DAC-6: set mode 640x480 0
[    2.894179] i2c-adapter i2c-1: unable to read EDID block.
[    2.894185] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.900974] [drm] fb0: inteldrmfb frame buffer device
[    2.900990] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.990773] render error detected, EIR: 0x00000010
[    2.990779] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.990806] render error detected, EIR: 0x00000010
[    3.001132] [drm] LVDS-8: set mode 1024x768 d
[    3.047547] Console: switching to colour frame buffer device 128x48
[    3.433346] PM: Starting manual resume from disk
[    3.433354] PM: Resume from partition 8:5
[    3.433357] PM: Checking hibernation image.
[    3.433517] PM: Resume from disk failed.
[    3.463259] EXT4-fs (sda1): barriers enabled
[    3.490304] kjournald2 starting: pid 352, dev sda1:8, commit interval 5 seconds
[    3.490321] EXT4-fs (sda1): delayed allocation enabled
[    3.490326] EXT4-fs: file extents enabled
[    3.506554] EXT4-fs: mballoc enabled
[    3.506578] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.324435] type=1505 audit(1257237129.703:2): operation="profile_load" pid=375 name=/usr/share/gdm/guest-session/Xsession
[    4.327862] type=1505 audit(1257237129.703:3): operation="profile_load" pid=376 name=/sbin/dhclient3
[    4.329034] type=1505 audit(1257237129.707:4): operation="profile_load" pid=376 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.329666] type=1505 audit(1257237129.707:5): operation="profile_load" pid=376 name=/usr/lib/connman/scripts/dhclient-script
[    4.376689] type=1505 audit(1257237129.755:6): operation="profile_load" pid=377 name=/usr/bin/evince
[    4.394774] type=1505 audit(1257237129.771:7): operation="profile_load" pid=377 name=/usr/bin/evince-previewer
[    4.405396] type=1505 audit(1257237129.783:8): operation="profile_load" pid=377 name=/usr/bin/evince-thumbnailer
[    4.432170] type=1505 audit(1257237129.811:9): operation="profile_load" pid=379 name=/usr/lib/cups/backend/cups-pdf
[    6.417600] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k 
[    6.628972] udev: starting version 147
[    6.694576] EXT4-fs (sda1): internal journal on sda1:8
[    7.024250] usb-storage: device scan complete
[    7.029387] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082N  LA00 PQ: 0 ANSI: 0
[    7.060468] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.060477] Uniform CD-ROM driver Revision: 3.20
[    7.060728] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    7.060865] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    7.198582] intel_rng: FWH not detected
[    7.450018] input: Panasonic Laptop Support as /devices/virtual/input/input6
[    7.467610] lp: driver loaded but no devices found
[    7.839249] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.866437] yenta_cardbus 0000:01:00.0: CardBus bridge found [10f7:8338]
[    8.992777] yenta_cardbus 0000:01:00.0: ISA IRQ mask 0x0cb8, PCI irq 9
[    8.992785] yenta_cardbus 0000:01:00.0: Socket status: 30000006
[    8.992797] yenta_cardbus 0000:01:00.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    8.992804] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[    8.993193] yenta_cardbus 0000:01:00.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[    8.993199] yenta_cardbus 0000:01:00.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[    8.993432] yenta_cardbus 0000:01:00.1: CardBus bridge found [10f7:8338]
[    9.120782] yenta_cardbus 0000:01:00.1: ISA IRQ mask 0x0cb8, PCI irq 9
[    9.120790] yenta_cardbus 0000:01:00.1: Socket status: 30000006
[    9.120798] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #03 to #06
[    9.120813] yenta_cardbus 0000:01:00.1: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    9.120819] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x2000-0x2fff: clean.
[    9.121214] yenta_cardbus 0000:01:00.1: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[    9.121220] yenta_cardbus 0000:01:00.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[    9.134480] input: LBPS/2 Fujitsu Lifebook TouchScreen as /devices/platform/i8042/serio3/input/input7
[    9.323374] psmouse serio4: ID: 10 00 64
[    9.810546] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[    9.812248] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[    9.812973] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[    9.813586] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[    9.814431] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[    9.828288] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    9.828297] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    9.828417] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    9.830423] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    9.832104] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[    9.832816] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    9.833429] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    9.834268] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    9.887324] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input8
[   10.152048] intel8x0_measure_ac97_clock: measured 55131 usecs (2656 samples)
[   10.152055] intel8x0: clocking to 48000
[   12.956004] __ratelimit: 6 callbacks suppressed
[   12.956047] type=1505 audit(1257237138.331:12): operation="profile_replace" pid=815 name=/usr/share/gdm/guest-session/Xsession
[   12.959310] type=1505 audit(1257237138.335:13): operation="profile_replace" pid=816 name=/sbin/dhclient3
[   12.960494] type=1505 audit(1257237138.339:14): operation="profile_replace" pid=816 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.961128] type=1505 audit(1257237138.339:15): operation="profile_replace" pid=816 name=/usr/lib/connman/scripts/dhclient-script
[   12.969019] type=1505 audit(1257237138.347:16): operation="profile_replace" pid=817 name=/usr/bin/evince
[   12.994051] type=1505 audit(1257237138.371:17): operation="profile_replace" pid=817 name=/usr/bin/evince-previewer
[   13.005904] type=1505 audit(1257237138.383:18): operation="profile_replace" pid=817 name=/usr/bin/evince-thumbnailer
[   13.020883] type=1505 audit(1257237138.399:19): operation="profile_replace" pid=820 name=/usr/lib/cups/backend/cups-pdf
[   13.022559] type=1505 audit(1257237138.399:20): operation="profile_replace" pid=820 name=/usr/sbin/cupsd
[   13.027183] type=1505 audit(1257237138.403:21): operation="profile_replace" pid=821 name=/usr/sbin/tcpdump
[   13.712338] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   15.157023] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.817951] [drm] DAC-6: set mode 640x480 0
[   18.361089] [drm] DAC-6: set mode 640x480 0
[   18.828406] i2c-adapter i2c-1: unable to read EDID block.
[   18.828414] i915 0000:00:02.0: LVDS-1: no EDID data
[   18.900345] [drm] DAC-6: set mode 640x480 0
[   19.395203] [drm] DAC-6: set mode 640x480 0
[   19.825453] ppdev: user-space parallel port driver
[   19.953879] i2c-adapter i2c-1: unable to read EDID block.
[   19.953891] i915 0000:00:02.0: LVDS-1: no EDID data
[   23.784034] eth0: no IPv6 routers present
[   25.838592] [drm] DAC-6: set mode 640x480 0
[   26.330829] [drm] DAC-6: set mode 640x480 0
[   26.794871] i2c-adapter i2c-1: unable to read EDID block.
[   26.794879] i915 0000:00:02.0: LVDS-1: no EDID data
[   26.878376] [drm] DAC-6: set mode 640x480 0
[   27.371144] [drm] DAC-6: set mode 640x480 0
[   27.862677] i2c-adapter i2c-1: unable to read EDID block.
[   27.862686] i915 0000:00:02.0: LVDS-1: no EDID data
[   28.092103] [drm] DAC-6: set mode 640x480 0
[   28.584202] [drm] DAC-6: set mode 640x480 0
[   29.048044] i2c-adapter i2c-1: unable to read EDID block.
[   29.048052] i915 0000:00:02.0: LVDS-1: no EDID data
[   37.244128] Clocksource tsc unstable (delta = -120670820 ns)
[   41.995992] [drm] DAC-6: set mode 640x480 0
[   42.487990] [drm] DAC-6: set mode 640x480 0
[   42.954364] i2c-adapter i2c-1: unable to read EDID block.
[   42.954375] i915 0000:00:02.0: LVDS-1: no EDID data
[   43.067207] [drm] DAC-6: set mode 640x480 0
[   43.567530] [drm] DAC-6: set mode 640x480 0
[   44.032230] i2c-adapter i2c-1: unable to read EDID block.
[   44.032238] i915 0000:00:02.0: LVDS-1: no EDID data
[   44.152385] [drm] DAC-6: set mode 640x480 0
[   44.662148] [drm] DAC-6: set mode 640x480 0
[   45.133077] i2c-adapter i2c-1: unable to read EDID block.
[   45.133086] i915 0000:00:02.0: LVDS-1: no EDID data
[   47.200422] [drm] DAC-6: set mode 640x480 0
[   47.691957] [drm] DAC-6: set mode 640x480 0
[   48.150595] i2c-adapter i2c-1: unable to read EDID block.
[   48.150602] i915 0000:00:02.0: LVDS-1: no EDID data
[  243.246534] UDF-fs: Partition marked readonly; forcing readonly mount
[  243.305991] UDF-fs INFO UDF: Mounting volume 'NEWDISC', timestamp 2009/10/29 19:46 (11e0)


I am not sure if this is what you need. if you need more then I will prove that to. 

Thank you

---

### Post by Bondy29 on 2009-11-03
If I can get Bluetooth working to that would be handy. but I am not sure if you can tell if my cf18 is fitted with it from what is there

---

### Post by lavinog on 2009-11-03
```
[ 9.134480] input: LBPS/2 Fujitsu Lifebook TouchScreen as /devices/platform/i8042/serio3/input/input7
```

this looks like your touchscreen...I haven't been able to find anything on about it.
you may want to look at this page: [https://help.ubuntu.com/community/TabletSetup](https://help.ubuntu.com/community/TabletSetup)
```
cat /sys/bus/usb/devices/*/product
```

I don't see any wireless devices detected.  I also can't find any specs for this laptop online.  Is the wireless switch turned on?

---

### Post by Bondy29 on 2009-11-04
my system gives me this as the wireless card. To get this I typed" sudo lshw -C network" which is from the help tab.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:0b:97:30:f5:34
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:9 ioport:2000(size=256) memory:e0200000-e02000ff


yet it appears that the standard wireless card could be a:

Intel PRO/Wireless 2915ABG [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]network[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/#") 802.11a/b/g.

how can I turn on the wireless switch?

I so far have not been able to get the touch scren working with the advice in the last thread but I am going to keep trying 

Thank you

---

### Post by lavinog on 2009-11-04
> **Bondy29 said:**
> my system gives me this as the wireless card. To get this I typed" sudo lshw -C network" which is from the help tab.
```

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:0b:97:30:f5:34
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:9 ioport:2000(size=256) memory:e0200000-e02000ff

```

this is your ethernet card, not your wireless card.

> 
yet it appears that the standard wireless card could be a:

Intel PRO/Wireless 2915ABG [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]network[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/#") 802.11a/b/g.

how can I turn on the wireless switch?

The information you posted doesn't mention a 2915 anything.  I assume that this laptop is a couple of years (at least 4) old.  Is it recent enough to have a 802.11a capable card?

Many laptops have a physical switch or a button to turn on/off the wireless radio to conserve the battery.  Some laptops use the fn key combined with another key on the keyboard. (many laptops use Fn+F2)

What happens when you do this:
```

sudo modprobe ipw2200
dmesg|tail

```

---

### Post by Bondy29 on 2009-11-04
This is what I got when I ran the last code

[   54.994655] [drm] DAC-6: set mode 640x480 0
[   55.486169] [drm] DAC-6: set mode 640x480 0
[   55.963274] i2c-adapter i2c-1: unable to read EDID block.
[   55.963281] i915 0000:00:02.0: LVDS-1: no EDID data
[  100.413193] lib80211: common routines for IEEE802.11 drivers
[  100.413204] lib80211_crypt: registered algorithm 'NULL'
[  100.452956] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  100.452966] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  100.485513] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  100.485523] ipw2200: Copyright(c) 2003-2006 Intel Corporation

I Hope this helps.

---

### Post by lavinog on 2009-11-05
What about this:
```
sudo modprobe ipw2200
lspci

```

---

### Post by Bondy29 on 2009-11-05
This what I got back after I typed the modprobe ipw2000 code.

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8a)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8a)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by lavinog on 2009-11-05
I don't see anything that looks like a wireless card.
Are you sure this has wireless?  Does the wireless work with windows?

---

### Post by Bondy29 on 2009-11-06
yes the wireless was working in windows. and I thought all of this was the wireless card information.

 lib80211: common routines for IEEE802.11 drivers
[  100.413204] lib80211_crypt: registered algorithm 'NULL'
[  100.452956] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  100.452966] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  100.485513] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  100.485523] ipw2200: Copyright(c) 2003-2006 Intel Corporation

As you can see Ubuntu seems to be registering wireless in some form with the antenna wireless symbol next to the battery in the top right hand corner of the attached file or is that a standard feature regardless of if there is wireless or not.

---

### Post by lavinog on 2009-11-06
> **Bondy29 said:**
> yes the wireless was working in windows. and I thought all of this was the wireless card information.

 lib80211: common routines for IEEE802.11 drivers
[  100.413204] lib80211_crypt: registered algorithm 'NULL'
[  100.452956] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  100.452966] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  100.485513] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  100.485523] ipw2200: Copyright(c) 2003-2006 Intel Corporation

I get that same message on my desktop (no wireless cards)
lspci should say if you have a wireless card, and I didn't see anything.
> 
As you can see Ubuntu seems to be registering wireless in some form with the antenna wireless symbol next to the battery in the top right hand corner of the attached file or is that a standard feature regardless of if there is wireless or not.
what happens when you click on the icon?

Do you still have windows available to see what wireless card is detected by windows?

---

### Post by smdahmed on 2009-11-08
I seem to have a similar problem to that of yourself. Can you please try to boot up using the recovery option of the kernel.

Once you are presented with the recovery options, continue to choose 'Proceed with the normal boot'. Login with your login credentials and then give the command 'startx'.

You should be presented with the normal GUI and let us know if you see the wifi working.

Good Luck.

---

