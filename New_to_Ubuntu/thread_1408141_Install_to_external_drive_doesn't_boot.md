---
title: "Install to external drive doesn't boot"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by sync00 on 2010-02-16
I formatted an external drive with one ntfs partition and 3 ext3 partitions. On the last configuration step of the install I choose the advanced setting and selected the ext3 partition that I installed Ubuntu to for Grub.

When I boot the computer and choose to boot from usb device I get the message that BOOTMGR is missing. Does Grub need to be in the first partition of the drive? I put it in the second partition.

---

### Post by cariboo on 2010-02-17
Grub should be installed to the first partition of the hard drive, especially if you don't have grub installed on the first hard drive.

If you have grub installed on the first partition of the first hard drive, you then can install grub from another install just about anywhere you want, using the chainloader.

---

