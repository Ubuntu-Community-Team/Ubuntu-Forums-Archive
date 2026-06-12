---
title: "LAN Internet slow in Ubuntu compared to Windows in dual boot"
date: 2020-01-16
forum: Networking &amp; Wireless
---

### Post by maramsumanth on 2020-01-16
I have installed ubuntu budgie 18.04 alongside windows 10 in dual boot. When connected through ethernet, in windows the internet speed is around 500-600 Mbps. But in ubuntu it is as slow as 4-5 Mbps. Do I need to install/update any drivers. please help!

---

### Post by praseodym on 2020-01-16
Please run the wireless script from the sticky thread and show the output

---

### Post by TheFu on 2020-01-16
We need information about the specific device, current driver, current connection in order to help.  If this isn't a wireless issue, then one of the following commands should provide the data:

```
# my favorite cmd has the device name, driver used, and options
sudo lshw -C network

# A few options if lshw isn't available ; PCI only, no USB.
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 

# USB network devices won't show up in the PCI
sudo lsusb -v  |egrep 'Ether|Network'
```

**lshw** will provide everything about the NIC and driver. You might need to install it. It is handy for all sorts of other stuff too.

---

### Post by maramsumanth on 2020-01-16
**Output for [COLOR=#000000][FONT=&amp]sudo lshw -C network :-[/FONT][/COLOR]**

  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: 18:60:24:14:51:04
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.55.1.148 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:3000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 10
       serial: a0:af:bd:eb:13:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-37-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:b1000000-b1001fff


**Output for [COLOR=#000000][FONT=&amp]lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' :-[/FONT][/COLOR]**

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at b1104000 (64-bit, non-prefetchable) [size=4K]
    Memory at b1100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


03:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)
    Subsystem: Intel Corporation Device 2110
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at b1000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


**NO Output for **[COLOR=#000000][FONT=&amp]**sudo lsusb -v  |egrep 'Ether|Network' :-**


**Output for lshw:-**

[/FONT][/COLOR]ubuntu                      
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7891MiB
     *-cpu
          product: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 498MHz
          capacity: 3100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 620
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:131 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:b1320000-b1327fff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:b1332000-b1332fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:b1310000-b131ffff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:b1333000-b1333fff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:128 memory:b1334000-b1334fff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:b1330000-b1331fff memory:b1337000-b13370ff ioport:5080(size=8) ioport:5088(size=4) ioport:5060(size=32) memory:b1335000-b13357ff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:4000(size=4096) memory:b1200000-b12fffff ioport:90000000(size=268435456)
           *-display
                description: Display controller
                product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / R7 M520]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 83
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:130 memory:90000000-9fffffff memory:b1200000-b123ffff ioport:4000(size=256) memory:b1240000-b125ffff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:3000(size=4096) memory:b1100000-b11fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eno1
                version: 15
                serial: 18:60:24:14:51:04
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.55.1.148 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:16 ioport:3000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:b1000000-b10fffff
           *-network
                description: Wireless interface
                product: Dual Band Wireless-AC 3168NGW [Stone Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlo1
                version: 10
                serial: a0:af:bd:eb:13:f6
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-37-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:129 memory:b1000000-b1001fff
        *-isa
             description: ISA bridge
             product: Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:b132c000-b132ffff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:132 memory:b1328000-b132bfff memory:b1300000-b130ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b1336000-b13360ff ioport:5040(size=32)
     *-scsi
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW GUE1N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: UE00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by maramsumanth on 2020-01-16
[https://pastebin.com/eUWdewkH](https://pastebin.com/eUWdewkH) contains output of wireless script

---

### Post by TheFu on 2020-01-16
a) only wanted 1 of the command outputs.  Posting everything dilutes what is important.
b) using **code tags** would help make it easier to read. I demonstrated it in my original post.

This is what is important to seeking a solution, assuming it is NOT a configuration/routing issue:
```
  Realtek RTL8111/8168/8411 version=15 driver=r8169
```
I would search for solutions using that core information.

I have one of these NICs, version=0c, using the driver=r8169 driver. It works with similar limited bandwidth.
```
$ iperf3 -c istar
Connecting to host istar, port 5201
[  4] local 172.22.22.13 port 48836 connected to 172.22.22.20 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  66.4 MBytes   557 Mbits/sec    0    324 KBytes       
[  4]   1.00-2.00   sec  65.6 MBytes   550 Mbits/sec    0    339 KBytes      

```
My other systems all use Intel NICs.
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 56482 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   922 Mbits/sec    0    106 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   921 Mbits/sec    0    113 KBytes  
```
This is a common difference. Intel just works better than Realtek or Marvell. Tested from the same client, going over the same network cables, through the same switches.

---

### Post by maramsumanth on 2020-01-17
So, what is the solution to this problem now?

---

### Post by TheFu on 2020-01-17
> **maramsumanth said:**
> So, what is the solution to this problem now?

First, can you verify performance using iper3?  

So far, we have a claim that it is slow, but nothing says which program(s) are being used. 
Which two points are involved?  If one is wifi, there's no way for a GigE connection between the wifi to be faster than that limited link.

---

### Post by maramsumanth on 2020-01-17
To my surprise, I have received an update around 72.6 Mb. Upon updating and rebooting solved my problem of slow internet. Now the internet speed is aroung 900 Mbps. I was thinking why didn't this update came during installation of ubuntu!

---

