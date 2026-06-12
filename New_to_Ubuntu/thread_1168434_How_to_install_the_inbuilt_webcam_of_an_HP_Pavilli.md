---
title: "How to install the inbuilt webcam of an HP Pavillion 6000"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Toobs on 2009-05-24
Hi guys 

I am 1 day into my Ubuntu experience after i wiped my Vista of my computer in a severe case of "windows rage" yesterday.

I am happy with the speed and getting my head around how it works but I have not been able to get my inbuilt webcam to work. I did not manage to install easycam2 because some python problem. 

Is anybody able to give me a step by step guide?

Thx

---

### Post by nhasian on 2009-05-24
in a terminal type:

```
lsusb
```

i have the same laptop as yours a DV6500 and DV9500 and my camera is listed as:

> Bus 002 Device 003: ID 04f2:b023 Chicony Electronics Co., Ltd 


it works automatically for me.  I didnt have to do anything special.  you can test it out with cheese.

```
sudo apt-get install cheese
```

---

### Post by Toobs on 2009-05-24
Thx

i have installed cheese but it cannot find the camera either. Big stop sign no camera found

If I look for it I get this

tobias@tobias-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Not sure how to read that

I then proceded to install easycam but that did not work either pelase see below


tobias@tobias-laptop:~$ sudo apt-get install easycam2-gtk
[sudo] password for tobias: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
E: Broken packages
tobias@tobias-laptop:~$

I am sure it is possible but I need a bit of help to understand all this

---

### Post by nhasian on 2009-05-25
instead of lspci,

try:

```
lsusb
```

or

```
lshw
```

mine is listed as:

>              *-usb
                   description: Video
                   product: HP Webcam
                   vendor: Chicony Electronics Co., Ltd.
                   physical id: 4
                   bus info: usb@2:4
                   version: 6.06
                   serial: SN0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s


---

### Post by Toobs on 2009-05-25
Thanks for the tip. i put it in and got this:


tobias@tobias-laptop:~$ lshw
WARNING: you should run this program as super-user.
tobias-laptop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1001MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:52:18:4b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=10.0.1.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 00
                serial: 00:16:36:e9:51:aa
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 module=e1000e multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:07:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@0000:07:05.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@0000:07:05.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@0000:07:05.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 5.4
                bus info: pci@0000:07:05.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:b2:2f:13:93:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
tobias@tobias-laptop:~$ lsusb
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tobias@tobias-laptop:~$ Isusb

---

### Post by stanyo on 2009-06-16
I have the same problem with my dv6000. Exactly model number is 6058ea. I use fresh installation of Ubuntu 9.04.
Chipset is nvidia. The camera work with Vista. In ubuntu not.
And I have another problem with my Wifi module. In vista I didnt see it in device manager, and I think have hardware problem. Vendor of wifi module is Gemtek (determined from mac address 0014a5). The output of the lshw command is:

 *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.8.2
          slot: Socket S1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
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
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 99U5295-012.A00LF
             vendor: F789000000000000
             physical id: 0
             serial: A2CC6E13
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             product: 99U5295-012.A00LF
             vendor: F789000000000000
             physical id: 1
             serial: A2CC4E13
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.8.2
          size: 1600MHz
          capacity: 1600MHz
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
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce Go 7200
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi2
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GMA-4082N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: HQ04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: ST9120821AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 7.24
             serial: 5PL1V5BH
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=f3c5f3c5
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: aaf14249-8a96-434d-81e9-47a09a1cf082
                size: 39GiB
                capacity: 39GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-06-12 21:48:24 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 40cb68d5-a59f-7d4b-b8e5-9245d466b395
                size: 55GiB
                capacity: 55GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-06-13 16:30:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: d70eb689-060b-46f8-940d-54e08fce518a
                size: 15GiB
                capacity: 15GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-06-14 13:13:22 filesystem=ext4 modified=2009-06-16 07:59:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-06-16 07:59:32 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 1043MiB
                capacity: 1043MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1043MiB
                   capabilities: nofs
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:07:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-system:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:07:05.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64 module=sdhci_pci
        *-system:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:07:05.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
        *-system:2 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:07:05.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-generic UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 5.4
             bus info: pci@0000:07:05.4
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:36:74:13:66
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.180 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:91:de:95:7a:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Any suggestions? 
Thanks!

EDIT: I found webcam drivers but I dont know how to install them. [http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)

---

### Post by galland on 2009-11-19
To install Arakhne.org's packages, please follow the instructions at [http://www.arakhne.org/ubuntu.html](http://www.arakhne.org/ubuntu.html)

Stéphane.

---

