---
title: "find /boot/grub/stage1"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by imjscn on 2010-06-17
I have grub installed, and I see stage1 is in the /boot/grub folder.

In the grub> directory, I type in find /boot/grub/stage1, I got error 15 saying "File  not found".

This command is suppose to return parameter in the format of (hdX,Y). that is used in bringing grub menu on next boot, according to this article:

[http://chi3x10.wordpress.com/2008/02/27/restore-corrupted-grub-mbr-from-a-live-ubuntu-cd/]("http://chi3x10.wordpress.com/2008/02/27/restore-corrupted-grub-mbr-from-a-live-ubuntu-cd/")

I think I type in everything correctly. Could anybody help me solve this problem?

---

### Post by oldfred on 2010-06-18
kansasnoob has all the command to chroot on one line. Easy to copy and rum. You do have to make sure to change the partition if it is not sda5.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

