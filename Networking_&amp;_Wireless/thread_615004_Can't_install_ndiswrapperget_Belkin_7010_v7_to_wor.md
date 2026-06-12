---
title: "Can't install ndiswrapper/get Belkin 7010 v7 to work."
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by MartyrMachine on 2007-11-16
Hey, totally new to Linux here. I've been doing tons of homework on this stuff, but I just cannot get my Belkin 7010 v7 to work. I've downloaded and attempted to extract ndiswrapper,using the tar -zxvf ndiswrapper-version.tar.gz  command, and it will not extract/install. So, I extracted it manually, and did the make uninstall, then make, and it gave me an Error1 and Error2, whatever that means. I've downloaded the Realtek net8185 driver.  Here's the results of lshw, iwconfig, and pccardctl ident.



lshw;

ubuntu                    
    description: Computer
    product: Inspiron 2650
    vendor: Dell Computer Corporation
    version: Revision A0
    serial: FJYJL11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific uuid=44454C4C-4A00-1259-854A-46C04F4C3131
  *-core
       description: Motherboard
       product: Inspiron 2650
       vendor: Dell Computer Corporation
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: PHOENIX TECHNOLOGIES LTD.
          physical id: 4
          version: A02 (04/19/2002)
          size: 100KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect pcmciaboot edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz
          vendor: Intel Corp.
          physical id: 8
          bus info: cpu@0
          version: 15.2.4
          slot: U49
          size: 1200MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 8KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 256MB
          capacity: 512MB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: J6A
             size: 128MB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: J7A
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: ec000000
          bus info: pci@00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: iomemory:e0000000-e0ffffff iomemory:f0000000-f7ffffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1800-181f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:5
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 78
                serial: 00:06:5b:ba:22:9f
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
                resources: ioport:3000-307f iomemory:e8000000-e800007f irq:10
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:e8001000-e8001fff irq:10
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1840-184f iomemory:26000000-260003ff irq:11
           *-disk
                description: SCSI Disk
                product: FUJITSU MHS2020A
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8307
                serial: NL12T3315B5U
                size: 18GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 18GB
                   capabilities: primary bootable
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM SN-124
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: N102
                capabilities: removable audio
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1860-187f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:1880-18bf irq:10
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:2400-24ff ioport:2000-207f irq:10
     *-network UNCLAIMED
          description: Ethernet controller
          product: Belkin
          vendor: Belkin
          physical id: 0
          bus info: pci@03:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=64 mingnt=32
          resources: iomemory:28000000-280003ff irq:10
_________________________________________________
iwconfig;


martyr@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
_________________________________________________
pccardctl ident;

martyr@ubuntu:~$ pccardctl ident
Socket 0:
  no product info available
__________________________________________________




Hopefully this information will help. I'm having to switch to Windows every time I get online, so it's hard. Thanks in advance.

---

### Post by drunkardivan on 2007-11-16
I'm having the same issue, with the exact same card.

---

### Post by MartyrMachine on 2007-11-16
Any suggestions, help, anything? I really don't want to give up on linux (specifically Ubuntu) for the 5th time in 4 years.](*,)

---

### Post by woopud on 2007-11-16
Hi,i'm using the Belkin F5D7010 v7 PCMIA on my laptop without problems.  Can you connect at all with a Ethernet cable ?  If so, just use Synaptic to download and install Ndiswrapper and I can help you set up your wireless.

Bert

---

### Post by MartyrMachine on 2007-11-17
Yes, I can connect via ethernet. I would appreciate any help I can get!

---

### Post by woopud on 2007-11-18
Okay, when you're connected to the internet via ethernet cable open up Synaptic and install ndiswrapper-common and ndiswrapper-utils.  If you got that I can email you the right drivers. (rtl8185).

Bert

---

### Post by darck1 on 2008-03-04
> **woopud said:**
> Okay, when you're connected to the internet via ethernet cable open up Synaptic and install ndiswrapper-common and ndiswrapper-utils.  If you got that I can email you the right drivers. (rtl8185).

Bert

Has anybody had any luck getting the rtl8185 drivers to work in 64bit Ubuntu? I'm using Gutsy Gibbon AMD64. I got the latest ndiswrapper (1.9? Can't remember right now and I don't have my laptop with me) and used the standard 8185 drivers for WinXP. They didn't work because they were 32bit and my installation is 64bit. I tried using the 64 bit drivers and that didn't work at all. 

The driver version is "1097" downloaded from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L")

I'll be more than willing to post more information when I have it (ie. I don't have my laptop with me right now).

The card I have is F5D7010 v7 . I thiink the id was 701F but I couldn't swear to that.

---

