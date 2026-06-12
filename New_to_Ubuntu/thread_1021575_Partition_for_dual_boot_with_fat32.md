---
title: "Partition for dual boot with fat32"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by scuicho on 2008-12-25
I just replaced a failed hard drive on my acer trvelmate and I want to do a dual boot however when I try to install windows from the recovery discs it comes up with an error message. My computer used to use fat32 could the error be related to my new hard drive using ntfs? If so is it possible to partition part of my disc for fat32 and leave the rest ntfs for Ubuntu? If so does anyone know any guides for doing this? 

Thanks, kris

---

### Post by cariboo on 2008-12-25
Linux doesn't use ntfs, the standard Linux file system is ext3, there are several other file systems available during installation, but I would suggest sticking with ext3, until you have used Linux for a while. 

I would also suggest using ntfs for Windows, at is is much more robust, and you will run into fewer problems, for example the 4Gb file size limit for vfat file systems.

I would suggest installing Windows on a blank hard drive and set the windows partiton to the size you need, and leave the rest of the hard drive blank and let the Ubuntu installer partition the remaining free space.

Jim

---

### Post by Miljet on 2008-12-25
I think your problem has nothing to do with using NTFS. Recovery disks are meant to repair a damaged file system that is already installed, not for doing a complete new installation. You will probably need your original Windows install disk.

---

