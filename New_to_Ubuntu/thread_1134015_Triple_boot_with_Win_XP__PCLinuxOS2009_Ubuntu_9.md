---
title: "Triple boot with Win XP / PCLinuxOS2009/ Ubuntu 9"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ed325i on 2009-04-23
Can I safely triple boot with Ubuntu / Kubuntu 9.04?  I currently have Win XP, PCLinus OS 2009.1, and Linux Mint 6 KDE installed.  I will probably replace Mint 6 with Ubuntu 9.04.  Is it safe to delete and repartition the current Mint EXT3 partition to EXT4, and install 9.04?  Is there anything special that I have to do, so that 9.04 and its GRUB will coexist with WIN XP NTFS, PCLOS EXT3?  Thanks.

---

### Post by zvacet on 2009-04-23
I think you should not have problems with that,because you already have Mint installed witch is Ubuntu-based and if that works well I don´t see why should be something different with Ubuntu.

---

### Post by cariboo on 2009-04-23
Keep in mind that grub from the last installed distribution is the one that is active.

---

### Post by ed325i on 2009-04-23
> **cariboo907 said:**
> Keep in mind that grub from the last installed distribution is the one that is active.

Not a problem.  Grub from 9.04 should be able to see Win XP and PCLOS.

Mixing NTFS, EXT3, and EXT4 should not be an issue?

---

### Post by cariboo on 2009-04-23
It shouldn't be an issue, I no longer have any ntfs partitions, but during the alpha releases I still had Windows 7 installed plus an eSATA drive formatted to ext3, all the partitions could be accessed.

---

### Post by ed325i on 2009-04-23
Thanks.  Just installed 9.04 with EXT4.

Boots quickly.

Nvidia drivers are missing.

---

