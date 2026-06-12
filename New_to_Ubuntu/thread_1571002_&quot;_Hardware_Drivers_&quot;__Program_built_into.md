---
title: "&quot; Hardware Drivers &quot;  Program built into linux 9.10"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2010-09-09
Question how can I install a Nvidia Ge-Force Video Card Driver when It dose not show up in "  Hardware Drivers " . When I left click on System---  Administration---  Hardware Drivers  no Nvidia Drivers show up even though I installed one through   Applications--- Ubuntu Software center.  Also I downloaded the right driver from Nvidia and put it on my desktop tried to run it as root in Terminal didn't work.  What am I doing wrong here ?????????.

---

### Post by jtarin on 2010-09-09
Let's take one step at at time. What exactly did you download from the software center? What graphics card/chip are you running?

---

### Post by RemmyNumber7 on 2010-09-10
I am running now in low graphics mode, I have a 64 megabyte ati agp card in right now.  But I want to install a Ge-Force 6600 DDR 256MB AGP video Card. from what I read on this forum the ATI card I have in it now is to low of a version for Ubuntu to get a driver for it. 

every time I look in System--**Admin**-- **Hardware Drivers** --no drivers are there even if I go to the software Center and install the right Nvidia driver for it. It doesn't show up in **Hardware Drivers** ??????????????



This is the specs for my motherboard I am running on a gig of ram in it. 

