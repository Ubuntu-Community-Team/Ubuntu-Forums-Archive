---
title: "No Startech drive shows in Karmic Kaola"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by GrampaDan on 2010-01-04
My HP-Mini 2140 came with Vista. I have a Startech duo dock ( Satadock22ue ) with two Western Digital 250 Gb drives. Worked well in Vista.
 
Now I've booted Vista off the computer. I'm running Karmic Koala Netbook Remix with all the latest patches. Works great except my Startech controller isn't seen and the two hard drives don't show. (They are formatted NTFS, and I could reformat them to FAT32).
 
What do I need to search for to find the information I need to get the drives working in Ubuntu?

---

### Post by GrampaDan on 2010-01-04
> **GrampaDan said:**
> ...Works great except my Startech controller isn't seen and the two hard drives don't show. ...
 
 I went to startech support and all they said was that it should work natively in Ubuntu.

---

### Post by doas777 on 2010-01-04
please run:
```

sudo fdisk -l

```
and post back with the output.

---

### Post by adam814 on 2010-01-04
Reformatting to FAT32 wouldn't make a difference.  NTFS is supported by any decent partitioning utility.  Even if the kernel doesn't support a filesystem it would still see the disks and partitions.

I see on the Startech site it says it works on Linux, so if everything else is in order it should work.

Are you connecting it with eSATA or USB?  I'd think your best shot would be with USB.

Right after you connect it type this in a terminal and post the output:
```
dmesg | tail
```

---

### Post by GrampaDan on 2010-01-05
> **doas777 said:**
> please run:
```

sudo fdisk -lDisk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150271978+  83  Linux
/dev/sda2           18709       19457     6016342+   5  Extended
/dev/sda5           18709       19457     6016311   82  Linux swap / Solaris

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 17 sectors/track, 5603 cylinders
Units = cylinders of 1394 * 512 = 713728 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           6        5604     3901440    b  W95 FAT32


```and post back with the output.
Here's the output forom fdisk: (Still with the esata cable attached)

---

### Post by GrampaDan on 2010-01-05
> **adam814 said:**
> 

Are you connecting it with eSATA or USB?  I'd think your best shot would be with USB.

Right after you connect it type this in a terminal and post the output:
```
dmesg | tail
```

Okay, I have the USB cable attached to the unit.

Here's the output from the dmesg | tail

root@HP-Mini:/home/dan# dmesg | tail
[200884.432165] ecryptfs_read_lower: octets_read = [-4]; expected [4096]
[200884.432182] ecryptfs_decrypt_page: Error attempting to read lower page; rc = [-22]
[200884.432200] ecryptfs_readpage: Error decrypting page; rc = [-22]
[200884.432664] ecryptfs_read_lower: octets_read = [-4]; expected [4096]
[200884.432681] ecryptfs_decrypt_page: Error attempting to read lower page; rc = [-22]
[200884.432699] ecryptfs_readpage: Error decrypting page; rc = [-22]
[274777.069132] usb 1-8: new high speed USB device using ehci_hcd and address 5
[274777.205922] usb 1-8: configuration #1 chosen from 1 choice
[274777.206394] hub 1-8:1.0: USB hub found
[274777.207871] hub 1-8:1.0: 4 ports detected
root@HP-Mini:/home/dan# 

And from fdisk -l

root@HP-Mini:/home/dan# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150271978+  83  Linux
/dev/sda2           18709       19457     6016342+   5  Extended
/dev/sda5           18709       19457     6016311   82  Linux swap / Solaris

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 17 sectors/track, 5603 cylinders
Units = cylinders of 1394 * 512 = 713728 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           6        5604     3901440    b  W95 FAT32

---

### Post by adam814 on 2010-01-05
Hmm...you had the hardware working in Vista...all indications are that it's at least reported to work with Ubuntu...yet no dice.  This is a tricky one.

Can you post the output from "sudo lsusb" to see if the controller shows up at all?

---

### Post by GrampaDan on 2010-01-07
> **adam814 said:**
> Hmm...you had the hardware working in Vista...all indications are that it's at least reported to work with Ubuntu...yet no dice.  This is a tricky one.

Can you post the output from "sudo lsusb" to see if the controller shows up at all?
This is the result with the USB cable connected:

root@HP-Mini:/home/dan# sudo lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 090c:6200 Feiya Technology Corp. 
Bus 001 Device 002: ID 04f2:b12e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And this is the result with the e-sata controller plugged into the express card slot of the netbook.

root@HP-Mini:/home/dan# sudo lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 090c:6200 Feiya Technology Corp. 
Bus 001 Device 002: ID 04f2:b12e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think I'll to install VirtualBox, stick Windows 7 onto a virtual disk and see if it spots the controller. Or maybe the controller just died, but then it doesn't see it using the USB either. Feel like I'm pulling straws

---

### Post by adam814 on 2010-01-07
Are you connecting the controller through a hub?  I notice it shows one connected when you have it plugged in via USB and not when you don't.

If so you could try connecting directly to eliminate issues with the hub.

---

