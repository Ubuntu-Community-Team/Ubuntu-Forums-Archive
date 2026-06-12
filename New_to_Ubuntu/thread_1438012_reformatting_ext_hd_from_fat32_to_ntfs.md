---
title: "reformatting ext hd from fat32 to ntfs"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by aam-aadmi on 2010-03-24
Hi All,

I am using Ubuntu 9.10 and have a extrenal hard drive (WD MyBook 2.0: 320 GB). I would like to reformat this external drive to NTFS; it is currently formatted as FAT32. I tried doing so using g-parted but am unable to do so. Using GParted, when I select the device, the format option is greyed out.

Is there any other way to do this re-formatting?

Thanks.
Aam-aadmi

---

### Post by philinux on 2010-03-24
Unmount it first.

---

### Post by rory526 on 2010-03-24
I don't know why you'd want to format it to ntfs.
anyway... in Gparted, try unmounting the external hard drive partition before trying to format it. (Highlight relevant partition, Patrition -> Unmount, Partition -> Format)

---

### Post by coffeecat on 2010-03-24
Apart from unmounting the drive, you also need to install the package 'ntfsprogs' before Gparted can create a NTFS partition. This is a frequent gotcha. The live CD has ntfsprogs, but this isn't included in a default install, so when you install Gparted, you can't create or resize an NTFS partition.

---

### Post by aam-aadmi on 2010-03-24
Thanks everybody. That works.

Aam-aadmi

---

