---
title: "Absolute nightmare with dual boot!"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Truemedia on 2010-08-12
Time after time I am getting nowhere with dual booting windows and ubuntu, they just never work permanently. After making new topics for more and more problems I am getting, and trying to find a solution to them I'm afraid my whole computer is going to go to hell unless I completely wipe out ubuntu, or solve the problems now.

Iv'e had bits of help on various topics from friendly knowledgeable people, but before my problems are solved my topics disappear into the depths of page numbers unknown, and rarely bumping the topics or researching what to do and being more specific on the errors I'm getting hasn't really got me anywhere.

After trying to reinstall ubuntu for the 6th time, after various other installations to quickly avoid my problems for a short amount of time, and try to start from fresh this time it didn't actually work. And now not only does my ubuntu install still go to a grub bash screen same as before, but now windows is really acting scarily broken.

To briefly explain my situation, first time ubuntu I tried through wubi, and space began causing me problems (my 1 primary hard drive quickly became full so I reinstalled wubi). After freeing up some space, in ubuntu an update caused lockout of windows and ubuntu. To solve that someone told me how to restore windows and after that got rid of wubi. Then to try ubuntu without wubi I went to create a 2nd partition but accidently installed over windows and once again locked out (restoring windows boot and deleting ubuntu solved this). Then after careful research tryed an external hard drive ubuntu installation. That worked well but then updates once again locked me out of only ubuntu (not windows) with grub error screen. Everyone suggested reinstalling grub, and it worked until another update caused a different grub screen hinting at no error but to type bash functions?. Found no answers to this so reinstalled ubuntu again watching to avoid grub updates next time, yet accidentally it was in the update which I didn't see. Tryed reinstalling for the 6th time, but now that doesn't even work.

Just the grub black and white screen hinting I can use bash like commands, and windows (which I did't even touch with settings) is telling me I have a corrupt disk? and is not let me install software or down anything? 

```
any_application_I_am_using.exe - Corrupt Disk
the file system on the disk is corrupt and unusable. Please run the Chkdsk utility on the volume C:.   
```

This is what windows is bringing up in a task bar error bubble now every time I try to do anything, and when I click on it, nothing.

I will boot the liveCD and provide all the information for my setup I can below, but please anyone I really need help to stop this, it is completely stopping me doing anything on my PC and just hasn't gone away no matter what Iv'e tried so far :(.

Please, I love the idea of ubuntu and would like to continue using it in future despite the horrific experience I have had with setting it up against a windows system, and don't want to have to avoid it, to have a Pc that actually works.

Any help is appreciated and I thank anyone for their help, but if you think you know the solution please don't ignore this topic, as I have been trying for so long to get this to work. Thanks

---

### Post by ghettobird on 2010-08-12
Ya that would suck. I'm not sure of your setup, but I would say keep all OS's on a separate drive that way theres no bickering between the two. As for GRUB, I left it alone and it recognized the windows loader and put it in it's respective pecking order.

---

### Post by Paul820 on 2010-08-12
Have you ran chkdsk on windows? Sounds like installing ubuntu has messed up some files. It is best to defragment your drive and back up any critical data before installing a dual boot, as windows has a habit of throwing files across as much of the drive as it can. Read this on how to run chkdsk [http://www.updatexp.com/windows-xp-chkdsk.html]("http://www.updatexp.com/windows-xp-chkdsk.html")

---

### Post by Truemedia on 2010-08-12
Using the livecd to boot and then going into terminal this is what Iv'e got from the following commands:

**sudo lshw** (hardware)
```
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: K10N78hSLI-GLAN
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.00 (04/25/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 2700MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP78S [GeForce 8200] LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:2f00(size=256)
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
          resources: irq:10 ioport:2900(size=64) ioport:2d00(size=64) ioport:2e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
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
          resources: memory:f9f80000-f9ffffff
     *-memory:3 UNCLAIMED
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
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:f9f7f000-f9f7ffff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f9f7ec00-f9f7ecff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:f9f7d000-f9f7dfff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:f9f7e800-f9f7e8ff
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
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
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
          resources: irq:21 memory:f9f78000-f9f7bfff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:28 ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=16) memory:f9f76000-f9f77fff
        *-disk
             description: ATA Disk
             product: ST3250310AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AH
             serial: 6RYCWBZV
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=f90c5490
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 50bf9323-5f2e-084a-bad5-f4780597e142
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-02-28 21:57:01 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7173S
             vendor: Optiarc
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1-00
             serial: [Optiarc DVD RW AD-7173S 1-00 Dec21,2006
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /cdrom
                configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:19:66:71:b7:3c
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:29 memory:f9f7c000-f9f7cfff ioport:b880(size=8) memory:f9f7e400-f9f7e4ff memory:f9f7e000-f9f7e00f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:d000(size=4096) memory:fa000000-fd7fffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G96 [GeForce 9400 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:19 memory:fc000000-fcffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:dc00(size=128) memory:fd780000-fd7fffff(prefetchable)
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:f5f00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 13
          bus info: pci@0000:00:13.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26 ioport:e000(size=4096) memory:fd800000-febfffff ioport:f6000000(size=49283072)
     *-pci:4
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:27 ioport:f8f00000(size=1048576)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: b
          bus info: usb@2:2
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/scd1
             logical name: /dev/sr1
             capabilities: audio
             configuration: status=ready
        *-disk
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdb
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0005766e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@8:0.0.1,1
                logical name: /dev/sdb1
                version: 1.0
                serial: b709666b-25a6-4db1-bbd5-85ad16a56616
                size: 292GiB
                capacity: 292GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-08-12 18:17:27 filesystem=ext4 lastmountpoint=/target&#65533;&&#65533;&#65533;&#65533;&#65533;7&#65533;(&#65533;&&#65533;&#65533;&#65533;T&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;Mw&#65533;&#65533;&#65533;&#65533;&#65533;|&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-08-12 18:31:17 mounted=2010-08-12 18:20:11 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@8:0.0.1,2
                logical name: /dev/sdb2
                size: 5883MiB
                capacity: 5883MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 5883MiB
                   capabilities: nofs
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:12:90:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.4 multicast=yes wireless=IEEE 802.11bg
ubuntu@ubuntu:~$ 

```

and below this from **sudo fdisk -l** (software, os, kernel)
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf90c5490

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196344    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320046346240 bytes
255 heads, 63 sectors/track, 38910 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005766e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38160   306518016   83  Linux
/dev/sdb2           38160       38910     6024193    5  Extended
/dev/sdb5           38160       38910     6024192   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Other info I can provide that might be useful is the windows os is Vista, The two hard drives are 1 internal and 1 external (usb hard drive). I can access the liveCD, and boot it with access to the internet. its a 64bit system (amd) and my three most recent reinstall trys (as mentioned before) involved installing ubuntu and the grub on the external hard drive by completely erasing the external hard drive.

I havn't attempted to try to solve what windows wants me to yet, because I am not sure where to start with that, but am looking into the links provided already.

---

### Post by Truemedia on 2010-08-12
Ok when i restarted windows, it automatically did the correction process so windows looks clean now (couls see a random grub folder on the c drive on livecd before this for some strange reason even though I avoided installing on c drive)

Will edit this post with exact grub message when I can boot my computer again.

---

