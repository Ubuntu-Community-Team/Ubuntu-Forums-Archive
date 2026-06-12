---
title: "formatting partitions"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by SteelCore on 2010-01-19
My PC has 2 320G harddisks. I want to install a few Ubuntus in the first 50 Gb of the first harddisk and leave the rest of it and the second harddisk as 2 FAT32 partitions for storage. My question is what is the best way to format these 2 storage partitions. Is it during the installation or afterwards with gparted?
when I try it during the installation and I chose FAT32 for the storage area I get /dos and /windows as mounting point options and that has confused me since I don't have a Windows or DOS on that harddisk. Thanks for any help.

---

### Post by adam814 on 2010-01-19
You don't have to set up mount points at install.  Those are suggestions (I happen to use /windows but it makes sense as I dual-boot and it's my Vista partition).

You can just leave the mount point blank and/or leave it as free space.  You can change partitions, format, or add the entries you want in /etc/fstab after you get Ubuntu running.  Which is better just depends on personal preference.

---

### Post by SteelCore on 2010-01-20
If I don't chose a mount point I get a warning saying that if a mount point is not chosen I will not be able to use the partition.

---

### Post by adam814 on 2010-01-20
Hmm...it's been a while since I've done a clean install, but I definitely mount partitions I didn't configure in the installer.

It's more like you won't be able to use them on the first boot without manually mounting.

It looks like you have two options:
1) Settle for using /windows or /dos as a mount point for them and do it in the installer.
2) Ignore the warning and set it up manually from your running system.

---

