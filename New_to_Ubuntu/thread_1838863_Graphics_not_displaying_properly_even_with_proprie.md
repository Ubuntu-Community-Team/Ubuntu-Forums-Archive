---
title: "Graphics not displaying properly even with proprietary driver"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by eversilentone on 2011-09-04
Hi, I have a Radeon HD 5800 (not sure how to find out which) and I have the proprietary driver installed.  I can watch movies, etc, and play some games, but I don't think the 3D part is working properly?  I want to play Guild Wars and I've installed it ok, but it doesn't display the log on screen, only the graphics behind it.  Wine site says it's platinum and should run fine and to check other games.

Supertuxkart also uses 3D and Wine suggested I test that before "blaming" it, and sure enough it doesn't work.  So I'm stumped - I'm not after help running the games so much as how can I make sure my graphics card works properly?
```
james@james-System-Product-Name:~$ lshw
WARNING: you should run this program as super-user.
james-system-product-name 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 4022MiB
     *-cpu
          product: AMD Phenom(tm) II X6 1055T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.10.0
          size: 2800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RD890 Northbridge only single slot PCI-e GFX Hydra part
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:72 ioport:e000(size=4096) memory:fe900000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Radeon HD 5800 Series (Cypress LE)
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:87 memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:e000(size=256) memory:fe9c0000-fe9dffff
           *-multimedia
                description: Audio device
                product: Cypress HDMI Audio [Radeon HD 5800 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:86 memory:fe9bc000-fe9bffff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:73 ioport:d000(size=4096) memory:fe800000-fe8fffff
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:44 memory:fe8fe000-fe8fffff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:45 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16)
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port E)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:74 ioport:c000(size=4096) memory:fe700000-fe7fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:46 memory:fe7ff800-fe7fffff ioport:c800(size=256)
        *-pci:3
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:75 ioport:b000(size=4096) memory:fe600000-fe6fffff
           *-network
                description: Ethernet interface
                product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 11
                serial: 20:cf:30:2a:53:da
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes port=twisted pair
                resources: irq:78 memory:fe6fc000-fe6fffff ioport:b800(size=256) memory:fe6c0000-fe6dffff
        *-pci:4
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port G)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:76 memory:fe500000-fe5fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:50 memory:fe5fe000-fe5fffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:77 ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=8) ioport:7000(size=4) ioport:6000(size=16) memory:fe3fe000-fe3fe3ff
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe3f7000-fe3f7fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe3fe400-fe3fe4ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe3fc000-fe3fcfff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe3fe800-fe3fe8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD reader
                product: DVD-ROM SH-D163C
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB01
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fe3f8000-fe3fbfff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: memory:fe400000-fe4fffff
           *-network
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: Ralink corp.
                physical id: 6
                bus info: pci@0000:01:06.0
                logical name: wlan0
                version: 00
                serial: c8:3a:35:c7:43:67
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-11-generic-pae firmware=0.8 ip=192.168.0.102 latency=64 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:fe4f8000-fe4fffff
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe3fd000-fe3fdfff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe3ff000-fe3fffff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe3fec00-fe3fecff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

EDIT - I've added my hardware (I think?!) if that helps?  Still can't work out which model graphics card I have beyond that it is the 5800 series...

---

### Post by kaldor on 2011-09-04
In the ATI Control Centre, disable the vertical refresh stuff. That did wonders for me.

Not on my AMD powered PC, but from memory...

ATI Control Center > 3D > Performance > Vertical Refresh (or something like that; it's a link) and then you should get some slider bar. Slide it left; Always off.

How did you install the proprietary driver? Via Ubuntu's tool or the AMD website?

---

### Post by eversilentone on 2011-09-04
Thanks for the reply.  I couldn't fine anything that said vertical refresh but will keep looking.  Any other ideas?

I should add that I installed the prop driver via Ubuntu rather than through the site.

---

### Post by Mark Phelps on 2011-09-05
Are you running Ubuntu 11.04? That could be the problem because there is not a single entry in the Wine ratings for Ubuntu 11.04.  So, no one has rated it for the current version.  The Platinum ratings you see are all for older Ubuntu versions.

Also, the other game is not even listed.  So, if you're trying to run it in Wine, it's likely NOT to work.

---

### Post by eversilentone on 2011-09-05
Supertuxkart is linux native so should run regardless.  I hadn't noticed that they were tested on older versions of Ubuntu, that could be the problem, I guess?

Also, I opened up my machine and looked at the label: my graphics card is the 5830 in case that makes any difference?

---

