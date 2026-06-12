---
title: "How do I know what is sda, sdb, sdc ?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-08-14
Hi
I would like to know what device (disk, usb etc...) is at sda, sdb, etc...
What command can I use to know that ?

Thanks

---

### Post by zerhacke on 2009-08-14
You could use 

```
sudo fdisk /dev/sda
```

And so on for each disk.  It will tell you how big each disk is.  If your discs are not the exact same size, you'll know which is which.

---

### Post by Pierrot Lafouine on 2009-08-14
Hi
I tried what the command sudo fdisk, this is the output.

xx@yyy:/dev$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 3882.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 


It doesn't tell if its a USB or hdd etc...  I also tried list, and print, no mention of what is the hardware attached to sdb.  How can I know that ?

---

### Post by unutbu on 2009-08-14
Press 'q' to quit fdisk.
Then try

```
sudo fdisk -l
```

(Since some fonts make this hard to tell, note that "-l" is a dash followed by a lowercase L.)

---

### Post by Pierrot Lafouine on 2009-08-14
The output :
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6        1520   da  Non-FS data
/dev/sdb2               7          10        1024   da  Non-FS data
/dev/sdb3              13        3882      990720   83  Linux

Still no mention of USB / SATA driver etc...

---

### Post by oldfred on 2009-08-14
this will list the drive id
```
ls -l /dev/disk/by-id
```

---

### Post by scorp123 on 2009-08-14
> **Pierrot Lafouine said:**
> The output :
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6        1520   da  Non-FS data
/dev/sdb2               7          10        1024   da  Non-FS data
/dev/sdb3              13        3882      990720   83  Linux

Still no mention of USB / SATA driver etc... Try this one:

```
sudo apt-get install procinfo lshw
```
These are two small but useful utilities that can spit out all sorts of info about your system.

Once they are installed you can do this:
```
sudo lshw -businfo
```

This then produces output like this:

