---
title: "Very Beginner, Manual Install, Help?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by njstout04 on 2009-05-31
Ok, first post here, and sorry to make a new thread, but I did search. I'll try to keep it short. I want to (manual) install Ubuntu (downloaded ~1 month ago) on a hp pavillion dv6985se. I have the 64bit version of Ubuntu (64bit system), and my question is, for the partition, I use ext3, yes? And mount it at "/" if I'm trying to dual boot (with vista)? Many thanks for any help :)

---

### Post by ddnev45 on 2009-05-31
Yes. The default format is ext3 and it's stable; by default the first partition will mount at "/".

Might be good for you to search the ["Tutorial and Tips"]("http://ubuntuforums.org/forumdisplay.php?f=100") forum for threads about dual booting with Vista.

---

### Post by SunnyRabbiera on 2009-05-31
yes use ext3, ext4 is still new and not that stable yet...

---

### Post by liamnixon on 2009-05-31
Yes, at least one partition has to be mounted at / for Linux to function (it's the 'root' of the filesystem, and sorry in advance if you know all this already).

Dual-booting has more to do with the boot loader (in this case Grub) than where you mount the partition.  Ubuntu should set that up for you, though.

---

### Post by Six-Blade Knife on 2009-05-31
ext3 is the filesystem you should install Ubuntu on, but I suggest you to create more than just one partition: if you're new to linux and ubuntu you'll probably screw up things (or suppose to), so it might be helpful to create at least two partitions: one partition will mount at / (say 10GB) and the other one at "home".
This way you won't lose your data (your home directory is located in /home/<your-username>) by reinstalling/formatting/whatever the system.
Vista will not give a damn about ubuntu (unless you seize its partition)

---

