---
title: "Question - format for 64gb usb drive"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by paker on 2009-11-13
Is FAT32 the best way to format a 64gb usb drive? It will be used on Ubuntu9.04, Windows Vista and Windows XP. If formated to FAT32, will Windows see all 64GB?

---

### Post by NickJones on 2009-11-13
The WUBI installer allows you to install Ubuntu onto a NTFS or FAT partition. I think that may be your best option.

---

### Post by paker on 2009-11-13
Thanks for the quick reply. My question was not about putting Ubuntu Installer on a thumb drive. 

I have computers running Windows XP, Windows XP Professional, Windows Vista, and Ubuntu 9.04. I want to be able to use the thumb drive with all of them. What format do you recommend for the USB thumb drive?

---

### Post by Iksf on 2009-11-13
FAT32 may be a pile of garbage but for what you seem to want it is the best option. If you did not have to use Windows you could have some real quality filesystems on their though

---

### Post by durand on 2009-11-13
I've formatted my 640GB external hard drive as FAT32 without any problems in ubuntu, windows or my PS3 (the main reason it was fat and not ntfs..) You can use ntfs if you want because its supported on ubuntu and windows. It might help if you have huge files but I'm not sure of other benefits.

---

### Post by sc30317 on 2009-11-13
fat32 or ntfs.  Keep in mind that fat32 has a 4GB file size limitation, so you cannot save any files on that flash drive that are larger then 4GB if it is formatted in fat32

---

