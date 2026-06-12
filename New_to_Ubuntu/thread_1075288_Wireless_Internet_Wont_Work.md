---
title: "Wireless Internet Wont Work"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by koopa225 on 2009-02-20
Ok, I have been through numerous threads and nothing has seemed to work for me so far, I am new to Ubuntu and still learning. When I was using windows my wireless worked fine, now I am strictly using Ubuntu and my wireless wont work at all. When i right click the network thing in the right hand corner the box enable wireless is checked, but when I left click it wireless networks is greyed out. I am really getting frustrated trying to figure this out can somebody help me please.

---

### Post by binbash on 2009-02-20
paste the output of sudo lshw so we can see which chipset you are using

---

### Post by koopa225 on 2009-02-22
coreys-notebook           
    description: Portable Computer
    product: MX7122
    vendor: Gateway
    version: 0100
    serial: N3265 H10 28060
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=1 uuid=80C43681-C564-0010-A097-BF1B79D478E4
  *-core
       description: Motherboard
       product: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       vendor: Gateway
       physical id: 0
       version: 65.08.00
       serial: V65RM050071Y7F500X
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 65.08.00 (06/28/2005)
          size: 101KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          slot: Socket 754
          size: 2200MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: S2
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:03:25:35:83:eb
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=72.219.21.20 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2080A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: NSA2T612984K
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4b36bdea
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: a88683c7-6813-462d-b8b1-b63dc7fa18c3
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-10 02:15:11 filesystem=ext3 modified=2009-02-21 22:46:07 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-21 22:46:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1278MiB
                   capacity: 1278MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1278MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD-RW GWA-4082N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CG03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 5
                bus info: pci@0000:08:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 7
                bus info: pci@0000:08:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:08:0e.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:95:73:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:62:4e:c4:b1:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by lkraemer on 2009-02-22
This should be easy!

As your output displays you have a:
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation

So, use SEARCH and look for BCM4318 in this forum.

You have two ways to go.  Use the Windows drivers with ndiswrapper,
or by using the bcm43xx-fwcutter and the firmware.  I don't know what is
currently recommended, or what Distro you are running, or what version,
but I used the Windows Drivers and ndiswrapper with 8.04 LTS.

If you boot Windows and go look at the Wifi Drivers you will most likely
find that bcmwl5.inf is used, or something similar.  You will need these
files (inf & sys) if you use ndiswrapper.

OR 

SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER
SEARCH bcm43xx-fwcutter

...........there's that dad burn SEARCH again......

This should give you the firmware:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Once the firmware is extracted, you should be able to modprobe bcm43xx
it and be up and running.

It's up to you to search out the best method nowdays for your machine.

I used Jamie Jackson's writeup, and it worked fine for me on 8.04 LTS,
but you might be using a later version.  SEARCH & GOOGLE will help
you find the correct best answers.

For REF:
[http://ubuntuforums.org/showthread.php?t=870086](http://ubuntuforums.org/showthread.php?t=870086)

Now, isn't SEARCHING FUN?  It's an ADVENTURE!

lkraemer

---

