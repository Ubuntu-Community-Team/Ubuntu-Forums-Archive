---
title: "Trouble Installing XP [For Games]"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Testrum on 2009-03-06
Well I tried installing Windows XP and I got some error telling me to run chkdsk f ??? not sure if thats for Ubuntu or if I'm supposed to magically run Windows XP lol. I would like to dual boot with Ubuntu as my primary os and about 70-80 GB for Windows XP for various games and other things.

---

### Post by balaknair on 2009-03-07
chkdsk is a command prompt tool in Windows(it'll be present on the WinXP CD). When booting from the XP CD, select the option to repair or recover(by pressing 'R'), then start chkdsk by typing in *chkdsk /r* to repair a corrupted drive. This will fix the problem if it is a disk with a damaged partition table. If you already have Ubuntu on it, and there is no space at the beginning of the disk for XP, you will have to delete the Ubuntu partitions and format the disk, as XP does not recognize ext3 filesystems.

_More Likely Cause_: If the drive is a SATA drive, XP will not install since it lacks the SATA drivers on the CD. Solution- at system power on, enter BIOS settings and disable SATA mode for the hard drive. XP will now be able to detect the drive properly, and you can proceed with the install. After installing XP, you can install the SATA drivers, and if you want you can now switch back to SATA mode setting in BIOS.


On an empty hard disk:
The best option is to install WinXP **before** you install Ubuntu. Windows needs to be on the first primary partition of your hard drive, or it won't boot. Besides, it will overwrite the MBR, so you won't be able to boot any non-Windows OS you had installed previously. So install WinXP first, then install Ubuntu, and Ubuntu will be the primary OS by default in the GRUB bootloader.

If you have already installed Ubuntu on the disk:
Unless you have >10GB space available in the initial portion of the disk to create a primary partition for your new WinXP install(as would be the case if you're overwriting a previous Windows installation), you will have to format/repartition the drive. Windows can only boot from the first hard drive partition. So my suggestion would be to back up important stuff on your Ubuntu install, wipe the disk clean, install WinXP on the first partition, and install Ubuntu in the remaining space.

---

### Post by Testrum on 2009-03-07
> **balaknair said:**
> chkdsk is a command prompt tool in Windows(it'll be present on the WinXP CD). When booting from the XP CD, select the option to repair or recover(by pressing 'R'), then start chkdsk by typing in *chkdsk /r* to repair a corrupted drive. This will fix the problem if it is a disk with a damaged partition table. If you already have Ubuntu on it, and there is no space at the beginning of the disk for XP, you will have to delete the Ubuntu partitions and format the disk, as XP does not recognize ext3 filesystems.

_More Likely Cause_: If the drive is a SATA drive, XP will not install since it lacks the SATA drivers on the CD. Solution- at system power on, enter BIOS settings and disable SATA mode for the hard drive. XP will now be able to detect the drive properly, and you can proceed with the install. After installing XP, you can install the SATA drivers, and if you want you can now switch back to SATA mode setting in BIOS.


On an empty hard disk:
The best option is to install WinXP **before** you install Ubuntu. Windows needs to be on the first primary partition of your hard drive, or it won't boot. Besides, it will overwrite the MBR, so you won't be able to boot any non-Windows OS you had installed previously. So install WinXP first, then install Ubuntu, and Ubuntu will be the primary OS by default in the GRUB bootloader.

If you have already installed Ubuntu on the disk:
Unless you have >10GB space available in the initial portion of the disk to create a primary partition for your new WinXP install(as would be the case if you're overwriting a previous Windows installation), you will have to format/repartition the drive. Windows can only boot from the first hard drive partition. So my suggestion would be to back up important stuff on your Ubuntu install, wipe the disk clean, install WinXP on the first partition, and install Ubuntu in the remaining space.
Okay, How do I go about deleting my Ubuntu partition?

---

### Post by theozzlives on 2009-03-07
all you have to do is resize Ubuntu to make room for Windows. Move the free space to the front of the drive and install Windows. Do all this with the Partition Editor on your Ubuntu CD (System > Administration > Partition Editor).

NOTE: You'll have to setup GRUB.

---

### Post by Testrum on 2009-03-07
> **theozzlives said:**
> all you have to do is resize Ubuntu to make room for Windows. Move the free space to the front of the drive and install Windows. Do all this with the Partition Editor on your Ubuntu CD (System > Administration > Partition Editor).

NOTE: You'll have to setup GRUB.
Eh, wiping the HD isn't that big of a deal for me. I downloaded DBAN and I'm burning it then going to Nuke the HD and reinstall everything.

---

### Post by ivanvajar on 2009-03-07
Please, be sure you install Windows first, so you don't have to reconfigure your boot loader.

---

### Post by Hobgoblin on 2009-03-07
> **Testrum said:**
> Eh, wiping the HD isn't that big of a deal for me. I downloaded DBAN and I'm burning it then going to Nuke the HD and reinstall everything.

A bit OTT.

The Windows installer should offer to remove all the partitions (which will be seen as "unknown" to Windows) during install.

---

