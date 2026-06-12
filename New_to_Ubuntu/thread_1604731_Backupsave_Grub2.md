---
title: "Backup/save Grub2"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Septuagenarian on 2010-10-24
I recently had problems following upgrade to Ubuntu 10.10 with grub 2 not recognising the ntfs partition. After help from the experts on this forum all is now well,but,to avoid the same problem happening again, is it possible to save the grub/mbr or whatever to say a floppy disk (remember them?)or flash drive so I can restore it ? I know it is possible to reinstall from the live CD but get confused with the chmod and mounting procedure, and last time I tried sudo grub-update,or sudo grub install I got in a right mess. Please keep it simple,thanks.

---

### Post by sikander3786 on 2010-10-24
Please see this link.

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by oldfred on 2010-10-24
You can but if you want simple and safe I do not recommend it. You have to use dd to copy bits from the first sector of the drive and then copy that back to the exact location. It is very doable but a lot more dangerous as if you copy to the wrong place or copy the wrong amount of data, you destroy system.

I do not know if you had to do the full chroot reinstall of grub but the standard reinstall is actually two lines if you know the partition your install is in.

If you know it is sda5, then this is all you should have to do to reinstall grub2.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

If you really want the command:
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Note that the MBR's code area, where the boot loader normally resides, is 440 bytes long.The next four bytes contain a disk ID number, and the next two bytes are normally 0. 
You also may or may not want to backup bs=512 as that includes partition table, but if you change partitions and restore old table you may totally corrupt system.

---