```
  	 	 	 	p { margin-bottom: 0.08in; }  jim-desktop                
     description: Desktop Computer  
     product: MS-7032  
     vendor: MSI  
     version: 1.0  
     serial: 00000000  
     width: 32 bits  
     capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp  
     configuration: chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009  
   *-core  
        description: Motherboard  
        product: MS-7032  
        vendor: MSI  
        physical id: 0  
        version: 1.0  
        serial: 00000000  
        slot: To Be Filled By O.E.M.  
      *-firmware  
           description: BIOS  
           vendor: American Megatrends Inc.  
           physical id: 0  
           version: 080011 (11/24/2005)  
           size: 64KiB  
           capacity: 448KiB  
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification  
      *-cpu  
           description: CPU  
           product: AMD Athlon(tm) 64 Processor 3700+  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 4  
           bus info: cpu@0  
           version: 15.4.10  
           serial: To Be Filled By O.E.M.  
           slot: CPU 1  
           size: 2400MHz  
           capacity: 2400MHz  
           width: 64 bits  
           clock: 200MHz  
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up  
         *-cache:0  
              description: L1 cache  
              physical id: 5  
              slot: L1-Cache  
              size: 128KiB  
              capabilities: pipeline-burst internal varies data  
         *-cache:1  
              description: L2 cache  
              physical id: 6  
              slot: L2-Cache  
              size: 1MiB  
              capacity: 1MiB  
              capabilities: pipeline-burst internal varies unified  
      *-memory  
           description: System Memory  
           physical id: 28  
           slot: System board or motherboard  
           size: 1GiB  
         *-bank:0  
              description: DIMM DDR Synchronous 400 MHz (2.5 ns)  
              product: PartNum0  
              vendor: Manufacturer0  
              physical id: 0  
              serial: SerNum0  
              slot: DIMM0  
              size: 1GiB  
              width: 64 bits  
              clock: 400MHz (2.5ns)  
         *-bank:1  
              description: DIMM [empty]  
              product: PartNum1  
              vendor: Manufacturer1  
              physical id: 1  
              serial: SerNum1  
              slot: DIMM1  
      *-pci:0  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 00  
           width: 32 bits  
           clock: 66MHz  
           configuration: driver=agpgart-amd64 latency=64  
           resources: irq:0 memory:f0000000-f7ffffff(prefetchable)  
         *-pci  
              description: PCI bridge  
              product: VT8237 PCI bridge [K8T800/K8T890 South]  
              vendor: VIA Technologies, Inc.  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci pm bus_master cap_list  
              resources: ioport:b000(size=4096) memory:ff500000-ff5fffff memory:deb00000-eeafffff(prefetchable)  
            *-display:0 UNCLAIMED  
                 description: VGA compatible controller  
                 product: Radeon RV250 If [Radeon 9000]  
                 vendor: ATI Technologies Inc  
                 physical id: 0  
                 bus info: pci@0000:01:00.0  
                 version: 01  
                 width: 32 bits  
                 clock: 66MHz  
                 capabilities: agp agp-2.0 pm bus_master cap_list  
                 configuration: latency=64 mingnt=8  
                 resources: memory:e8000000-ebffffff(prefetchable) ioport:b800(size=256) memory:ff5f0000-ff5fffff memory:ff5c0000-ff5dffff(prefetchable)  
            *-display:1 UNCLAIMED  
                 description: Display controller  
                 product: Radeon RV250 [Radeon 9000] (Secondary)  
                 vendor: ATI Technologies Inc  
                 physical id: 0.1  
                 bus info: pci@0000:01:00.1  
                 version: 01  
                 width: 32 bits  
                 clock: 66MHz  
                 capabilities: pm bus_master cap_list  
                 configuration: latency=64 mingnt=8  
                 resources: memory:e4000000-e7ffffff(prefetchable) memory:ff5e0000-ff5effff  
         *-storage  
              description: RAID bus controller  
              product: VIA VT6420 SATA RAID Controller  
              vendor: VIA Technologies, Inc.  
              physical id: f  
              bus info: pci@0000:00:0f.0 
              version: 80  
              width: 32 bits  
              clock: 33MHz  
              capabilities: storage pm bus_master cap_list  
              configuration: driver=sata_via latency=64  
              resources: irq:20 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) ioport:d800(size=256)  
         *-ide  
              description: IDE interface 
              product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE  
              vendor: VIA Technologies, Inc.  
              physical id: f.1  
              bus info: pci@0000:00:0f.1 
              logical name: scsi0  
              logical name: scsi1  
              version: 06  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide pm bus_master cap_list emulated  
              configuration: driver=pata_via latency=32  
              resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)  
            *-disk  
                 description: ATA Disk  
                 product: WDC WD800JB-00JJ  
                 vendor: Western Digital 
                 physical id: 0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/sda  
                 version: 05.0  
                 serial: WD-WCAM91155603 
                 size: 74GiB (80GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=0005c311  
               *-volume:0  
                    description: EXT4 volume  
                    vendor: Linux  
                    physical id: 1  
                    bus info: scsi@0:0.0.0,1  
                    logical name: /dev/sda1  
                    logical name: /  
                    version: 1.0  
                    serial: bd5f706f-a97a-4a8d-99f7-ca365d428215  
                    size: 71GiB  
                    capacity: 71GiB  
                    capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized  
                    configuration: created=2010-08-25 04:54:00 filesystem=ext4 label=My Drive lastmountpoint=/&#65533;-1&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x~&#65533;&#65533;yf&#65533;pw&#65533;&#65533;pw&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;~&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;`&&#65533;&#65533; modified=2010-09-01 15:22:10 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-02 03:36:21 state=mounted  
               *-volume:1  
                    description: Extended partition  
                    physical id: 2  
                    bus info: scsi@0:0.0.0,2  
                    logical name: /dev/sda2  
                    size: 2933MiB  
                    capacity: 2933MiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 2933MiB 
                       capabilities: nofs  
            *-cdrom  
                 description: DVD-RAM writer  
                 product: DVDRAM GSA-4160B  
                 vendor: HL-DT-ST  
                 physical id: 1  
                 bus info: scsi@1:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/dvdrw  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: A303  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 status=nodisc  
         *-usb:0  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10  
              bus info: pci@0000:00:10.0 
              version: 81  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=64  
              resources: irq:21 ioport:d400(size=32)  
         *-usb:1  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10.1  
              bus info: pci@0000:00:10.1 
              version: 81  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=64  
              resources: irq:21 ioport:d000(size=32)  
         *-usb:2  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10.2  
              bus info: pci@0000:00:10.2 
              version: 81  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=64  
              resources: irq:21 ioport:cc00(size=32)  
         *-usb:3  
              description: USB Controller  
              product: VT82xxxxx UHCI USB 1.1 Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 10.3  
              bus info: pci@0000:00:10.3 
              version: 81  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=uhci_hcd latency=64  
              resources: irq:21 ioport:c800(size=32)  
         *-usb:4  
              description: USB Controller  
              product: USB 2.0  
              vendor: VIA Technologies, Inc.  
              physical id: 10.4  
              bus info: pci@0000:00:10.4 
              version: 86  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:21 memory:ff6ffc00-ff6ffcff  
         *-isa  
              description: ISA bridge  
              product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]  
              vendor: VIA Technologies, Inc.  
              physical id: 11  
              bus info: pci@0000:00:11.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa pm bus_master cap_list  
              configuration: latency=0  
         *-multimedia  
              description: Multimedia audio controller  
              product: VT8233/A/8235/8237 AC97 Audio Controller  
              vendor: VIA Technologies, Inc.  
              physical id: 11.5  
              bus info: pci@0000:00:11.5 
              version: 60  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm cap_list  
              configuration: driver=VIA 82xx Audio latency=0  
              resources: irq:22 ioport:c400(size=256)  
         *-network  
              description: Ethernet interface  
              product: VT6102 [Rhine-II] 
              vendor: VIA Technologies, Inc.  
              physical id: 12  
              bus info: pci@0000:00:12.0 
              logical name: eth0  
              version: 78  
              serial: 00:13:d3:ee:22:8f  
              size: 100MB/s  
              capacity: 100MB/s  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
              configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.10 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s  
              resources: irq:23 ioport:c000(size=256) memory:ff6ff800-ff6ff8ff  
      *-pci:1  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 101  
           bus info: pci@0000:00:00.1  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:2  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 102  
           bus info: pci@0000:00:00.2  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:3  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 103  
           bus info: pci@0000:00:00.3  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:4  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 104  
           bus info: pci@0000:00:00.4  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:5  
           description: Host bridge  
           product: K8T800Pro Host Bridge  
           vendor: VIA Technologies, Inc.  
           physical id: 105  
           bus info: pci@0000:00:00.7  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:6  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 106  
           bus info: pci@0000:00:18.0  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:7  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] Address Map  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 107  
           bus info: pci@0000:00:18.1  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:8  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] DRAM Controller  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 108  
           bus info: pci@0000:00:18.2  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:9  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] Miscellaneous Control  
           vendor: Advanced Micro Devices [AMD]  
           physical id: 109  
           bus info: pci@0000:00:18.3  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=k8temp  
           resources: irq:0
 

 

 

 

 

 

 

 

 

 

 

 

  00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge  
 00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]  
 00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)  
 00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)  
 00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)  
 00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)  
 00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)  
 00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)  
 00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)  
 00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]  
 00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)  
 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)  
 01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01
