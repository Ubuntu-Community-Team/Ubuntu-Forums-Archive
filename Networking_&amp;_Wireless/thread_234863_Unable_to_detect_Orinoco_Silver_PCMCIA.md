---
title: "Unable to detect Orinoco Silver PCMCIA"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by candyoff on 2006-08-12
Dear all

I am a totally newbabe in linux. 
Its my first time using linux (and yes, I chosen Ubuntu :)
I have spent few hours finding solution for my problem but seem i am able to solve it probably due to my limited experiences. 
I have installed Ubuntu in my windows xp using VMware. 
The wired lan worked straight away. 
Click on Admin, Networking, but cant find "wireless" there. 
I have tried to follow the guide in 
WifiDocs/WirelessTroubleShootingGuide
But not sure how it really work...

My specs:
Lucent Orinoco Silver PCMCIA
Ubnutu 6.06

below are some Details

lshw

  description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 256MB
     *-cpu
          product: Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: ec000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1050-105f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: VMware Virtual IDE Hard Drive
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 100GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: VMware Virtual IDE CDROM Drive
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 697MB
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1060-107f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9
        *-display
             description: VGA compatible controller
             product: [VMware SVGA II] PCI Display Adapter
             vendor: VMware Inc
             physical id: f
             bus info: pci@00:0f.0
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: ioport:1440-144f iomemory:f0000000-f7ffffff iomemory:e8000000-e87fffff
        *-network
             description: Ethernet interface
             product: 79c970 [PCnet32 LANCE]
             vendor: Advanced Micro Devices [AMD]
             physical id: 10
             bus info: pci@00:10.0
             logical name: eth0
             version: 10
             serial: 00:0c:29:af:f6:a1
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical logical
             configuration: broadcast=yes driver=pcnet32 ip=192.168.79.128 multicast=yes
             resources: ioport:1080-10ff irq:185
        *-multimedia
             description: Multimedia audio controller
             product: ES1371 [AudioPCI-97]
             vendor: Ensoniq
             physical id: 11
             bus info: pci@00:11.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ENS1371
             resources: ioport:1400-143f irq:177

sudo cardctl ident

no pcmcia driver in /proc/devices

lcpci

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
0000:00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
0000:00:10.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
0000:00:11.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Once again, I am totally new in linux and the commands are totally stranger to me. 
Hope someone can give me a details guide. 
I wont able to understand how to copy/backup a files (unless u give me the step by step command guide)

Once again, Thanks!

References link:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://prdownloads.sourceforge.net/orinoco](http://prdownloads.sourceforge.net/orinoco)
[http://www.nongnu.org/orinoco/documentation/index.html](http://www.nongnu.org/orinoco/documentation/index.html)

---

### Post by candyoff on 2006-08-16
I install Ubuntu in VMware. 
VMmare doesnt detect PCMCIA
I dual boot with Windows Xp. 
Problem Solved

Thanks all

Regards

---

