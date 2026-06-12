---
title: "Upgrade RAM"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Jetfirehack on 2009-08-06
I want to upgrade my memory, and I think I need some help with that. I don't know how to pick out memory that'd be compatible for my system.

How would I go about looking for memory? I went on Crucial.Com but they don't have any memory upgrades for Seanix computers, so I was wondering about this.

I think it has something to do with set of characters, however:
GA-8S661FXM-775

```
*****@*****-desktop:~$ sudo lshw
******-desktop               
    description: Desktop Computer
    product: PROD00000000
    vendor: Seanix Technology Inc
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: GA-8S661FXM-775
       vendor: Seanix Technology Inc
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2c (10/19/2004)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 775
          size: 2933MHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 775
          size: 2933MHz
          capacity: 4GHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
           *-disk
                description: ATA Disk
                product: WDC WD800BB-00JH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM92350469
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4d4c4d4b
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2434abe3-29f9-47b7-a9be-69b8c2ae10ae
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2008-10-18 04:40:34 filesystem=ext3 modified=2009-08-06 18:18:08 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-06 18:18:08 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1380MiB
                   capacity: 1380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1380MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVDRW DDW-081
                vendor: NU
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BX32
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:0f:ea:55:cf:76
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.146 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:0e:a9:1e:c6:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by philcamlin on 2009-08-06
type this in :)

```
sudo dmidecode --type memory
```

---

### Post by powel212 on 2009-08-06
>      *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits


What I am seeing is you have a 2 slot Gigabyte motherboard that can expand to a maximum of 2 gigs RAM of DIMM 400.

You appear to have one 512M 400 DIMM in there now. If you go to the store and ask for DIMM 400 and buy 2 one Gig sticks you can just take the old one out and put it on a shelf and plug the 2 new ones in.

Your motherboard
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1842](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1842)

The RAm
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1170139&CatId=1043](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1170139&CatId=1043)

It is pretty easy to install just make sure your computer is off and unplugged. You can only put the RAM in one way and if you take note of how it is oriented when you take the one stick you have out it should be quite clear how the new ones go in.

I hope that helps

Powel

---

### Post by Jetfirehack on 2009-08-06
> **philcamlin said:**
> type this in :)

```
sudo dmidecode --type memory
```

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0006, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 2048 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0007
		0x0008
	Enabled Error Correcting Capabilities:
		None

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1 2
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 3 4
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 2 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz (2.5 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  


```

I'm pretty sure I just need memory compatible with:
GA-8S661FXM-775

---

### Post by starcraft.man on 2009-08-06
This is your montherboard: [GA-8S661FXM-775]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1842")

It's an old one, but I assume still functioning well.

This is what your board supports:
> Supports DDR 400/333/266 up to 2GB Memory
Available with 2 DIMM slots supporting up to 2GB of DDR400/DDR333/DDR266 memory, GA-8S661FXM-775 (Rev 1.x) provides the highest performance platform with the highest bandwidth (3.2GB/s) mainstream DDR memory solution.

You have two available slots and only 1 filled with 512MB stick of DDR 400. The best you can upgrade to with this board would be two sticks of DDR 400 1GB. When buying RAM they must say **PC-3200**. 

See example below. It's only one stick, you'd have to put two orders in. You can buy these locally btw, I'm sure they are on sale.

You may want to look into a whole PC upgrade at same time, while a RAM upgrade is very good for a machine like that it won't turn it into a Core 2 pc. That's a value decision you make though, I just give opinion. Nothing wrong with p4 I suppose, I had mine for over 7 years.

Edit: Sigh, too slow. >.>

---

### Post by Jetfirehack on 2009-08-06
Ok thanks, I think I know what to do now.

---

### Post by philcamlin on 2009-08-06
you have 512M 400 DIMM in you pc already so you want to go to the store and go get the same model type :)

---

### Post by Jetfirehack on 2009-08-06
> **starcraft.man said:**
> This is your montherboard: [GA-8S661FXM-775]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1842")

It's an old one, but I assume still functioning well.

This is what your board supports:


You have two available slots and only 1 filled with 512MB stick of DDR 400. The best you can upgrade to with this board would be two sticks of DDR 400 1GB. When buying RAM they must say **PC2-3200**. 
[URL="http://www.ncixus.com/products/15877/KVR400D2N3%2F1G/Kingston/"]
This is an example what to buy.[/URL] It's only one stick, you'd have to put two orders in. You can buy these locally btw, I'm sure they are on sale.

You may want to look into a whole PC upgrade at same time, while a RAM upgrade is very good for a machine like that it won't turn it into a Core 2 pc. That's a value decision you make though, I just give opinion. Nothing wrong with p4 I suppose, I had mine for over 7 years.

Edit: Sigh, too slow. >.>
Link you gave me says DDR2, and below it says it's not compatible w/ DDR1 boards, would that be an issue for me?

---

### Post by philcamlin on 2009-08-06
> **Jetfirehack said:**
> Link you gave me says DDR2, and below it says it's not compatible w/ DDR1 boards, would that be an issue for me?

just to be sure i would take one of the ram slots out of my pc and compare to the ones your buying in the store if it looks the same its good

---

### Post by starcraft.man on 2009-08-06
> **Jetfirehack said:**
> Link you gave me says DDR2, and below it says it's not compatible w/ DDR1 boards, would that be an issue for me?

Your right, my bad. **PC-3200**. Apologies, I was typing too fast.

[Link.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820208133&Tpk=PC%203200") That is the correct RAM you should be looking for. Look around and compare. It should always say PC-3200 though, that is designation for first gen DDR 400. As long as you verify the model is the same as I write here, it doesn't matter who makes it will work in board.

More options:
[NCIX]("http://www.ncixus.com/products/1297/412/DDR%20Desktop%20Memory/1GB/")
[Tiger Direct]("http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=1600&name=1024MB-PC3200-Memory&Nav=|c:1043|&Sort=0&Recs=10")

---

### Post by Jetfirehack on 2009-08-06
> **philcamlin said:**
> just to be sure i would take one of the ram slots out of my pc and compare to the ones your buying in the store if it looks the same its good
lol.

---

