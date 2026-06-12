---
title: "unknown monitor Acer Aspire 1360"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by shawn1968 on 2011-06-08
Hi everybody, 
I am a complete noob in Ubuntu, and I thought I' d give it a try with my old Acer Aspire 1360. I booted from the cd and when the desktop came up it was all distorted and out of rate. I tried to change the res to the 1024x768(the correct one for my monitor) and it doesn't work, nor any other resolution. I tried the detect monitor button but it keeps returning "monitor unknown"  Any suggestions????

Thank you in advance

---

### Post by wildmanne39 on 2011-06-08
> **shawn1968 said:**
> Hi everybody, 
I am a complete noob in Ubuntu, and I thought I' d give it a try with my old Acer Aspire 1360. I booted from the cd and when the desktop came up it was all distorted and out of rate. I tried to change the res to the 1024x768(the correct one for my monitor) and it doesn't work, nor any other resolution. I tried the detect monitor button but it keeps returning "monitor unknown"  Any suggestions????

Thank you in advance
Hi, you can manually set your monitor, I am going to give you to links, please be careful if you are not sure how to do what the instructions say better to leave them alone.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
Hi, I would try this first one first,please make a back up of the xconfig file before you change it so if you have to change it back you can.

---

### Post by shawn1968 on 2011-06-09
> **wildmanne39 said:**
> Hi, you can manually set your monitor, I am going to give you to links, please be careful if you are not sure how to do what the instructions say better to leave them alone.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
Hi, I would try this first one first,please make a back up of the xconfig file before you change it so if you have to change it back you can.
Thanks for the advise, but as far as I can tell these two suggestions are either to bypass the GUI Tool or to add another resolution if not present. 
The problem is that my resolution exists in the drop down, but even if you choose it the output is distorted and again out of rate. 
It probably has to do with missing drivers, but since I am new to this I do not know what to do.......:confused::confused::confused::confused::confused:

---

### Post by wildmanne39 on 2011-06-09
> **shawn1968 said:**
> Thanks for the advise, but as far as I can tell these two suggestions are either to bypass the GUI Tool or to add another resolution if not present. 
The problem is that my resolution exists in the drop down, but even if you choose it the output is distorted and again out of rate. 
It probably has to do with missing drivers, but since I am new to this I do not know what to do.......:confused::confused::confused::confused::confused:
Hi, have you checked in additional drivers to see if there is a driver for your video card? If there is not put this command in a terminal so we can see what hardware you have.
```
sudo lshw
``` post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by shawn1968 on 2011-06-09
> **wildmanne39 said:**
> Hi, have you checked in additional drivers to see if there is a driver for your video card? If there is not put this command in a terminal so we can see what hardware you have.
```
sudo lshw
``` post it back here by clicking on new reply and click # and paste the information between the brackets.
Txs, I will do and report back.

---

### Post by shawn1968 on 2011-06-09
#To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw
```
[CENTER]ubuntu                    
    description: Computer
    version: -1
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=6F073C00-562B-11D9-B3A7-ADBC1E9722D0
  *-core
       description: Motherboard
       product: Aspire 1360
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXA360532445202FB0M000
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V1.09
          date: 10/26/2004
          size: 111KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 2800+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket 754
          size: 800MHz
          capacity: 2500MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: S2
             size: 256MiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:e0000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:d1000000-d1ffffff memory:f0000000-f3ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: IPN 2220 802.11g
             vendor: InProComm Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64 maxlatency=32 mingnt=32
             resources: ioport:1c00(size=32) memory:d0006000-d000601f memory:d0005000-d00057ff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:40000000-40000fff ioport:2000(size=256) ioport:2400(size=256) memory:30000000-33ffffff memory:34000000-37ffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:18 memory:40001000-40001fff ioport:2800(size=256) ioport:2c00(size=256) memory:38000000-3bffffff memory:3c000000-3fffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
             vendor: Texas Instruments
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:d0005800-d0005fff memory:d0000000-d0003fff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c20(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c40(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c60(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:d0006400-d00064ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c80(size=16)
           *-disk
                description: ATA Disk
                product: HITACHI_DK23EB-4
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00K0
                serial: BC5815
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d39dd39d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 34a116fe-c851-d54f-bae9-a93def53970f
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-07-25 09:27:37 filesystem=ntfs state=clean
           *-cdrom
                description: DVD writer
                product: CD/DVDW TS-L532A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: TI50
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:1000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:1400(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0a:e4:a1:63:ea
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.108 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:1800(size=256) memory:d0006800-d00068ff
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0[/CENTER]
```
ubuntu@ubuntu:~$



