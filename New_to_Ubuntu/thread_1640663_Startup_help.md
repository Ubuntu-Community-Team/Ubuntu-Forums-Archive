---
title: "Startup help"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Trandre on 2010-12-08
Hi 
I have an Odd query. Two times my 64 bit machine has chrashed after restart after the update from update manager(reinstalled to solve). Now I have updated again, but have not restarted. What information should i post on the system, to help me understand why it will not startup after the reboot?

---

### Post by Hippytaff on 2010-12-08
Have you got an Nvidia Graphics card?

---

### Post by Trandre on 2010-12-08
Yes I have

---

### Post by philinux on 2010-12-08
Have you enable the graphics card driver?

system>admin>additional drivers

---

### Post by sikander3786 on 2010-12-08
Is this a Wubi install (inside Windows) or a proper dual boot setup (Ubuntu on its own partition)?

---

### Post by Trandre on 2010-12-08
I have enabled the graphics card driver Nvidia X server settings

And yes this is a Wubi install

```
famfem@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
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
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 933MHz
          capacity: 933MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci:0
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
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:6000(size=4096) memory:d2000000-d30fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 230M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff(prefetchable) ioport:6000(size=128) memory:d3080000-d30fffff(prefetchable)
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:d3000000-d3003fff
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
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:db105c00-db105fff
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
             resources: irq:22 memory:db100000-db103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:5000(size=4096) memory:da100000-db0fffff ioport:d3100000(size=16777216)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 70:1a:04:54:77:26
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=10.0.0.51 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:16 memory:da100000-da10ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:4000(size=4096) memory:d9100000-da0fffff ioport:d4100000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 00:26:9e:8f:ed:82
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:35 ioport:4000(size=256) memory:d4104000-d4104fff(prefetchable) memory:d4100000-d4103fff(prefetchable) memory:d4110000-d411ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:32 ioport:3000(size=4096) memory:d8100000-d90fffff ioport:d5100000(size=16777216)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:16 memory:d8100000-d81007ff memory:d8100d00-d8100d7f memory:d8100c80-d8100cff memory:d8100c00-d8100c7f
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d8100b00-d8100bff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d8100a00-d8100aff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d8100900-d81009ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:04:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d8100800-d81008ff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:33 ioport:2000(size=4096) memory:d7100000-d80fffff ioport:d6100000(size=16777216)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:db105800-db105bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:34 ioport:7048(size=8) ioport:7054(size=4) ioport:7040(size=8) ioport:7050(size=4) ioport:7020(size=32) memory:db105000-db1057ff
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
             resources: memory:db106000-db1060ff ioport:7000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 04
          width: 32 bits
          clock: 33MHz

```

---

### Post by sikander3786 on 2010-12-08
> **Trandre said:**
> I have enabled the graphics card driver Nvidia X server settings

And yes this is a Wubi install

You need to reboot and see what happens. Based on your issue, either Problem # 1 or Problem # 2 from this guide would apply and there are solutions listed as well ;-)

courtesy of forum member Rubi1200

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you don't feel confident, feel free to post back here or in that thread, whichever you prefer.

After the problem is Solved, I would suggest to apply the *Permanent Fix* from that page in order to avoid the update problems in future.

Good Luck!

---

### Post by Trandre on 2010-12-09
solved, jippi, thanks for the help

---

