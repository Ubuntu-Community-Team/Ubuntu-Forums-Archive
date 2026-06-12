---
title: "I see HD in Windows but not in Ubuntu"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by emiliano67 on 2009-09-03
Hi everyone,
I have two HD on my computer. On the main one I have Ubuntu and Windows XP. The second one is half formatted as FAT32 and half empty space. I can see the second HD when I'm running Windows but I cannot when I run Ubuntu.

I tried *df* and it sees everything (the Windows partition, cdrom, floppy and Ubuntu partition) but not the other HD. Same with *cat /etc/mtab*, also *fdisk -l* sees everything except the second HD. 

Doing *cat /etc/fstab* sees all Ubuntu but not the Windows partition.

How do I find the second HD that I would like to use as storage? Once found, I know how to mount it, I think.
Thanks

---

### Post by kansasnoob on 2009-09-03
> **emiliano67 said:**
> Hi everyone,
I have two HD on my computer. On the main one I have Ubuntu and Windows XP. The second one is half formatted as FAT32 and half empty space. I can see the second HD when I'm running Windows but I cannot when I run Ubuntu.

I tried *df* and it sees everything (the Windows partition, cdrom, floppy and Ubuntu partition) but not the other HD. Same with *cat /etc/mtab*, also *fdisk -l* sees everything except the second HD. 

Doing *cat /etc/fstab* sees all Ubuntu but not the Windows partition.

How do I find the second HD that I would like to use as storage? Once found, I know how to mount it, I think.
Thanks