```
 
thank you for taking the time to help

---

### Post by jtarin on 2010-09-10
> install the right Nvidia driver for it. It doesn't show up in Hardware Drivers ??Nvidia drivers are for Nvidia hardware. You have an ATI card/chip according to your specs. With that in mind lookover this [thread ]("http://ubuntuforums.org/showthread.php?t=727371")and come back with questions.

---

### Post by cgroza on 2010-09-10
Install the Nvidia card and then check the Hardware Drivers. It should show up there. The Hardware Drivers show drivers for currently  installed hardware only.

---

### Post by 3Miro on 2010-09-10
Yes, jtarin is right. There doesn't appear to be any Nvidia hardware installed on your machine. Naturally Hardware Manager does not detect any and anything that you have installed will not work.

Is the Nvidia card plugged in and is you monitor plugged into it (from the info posted, the answer should be "no"). If the card is plugged into the computer, then there might be a hardware issue.

---

### Post by RemmyNumber7 on 2010-09-12
> **jtarin said:**
> Nvidia drivers are for Nvidia hardware. You have an ATI card/chip according to your specs. With that in mind lookover this [thread ]("http://ubuntuforums.org/showthread.php?t=727371")and come back with questions.
 
 
 
 
bottom line here I don't have no ati or nvidia drivers  in **Hardware Drivers**. I have no drivers in there at all

---

### Post by RemmyNumber7 on 2010-09-12
> **cgroza said:**
> Install the Nvidia card and then check the Hardware Drivers. It should show up there. The Hardware Drivers show drivers for currently installed hardware only.
 
 
 
I can't put in the nvidia card in the computer because the desktop dose not come up just on the ati card but it is in low graphics mode

---

### Post by RemmyNumber7 on 2010-09-12
I understand Nvidia cards are for nvidia drivers or nvidia hardware. And the same for Ati too. but the reason i have the ati in now is because everytime I put in the Nvidia card and restart the desktop dose not come up just a black screen. I mean not even the monitor reconised it either.

---

### Post by jtarin on 2010-09-12
You have to disable the oncard chip in your bios.

---

