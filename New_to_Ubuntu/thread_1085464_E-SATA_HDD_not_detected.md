---
title: "E-SATA HDD not detected"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by fr.theo on 2009-03-03
I have a P5K3 Deluxe ASUS main board with an Jmicron JMB363  PATA/SATA controller on board, I connected a Western Digital My Book 1TB drive to the ESATA slot. Windows XP with the right drivers is able to detect the drive however Ubuntu cannot see it at all, although I notice on boot up that the drive light flashes.

I am not sure why I cannot see the drive, I have tried to look for a solution on the internet but have found none any Help would be appreciated.

---

### Post by fr.theo on 2009-03-20
I have exhausted all possible resources concerning this topic I am not sure but I think I have read almost every post imaginable to find a solution but with no luck.Windows xp can see my drive no problems when I boot the system to Ubuntu I notice that it either switches the device of when trying to detect it or it does not see it at all, I have a WD 1GB My Book Home Edition with fire wire, esata, usb. 


here is an Output of lsmod, fdisk -l, dmesg, lspci. NOTE: I only have two 1GB external hdd, I do not have any 1GB internal drive and only my usb WD 1GB is showing.

```
 
_LSPCI: _

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)

_FDISK -L_

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd29fd29f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38161   306528201   83  Linux
/dev/sdb2           38162       38913     6040440    5  Extended
/dev/sdb5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56d34d1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       29649   238155561   83  Linux
/dev/sdc2           29650       30401     6040440    5  Extended
/dev/sdc5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c159ba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       38913   312568641    7  HPFS/NTFS

[COLOR="Red"]Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes[/COLOR]
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06320631

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

_LSMOD:_

pata_jmicron            8448  0 
pata_acpi               9856  0 

_DMESG:_

[   47.589744] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   47.589780] scsi2 : pata_jmicron
[   47.589811] scsi3 : pata_jmicron
[   47.590322] ata3: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[   47.590324] ata4: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[   47.632018] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]


```

can anyone help this is getting frustrating. 

Thanks

---

### Post by aprete on 2009-03-24
I just got a 500GB Seagate Free Agent Xtreme drive.  It is detected immediately (shows up on the Gnome desktop) when I plug it in using the USB cable that came with it (but not the FireWire cable but I'm not going to bother with FireWire).

I bought an eSATA cable today for the increased speed.  I'm having no problems using it, but I have to mount it manually before it appears on the Gnome desktop.  I have two 250GB WD internal drives that are sda and sdb, so I guessed that the new one was sdc, and entered the following command:

 sudo mount -t ntfs /dev/sdc1 /media/disk2

and it showed up and I can use it.  I'm sure all I need is an edit to fstab.

My configuration is similar to yours:  ASUS P5B motherboard with Jmicron controller.  I'm running Intrepid 8.10.

---

### Post by aprete on 2009-03-25
Another thing to check:  Look at the messages issued by the Jmicron controller when the system is booting.  You should see the new drive there.  If you don't, you may have a problem with your BIOS configuration or the configuration of the Jmicron controller.  If you see it there but Ubuntu Linux still doesn't detect it, then it's a problem with your software or your drivers.

---

### Post by aprete on 2009-03-28
You can disregard my last message.  The disk can be off or disconnected when the machine boots.  The controller will recognize it when it is turned on.  The O/S will recognize it if it has the right driver (for the controller) installed.  Under Windows I had to install the controller driver (from Jmicron's website).  Ubuntu apparently has the drivers in it already.  Once I set the BIOS to AHCI plug & play worked in Windows and mounts worked in Ubuntu.  The only thing that I don't have working yet is automount in Ubuntu.

---