sorry for the big post but i did what you said!!!!!

---

### Post by wildmanne39 on 2011-06-09
> **shawn1968 said:**
> #To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw
```
ubuntu                    
    description: Computer
    version: -1
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=6F073C00-562B-11D9-B3A7-ADBC1E9722D0
  *-core
       description: Motherboard
       product: Aspire 1360
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXA360532445202FB0M000
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V1.09
          date: 10/26/2004
          size: 111KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 2800+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket 754
          size: 800MHz
          capacity: 2500MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: S2
             size: 256MiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:e0000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:d1000000-d1ffffff memory:f0000000-f3ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: IPN 2220 802.11g
             vendor: InProComm Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64 maxlatency=32 mingnt=32
             resources: ioport:1c00(size=32) memory:d0006000-d000601f memory:d0005000-d00057ff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:40000000-40000fff ioport:2000(size=256) ioport:2400(size=256) memory:30000000-33ffffff memory:34000000-37ffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:18 memory:40001000-40001fff ioport:2800(size=256) ioport:2c00(size=256) memory:38000000-3bffffff memory:3c000000-3fffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
             vendor: Texas Instruments
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:d0005800-d0005fff memory:d0000000-d0003fff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c20(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c40(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c60(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:d0006400-d00064ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c80(size=16)
           *-disk
                description: ATA Disk
                product: HITACHI_DK23EB-4
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00K0
                serial: BC5815
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d39dd39d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 34a116fe-c851-d54f-bae9-a93def53970f
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-07-25 09:27:37 filesystem=ntfs state=clean
           *-cdrom
                description: DVD writer
                product: CD/DVDW TS-L532A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: TI50
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:1000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:1400(size=256)
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0a:e4:a1:63:ea
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.108 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:1800(size=256) memory:d0006800-d00068ff
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
ubuntu@ubuntu:~$
```



sorry for the big post but i did what you said!!!!!
Hi, I have spent a lot of time searching for an answer to your problem I have not found one, still the 2 ways to change resolution is by the 2 links I gave you in the previous post. You still not not say have you looked in the additional drivers to see if there is a driver for your video card? Also I had a resolution problem when I installed natty and I had to fix it in the xorg file. I think it is now under x11 then xconfig file.

---

### Post by shawn1968 on 2011-06-10
> **wildmanne39 said:**
> Hi, I have spent a lot of time searching for an answer to your problem I have not found one, still the 2 ways to change resolution is by the 2 links I gave you in the previous post. You still not not say have you looked in the additional drivers to see if there is a driver for your video card? Also I had a resolution problem when I installed natty and I had to fix it in the xorg file. I think it is now under x11 then xconfig file.

I did check in the additional drivers and there is nothing there.
Thank you for trying. I guess my Acer is not up to the task. If I was to install a previous version of Ubuntu, do you think that i will have a chance???????

---

### Post by wildmanne39 on 2011-06-10
> **shawn1968 said:**
> I did check in the additional drivers and there is nothing there.
Thank you for trying. I guess my Acer is not up to the task. If I was to install a previous version of Ubuntu, do you think that i will have a chance???????
Hi, when I was looking for the answer to your problem I think people had the same problem with previous versions of ubuntu as well, I do not remember for sure but I think it was with all versions.

---

