---
title: "Ubuntu doesn't load in grub after installing PC/OS 2009 on separate partition"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Flywaver on 2009-03-12
Here is my problem! 

I had one NTFS partition with Windows 7 and one EXT4 with Ubuntu 9.04 Alpha 5...I went on to install PC/OS 2009 on the windows partition and when all was finished I would just have PC/OS 2009 in grub! And from within PC/OS I can't even see the EXT4 (Ubuntu) partition but I can see it if I do: sudo fdisk -l
it shows up as: /dev/sda6 16709 19457 22081311 83 Linux

So.....how do I edit grub so I can be able to boot again in Ubuntu? 

I tried QGrubEditor but since I don't remember the version of the kernel used in my Ubuntu I can't really fill in the infos! :(

Thanks in advance!
Cheers!

---

### Post by jubxie on 2009-03-12
Try super grub. Download the .iso file and rip a bootable disc. Then reboot and it will guide you through the fix. It's a good thing to have around anyway.

[http://stmaarten.globat.com/~supergrubdisk.org/](http://stmaarten.globat.com/~supergrubdisk.org/)

---

