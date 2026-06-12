---
title: "Can I Get Better Internet Speed With USB On a PCIe x1 Card?"
date: 2019-12-23
forum: Networking &amp; Wireless
---

### Post by soundchaser59 on 2019-12-23
My machine is pretty much limited to 100mbps connections to the outside world, by ethernet port and I suppose the usb 2 ports are bottlenecked because they are sharing a bus on the mobo with other data streams, etc. I understand the ethernet port is old and is limited to 100mbps, but usb2 is supposed to be able to handle around 400mbps. I believe my internet is maxing out at 100mbps or less whether it's wireless or ethernet, even though my wireless usb2 adapter is supposedly capable of 400mbps (it supports n and ac) and my ISP connection is "guaranteed" to be a base minimum of 300mbps (over fiber network, it's the most "basic" tier of service they offer). They don't throttle anything and I'm thinking the most likely explanation for the online speed tests consistently coming back 60-70mbps is this old hardware. 

I notice I have a free PCIE x1 slot on my mobo, which is allegedly capable of 1GB/sec. (the x16 slot is taken by the graphics card) Can I bump up my internet speed if I get a PCIE x1 usb card? Would that allow my usb wireless adapter to bump up to handle the 300mbps that my ISP is providing? Would I be better getting a wireless card for that x1 slot? My bios says the on board usb slots are enabled to support both 1.1 and 2.0, but the specs reported below only indicate usb ports as 1.1 

(in a few days my ram will bump up to 8gb) 
In case anyone will ask, here are the hardware specs reported by sudo lshw: 

```
rootbeer@SC59:~$ sudo lshw
[sudo] password for rootbeer: 
sc59                        
    description: Desktop Computer
    product: M61PME-S2P
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal chassis=desktop uuid=30303234-3144-3032-4636-3835FFFFFFFF
  *-core
       description: Motherboard
       product: M61PME-S2P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 12/30/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          slot: Socket M2
          size: 2200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl cpuid extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-memory:0
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:e000(size=64) ioport:1c00(size=64) ioport:c400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fa007000-fa007fff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 5.0.0-37-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 5.00
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb:0
                description: Keyboard
                product: USB Keyboard
                vendor: SIGMACHIP
                physical id: 2
                bus info: usb@2:2
                version: 1.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
           *-usb:1
                description: Mouse
                product: USB Receiver
                vendor: Logitech
                physical id: 4
                bus info: usb@2:4
                version: 30.00
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fa006000-fa0060ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 5.0.0-37-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 5.00
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb
                description: Generic USB device
                product: 802.11ac WLAN Adapter
                vendor: Realtek
                physical id: 1
                bus info: usb@1:1
                version: 2.00
                capabilities: usb-2.10
                configuration: driver=rtl8812au maxpower=500mA speed=480Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fa000000-fa003fff
     *-ide
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:26 memory:fa004000-fa004fff ioport:c800(size=8)
     *-storage
          description: RAID bus controller
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fa005000-fa005fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0 ioport:b000(size=4096) memory:f8000000-f9ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: Redwood XT [Radeon HD 5670/5690/5730]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:25 memory:e0000000-efffffff memory:f9000000-f901ffff ioport:b000(size=256) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Redwood HDMI Audio [Radeon HD 5000 Series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:24 memory:f9020000-f9023fff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: a
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3320620AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: K
             serial: 9QF558KP
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=c6ec44d1
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 33394b75-d28b-41ad-b7a7-af88193301b0
                size: 298GiB
                capacity: 298GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-12-22 14:21:42 filesystem=ext4 lastmountpoint=/ modified=2019-12-22 20:30:39 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-12-22 20:30:43 state=mounted
     *-scsi:1
          physical id: b
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: CT500MX500SSD1
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 023
             serial: 1846E1D7E1B6
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=16e20f2f
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 8f7ebbfc-72ef-44ef-97d1-efdb30244c19
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2019-12-21 02:22:47 filesystem=ext4 lastmountpoint=/ modified=2019-12-22 13:48:22 mounted=2019-12-22 13:48:23 state=clean
     *-scsi:2
          physical id: c
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4120B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlx00e04c082948
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.11 multicast=yes wireless=IEEE 802.11bgn
rootbeer@SC59:~$ 

```

---

### Post by mörgæs on 2019-12-23
> **soundchaser59 said:**
> They don't throttle anything and I'm thinking the most likely explanation for the online speed tests consistently coming back 60-70mbps is this old hardware. 

If I were so lucky to get that bandwidth using any kind of hardware I would not try to chance anything. Which tasks are you not able to complete?

---

