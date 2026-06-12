---
title: "Looking for network card help"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by randy_pierson on 2007-02-28
I'm trying to install an old 3Com EtherlinkIII network card # 3C5098-TP, it has a 3Com 40-0130-003 chip. Edgy more or less ignores the card. Does anyone know what I need to do to get this card to work?

---

### Post by RomeReactor on 2007-02-28
Hi. First we need to know what chipset of your card has, so please type

```
lspci
```

into the terminal (Applications-->Accessories-->Terminal) and press enter; post back the output it gives you.

---

### Post by randy_pierson on 2007-02-28
Terminal says; bash: ispci: command not found.

---

### Post by randy_pierson on 2007-02-28
i love fonts, my bad,

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

---

### Post by rjfioravanti on 2007-02-28
lspci  not ispci

---

### Post by randy_pierson on 2007-02-28
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)
 

sorry for the confusion
:oops:

---

### Post by RomeReactor on 2007-02-28
That's odd, i don't see your wireless installed, only the ethernet; are you sure the card is properly installed? Try running

```
lshw
```

in the terminal and post back the output please.

---

### Post by randy_pierson on 2007-02-28
the card is a ethernet (AUI,10Base-T)

---

### Post by RomeReactor on 2007-02-28
So it's a **wired** connection? my mistake, thought you were talking about wireless. I'm not very knowledgeable about ethernet cards. I assume it isn't this one?

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
**00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)**
00:0f.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

---

### Post by randy_pierson on 2007-02-28
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 215MB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.5
          size: 400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 620 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: e0000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE
             resources: ioport:4000-400f irq:14
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD84AA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 8063MB
              *-cdrom
                   product: ATAPI CDROM
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capabilities: packet
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   product: SAMSUNG SV0432D
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 4112MB
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=sis5595_smbus
        *-generic UNCLAIMED
             product: ACPI
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.1
             bus info: pci@00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
        *-usb
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e5901000-e5901fff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-11-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: Generic USB Hub
                   vendor: ALCOR
                   physical id: 2
                   bus info: usb@1:2
                   version: 3.12
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: Generic USB device
                      product: CIF Single Chip
                      vendor: Pixart Imaging Inc.
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=spca5xx maxpower=500mA speed=12.0MB/s
                 *-usb:1
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: Logitech
                      physical id: 4
                      bus info: usb@1:2.4
                      version: 21.10
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 530/620 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 2a
                size: 8MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                resources: iomemory:e5000000-e57fffff iomemory:e5800000-e580ffff ioport:c000-c07f irq:11
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: Linksys
             physical id: d
             bus info: pci@00:0d.0
             logical name: eth1
             version: 11
             serial: 00:18:f8:08:1f:04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip ip=xxx.xxx.xxx.xxx multicast=yes
             resources: ioport:d000-d0ff iomemory:e5900000-e59003ff irq:10
        *-multimedia
             description: Multimedia audio controller
             product: ES1969 Solo-1 Audiodrive
             vendor: ESS Technology
             physical id: f
             bus info: pci@00:0f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ESS ES1938 (Solo-1)
             resources: ioport:d400-d43f ioport:d800-d80f ioport:dc00-dc0f ioport:e000-e003 ioport:e400-e403 irq:12

---

### Post by randy_pierson on 2007-02-28
](*,)

---

