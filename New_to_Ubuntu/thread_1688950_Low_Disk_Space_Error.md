---
title: "Low Disk Space Error"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Singer on 2011-02-16
hello friends 
i am new to ubuntu. i installed ubuntu using Wubi on a 15 Gb partition. I see there is free space of about 11 Gb but now i am getting low disk space error. as per the instruction of Mr. Paqman i checked System Monitor and there under the system tab i see 11Gb free disk space and in the file systems tab i see a Device location [/dev/loop0] with the directory [/] and total space of 2.6 Gb with free space 300 Mb. i see other drives with enough space left over.
so what can i do to solve the low disk space problem or like redirect new software installation to the original drive (which has 11 gb still left over)
Please Help
Singer.

---

### Post by mikewhatever on 2011-02-16
The thing is, wubi doesn't use partitions. It uses the file - /dev/loop - to install Ubuntu into.

---

### Post by bcbc on 2011-02-16
If your total space on /dev/loop0 is 2.6GB then you installed wubi with the absolute minimum sized root.disk (3GB). You can't do much with this.

Since you have that separate partition you might consider installing Ubuntu directly to it, not with Wubi - and then you can make use of the full 15GB. Wubi is just a virtual disk (\ubuntu\disks\root.disk) that sits in that partition.

If you want to stick with Wubi you can try [resizing]("http://ubuntuforums.org/showthread.php?t=1625371") the virtual disk - but unless you have data/settings you don't want to lose it's probably just easier to reinstall. And if that's the case, consider doing a direct install, not wubi.

Just note, when you uninstall or reinstall Wubi it removes the old virtual disk and all the data on there is deleted - so back up important files.

---

