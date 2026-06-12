---
title: "HELP! No more free-space option on install!"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by diafygi on 2010-10-11
HELP! I deleted my 10.04 Ubuntu partition and can't install 10.10!

I have several partitions on my computer (WinXP, storage, and Ubuntu+swap), and I usually just replace the Ubuntu/Swap partition when a new version of Ubuntu comes out. The Ubuntu and swap partitions are on an extended partition.

This time, I booted into the 10.10 Live CD, deleted the 10.04 Ubuntu and swap partitions gparted (like I always do), then tried to install 10.10. However, the "use largest continuous free space" option was gone from the install menu!!! Where did it go? How do I install 10.10 onto that free space I just opened up? I've never used the advanced partition menu, so I'm scared that I'll delete my WinXP or storage partitions.

PLEASE ADVISE! I'm posting this from the Live CD! I've attached a screenshot of my partitions according to gparted.

---

### Post by diafygi on 2010-10-13
There is a bug entry on this issue ([#652852]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852")). I was able to install 10.10 by following the [workaround]("http://sites.google.com/site/easylinuxtipsproject/partitioning") posted in the bug report.

---

### Post by corcomp84 on 2010-10-13
do you want to keep ubuntu 10.04?  because as long as you dont delete the ntsf partition which is windows then you will be fine.. is the dev/sda4 your storage partition? because that would be impossible for windows to see.. are you sure you deleted the right partition? I would think that 10.04 is installed on the dev/sda4 partition and the rest at the end would be the swap or storage..

---

### Post by diafygi on 2010-10-13
> **corcomp84 said:**
> is the dev/sda4 your storage partition?

Yes, I use that for storage for video editing, which is done in Ubuntu. I don't need to see that partition from the Windows XP partition. If I ever need a file from that partition in Windows, I copy the file to the ntfs partition in Ubuntu then reboot into Windows.

---

### Post by corcomp84 on 2010-10-13
I would do this, because I cant Imagen your OS's run very well with such little room.. I would take your storage partition and back it up off the computer.. That way you have all that space freed up.. Then I would delete the dev/sda4 all together along with the unused partitions at the end.. once that is done resize the widows partition so that you have more room at least an extra 3 or 4 GB.. then rebuild your partitions.. Just have one big partition for ubuntu and your storage, and install ubuntu 10.04 so that you dont have to keep upgrading your system.. Build a 512mb swap partition at the end and call it a day.. then move all your storage data back to the new partitions.. When you are all done you will have two main partitions and then a swap..

---

### Post by corcomp84 on 2010-10-13
you should be fine for about two years.. I would be scared every time that I was going to loose my data, if you want to play around with updating your OS every six months then I would recommend an external storage device that can be unplugged or turned off during your updating process.. Its just a precaution.. but thats just me.. good luck..

---

