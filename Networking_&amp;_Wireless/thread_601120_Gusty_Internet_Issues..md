---
title: "Gusty Internet Issues."
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by Alucard-sama on 2007-11-02
I just installed gutsy and was unable to use the net.
After following this tutorial: [http://youtube.com/watch?v=Sd8nHsUevAY](http://youtube.com/watch?v=Sd8nHsUevAY),
I'm able to connect using Firefox, but I'm still unable to connect using anything else (eg: Aptitude, Evolution, Pidgin, etc.)
Anybody know how to fix this?

---

### Post by Alucard-sama on 2007-11-03
Nobody? :(

---

### Post by Buster95 on 2007-11-03
Hello Alucard-sama,
In order to get help, you may need to provide as much specific information as you can. For example:
1 what you are using (brand, model etc)
2 what IS working (Is wired OK?Is wireless OK?etc)
3 key terminal outputs (lspci, lsusb, lshw, etc)

Then the experts on this site will certainly help you.
Cheers

---

### Post by Alucard-sama on 2007-11-03
K I'm using a D-Link DSL-502T.
It's plugged in through Ethernet and dosn't seem to be having any problems (ie all lights are on except USB.
I don't have a wireless card.
Most programs are working now (ie DC++, Firefox, etc.) but Pidgin and Synaptic/Apt still aren't.

 This is the output from lspci:
> 00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 9100 IGP
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


This is the output from lsusb:
> Bus 003 Device 002: ID 1307:0163  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

This is the output from lshw (I think some might have got cut off?):
> width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SMBus
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 17
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Dual Channel Bus Master PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   product: ST340014A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
              *-disk:1
                   product: Maxtor 6Y080P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 76GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: LITE-ON DVDRW SOHW-1653S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 698MB
                   capabilities: packet
              *-cdrom:1
                   product: _NEC DVD+/-RW ND-3530A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:19:e0:0c:c6:38
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 10
                serial: 00:01:2e:01:e4:1b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.1.1.4 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage
alucard-sama@Ken-Linux:~$ sudo lshw
[sudo] password for alucard-sama:
ken-linux                 
    description: Desktop Computer
    product: RS300-SB200
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: RS300-SB200
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/05/2003)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.2.9
          slot: Socket 478
          size: 2600MHz
          clock: 100MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 256MB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: Radeon 9100 IGP Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp
        *-pci:0
             description: PCI bridge
             product: Radeon 9100 IGP AGP Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon 9100 IGP
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga bus_master cap_list
                configuration: latency=64 mingnt=8
        *-usb:0
             description: USB Controller
             product: OHCI USB Controller #1
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: OHCI USB Controller #2
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: EHCI USB Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SMBus
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 17
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Dual Channel Bus Master PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: ST340014A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 8.01
                   serial: 5JXMG93R
                   size: 37GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 37GB
                      capabilities: primary bootable
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6Y080P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: YAR41BW0
                   serial: Y2FDS1HE
                   size: 76GB
                   capacity: 76GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux swap / Solaris partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 972MB
                      capabilities: primary nofs
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      capacity: 75GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: DVD writer
                   product: LITE-ON DVDRW SOHW-1653S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: CS07
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: DVD writer
                   product: _NEC DVD+/-RW ND-3530A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 102B
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=nodisc
        *-isa
             description: ISA bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:19:e0:0c:c6:38
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 10
                serial: 00:01:2e:01:e4:1b
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.4 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
     *-scsi
          physical id: 1
          bus info: usb@3:2
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Flash Disk
             vendor: USB 2.0
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0.00
             size: 1967MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sda
                size: 1967MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: FAT16 partition
                   physical id: 1
                   logical name: /dev/sda1
                   capacity: 1967MB
                   capabilities: primary bootable


EDIT: Sorry if that post was a bit bloated but I didn't want to miss anything important by being selective about the output I posted.

---

