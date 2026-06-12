---
title: "Wired Connection Problems &gt;.&lt;"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Mastamaul on 2011-02-06
Hello So New to Ubuntu kinda Sorta, i recently installed ubunto 10.10 and i have no wired connection now my computer is custom built with a Evga P55 motherboard. i have it plugged in but it says no internet connection available any suggestion would be nice, i tried looking on the forums but i got lost at all the thing people suggested and alot of people had wireless problems or have a dual boot. i have a fresh partition with nothing on it but ubuntu.

---

### Post by davidmohammed on 2011-02-06
do you mean that you dont have a RJ45 (ethernet port)?

type 

lspci

and

lsusb

and

lshw

in a terminal and post the results for each command in a reply (enclosed in CODE tags)

---

### Post by Mastamaul on 2011-02-06
lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:05.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 3 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.3 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 05)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
02:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
```

lsusb
```
Bus 009 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 047d:2043 Kensington 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1395:3556 Sennheiser Communications USB Headset
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw
```
mastamaul                 
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3955MiB
     *-cpu
          product: Intel(R) Core(TM) i5 CPU         760  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
     *-pci
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:d000(size=4096) memory:fbe00000-fbefffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:48 memory:c0000000-cfffffff memory:fbee0000-fbefffff ioport:d000(size=256) memory:fbec0000-fbedffff
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:50 memory:fbebc000-fbebffff
        *-pci:1
             description: PCI bridge
             product: Core Processor PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:e000(size=4096) memory:fbf00000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:51 memory:d0000000-dfffffff memory:fbfe0000-fbffffff ioport:e000(size=256) memory:fbfc0000-fbfdffff
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:52 memory:fbfbc000-fbfbffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-network UNCLAIMED
             description: Ethernet controller
             product: 82578DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:fbdc0000-fbddffff memory:fbdfc000-fbdfcfff ioport:cc00(size=32)
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c880(size=32)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:2
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c480(size=32)
        *-usb:3
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fbdfa000-fbdfa3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:49 memory:fbdf4000-fbdf7fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:1000(size=4096) memory:f0000000-f01fffff ioport:f0200000(size=2097152)
        *-usb:4
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c400(size=32)
        *-usb:5
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c080(size=32)
        *-usb:6
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c000(size=32)
        *-usb:7
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bc00(size=32)
        *-usb:8
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbdf8000-fbdf83ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff90(size=16) ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbdff800-fbdff8ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=8) ioport:b080(size=4) ioport:b000(size=16) ioport:ac00(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
```

---

### Post by davidmohammed on 2011-02-07
the unclaimed ethernet device is worrying

there is a blog post [here]("http://ronenagranat.blogspot.com/2011/01/ubuntu-1010-wired-internet-fail-intel.html") that could be your issue - especially as you said that this is a custom build.

---

