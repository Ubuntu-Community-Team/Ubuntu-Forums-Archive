---
title: "Going from Dual to Single Boot machine"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by newport_j on 2010-05-07
How do I go back to a single boot machine from a dual boot machine? I must comply with my company's request so I must have a single boot machine. I choose Ubuntu over Windows XP.

I have dual boot machine (Ubuntu 8.04 and Windows XP). I need only an Ubuntu 8.04 system. I have removed all of my Windows XP apps that I want to save - they are safe. So I can clean Windows XP off the hard drive with no problem. How do I do it?

Newport_j

---

### Post by U.Ravi Kumar on 2010-05-07
You can try deleting the partition on which windows xp is installed if you want to remove it. But if Windows XP is installed on C, you can not directly delete it, because you can not delete a primary partition without deleting logical partitions first. If you do that all your partitions will be corrupted. So try uninstalling both windows and ubuntu and try installing Ubuntu.

---

### Post by Georgia boy on 2010-05-07
Check out the following threads to see if they will help.

[https://answers.launchpad.net/ubuntu/+question/7194](https://answers.launchpad.net/ubuntu/+question/7194)

[http://www.linuxforums.org/forum/ubuntu-help/76001-uninstall-windows-xp-install-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/76001-uninstall-windows-xp-install-ubuntu.html)

and also check out this thread that has been posted in the forums:

[http://ubuntuforums.org/showthread.php?t=1475809&highlight=removing+windows](http://ubuntuforums.org/showthread.php?t=1475809&highlight=removing+windows)


Tom

---

### Post by newport_j on 2010-05-07
When you boot into GParted, how do you know which option to select from GParted's own boot menu?

I want to delete the Windows XP partition, but how? I can't get past the boot menu choices.


Newport_j

---

### Post by cap10Ibraim on 2010-05-07
isn't there a manual option ? you can choose to destroy partitions

---

### Post by newport_j on 2010-05-07
I will see about manual option.

In regarding backing up files, by all means that is an excellent idea. I put a 700 MB CD in and move files and directories to to CD/DVD creator. 

It is an old computer and can only create CD's.

When I click write it says insert a CD with 1 GB space. I have ones (TDK) that are only 700 MB's. No 1 GB's are out there. How do I modify to take 700 MB CD's. 

Newport_j

---

### Post by clive littlewood on 2010-05-07
> **newport_j said:**
> I will see about manual option.

In regarding backing up files, by all means that is an excellent idea. I put a 700 MB CD in and move files and directories to to CD/DVD creator. 

It is an old computer and can only create CD's.

When I click write it says insert a CD with 1 GB space. I have ones (TDK) that are only 700 MB's. No 1 GB's are out there. How do I modify to take 700 MB CD's. 

Newport_j

You could try to compress the files then add to CD. (right click compress)

Then when you re-install extract the files (right click extract)


Hope this helps

Clive

---

### Post by newport_j on 2010-05-07
There is no right click compress option, but there is a right click archive. Is that it?

Newport_j

---

