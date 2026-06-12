---
title: "OS locking up - Ubuntu 10.10"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by lsward on 2011-01-29
My system is locking up occasionally and I can't get the computer to reboot so I have to do a press the power button and then start the computer again.  I know this will possible damage the HD if this happens to often.  How do I find out what is going on and prevent something like this from occurring again?

---

### Post by Temposs on 2011-01-29
Well, I don't think that the computer freezing will cause the hard drive to be damaged, but rather that it is a possible sign of hard drive damage.

Try this for now:
Go to System->Administration->Disk Utility. Find your hard drive listed on the left side and click on it. Then find the button that says "Check Filesystem" and see if it finds any errors. EDIT: Also find the section in that window called SMART Status and see if it says "Drive Healthy" or something else.

---

### Post by NightwishFan on 2011-01-29
Does it lock up with flashing keyboard lights? If so you are having a kernel panic. Try looking through System -> Administration -> Log File Viewer. Syslog is a good start. If you remember the time when it locked up it will be in one of the syslogs at that time.

---

### Post by dirghrabadia on 2011-01-30
If I were you, I would download and install all the system updates. I had a similar problem in 9.10, but was resolved once I updated it.

---

### Post by robert shearer on 2011-01-30
As to what is locking up your machine you have given too little info to even guess at.

How about for starters posting the output from..
```
sudo lshw
```

When the machine freezes **don't** hit the power button. This is a certain way to file corruption and can damage your drive.

Instead learn the sequence to safely shut-down/reboot from here...
[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

Note rseiub reboots and rseiuo turns off.

you may have to repeat the sequence a couple of times and leave 1 second between each key combo.
The alt+sysreq+s can be repeated a few times if there are a lot of files to sync.

---

### Post by lsward on 2011-01-30
here are the log files:
```

lincoln-presario-r3000-pc777av
    description: Notebook
    product: Presario R3000 PC777AV
    vendor: Hewlett-Packard
    version: F.43
    serial: CND4490G8B
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=EF02572C-12FF-11D9-8E73-000FB00F4B8E
  *-core
       description: Motherboard
       product: 089C
       vendor: Hewlett-Packard
       physical id: 0
       version: 31.43
       serial: CND4490G8BABCDEF
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.43 (12/15/2004)
          size: 108KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot smartbattery
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: JP8
          size: 3200MHz
          capacity: 3200MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 8KiB
             capacity: 1MiB
             capabilities: burst internal write-back
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
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 768MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: U5
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: U6
             size: 256MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Radeon 9100 IGP Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:d2000000-d3ffffff memory:d0000000-d0000fff
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
             resources: ioport:9000(size=4096) memory:d0100000-d01fffff memory:e0000000-efffffff
           *-display
                description: VGA compatible controller
                product: RS300M AGP [Radeon Mobility 9100IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:16 memory:e0000000-efffffff ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:d0001000-d0001fff
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
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:d0002000-d0002fff
        *-serial UNCLAIMED
             description: SMBus
             product: SMBus
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 16
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
             resources: ioport:8040(size=16) memory:40000000-400003ff
        *-ide
             description: IDE interface
             product: Dual Channel Bus Master PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8060(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8026GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PA00
                serial: Y49P1234T
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ba56d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 3b5131f5-afe0-4488-acc8-30bb42ddd08c
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-27 19:58:02 filesystem=ext4 lastmountpoint=/&#65533;&#65533;H&#65533;G&#65533;&#65533;lM&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; ~b&#1764;q!&#65533;&#65533;lM&#65533;~b&#65533;8&#65533;x&#65533;8&#65533;x&#65533;&#65533;G&#65533; &#65533;8~b&#65533;It!&#65533;&#65533;j modified=2011-01-27 20:32:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-30 20:18:09 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2248MiB
                   capacity: 2248MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2248MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-R2512
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1A04
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
             product: IXP200 3COM 3C920B Ethernet Controller
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:d0200000-d02fffff memory:38000000-3fffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:d0208000-d02087ff memory:d0200000-d0203fff
           *-network:0
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:18 memory:d0204000-d0205fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:0f:4b:8e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:19 ioport:a000(size=256) memory:d0208800-d02088ff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:d0209000-d0209fff ioport:a800(size=256) ioport:ac00(size=256) memory:38000000-3bffffff memory:44000000-47ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1620 PC Card Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d020a000-d020afff ioport:1400(size=256) ioport:1800(size=256) memory:3c000000-3fffffff memory:48000000-4bffffff
           *-generic UNCLAIMED
                description: System peripheral
                product: PCI1620 Firmware Loading Function
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=7
                resources: ioport:a400(size=64)
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:16 memory:d0206000-d0206fff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 7.1
                bus info: pci@0000:02:07.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:18 memory:d0207000-d0207fff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16
                resources: irq:19 memory:d0208c00-d0208cff
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
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:5 memory:d0003000-d00030ff
        *-communication
             description: Modem
             product: IXP AC'97 Modem
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2
             resources: irq:5 memory:d0003400-d00034ff
  *-battery
       physical id: 1
       slot: Left Front
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: inbound
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:9f:1d:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-25-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```
I have tried using the sequence for shutting it down and it never worked.  I know you are not suppose to press the power button.  I also have done all my updates.  I did a files system check in disk utility and it said I have a few bad sectors.  I'm going to try to repair that, but what else should I be looking for.  Let me know if the output from sudo lshw has an clues.  Thanks for the help.

---

