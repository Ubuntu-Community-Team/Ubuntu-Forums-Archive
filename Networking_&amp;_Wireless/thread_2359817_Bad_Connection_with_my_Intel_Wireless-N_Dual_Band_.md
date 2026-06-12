---
title: "Bad Connection with my Intel Wireless-N Dual Band 7260 Adapter"
date: 2017-04-28
forum: Networking &amp; Wireless
---

### Post by mmkthecoolest on 2017-04-28
I'm running Ubuntu 14.04 and can only get Internet working for a while. After a few moments of browsing, the router is still connected but I get no Internet connection. I have no idea how to fix this. Please keep in mind that I am new to Ubuntu.

System Information:

```
PCI (sysfs)  
mmk-aspire-v7-582pg       
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7864MiB
     *-cpu
          product: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:51 memory:b3000000-b33fffff memory:c0000000-cfffffff ioport:5000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:52 memory:b3610000-b3613fff
        *-usb:0
             description: USB controller
             product: Lynx Point-LP USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:b3600000-b360ffff
        *-communication
             description: Communication controller
             product: Lynx Point-LP HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:b3618000-b361801f
        *-multimedia:1
             description: Audio device
             product: Lynx Point-LP HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:b3614000-b3617fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:9fb00000-9fcfffff ioport:9fd00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:b3500000-b35fffff
           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 73
                serial: ac:7b:a1:65:0c:11
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-80-generic firmware=25.17.12.0 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:50 memory:b3500000-b3501fff
        *-pci:2
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:b3400000-b34fffff
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:45 memory:b3405000-b3405fff memory:b3410000-b341ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:05:00.1
                logical name: eth0
                version: 14
                serial: c4:54:44:2b:66:4f
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:47 ioport:4000(size=256) memory:b3404000-b3404fff memory:b3400000-b3403fff
        *-pci:3
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:b2000000-b2ffffff ioport:a0000000(size=301989888)
           *-display
                description: 3D controller
                product: GK107M [GeForce GT 750M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nouveau latency=0
                resources: irq:53 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)
        *-usb:1
             description: USB controller
             product: Lynx Point-LP USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b361c000-b361c3ff
        *-isa
             description: ISA bridge
             product: Lynx Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Lynx Point-LP SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:b361b000-b361b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b3619000-b36190ff ioport:5040(size=32)
```

---

### Post by ajgreeny on 2017-04-28
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

See **Wifi-Info** in my signature below and follow the instructions there to run the Wifi-Info-Script.	 Post back the output you get in code tags please, which will show us a lot more about your system's wifi setup. 

However, I suspect you might have more success with that card were you using Ubuntu 16.04.

---

