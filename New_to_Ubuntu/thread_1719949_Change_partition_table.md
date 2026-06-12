---
title: "Change partition table"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-04-02
how can I change the partition table to MBR from GUID?

---

### Post by oldfred on 2011-04-02
Make sure you have good backups. You will not be able to boot windows unless you have efi not BIOS. Any partition changes has some risk.

I would also make a backup of partition table and save to another device.
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

Download the newest copy of gdisk:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


Conversion - See several posts by srs5694:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

You will need another small partition for grub booting:
If you have gpt you need another small (8-32mb) partition for grub. Are you using efi or BIOS compatible mode?
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

srs5694 is pretty active in this forum. If you add gpt to your title he will probably add some additional info:

---

