---
title: "can not seem to get wireless up and running"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by josephmills on 2011-03-15
hi there I cant get my computers wireless up and running. I have looked all around (Internet) and still cant get it going. This is what I am working with 

ifconfig gives  no wlan0

iwconfig gives me this 
o        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
and this is the wireless card 
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
well thanks for taking he time to read this

---

### Post by Eiji Takanaka on 2011-03-15
i suspect it may be driver related.

Stating your machine and o/s credentials plus listing drivers and hw (lshw and lspci) might be a place to start on here dude.

Gambatte!

---

### Post by josephmills on 2011-03-15
> **Eiji Takanaka said:**
> i suspect it may be driver related.

Stating your machine and o/s credentials plus listing drivers and hw (lshw and lspci) might be a place to start on here dude.

Gambatte!

my machine is a compaq presario cq60 
my operating system is ubuntu 10.10 desktop  (full partition )
 lshw 
```

   description: Notebook
    product: Compaq Presario CQ60 Notebook PC
    vendor: Hewlett-Packard
    version: F.34
    serial: 2CE90854PR
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=35768FC0-04B1-11DE-9218-C598ECBD69CF
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.48
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.34 (12/23/2008)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon Dual-Core QL-62
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 2GHz
          capacity: 2GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:41 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8A2L-A
             vendor: Slimtype
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 7H63
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: TOSHIBA MK1652GS
             vendor: Toshiba
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: LV01
             serial: 29JOTAZPT
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000d26f4
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 7e997494-4d88-4566-abbd-885f62d82d68
                size: 143GiB
                capacity: 143GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-03-15 09:31:46 filesystem=ext4 lastmountpoint=/&#65533;WjS&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;u!&#65533;&#65533;Q&#65533;&#65533;@&#65533;&#65533;j&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;h&#65533;&#65533;Yx!&#65533;o modified=2011-03-15 09:55:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-15 12:49:59 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 5999MiB
                capacity: 5999MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5999MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:6b:db:c4
          size: 100MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.254.1 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:c2000000-c20fffff
        *-network DISABLED
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:24:2b:a7:8b:5c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.35-27-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb

```
and here is lspci

```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
any thing useful

---

### Post by Eiji Takanaka on 2011-03-15
O.k so now you've got the name of your wireless device you could try searching the forums for problems with that device (ath5k is the driver for the wireless) by the looks in your case).

It says network disabled though which suggests a configurational setting/problem.

You have tried right clicking the wireless icon in the network manager and clicking 'enable wireless' right?

---

### Post by josephmills on 2011-03-15
> **Eiji Takanaka said:**
> O.k so now you've got the name of your wireless device you could try searching the forums for problems with that device (ath5k is the driver for the wireless) by the looks in your case).

It says network disabled though which suggests a configurational setting/problem.

You have tried right clicking the wireless icon in the network manager and clicking 'enable wireless' right?


yes I have tried right clicking the wireless icon in the network manager and clicking 'enable wireless
I have also tried to go to system-> addmin->additional drivers and nothing shows up for wifi that is. 
I have looked all over the forum ( [http://www.googlubuntu.com](http://www.googlubuntu.com) )and it is all for 9,04 and so on if you find a nice link I would like to see it. when I input ifconfig I get no wlan0 so I know that I need a driver but which one is the question where is that tar? I also upgraded and updated too. thanks for your help!

---

### Post by Eiji Takanaka on 2011-03-15
Try starting a thread with more specific details then fella, i.e problem with atheros wi-fi driver ath5k...do some research, ask some more questions. 

Sorry i can't help ya any further it sounds more driver specific, and sadly i dont work for atheros eh?

Like i say though it sounds odd to me that it says in your list of details it says *network disabled* this makes me think its a config problem as opposed to a driver issue. 

Good luck in your quest dude. ;)

---

### Post by josephmills on 2011-03-15
i dont know what I did but I rebooted the computer, and wifi works

---

### Post by Eiji Takanaka on 2011-03-15
haha that sometimes does the trick!

rock on dude.

---

### Post by 5149.5 on 2011-03-15
> **josephmills said:**
> i dont know what I did but I rebooted the computer, and wifi works 


Helpdesk! Good morning! How can I help you? 

Blah-ba-blah blah blah blah.

OK. Power cycle your machine and if that doesn't help, call me back. :guitar:

---

### Post by Eiji Takanaka on 2011-03-15
It can work, but if you see the adverts here in the u.k for the royal navy it makes you f*cking cringe man seriously...

Young navy lad whilst laughing casually "Yes and if the nuclear missiles navigation system  happens to malfunction, well we just turn it off and on again" 

Seriously though man there is a genuine royal navy advert that goes something along those lines, makes me flipping cry laughing every time i see it.

---

