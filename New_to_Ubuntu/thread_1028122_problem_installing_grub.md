---
title: "problem installing grub"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by NO2 on 2009-01-02
well iam new to linux
i have quite an old computer with 256mb ram so i was trying to install ubuntu 6.06
i changed the format of hda6 to ext3 and also created a linux swap partition
at the end of the installation there was a problem in the installation of grub
i tried the command as root grub-install /dev/hda
it displays someting like cannot create /boot
what should i do?

---

### Post by Michael.Godawski on 2009-01-02
hi NO2, 

what installation method are you using live CD or alternate CD?

Do you want make a dual-boot or will Ubuntu be the only operating system?

Have you checked out these installation guides?:


[LIST]
[*]Licd CD install:[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
[*]Alternate CD install:[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[/LIST]

---

### Post by NO2 on 2009-01-02
i want to dual boot
i am using the live cd installation

---

### Post by NO2 on 2009-01-02
i tried this while using the live cd:

root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    19567169     9783553+   c  W95 FAT32 (LBA)
/dev/hda2        19567170    78236549    29334690    f  W95 Ext'd (LBA)
/dev/hda5        19567233    39134339     9783553+   b  W95 FAT32
/dev/hda6        39134403    56596994     8731296    b  W95 FAT32
/dev/hda7        58701573    78236549     9767488+   b  W95 FAT32
/dev/hda8        56597058    58701509     1052226   82  Linux swap / Solaris

Partition table entries are not in disk order
root@ubuntu:/home/ubuntu# grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

i don't know what to do now

---

