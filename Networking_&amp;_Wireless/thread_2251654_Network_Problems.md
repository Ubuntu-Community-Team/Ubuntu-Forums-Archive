---
title: "Network Problems"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by Curbie on 2014-11-05
I made the transition from Win to Xubuntu about two years ago (I think) and have never had any real problems until now. A coupe days ago, when I got up, the system wouldn't connect to the web with a "Server not found" error in Firefox and ping gives a "unknown host" message, after chasing the DLS provider around, they claim the problem is NOT with equipment (up to their modem). I tried to access the modem's menu through the browser by [http://192.168.2.1](http://192.168.2.1), which has worked in the past, but this time "Unable to connect - Firefox can't establish a connection to the server at 192.168.2.1".

When I right-click the network Icon on the desktop, it's context menu gives me "Enable Networking", a grayed out "Connection Information", and "Edit Connections..." options, I presume that since there's a "Enable Networking" option, that the network is not enabled, clicking the option, produces a "Network Disconnected - you are now offline" system message, but every thing else on the system seems to be operating just fine.

I built a new system for Ubuntu based on good recommendations from here, my OS is Xubuntu 12.04.1 64bit (I think the version is correct) neither lshw and lspci (attached) mention an Ethernet device which doesn't seem right, and all devices are part of the motherboard.

I'm trying to isolate whether this problem is hardware or software and how to fix it, right now I'm leaning towards a faulty Ethernet chip on the motherboard, but I'm confused because that motherboard is only about two years old.

Any help that would isolate this issue would be greatly appreciated! 


*************************************************************** OS: *****
	Xubuntu 12.04.1 64bit

***** lshw dump: *****
```

    description: Desktop Computer
    product: A780L3C (To Be Filled By O.E.M.)
    vendor: BIOSTAR Group
    serial: None
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A780L3C
       vendor: BIOSTAR Group
       physical id: 0
       serial: None
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014
          date: 07/31/2012
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X3 450 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) II X3 450 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=3 enabledcores=3
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fea00000-febfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780L [Radeon 3000]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:e000(size=256) memory:febf0000-febfffff memory:fea00000-feafffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:40 ioport:d000(size=8) ioport:c000(size=4) ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=16) memory:fe9ff800-fe9ffbff
           *-disk:0
                description: ATA Disk
                product: ST500DM002-1BD14
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KC45
                serial: Z3T24FRW
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000f390
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1ef20c10-da27-47c6-b744-46a1477a1313
                   size: 458GiB
                   capacity: 458GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-02-22 12:33:43 filesystem=ext4 lastmountpoint=/ modified=2013-02-22 13:27:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-11-04 21:36:30 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 7933MiB
                   capacity: 7933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7933MiB
                      capabilities: nofs
           *-disk:1
                description: EXT4 volume
                product: ST500DM002-1BD14
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                logical name: /media/data
                version: 1.0
                serial: ec1693e9-bb02-4c01-97ee-833bdd76325a
                size: 465GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: ansiversion=5 created=2013-02-23 21:15:51 filesystem=ext4 label=data lastmountpoint=/media/data modified=2014-11-04 21:39:43 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,barrier=1,data=ordered mounted=2014-11-04 21:39:43 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH24NS90
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/PIRATES_OF_THE_
                version: IN01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/PIRATES_OF_THE_
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe9fe000-fe9fefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe9fd000-fe9fdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe9ff000-fe9ff0ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe9fc000-fe9fcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe9fb000-fe9fbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe9fa800-fe9fa8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fe9f4000-fe9f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe9f9000-fe9f9fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
         width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```
***** lspci dump: *****
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]

