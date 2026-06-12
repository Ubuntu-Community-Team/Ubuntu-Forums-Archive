---
title: "Trying to delete, repartition SDHC card"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-02-18
Hey there,

I'm trying to delete and recreate the partition on my SDHC card in Xubuntu 9.04. It has a failed installation of Xubuntu on it, and all it's doing right now is collecting dust.

I tried running gparted on it, but it doesn't seem to have the support for MMC/SD cards.

Any ideas how I can reformat the SD card in FAT32?

Thanks,
--Red

---

### Post by gordintoronto on 2010-02-18
When you start gparted, in the top-right is a box which probably says something along the lines of dev/sda and the size.  To the right of that is a control used to change devices.

---

### Post by undecim on 2010-02-18
> **gordintoronto said:**
> When you start gparted, in the top-right is a box which probably says something along the lines of dev/sda and the size.  To the right of that is a control used to change devices.

Failing that, you will need to use a terminal.

If I remember correctly, SDHC cards show up either like a thumb drive at /dev/sd*, or as /dev/mmcblk* (and partitions on that will be /dev/mmcblk*p*), depending on your card reader.

can you open a terminal, run these two commands and post the output?
```
ls /dev/mmc*
sudo fdisk -l
```

---