### Post by TheFu on 2019-12-23
Wired connections will get you about 90+% of the bandwidth claimed.

Wifi connections will typically provide 50% of the bandwidth claimed on the box, but not all wifi adaptors can do that, with environment and vendor-to-vendor compatibility mattering greatly. More devices on a wifi LAN will drop the bandwidth, though AC shouldn't be as bad as N connections.  Having older, slow, devices on any wifi network can limit the speeds of newer devices greatly.  Being backwards compatible to devices that aren't using the newest standard impacts all the available bandwidth.

USB2 theoretical bus is 480 Mbps. Nobody ever sees anywhere near that theoretical limitation.  Nobody.  With USB3, the  theoretical bus limit is 5Gbps. Only NVMe storage comes close to that - usually in the 3.6Gbps range.  **Don't confuse Mbps and MBps**.  There is an 8x multiplier in there.  Networking equipment is ****always**** Mbps.  Always.  But most software will report bandwidth/throughput in MBps.

100 Mbps = 12.5 MBps

Don't mix those up or you will always be disappointed without reason.

Next you have to consider the real world capabilities of the other subsystems involved.  The fastest USB2 portable HDD disks I've ever seen would do only 20Mbps writes.  With faster USB3 flash, I've seen 70Mbps writes, when connected to a USB3 port.  Externally powered, USB2 HDDs might get 40Mbps writes.  Internal SATA HDDs can get 125 Mbps writes. Anyways, every storage subsystem will have different limitations. It might be that causing the limits, not the network.

USB2 network connections will probably only get 200 Mbps with a GigE adaptor.  I use a USB3-to-GigE adaptor with my laptop. ... 
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 49744 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   922 Mbits/sec    0    110 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   921 Mbits/sec    0    137 KBytes       
[  4]   2.00-3.00   sec   110 MBytes   921 Mbits/sec    0    137 KBytes
```
hadar has a GigE Intel  I211 NIC.   The connection between the systems goes through 2 GigE switches.

I moved my usb3 connection to a USB2 port and tested again:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 49842 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  40.6 MBytes   340 Mbits/sec    0   48.1 KBytes       
[  4]   1.00-2.00   sec  40.5 MBytes   340 Mbits/sec    0   49.5 KBytes       
[  4]   2.00-3.00   sec  40.5 MBytes   340 Mbits/sec    0   49.5 KBytes
```

This is an 8th-gen Core i5 laptop.  The internal bus easily handles multiple USB3 connections.  I doubt old USB2-only hardware will see 340Mbps.  Never know until you try.  I would if I were you - get a USB3-to-GigE adaptor. While you are at it, might as well get one with 2-4 USB3 ports on the adaptor too. Those are convenient and don't seem to impact anything else.  The device I have is:
```
 ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
```
Plug-in-play.  Got it off amazon for around $20.  Had a similar device before, but it broke after a few yrs of use. That one had a different internal GigE chip.

---

### Post by Yellow Pasque on 2019-12-23
You mention ethernet. If you can use that and don't need to be wireless, then the most effective solution is to get a PCI-e Gbit LAN card.

> **soundchaser59 said:**
> My bios says the on board usb slots are enabled to support both 1.1 and 2.0, but the specs reported below only indicate usb ports as 1.1
You're reading it incorrectly. The first controller (the one you have mouse/keyboard plugged in) reported as USB 1.x, but the second controller where you have your wireless is USB 2.x. Here's the important info:
```
*-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
        *-usbhost
             product: EHCI Host Controller
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb
                description: Generic USB device
                product: 802.11ac WLAN Adapter
                vendor: Realtek
                capabilities: usb-2.10
                configuration: driver=rtl8812au maxpower=500mA speed=480Mbit/s
```

---

### Post by slickymaster on 2019-12-23
*Thread moved to **Networking & Wireless**.*

---

### Post by soundchaser59 on 2019-12-25
> **TheFu said:**
> I would if I were you - get a USB3-to-GigE adaptor. While you are at it, might as well get one with 2-4 USB3 ports on the adaptor too. Those are convenient and don't seem to impact anything else.If I understand correctly everything I read, it seems to suggest that the PCIe slots do not have the bottleneck issues with the mobo bus like the usb2 slots and the older PCI slots have. Not sure about that, but it is promising if true. I did find a 4 port usb 3 card that is PCIe x1 format. 

I was also surprised to find that my other machine has an open PCIe x16 slot. It has two, and the first one is occupied by the graphics card, but it's tempting to think that I could get a second PCIe x16 card to get usb3 for that machine. I believe the x16 slots claim to offer 5GB/s speeds? Or is it 5gbps? Either way it would be blinding fast compared to the usb2 bottlenecks I'm dealing with now.

