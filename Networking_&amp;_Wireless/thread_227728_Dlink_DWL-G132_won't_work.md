---
title: "Dlink DWL-G132 won't work"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Jhodytropical on 2006-08-02
Hi all,
 I have a Dlink USB wireless that doesn't seem to work. I installed NDISWRAPPER through Synaptics and downloaded the 'Windows Driver' to my user directory and followed most of the steps specified on the previous forums to install it properly. But as soon as I type modprobe ndiswrapper the led on the Adapter would come on and freezes my system.Any ideas why?

Here are some info that my help:

------------------>>>>>>>-------------------->>>>>>>>>>

jhody@DeGuerre:~$ ndiswrapper -l
Installed ndis drivers:
athfmwdl                driver present, hardware present
neta5agu                driver present, hardware present

jhody@DeGuerre:~$ sudo lshw
deguerre
    description: Notebook
    product: Pavilion ze8500 (DP879E)
    vendor: Hewlett-Packard
    version: KH.F.15
    serial: CNF3480521
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00BB3071-751C-D811-86A0-000D9DCCC467
  *-core
       description: Motherboard
       product: 0850
       vendor: Hewlett-Packard
       physical id: 0
       version: NS570 Version PQ1B59
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: KF_KH.F.15 (10/16/2003)
          size: 108KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom pcmciaboot edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: WMT478/NWD
          size: 1596MHz
          capacity: 2667MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 8KB
             capacity: 1MB
             capabilities: burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 512KB
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J400
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: J401
     *-pci
          description: Host bridge
          product: RS200/RS200M AGP Bridge [IGP 340M]
          vendor: ATI Technologies Inc
          physical id: d4000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          resources: iomemory:d4000000-d7ffffff iomemory:d0009000-d0009fff
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon IGP 330M/340M/350M
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d8000000-dfffffff ioport:9000-90ff iomemory:d0300000-d030ffff irq:10
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451
             resources: ioport:1000-10ff iomemory:d0000000-d0000fff irq:5
        *-isa UNCLAIMED
             description: ISA bridge
             product: M1533 PCI to ISA Bridge [Aladdin IV]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-communication
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: driver=serial
             resources: iomemory:d0001000-d0001fff ioport:1400-14ff irq:10
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:d0002000-d0002fff irq:11
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@00:0b.0
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:2000-201f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b.1
             bus info: pci@00:0b.1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:2020-203f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-686 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: b.2
             bus info: pci@00:0b.2
             version: 51
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d0003000-d00030ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-686 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: USB WLAN Device
                   vendor: Atheros Communications Inc
                   physical id: 2
                   bus info: usb@3:2
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:d0003800-d0003fff iomemory:d0004000-d0007fff irq:10
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE
             resources: ioport:2040-204f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK4021GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: GA224C
                   serial: Y3F30698S
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 27GB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: SONY DVD+RW DW-P50A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.8e
                   serial: EA4FF385
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus
        *-network
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 00
             serial: 00:0d:9d:cc:c4:67
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=full ip=192.168.0.18 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: ioport:2400-24ff iomemory:d0008000-d0008fff irq:10
jhody@DeGuerre:~$

--------------------->>>>
Thanks in advance for your help

---

### Post by whiteguysamurai on 2006-08-02
I have the ag530 pci and it won't even allow my system to boot.

I don't know who to yell at, d-link or someone else.

---

### Post by Jhodytropical on 2006-08-19
any hint for usb wireless adapter ? anyone ?

---

### Post by Jhodytropical on 2006-08-19
Hi all

 I finally got the Dlink Dwl-G132 to work. please follow these steps (From this link : [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) )if you have a similar USB adapter. I hope this helps :

 How to install Windows Wireless Drivers (Ndiswrapper)

    * Read #General Notes
    * In order to install ndiswrapper you need a copy the windows drivers for your Wireless ethernet device.
    * This is only ment to be installed if your card isn't supported.
    * Please visit Official supported cards list 

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l

    * Unload ACX module and load ndiswrapper 

lsmod | grep acx
sudo rmmod acx (only if the module was found. It could also be acx_pci or similar)
modprobe ndiswrapper

    * Set ndiswrapper to load on startup 

sudo ndiswrapper -m
sudo gedit /etc/modules

    * Add the following module to the list 

ndiswrapper

    * Now you can configure your wireless card with ifconfig and iwconfig. 

    e.g. Supposing wlan0 is your wireless device. 

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig

    * You sould now be able to see the MAC address of the access point and signal rate.

---

