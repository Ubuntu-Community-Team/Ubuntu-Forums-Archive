---
title: "Compaq Presario 14XL242 - network card"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by existPierre on 2008-10-01
Hi,

I have a problem with my Compaq Presario 14XL242. The Network card has not been detected. I dont know name of this network card. Card is integrated, switched on in BIOS. In windows, after plugin of cabel into laptop, network is detected. I have fluxbuntu on this mashine. 

Sry for my english, is very bad :oops:

pls help [-o<](*,)


thanks

---

### Post by existPierre on 2008-10-13
pls help, this is very urgent and important :sad:

---

### Post by Ayuthia on 2008-10-13
Can you post the results of lspci -nn from the Terminal?

---

### Post by existPierre on 2008-10-13
[IMG]http://www.pixtube.eu/viewer.php?file=9zghucz81tlu126y3h91.jpg[/IMG]

[http://www.pixtube.eu/viewer.php?file=9zghucz81tlu126y3h91.jpg](http://www.pixtube.eu/viewer.php?file=9zghucz81tlu126y3h91.jpg)

---

### Post by existPierre on 2008-10-15
I know name: 
Conexant Combo - Modem/NIC with both an Ethernet 10/100 network connection and a 56K V.90 modem connection.

but i cant find driver for this card

---

### Post by existPierre on 2008-10-24
lshw:

```
ubuntu
    description: Notebook
    product: Compaq PC
    vendor: Compaq
    version: 0F07
    serial: 1V09FHP764H8
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=notebook uuid=80E09FF1-1D63-0010-9C89-C1CAB7C792DE
  *-core
       description: Motherboard
       product: 065Ch
       vendor: Compaq
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 4.06 (08/01/2000)
          size: 97KB
          capacity: 192KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: Socket 370
          size: 600MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 32KB
             capacity: 1MB
             capabilities: burst internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 128KB
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 64MB
          capacity: 384MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 64MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: VT8601 [Apollo ProMedia]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT8601 [Apollo ProMedia AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: CyberBlade i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 6a
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm vga bus_master cap_list
                configuration: latency=64
        *-isa:0
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 1b
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=64 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK6015MAP
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: U8.13 A
                   serial: 80L85392T
                   size: 5729MB
                   capacity: 5729MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 5433MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 295MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-C2402
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1007
                   serial: 8000107617
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-isa:1
             description: ISA bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: isa
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
```


lsusb:
```

Bus 001 Device 001: ID 0000:0000  
```

lspcmcia:

```
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
```

---