---

### Post by TheFu on 2019-12-25
PCIe bandwidth on the bus is determined by the bus architecture.  Some have dedicated performance, usually just the GPU slot with all others sharing the other bus.  Lower end motherboards have few buses with less bandwidth.  Prior to about 5 yrs ago, USB3 performance wasn't a consideration in motherboard bus architecture.  When USB3 became standard on systems, the entire PCI bus architecture was upgraded to support it.

I have $300 MSI core i5 motherboard from 2010 that can't handle a USB3 addon card performance and I have $50 2015-ish pentium motherboard that loves USB3 devices and surpasses the bus needs with 16TB of connected storage.

I would not assume that a 2nd 16x PCIe bus will work at that speed unless it is using two, paired, GPUs.

USB3 5 Gbps is a dream. Nobody gets that.  I have seen just under 4Gbps throughput, however using NVMe storage connected that way. If you have any questions about what most standards support, use wikipedia. [https://en.wikipedia.org/wiki/USB_3.0](https://en.wikipedia.org/wiki/USB_3.0)

I never said anything about PCIe in prior posts, BTW, so making conclusions is wrong from what was said.  However, I would definitely use a PCIe GigE adapter - get an Intel one - over any wifi solution.  I would avoid realtek and other brands to avoid many hassles and more CPU interrupts.  Get an intel NIC.

---

### Post by soundchaser59 on 2019-12-26
> **TheFu said:**
> I would definitely use a PCIe GigE adapterNot an option. This machine cannot be wired to the router.....unless I start drilling holes in cinder block. I would prefer a wired gb connection, but it just isn't available in this part of the building. 

I just received my pcie x1 card and installed it. It worked as soon as I booted the machine. I moved my wireless usb adapter from the old usb slot to the usb port on the new card and the wireless just kept on working.......only a lot faster. It is very noticeable. For example, a 100mb file that took several minutes to download yesterday was finished downloading in less than a minute today. I notice it also seems to depend on the web site serving the file, some seem to let it flow faster than others. I also notice I can now watch hi res youtube videos with no stuttering or buffering, and if I click the timeline to skip ahead it will locate to that point and start playing within a second or so, instead of making me wait several seconds for it to skip forward. 

I am tempted to get another card for my other computer.

---

### Post by soundchaser59 on 2020-01-05
> **TheFu said:**
> .....I would definitely use a PCIe GigE adapter - get an Intel one - over any wifi solution.  I would avoid realtek and other brands to avoid many hassles and more CPU interrupts.  Get an intel NIC.I just broke my usb wireless connection again....for the last time. After pulling my hair out trying to restore it one more time I remembered this thread and your recommendation to go instead with a pcie gigabit card. I started looking on gar-bay when I realized I wasn't sure which brands to favor. Found this thread again and am glad I did, because I had been overlooking the Intel cards. I will try one, they aren't very expensive. 

So I finally bit the bullet and pulled an extra long cat6 cable from upstairs to the basement, with the intention of test driving a pcie x1 gigabit ethernet card. I'm also now cloning my ssd to a sata hdd maybe once a week, so if anything breaks I can simply grab a copy of the newest files to a usb stick and then restore from the clone. That's how I fixed my broken wireless connection this time. In a few days I'll have a pcie x1 card to install and my wireless problems will go up in.......ether.... :) :popcorn: 

So thanks for the info and the tip. Took me a while to realize the wisdom, but your tip was good advice. Well worth the trouble of fishing that darn cable thru that chase space.

---

### Post by soundchaser59 on 2020-01-05
After a bit of research I have come to think maybe this adapter will work fine with Linux (either Ubuntu or Mint).....? 
This one is easily available for between $20-30 bucks.  [FONT=franklin gothic medium][SIZE=3]

Intel EXPI9301CTBLK 10/100/1000Mbps PCI-E x1 RJ45 Ethernet Gigabit Network Adapter [/SIZE][/FONT]

---

### Post by Yellow Pasque on 2020-01-06
> Intel EXPI9301CTBLK 10/100/1000Mbps PCI-E x1 RJ45 Ethernet Gigabit Network Adapter
The card uses the venerable Intel 82574L chipset. It should be supported "out of the box" on any modern version of Ubuntu (>= 16.04).

---

### Post by hk42 on 2020-01-06
I used a realtek RTL8153 USB3 to gigabit Ethernet adapter.
They are cheap and even on a USB2 port there is a least an x2 improvement over 100mbps cards.

---

