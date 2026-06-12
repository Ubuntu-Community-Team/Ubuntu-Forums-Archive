---
title: "lan card"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by hi100 on 2007-10-25
Hi i have buyed  a second hand laptop.I have installed xubuntu in it and it can not detect the lan card .

can someone pls help me.I want to use cable internet

---

### Post by Lambert on 2007-10-25
Are you talking an ethernet connection?

run this command and post output.

```

sudo lshw -C network

```

---

### Post by hi100 on 2007-10-28
Hi,

Thanks for your reply.when i use this command no output comes out.

---

### Post by Lambert on 2007-10-28
try just

```


sudo lshw

```

this will show all your hardware. You will just have to look for the section that looks to relate to your network device. If you need help, post the entire output and someone will help you.

---

### Post by hi100 on 2007-10-28
Hi thanks for your reply. it gives this output

 capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial pc98 acpi agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: *Socket 370*
          size: 700MHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 503MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: CN04
             size: 256MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: CN04
     *-pci
          description: Host bridge
          product: M1621
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-ali module=ali_agp
        *-pci
             description: PCI bridge
             product: PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: CyberBlade/i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 5d
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm vga bus_master cap_list
                configuration: latency=64
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64 maxlatency=24 mingnt=2
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: c3
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=32 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHM2060AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 4723
                   serial: 01073846
                   size: 5729MB
                   capacity: 5729MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 5428MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 298MB
                      capacity: 298MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 298MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: QSI DVD-ROM SDR-081
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: EHA8
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
  *-battery
       physical id: 1
       slot: Right Front

---

### Post by kevdog on 2007-10-28
Unless it shows up when you do

lshw -C network

The card might be dead--RIP

---

### Post by hi100 on 2007-10-28
Hi,

I have buyed a new  belkin wireless usb but unable to install it.it is belkin f5d7050 version 3001uk but i am unable to install it.now i am thinking to buy a new ethernet lan card.

Can u suggest me the ethernet card which is compatabile with ubuntu and my laptop .

---