```

---

### Post by kc1di on 2014-11-05
I don't see a network controller on either one of you dumps. Which would lead me to believe it's a hardware issue. and your controller has gone bad.
But that's just a guess.

---

### Post by Bucky Ball on 2014-11-05
Make and model of machine, please. Also, if you change the title of your thread to something that describes your problem specifically you will improve your chances of help. Generic titles aren't the best as 99% of people on the forums have 'problems' with something. ;)

---

### Post by Curbie on 2014-11-06
kc1di, would you think that IF lshw could find a Ethernet controller, it would be included in the list? Is there another Ubuntu command other than lshw or lspci I should try instead?

Bucky Ball, "I built a new system for Ubuntu based on good recommendations from here" from parts purchased from TigerDirect, I wouldn't think it would have any "Make and model"? I don't know what the problem is, other than Network Problems, I didn't know if it was hardware, software, or DSL when I posted, I've since dug the Window machine out of the garage I used for communications with this forum when I was building the machine and configuring Xubuntu, so it's NOT the DSL. I'll change the title/subject to anything more appropriate, but I still don't really know what's more appropriate, suggestions?

---

### Post by Bucky Ball on 2014-11-06
> **Curbie said:**
> kc1di, would you think that IF lshw could find a Ethernet controller, it would be included in the list? Is there another Ubuntu command other than lshw or lspci I should try instead?

```
sudo lshw -C network
```

If your ethernet card is not there under 'ethernet interface' then it won't appear with any other command. It's not recognised, so ...

> ethernet card not recognised: 12.04 

... might be one suggestion for a thread title.

---

### Post by Curbie on 2014-11-06
Bucky Ball, I ran the sudo lshw -C network command and the Ethernet interface showed up with the -C network switch (included below), although it's labeled as DISABLED, where the plain lshw command doesn't show the Ethernet controller at all? So the question remains, hardware or software, why is it disabled, and how do I isolate which one?

*-network DISABLED      
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth0
       version: 05
       serial: b8:97:5a:25:fe:a8
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff

---

### Post by Bucky Ball on 2014-11-06
I know this sounds crazy, but there isn't a hardware switch for wireless on the machine? Apologies if obvious and you've tried, but worth a mention ...

PS: Not sure if that's the right driver for that card and not sure if it needs firmware. The kernel seems to have automatically installed that driver. Gotta shoot off but back shortly to have a dig ... 

You looking to get this going: RTL8101E/RTL8102E
And have this driver installed: driver=r8169 driverversion=2.3LK-NAPI 

You could try creating the connection manually by clicking the network icon>edit>add. You'll need your router/AP details.

---

### Post by Curbie on 2014-11-06
Bucky Ball, I don't know if there is a hardware switch for wireless on the machine, IF there is, it would have to be a jumper or setting in bios on the motherboard that I've NOT seen or used, the machine was setup for wired, as has always been as wired, and just stopped connecting to the web a couple mornings ago after boot up. All drivers where automatically installed by Xubuntu during installation, but now even when I tried to run Xubuntu from disk (CD), it doesn't find the web as it did when I was testing it before the transition from Windows? I've kept up with all Ubuntu upgrades when the download upgrades dialog pop up once or twice a week.

---

### Post by kc1di on 2014-11-06
Was there a kernel update recently?  

If there was you may want to try booting from the previous kernel and see if that brings a connection back. 
If that does not work , I would say it's a hardware problem.

---

### Post by SeijiSensei on 2014-11-06
Is the network adapter disabled in the BIOS?

---

### Post by Curbie on 2014-11-06
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"), I checked once and couldn't find anything related to the network adapter in BIOS, but kc1di's suggestion makes sense, so I'll revisit the bios and try the previous kernel.

thanks to both for the suggestions.

---

### Post by Curbie on 2014-11-06
OK, on the second trip through I found the network adapter in BIOS and it's enabled, I then booted under the last previous kernel and still no internet. It's looking fairly hardware to me too, unless anyone has another suggestion?

---

### Post by SeijiSensei on 2014-11-06
Have a spare Ethernet card you could pop into the machine?

---

### Post by Curbie on 2014-11-07
[[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"), good plan, so I just ordered one that has a user review that says it works seamlessly with Ubuntu 12.04. For $15.00 at least I should be able to rule hardware IN or OUT as the problem. Do you know if I should first disable the network adapter in BIOS before installing the PCI NIC card when it arrives? Thank for the simple isolation idea!

---

### Post by kc1di on 2014-11-07
> **Curbie said:**
> [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"), good plan, so I just ordered one that has a user review that says it works seamlessly with Ubuntu 12.04. For $15.00 at least I should be able to rule hardware IN or OUT as the problem. Do you know if I should first disable the network adapter in BIOS before installing the PCI NIC card when it arrives? Thank for the simple isolation idea!

Yes it would be a good Idea to disable it before trying the new one.

---

### Post by Curbie on 2014-11-07
kc1di's, thanks for all your help, I think this plan will answer the hardware/software, question if not temporarily fix the issue.

---

### Post by chili555 on 2014-11-07
I wonder if this is a factor:> configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half [COLOR="#FF0000"]firmware=N/A[/COLOR] latency=0 link=no multicast=yes port=MII speed=10Mbit/sHowever, firmware is required:```
chili@ThinkT60:~$ modinfo r8169
filename:       /lib/modules/3.8.0-37-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
firmware:       rtl_nic/rtl8168g-1.fw
firmware:       rtl_nic/rtl8106e-1.fw
firmware:       rtl_nic/rtl8411-1.fw
firmware:       rtl_nic/rtl8402-1.fw
firmware:       rtl_nic/rtl8168f-2.fw
firmware:       rtl_nic/rtl8168f-1.fw
firmware:       rtl_nic/rtl8105e-1.fw
firmware:       rtl_nic/rtl8168e-3.fw
firmware:       rtl_nic/rtl8168e-2.fw
firmware:       rtl_nic/rtl8168e-1.fw
firmware:       rtl_nic/rtl8168d-2.fw
firmware:       rtl_nic/rtl8168d-1.fw
version:        2.3LK-NAPI
<snip>
```Does dmesg hold any clues?```
dmesg | grep r8169
```Just a wild guess...

--------------------

EDIT: Here is an *lshw *I found on this forum a few moments ago:> broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full [COLOR="#FF0000"]firmware=rtl_nic/rtl8168d-1.fw[/COLOR] ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/sThe plot thickens.

---

### Post by Curbie on 2014-11-07
chile555, grep found no occurrence of the text "r8169" in dmesg.

```
modinfo r8169
filename:       /lib/modules/3.2.0-70-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
firmware:       rtl_nic/rtl8168f-2.fw
firmware:       rtl_nic/rtl8168f-1.fw
firmware:       rtl_nic/rtl8105e-1.fw
firmware:       rtl_nic/rtl8168e-3.fw
firmware:       rtl_nic/rtl8168e-2.fw
firmware:       rtl_nic/rtl8168e-1.fw
firmware:       rtl_nic/rtl8168d-2.fw
firmware:       rtl_nic/rtl8168d-1.fw
version:        2.3LK-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <[EMAIL="netdev@vger.kernel.org"]netdev@vger.kernel.org[/EMAIL]>
srcversion:     68C95644833EA999EB53AF1
alias:          pci:v00000001d00008168sv*sd00002410bc*sc*i*
alias:          pci:v00001737d00001032sv*sd00000024bc*sc*i*
alias:          pci:v000016ECd00000116sv*sd*bc*sc*i*
alias:          pci:v00001259d0000C107sv*sd*bc*sc*i*
alias:          pci:v00001186d00004302sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-70-generic SMP mod_unload modversions 
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)
```

---

### Post by Bucky Ball on 2014-11-07
Please use [code] tags. Neater, space-saving and easier to read. See the last link in my signature. Have added them to your last post as an example. ;)

---

### Post by chili555 on 2014-11-07
> chile555, grep found no occurrence of the text "r8169" in dmesg.Please load it explicitly and check again. ```
sudo modprobe -r r8169
sudo modprobe r8169
dmesg | grep r8169
```This is a technique I like to call 'poking the skunk.'

---

### Post by Bucky Ball on 2014-11-07
> **chili555 said:**
> This is a technique I like to call 'poking the skunk.'

Ha! Wondered what that stench was! ;)

Sorry, off topic. I give myself a warning.

---

### Post by Curbie on 2014-11-07
chile555, I removed and reloaded the r8169 module:
```
sudo modprobe -r r8169
sudo modprobe r8169
dmesg | grep r8169
```
grep found no occurrence of the text "r8169" in dmesg again,  and I tried the web once again for giggles with no joy, apparently, Pepe' doesn't respond to pokes?
After following your repair logic from "lshw -C network" to "firmware=N/A" to "driver=r8169" to "modprobe remove and reload" it was certainly worth a try, it seems more and more a hardware issue.

---

### Post by chili555 on 2014-11-08
> After following your repair logic from "lshw -C network" to "firmware=N/A" to "driver=r8169"When it shows "driver=r8169" is there a logical name shown, ideally eth0? If so,is there any mention of eth0 in the log?```
dmesg | grep eth0
```

---

### Post by Curbie on 2014-11-08
chili555, grep found no occurrence of the text "eth0" in dmesg, no logical name either.

---

### Post by chili555 on 2014-11-08
> **Curbie said:**
> chili555, grep found no occurrence of the text "eth0" in dmesg, no logical name either.Then I concur that it is probably a hardware problem. If this is a desktop, I suggest you remove and replace the NIC.

---

### Post by Curbie on 2014-11-08
chili555, the bad network adapter is part of an onboard chipset, I've ordered a PCI NIC that has an user review who states the NIC card I ordered worked seamlessly with his Ubuntu 12.04, and have now disabled the onboard network adapter through BIOS and am just waiting for the NIC card to come in (it shipped yesterday), hopefully, a new NIC card will fix the problem. I will update this thread's status and add a closing post if it does.

---

### Post by Curbie on 2014-11-16
The on-board network adapter of the motherboard did go bad, and disabling the network adapter in the BOIS and then installing the new PCI NIC solved the problem, simple hardware failure, and after two years of running Xubuntu basically 24/7 except for reboots require by upgrades Xubuntu has yet to even hiccup. Thanks to kc1di, Bucky Ball, SeijiSensei, chilli555 for all their time and help isolating such a simple problem!

---

### Post by Bucky Ball on 2014-11-18
All good. Thanks for sharing the fix and marking as solved to help others, and good luck with it all. ;)

---

