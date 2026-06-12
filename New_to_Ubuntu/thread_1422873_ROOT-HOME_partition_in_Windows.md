---
title: "ROOT-HOME partition in Windows?"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by paker on 2010-03-05
Like most of you, I always partition my hard disk to Root and Home, and install next revision in Root. I have a spare hard disk on which I want to install Windows XP. Can I do the same Root-Home partition in Windows XP Professional?

Next question: Can I keep both hard disks connected? ubuntu will be daily use. Windows XP only when I need to. How do I do this?

Thanks.

---

### Post by sandyd on 2010-03-05
> **paker said:**
> Like most of you, I always partition my hard disk to Root and Home, and install next revision in Root. I have a spare hard disk on which I want to install Windows XP. 

Can I do the same Root-Home partition in Windows XP Professional?
**yes, if your saying that you want a seperate C:\Documents and Settings\Username partition.**

Next question: Can I keep both hard disks connected? ubuntu will be daily use. Windows XP only when I need to. How do I do this?
**make one of them a slave drive and keep the other as a master.**

Thanks.
ive never tried it, but you can format the partition you want to use with ntfs.
Then, using a ubuntu livecd, copy the files over to the new partition.
Windows supports symbolic links (just as ubuntu does).
Create a symbolic link over from C:\Documents and Settings\Username to the drive letter of your home (windows) partition.
In winxp, you use linkd (command line) to create symbolic links.

---

### Post by uRock on 2010-03-05
Any time I install Windows, I make a 15gig partition for the OS then store everything in a second partition. If Windows crashes so hard that it has to be reinstalled or if you need to clean install a newer version, you don't have to worry as much about losing data. Backups are still my friend though.

---

