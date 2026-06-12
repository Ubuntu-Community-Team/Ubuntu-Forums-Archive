---
title: "Problem with Sitecom PCI wireless network card"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by rasmus02 on 2007-08-05
Hi,

I've only just installed Ubuntu 7.04 as a dual boot with XP on my desktop today, so I'm completely new to Linux. I've only got wireless internet access (or rather I could find a wire but it would be really messy).

I've been trying to get my network card to work, but unsuccessfully. The card is a Sitecom Wireless Network PCI Adapter 140Mbps WL-141 and works perfectly well, when I'm running XP. With Ubuntu, however, I cannot even find it.

I've looked at the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#") and searched through some posts here but I haven't been able to figure out what to do.

Using the lshw command gave:
```

$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1022MB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3700+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: NV44 [GeForce 6200 TurboCache(TM)]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=0
                resources: iomemory:fa000000-faffffff iomemory:d0000000-dfffffff iomemory:fb000000-fbffffff irq:5
        *-ide:0
             description: IDE interface
             product: ATI 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@00:12.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=sata_sil latency=64
             resources: ioport:fe00-fe07 ioport:fd00-fd03 ioport:fc00-fc07 ioport:fb00-fb03 ioport:fa00-fa0f iomemory:fe02f000-fe02f1ff irq:22
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: iomemory:fe02e000-fe02efff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb
                   description: Human interface device
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: iomemory:fe02d000-fe02dfff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 4
                   bus info: usb@2:4
                   version: 1.00
                   serial: 2004888
                   capabilities: usb-1.10 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: iomemory:fe02c000-fe02cfff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: ioport:400-40f iomemory:fe02b000-fe02b3ff
        *-ide:1
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:f800-f80f irq:16
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: LITE-ON DVDRW SOHW-1633S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0 UNCLAIMED
                description: Network controller
                product: ISL3886 [Prism Javelin/Prism Xbow]
                vendor: Intersil Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=28 mingnt=10
                resources: iomemory:fdefa000-fdefbfff irq:10
           *-multimedia
                description: Multimedia controller
                product: SAA7134/SAA7135HL Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 1
                bus info: pci@02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255
                resources: iomemory:fdeff000-fdeff3ff irq:21
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:21:63:03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:df00-dfff iomemory:fdefe000-fdefe0ff irq:20
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: iomemory:fdefd000-fdefd7ff ioport:de00-de7f irq:21
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: iomemory:fe02a000-fe02a0ff irq:17
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage



```

And typing "sudo pccardctl ident" gave nothing at all - I did type in the correct password.

Can you help me, please?

---

### Post by rasmus02 on 2007-08-06
BUMP - Please, I would be so disappointed, if I've got to dump linux just because I can't find a proper driver. Could someone maybe just tell me where to look?


Thanks in advance :)

---

### Post by rasmus02 on 2007-08-31
Help, please? Even just someone telling me how stupid I am would be preferable to this silence.

---

