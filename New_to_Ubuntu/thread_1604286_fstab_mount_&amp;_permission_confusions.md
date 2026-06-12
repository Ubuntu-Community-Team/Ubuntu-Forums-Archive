---
title: "fstab mount &amp; permission confusions"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by ymp on 2010-10-23
Since an install of U 10.10 over an U 9.04, I have had some file access problems and I am unsure what to change in my fstab.
Some areas of my disk no longer show up as diretories in the upper right section of Nautilus.
Syncing with UbuntuOne is greyed out, suggesting some permissions are not right.

Fstab reads as follows:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda8 during installation
UUID=896753b2-64f4-4786-ac0c-3673ca7166e3 /data           ext3    defaults        0       2
# /data2 was on /dev/sda9 during installation
UUID=BCDE-264C  /data2          vfat    utf8,umask=007,gid=46 0       1
# /home was on /dev/sda7 during installation
UUID=0038fee5-baf1-4e8e-bd2e-28200b3f65de /home           ext3    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=4A78585A785846BB /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=dba35a41-8826-4675-bf74-d5fd8741cb8e none            swap    sw              0       0

Editing advice appreciated.

---

