---
title: "Duel boot file acess"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by pinky117x on 2010-04-21
Hello I just recently made my computer a duel boot between ubutu and windows 7. I was looking through my hard drive on ubutu and I could see all my files from my other partition but I could only look at pictures not play videos. I would like to be able to access my videos wihtout having to restart the whole computer and go to my other operating system.If you could help that would be much appreciated.:confused:

---

### Post by -humanaut- on 2010-04-21
You need to change the permissions on the windows partition hit alt-f2 gksu nautilus then right click and change the permissions to Read & Write & Execute.

---

### Post by oldfred on 2010-04-21
Did you install the extras to allow playing videos?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Or is it permissions but with NTFS you cannot change them except when you mount the partition:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