```
> sudo lshw -businfo

Bus info          Device       Class       Description
======================================================
                               system      FL379AA-UUZ m9480ch
                               bus         Benicia
                               memory      64KiB BIOS
cpu@0                          processor   Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
                               memory      128KiB L1 cache
                               memory      6MiB L2 cache
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
                               memory      8GiB System Memory
                               memory      2GiB DIMM Synchronous 800 MHz (1.2 ns)
                               memory      2GiB DIMM Synchronous 800 MHz (1.2 ns)
                               memory      2GiB DIMM Synchronous 800 MHz (1.2 ns)
                               memory      2GiB DIMM Synchronous 800 MHz (1.2 ns)
cpu@1                          processor   
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
cpu@2                          processor   
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
cpu@3                          processor   
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
                               processor   Logical CPU
pci@0000:00:00.0               bridge      82G33/G31/P35/P31 Express DRAM Controller
pci@0000:00:01.0               bridge      82G33/G31/P35/P31 Express PCI Express Root Port
pci@0000:05:00.0               display     GeForce 9800 GT 512
pci@0000:00:1a.0               bus         82801I (ICH9 Family) USB UHCI Controller #4
usb@3             usb3         bus         UHCI Host Controller
pci@0000:00:1a.1               bus         82801I (ICH9 Family) USB UHCI Controller #5
usb@4             usb4         bus         UHCI Host Controller
pci@0000:00:1a.7               bus         82801I (ICH9 Family) USB2 EHCI Controller #2
usb@1             usb1         bus         EHCI Host Controller
usb@1:2                        bus         USB2.0 Hub
usb@1:2.1                      input       USB Multimedia Cordless Kit
usb@1:2.2                      input       USB Keyboard
pci@0000:00:1b.0               multimedia  82801I (ICH9 Family) HD Audio Controller
pci@0000:00:1c.0               bridge      82801I (ICH9 Family) PCI Express Port 1
pci@0000:04:00.0  wmaster0     network     AR5008 Wireless Network Adapter
pci@0000:00:1c.1               bridge      82801I (ICH9 Family) PCI Express Port 2
pci@0000:03:00.0               multimedia  CX23885 PCI Video and Audio Decoder
pci@0000:00:1c.2               bridge      82801I (ICH9 Family) PCI Express Port 3
pci@0000:02:00.0  eth0         network     RTL8111/8168B PCI Express Gigabit Ethernet controller
pci@0000:00:1d.0               bus         82801I (ICH9 Family) USB UHCI Controller #1
usb@5             usb5         bus         UHCI Host Controller
pci@0000:00:1d.1               bus         82801I (ICH9 Family) USB UHCI Controller #2
usb@6             usb6         bus         UHCI Host Controller
pci@0000:00:1d.2               bus         82801I (ICH9 Family) USB UHCI Controller #3
usb@7             usb7         bus         UHCI Host Controller
pci@0000:00:1d.3               bus         82801I (ICH9 Family) USB UHCI Controller #6
usb@8             usb8         bus         UHCI Host Controller
usb@8:1                        printer     deskjet 5600
usb@8:2                        multimedia  ORITE CCD Webcam(PC370R)
pci@0000:00:1d.7               bus         82801I (ICH9 Family) USB2 EHCI Controller #1
usb@2             usb2         bus         EHCI Host Controller
**[COLOR="Red"]usb@2:2           scsi8        storage     U3 Cruzer Micro[/COLOR]**
[B][COLOR="Red"]scsi@8:0.0.0      /dev/sdi     disk        16GB Cruzer
                  /dev/sdi     disk        16GB 
                  /dev/sdi1    volume      14GiB EXT3 volume[/COLOR][/B]
scsi@8:0.0.1      /dev/cdrom1  disk        Cruzer
                  /dev/cdrom1  disk        
usb@2:5                        bus         USB2.0 Hub
usb@2:5.1                      input       Beanbag Emulation Device
usb@2:5.2         scsi7        storage     USB2.0-CRW
[B]scsi@7:0.0.0      /dev/sde     disk        SCSI Disk
scsi@7:0.0.1      /dev/sdf     disk        SCSI Disk
scsi@7:0.0.2      /dev/sdg     disk        SCSI Disk
scsi@7:0.0.3      /dev/sdh     disk        SCSI Disk[/B]
pci@0000:00:1e.0               bridge      82801 PCI Bridge
pci@0000:01:00.0  scsi6        storage     AIC-7850
pci@0000:01:05.0               bus         FW323
pci@0000:00:1f.0               bridge      82801IR (ICH9R) LPC Interface Controller
**[COLOR="SeaGreen"]pci@0000:00:1f.2  scsi0        storage     82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller[/COLOR]**
[B][COLOR="SeaGreen"]scsi@0:0.0.0      /dev/sda     disk        640GB WDC WD6400AAKS-6
scsi@0:0.0.0,1    /dev/sda1    volume      158GiB Windows NTFS volume
scsi@0:0.0.0,2    /dev/sda2    volume      133MiB EXT3 volume
scsi@0:0.0.0,3    /dev/sda3    volume      423GiB Extended partition
                               volume      1953MiB Linux filesystem partition
                  /dev/sda6    volume      7812MiB Linux filesystem partition
                  /dev/sda7    volume      3906MiB Linux filesystem partition
                  /dev/sda8    volume      7812MiB Linux filesystem partition
                  /dev/sda9    volume      7812MiB Linux filesystem partition
                  /dev/sda10   volume      387GiB Linux filesystem partition
                  /dev/sda11   volume      7844MiB Linux swap / Solaris partition
scsi@0:0.0.0,4    /dev/sda4    volume      13GiB Windows NTFS volume
scsi@1:0.0.0      /dev/cdrom   disk        BDDVDRW GBC-H20L
scsi@2:0.0.0      /dev/sdb     disk        640GB WDC WD6400AAKS-6
scsi@2:0.0.0,1    /dev/sdb1    volume      596GiB Linux filesystem partition
scsi@3:0.0.0      /dev/sdc     disk        400GB SAMSUNG HD400LD
scsi@3:0.0.0,1    /dev/sdc1    volume      372GiB Solaris partition
scsi@4:0.0.0      /dev/sdd     disk        500GB WDC WD5000AAKB-0
scsi@4:0.0.0,1                 volume      465GiB EFI GPT partition[/COLOR][/B]
pci@0000:00:1f.3               bus         82801I (ICH9 Family) SMBus Controller
                  vboxnet0     network     Ethernet interface
                  pan0         network     Ethernet interface

```

As you can see above, this command will tell you which device is USB (highlighted red above) and which device is SATA (highlighted green above).

Is that what you wanted?

---

### Post by juanoleso on 2009-08-14
Thanks scorp123, i'll remember these.

---

### Post by Firestem4 on 2009-08-14
you can use a few different ways(seperating commands with spaces)

```
sudo fdisk -l

cat /proc/partitions

cat /proc/mounts

df -ah

mount -l

sudo parted -l

```

Linux/UNIX identifies devices more universally by use of a UUID which technically speaking helps avoid confusion since each UUID is "Universally Unique"

---

### Post by oldfred on 2009-08-15
I was just reading another post and louie showed this command.
```
sudo smartctl --all /dev/sda
```

---

### Post by Pierrot Lafouine on 2009-08-16
Thanks,
It works.

---