I'm about to conk out but post the output of these commands:

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
sudo blkid -c /dev/null
```

Also, apologies if you already said, but what version of Ubuntu is this? If you're unsure:

```
cat /etc/issue
```

Finally, I have doubts this will work, but you could try installing pmount:

```
sudo apt-get install pmount
```

---

### Post by kansasnoob on 2009-09-03
Oh poo! Forgot something:

```
sudo apt-get install ntfsprogs
```

Then reboot. Also be careful, ntfsprogs will allow you to modify files in Win that will destroy it (or fix it)!

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by emiliano67 on 2009-09-03
Fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b169b16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30401   192996877+   f  W95 Ext'd (LBA)
/dev/sda5            6375       18243    95337711    7  HPFS/NTFS
/dev/sda6           18244       29915    93755308+  83  Linux
/dev/sda7           29916       30401     3903763+  82  Linux swap / Solaris

```Fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=004c7fbf-67ea-4831-b23b-9fed61602903 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=41d88ae3-d08b-4851-89bf-58b1acb8ba90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```Blkid:
```
/dev/sda1: UUID="042C815B2C81491E" TYPE="ntfs" 
/dev/sda5: UUID="D40C4E3E0C4E1C3C" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="004c7fbf-67ea-4831-b23b-9fed61602903" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="41d88ae3-d08b-4851-89bf-58b1acb8ba90" 
```The version of Ubuntu is Ubuntu 8.04.3 LTS

---

### Post by emiliano67 on 2009-09-03
As far as ntfsprogs is concerned, I have no problem accessing the Windows part of the main HD, which is formatted NTFS. The second HD is actually FAT32 and empty space.

---

### Post by emiliano67 on 2009-09-03
I have tried reformatting it all Primary FAT32, no empty space. Still cannot find it on Ubuntu, on Windows no problem.

---

### Post by LewRockwell on 2009-09-03
your hard drive jumpers may be set incorrectly

windows may be fine with the "cable select" positioning of the drive jumpers...

but we have had much better success by placing the jumpers in their proper "master" and/or "slave" positions

as always, your mileage may vary

.

---

### Post by emiliano67 on 2009-09-03
That's what I think too, Some kind of problem with cables and jumpers. I will try to find out more online. Thanks anyway.

---

### Post by emiliano67 on 2009-09-04
Ok, this is what I was able to figure out:

[LIST=1]
[*]the main HDD (with Windows XP and Ubuntu installed) is a Seagate ST3250310AS Barracuda 7200.10 (250 GB), it's a SATA hard drive
[*]the one I would like to use as storage is a Seagate ST 320410A (20 GB), it' a ATA hard drive
[*]SATA doesn't need master/slave
[*]ATA does
[*]if I take the jumper off to make the ATA drive slave, it's not found in BIOS, and consequently cannot be found both in Windows and in Ubuntu
[*]so, the ATA drive has the jumpers set as master
[*]BIOS sees it. These are all the data from the BIOS that I think could be useful:
[LIST=1]
[*]IDE Primary Master [ST320410A] - the storage hdd (ATA)
[*]IDE Primary Slave [CD ROM] - atapi cd rom
[*]SATA 1 empty
[*]SATA 2 empty
[*]SATA 3 empty
[*]SATA 4 - [ST3250310AS]
[*]1st Booth Device [ST3250310AS] - Barracuda (correct) (SATA)
[*]2nd Booth Device [CD]
[*]3d Booth Device [Floppy]
[*]4th Booth Device [ST320410A] - the storage hdd
[*]On-Chip IDE Controller [Enabled]
[*]PCI IDE BusMaster [Disabled]
[*]On-Chip SATA Controller [Enabled]
[*]RAID Mode [IDE]
[*]COM Port 1 [3F8/IRQ4]
[*]COM Port 2 [2F8/IRQ3]
[*]Parallel Port [378]
[*]Parallel Port Mode [Bi-Directional]
[/LIST]
 
[/LIST]
That's it. There should be a way to set up a Sata and an ATA hard drive so that they work BOTH in Windows and in Linux (Ubuntu). With the settings as above, the storage ATA drive (ST320410A) shows up in Windows but NOT in Ubuntu.
Hope someone can help, since I think it's an interesting problem.
Thanks

---

### Post by emiliano67 on 2009-09-04
Some more data:

**RESULT OF lshw -C disk -C storage with the ATA hd disconnected**:

*-ide:0
description: IDE interface
product: 82801G (ICH7 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
logical name: scsi0
version: 01
width: 32 bits
clock: 33MHz
capabilities: ide bus_master emulated
configuration: driver=ata_piix latency=0 module=ata_piix

[INDENT]     *-cdrom
    description: DVD-RAM writer
    product: DVD-RAM GSA-H55N
    vendor: HL-DT-ST
    physical id: 0.1.0
    bus info: scsi@0:0.1.0
    logical name: /dev/cdrom
    logical name: /dev/dvd
    logical name: /dev/scd0
    logical name: /dev/sr0
    version: 1.05
    serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
    capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
    configuration: ansiversion=5 status=open
[/INDENT] 
*-ide:1
description: IDE interface
product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi3
version: 01
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=ata_piix latency=0 module=ata_piix

[INDENT]     *-disk
    description: ATA Disk
    product: ST3250310AS
    vendor: Seagate
    physical id: 0.1.0
    bus info: scsi@3:0.1.0
    logical name: /dev/sda
    version: 4.AA
    serial: 6RYMK6KF
    size: 232GiB (250GB)
    capabilities: partitioned partitioned:dos
    configuration: ansiversion=5 signature=9b169b16
[/INDENT] 
**RESULT OF lshw -C disk -C storage with the ATA hd connected**:

*-ide:0
description: IDE interface
product: 82801G (ICH7 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
version: 01
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=ata_piix latency=0 module=ata_piix

*-ide:1
description: IDE interface
product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi3
version: 01
width: 32 bits
clock: 66MHz
capabilities: ide pm bus_master cap_list emulated
configuration: driver=ata_piix latency=0 module=ata_piix

[INDENT]     *-disk
    description: ATA Disk
    product: ST3250310AS
    vendor: Seagate
    physical id: 0.1.0
    bus info: scsi@3:0.1.0
    logical name: /dev/sda
    version: 4.AA
    serial: 6RYMK6KF
    size: 232GiB (250GB)
    capabilities: partitioned partitioned:dos
    configuration: ansiversion=5 signature=9b169b16
[/INDENT] 
With the ATA drive connected (mid of the ribbon cable that goes from the CD ROM to the mainboard, the grey one) the CD ROM doesn't show and I just realized that it also doesn't work.

---

### Post by LewRockwell on 2009-09-04
what does your motherboard manual say about mixing ATA and SATA?

if you don't have a manual you might be able to find documentation somewhere online

some motherboards have connections for more than one type/style of component but it wasn't intended for those different types to be mixed(say, for example, slots for DDR and DDR2 ram...you can use one or the other but not both)

keep us posted on what you find out!

.

---

### Post by emiliano67 on 2009-09-04
[FONT=arial, helvetica][SIZE=2]MicroStar G31M3-F Socket 775 mATX Motherboard [/SIZE][/FONT][FONT=arial, helvetica][SIZE=2]MS-7528 Ver. 1.0[/SIZE][/FONT][FONT=arial, helvetica][SIZE=2], Intel G31 Chipset, Supports Intel Core2 Quad CPUs, Dual DDR2 800 Memory, SATA II hard drive, PCI-E, with Gb LAN, 8 Ch Audio. 
P/N: MS-7528-010.

**Features**:[/SIZE][/FONT]

[LIST][FONT=arial, helvetica][SIZE=2]
[*]9.6 in (L) x 8.6 in (W) Micro-ATX
[*]2 DIMMs w/ DDR2 800 upto 4GB
[*]1 PCI-E 16X; 2 PCI-E X1; 2 PCI; 6 USB
[*]Realtek ALC888 Flexible 7.1-channel audio
[*]GbLAN; SATA; ATA133
[*]Live Update; Dual Corecell; MSI Dual CoreCenter; DOT[/SIZE][/FONT]
[/LIST]
 
 [FONT=arial, helvetica][SIZE=2]**Specifications**:[/SIZE][/FONT]

[LIST][FONT=arial, helvetica][SIZE=2]
[*]**CPU**: Intel Core 2 Quad, Core 2 Duo, Pentium and Celeron in the LGA775 package
[*]**Chipset**:   
Intel G31 Chipset:  
- Supports FSB 800/1066/1333 
- Support Dual channel DDR2 667/800 
Intel ICH7 Chipset:  
- Hi-Speed USB (USB2.0) controller, 480Mb/sec, up to 8 ports 
- 4 SATA ports with transfer rate up to 3 Gb/s 
- PCI Master v2.3, I/O APIC 
- ACPI 2.0 compliant
[*]**Main Memory**:  
- Supports 2 unbuffered DIMM of 1.8 Volt DDR2 SDRAM 
- Supports up to 4GB memory size 
- Support Dual Channel DDR2 memory architecture 
- Supports DDR2 667/800 memory interface
[*]**Slots**:   
- 1 x PCI Express X16 slot (PCI Express Bus SPEC V1.0a compliant) 
- 1 x PCI Express X1 slot (PCI Express Bus SPEC V1.0a compliant) 
- 2 x PCI slots (support 3.3V/ 5V PCI bus interface)
[*]**On-Board IDE**:    
One Ultra DMA 66/100 IDE controller integrated in ICH7. 
- Supports PIO, Bus Master operation modes 
- Can connect up to 2 Ultra ATA drives 
SATA controller integrated in ICH7 
- Up to 3Gb/s transfer speed 
- Supports four SATA ports
[*]**Audio**: Chip integrated by Realtek ALC888  
- Flexible 7.1-channel audio with jack sensing 
- Compliant with Azalia 1.0 spec 
- Meet Microsoft Vista Premium SPEC
[*]**LAN**:  Supports PCIE LAN 10/100/1000 Fast Ethernet by 8111C
[*]**On-Board Peripherals**:              
- 2 x USB 2.0 connector support additional 4 ports 
- 1 x Floppy disk drive connector 
- 4 x Serial ATA II connectors 
- 1 x ATA100 IDE connector 
- Clear CMOS jumper 
- 1 x Serial port connector 
- 1 x SPDIF-out header 
- 1 x TPM module header 
- 1 x PS/2 keyboard 
- 1 x PS/2 mouse 
- 1 x Parallel port 
- 1 x Serial port 
- 4 x USB 2.0 ports 
- 1 x RJ45 LAN jack 
- 1 x Graphic Card port
[*]**BIOS**:  
- The mainboard BIOS provides "Plug & Play" BIOS which detects the peripheral devices and expansion cards of the board automatically. 
- The mainboard provides a Desktop Management Interface(DMI) function which records your mainboard specifications.
[*]**Dimensions**: 9.6 in.(L) x 8.6in.(W) micro-ATX Form Factor
[*]**Mounting**: 6 mounting holes[/SIZE][/FONT]
[/LIST]
Couldn't find anything specific on mixing ATA and SATA drives online and I don't have a manual.

---

### Post by emiliano67 on 2009-09-04
It works on Windows, though. Doesn't that mean it's able to mix ATA/SATA drives?

---

