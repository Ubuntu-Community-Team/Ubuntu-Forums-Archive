---
title: "lg super multi drives"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by monoiz15 on 2009-03-16
heyyyy my desktop has two lg super multi cd-rw dvd+r dl drives and neither of them are being detected. i was trying to burn a disc with brasero and when it didnt work i got imgburn and put it on wine.. i thought that was probly like not a good idea or whatever but when that didnt work i got a trial of nero linux and none of these picked up the devices.. then i got some common sense to go in my terminal and type lspci which gave me this:

monohome@mono-home-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:01.0 USB Controller: NEC Corporation USB (rev 41)
02:01.1 USB Controller: NEC Corporation USB (rev 41)
02:01.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:04.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

so the devices are not being found. can someone point me in the right direction??

---

### Post by halitech on 2009-03-16
lspci doesn't pick up my drives either

whats the output of```
lshw -C disk
```

---

### Post by mc4man on 2009-03-16
If your drives show up in lshw...(which they should) I'd try for a linux burning app k3b

As far as Imgburn (which I use), try going into the wine menu -> configure wine. Make sure the windows version is xp or nt 4.0. Then under the drives tab click the 'autodetect' box.

It's also better to set Imgburn's I/O to ASPI-WINASPI32.DLL
(tools -> setting's -> I/O

---

### Post by monoiz15 on 2009-03-16
root@mono-home-desktop:/home/monohome# lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: ST380020A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 5.46
       serial: 5GC15BS0
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6cbf57b9
  *-disk:1
       description: ATA Disk
       product: Maxtor 4D080H4
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: DAH0
       serial: D40926YE
       size: 76GiB (81GB)
       configuration: ansiversion=5 signature=54456027


i have 2 80 gig hard drives

---

### Post by halitech on 2009-03-16
and the 2 80gig hard drives are the only things being detected which is why nothing is working for burning. are the burners IDE or SATA? Did they work previously? Do they work in windows?

---

### Post by monoiz15 on 2009-03-16
they are ide and they work in windows

---

### Post by halitech on 2009-03-17
lets see the entire output of ```
lshw
```

surround it with code /code tags so we can see the entire thing.

---

### Post by monoiz15 on 2009-03-19
```

root@mono-home-desktop:/home/monohome# lshw
mono-home-desktop         
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: i850E-W83637
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (11/08/2002)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 512KiB
     *-cache
          description: L1 cache
          physical id: b
          slot: External Cache
          size: 20KiB
          capacity: 20KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MiB
             width: 16 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 256MiB
             width: 16 bits
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 256MiB
             width: 16 bits
        *-bank:3
             description: DIMM
             physical id: 3
             slot: A3
             size: 256MiB
             width: 16 bits
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16 module=ehci_hcd
           *-network:0
                description: Ethernet interface
                product: SMC2-1211TX
                vendor: Accton Technology Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth0
                version: 10
                serial: 00:00:e8:7f:ea:ff
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 10
                serial: 00:d0:68:00:aa:66
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.7 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ST380020A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 5.46
                serial: 5GC15BS0
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6cbf57b9
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 034e4c75-861b-48eb-9365-54e3ec735365
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-09 10:34:29 filesystem=ext3 modified=2009-03-18 21:40:06 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-18 21:40:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2949MiB
                   capacity: 2949MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2949MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 4D080H4
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: DAH0
                serial: D40926YE
                size: 76GiB (81GB)
                configuration: ansiversion=5 signature=54456027
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:db:96:d0:3d:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

