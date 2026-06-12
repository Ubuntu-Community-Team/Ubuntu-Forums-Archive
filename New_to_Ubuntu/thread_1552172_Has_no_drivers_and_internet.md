---
title: "Has no drivers and internet"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by dcb_dan on 2010-08-13
I just downloaded Ubuntu 10.04 from wubi through windows 7, on my dell inspiron laptop. I have no wireless internet and no internet through the cable.

I went to System>hard drive>drivers and it gives me the message "download package indexes failed. check network status. Most drivers will not be available." 

How do I get internet? how do I make my drivers available? what are drivers/what drivers should I have?

Searched it and tried some things but I've had no luck. So any help much appreciated.

---

### Post by zeroseven0183 on 2010-08-13
That's somewhat surprising. You should have at least an Internet connection. Anyway, can you post here the result of **lshw**?
1. open a Terminal (Applications > Accessories > Terminal)
2. type [B]lshw
[/B]3. press EnterThat will list down all the detected hardware on your laptop.

---

### Post by AlexDudko on 2010-08-13
You **must** have a wired connection! The driver must be included in the kernel.
For wireless execute commands in terminal:
> lspci
> lsusb
and see what wireless adapter you have.
Then search for the driver.

---

### Post by dcb_dan on 2010-08-13
[PHP]danielbourgeois@ubuntu:~$ lshw
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
          size: 3826MiB
     *-cpu
          product: Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:2000(size=4096) memory:cfe00000-cfefffff ioport:d0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Manhattan [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d0000000-dfffffff(prefetchable) memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:cfedc000-cfedffff
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f0406800-f040680f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0407000-f04073ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0400000-f0403fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:4000(size=4096) memory:c0000000-c01fffff memory:c0200000-c03fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:5000(size=4096) memory:f0300000-f03fffff memory:c0400000-c05fffff(prefetchable)
           *-network UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f0300000-f0303fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:3000(size=4096) memory:f0200000-f02fffff memory:c0600000-c07fffff(prefetchable)
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                version: c1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f0200000-f023ffff ioport:3000(size=128)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0407400-f04077ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
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
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:32 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:1820(size=32) memory:f0406000-f04067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0407800-f04078ff ioport:1840(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:f0405000-f0405fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
  *-scsi:0
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage
danielbourgeois@ubuntu:~$ 

[/PHP]
Thats the lshw command.

---

### Post by sydbat on 2010-08-13
A quick look tells me you have a Broadcom wireless card, which sometimes has compatibility problems with Linux distributions.

Have you/can you connect to the Internet when your laptop is wired to your modem/router? It should have no problem.

Once connected via the Ethernet cable, you should be able to find the correct drivers for the wireless card. They can be found under System > Administration > Hardware Drivers. 

Remember, you HAVE to be connected to the Internet so these drivers can be installed properly.

---

### Post by AlexDudko on 2010-08-13
Have you read this [thread]("http://guide.ubuntuforums.org/showthread.php?t=1505697")?

---

