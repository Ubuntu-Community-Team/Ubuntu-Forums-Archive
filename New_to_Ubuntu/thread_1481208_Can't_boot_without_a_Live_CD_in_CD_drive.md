---
title: "Can't boot without a Live CD in CD drive"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by jackflamer on 2010-05-12
Hi, I am pretty new for this. I recently start playing around with this nice OS. I have a problem which I can't solve, hope someone can help me out. Here it is,

I have a 500G hard disk. It was originally installed with Windows XP. Due to recent hardward failure, I decided to try Ubuntu. Becuase I was not sure about whether I would keep this as the primary OS, I use Ubuntu installer set my hard disk as follow,

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1bde1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    b  W95 FAT32
/dev/sda2            6080       60801   439554465    f  W95 Ext'd (LBA)
/dev/sda5           12750       25497   102398278+   b  W95 FAT32
/dev/sda6           25498       38245   102398278+   b  W95 FAT32
/dev/sda7           38246       60801   181181038+   b  W95 FAT32
/dev/sda8            6080       12401    50781402   83  Linux
/dev/sda9           12402       12749     2795278+  82  Linux swap / Solaris

I left the first partition for Windows installation which I haven't installed anything on it. So /dev/sda1 is empty. While I had installed Ubuntu on /dev/sda8 successfully, I could not boot into the system without leaving LiveCD in the CD-ROM drive. Otherwise, the screen showed just a blinking prompt, and halted there forever. 

I think this could be the GRUB issue, but I have no idea how to edit it. I took a look into the menu.lst file, there was nowhere I could found something /dev/hda1 or /dev/hda8. Can someone help?

BTW, when I can successfully boot into the system with the LiveCD in the cd drive, there is no GRUB menu. I think this maybe something related to I have only one OS installed.

---

### Post by ubunterooster on 2010-05-12
try ```
sudo update-grub
```

---

### Post by mick222 on 2010-05-12
what version of Ubuntu are you running there is no menu 1st in karmic or lucid.As said above run sudo update-grub in terminal that should sort it out.

---

### Post by jackflamer on 2010-05-12
Thank you ubunturooster, and mick222, I am using 9.04!
Run update-grup alone didn't fix the problem, however, I have found the solution based on your suggestion. I checked the flag of each partition using gparted, found the boot flag was set on on the first partition hda0 which I left for future installation of windows. I changed the boot flag to my linux ext3 partition, and run the update-grub, and it worked!

Thank you both again for providing suggestions!

---

