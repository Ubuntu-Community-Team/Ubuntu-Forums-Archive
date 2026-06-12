---
title: "partitioning hard drive to add windows"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by richard.scott-ettrick on 2010-06-08
I wish to partition my laptop hard drive to reinstall Windows 7 which I totally hashed when installing Lucid Lynx. I have programs which must have windows installed and will not run in wine. How do I do it? I love Ubuntu it works much better than Win#$!s:p

---

### Post by RiceMonster on 2010-06-08
The easiest way to do it would be to back up your data, install windows over the entire hard drive, then install ubuntu again as dual boot. If you add windows second rather than first, it becomes a lot more difficult.

---

### Post by derande on 2010-06-08
have you thought about running Windows as a virtual machine (VirtualBox) rather than dual booting? i have some programs i must continue to run in Win98 and VirtualBox works great for me.

---

### Post by bwallum on 2010-06-08
> **ricemonster said:**
> the easiest way to do it would be to back up your data, install windows over the entire hard drive, then install ubuntu again as dual boot. If you add windows second rather than first, it becomes a lot more difficult.

+1

---

### Post by richard.scott-ettrick on 2010-06-08
> **RiceMonster said:**
> The easiest way to do it would be to back up your data, install windows over the entire hard drive, then install ubuntu again as dual boot. If you add windows second rather than first, it becomes a lot more difficult.
My problem is Windows can't recognise the ext4 disk how do I get to a position where Windows will recognise the disk format?

---

### Post by RiceMonster on 2010-06-08
> **richard.scott-ettrick said:**
> My problem is Windows can't recognise the ext4 disk how do I get to a position where Windows will recognise the disk format?

Do you mean it doesn't recognize the partitions or your hard drive at all? Windows can't read ext4, so you will have to delete your partitions and install windows over it.

---

### Post by oldfred on 2010-06-08
You do not have to delete everything if you have an available primary partition. Windows does have to be in a primary partition but it does not have to be sda1. The issue always is that the install of windows will overwrite grub and you will have to reinstall grub. But that is easy. Just boot the liveCD and run a couple of commands.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows will not read ext4 partitions. They are working on drivers but I would not do it anyway. You normally do not want to write into system partitions whether NTFS or ext3. It is much better to create a shared NTFS partition for any data you may want in both systems.

---

### Post by richard.scott-ettrick on 2010-06-08
> **oldfred said:**
> You do not have to delete everything if you have an available primary partition. Windows does have to be in a primary partition but it does not have to be sda1. The issue always is that the install of windows will overwrite grub and you will have to reinstall grub. But that is easy. Just boot the liveCD and run a couple of commands.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows will not read ext4 partitions. They are working on drivers but I would not do it anyway. You normally do not want to write into system partitions whether NTFS or ext3. It is much better to create a shared NTFS partition for any data you may want in both systems.

Used Gparted to shrink Ubuntu part of HD. Then made new NTFS Partition. Installed Windows on that. Thanks for your help.

---

### Post by Paqman on 2010-06-08
> **RiceMonster said:**
>  If you add windows second rather than first, it becomes a lot more difficult.

I wouldn't say it's "a lot" more difficult. All you have to do is [reinstall Grub after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

