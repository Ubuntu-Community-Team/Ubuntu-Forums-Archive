---
title: "XP/Ubuntu Grub Boot Issues + advice"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by NeonSamurai on 2010-06-01
Been a while since I posted, but I've managed to mess up my dual boot XP/Ubuntu PC.

Basically I boot it up and get:

> Grub Loading stage1.5

Grub loading, please wait...
Error 17

Now I can boot from an Ubuntu live CD and I can check the contents of /boot/grub/menu.lst and it's fine (same as my backup copy), but still the machine won't boot. 

The problem has been caused by resizing a partition using disk management in XP, and since then the boot loader has been having the above error, even though the partition in question was not the active one.

my drive partitioning is as follows:

Sdb1 - XP partition (NTFS)
Sdb2 - Ubuntu
Sdb3 - Ubuntu
Sdb4 - NTFS

So I'm asking what to do to get my system booting again, but I'm also trying to understand the connection Grub has with the XP system and what would have happened to cause this. I'm guessing it's something to do with the MBR, but I'm drawing a blank on where I need to go to correct it.

Any help or advice would be very welcome.

Thanks


Mark

---

### Post by seawolf167 on 2010-06-01
You can try re-installing Grub[2] following the below instructions. The partition changes made by XP may have screwed something up; the Windows-only option would probably be something like "fixboot", "fixmbr"; hopefully re-installing Grub with the new partition info should fix this.

```
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
```

EDIT: fixed the link

---

### Post by oldfred on 2010-06-01
Reinstalling grub may solve it or if partitions have changed UUID's you may also have to edit fstab.

If the reinstall does not work run this so we can see your entire system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by NeonSamurai on 2010-06-02
Thanks **Seawolf167** & **Oldfred**,

Part of my question was understanding grubs relationship with the boot sequence. For example; do I reinstall grub on my primary linux partition, and if so how does the PC defer to it on boot?

Also in my situation with my Ubuntu partition on sdb2, would my commands be:

> $sudo mount /dev/sdb2 /mnt

sudo chroot /mnt

#grub-install /dev/sdb

#grub-install --recheck /dev/sdb

I have a copy of my grub menu list that I can use once grub is working.

Am I on the right track?

Thanks


Mark

---

### Post by NeonSamurai on 2010-06-02
Okay,

just tried installing grub as per those instructions. Here's what happened:

> root@ubuntu:/# grub-install /dev/sdb2
/dev/sbd2 does not have any corresponding BIOS drive.
root@ubuntu:/# grub-install --recheck /dev/sbd2
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda3: Not found or not a block device.

Not quite sure what's happening here. Does this mean that grub isn't the problem and that the BIOS is? If not, why can I not install grub on my ubuntu partition?

Thanks


Mark

---

### Post by NeonSamurai on 2010-06-02
Okay,

Here's what I did to get my grub working again:

> sudo grub
grub> find /boot/grub/stage1

this brought back the result (HD1,1) so I then did:

> grub> root (hd1,1)
grub> setup (hd1)
grub> quit

Which did the trick and now it's all back and working.

Thanks for the help and pointing me in the right direction.


Mark

---

### Post by oldfred on 2010-06-02
The first set of instruction you ran was for grub2 and will not work for grub legacy. Obviously the second set for grub legacy worked to install to sdb.

We now have to know if a user has grub2 - new installs of 9.10 or 10.04 or grub legacy from updates before 9.10. Even 9.10 can be old grub from an update or grub2.

---

