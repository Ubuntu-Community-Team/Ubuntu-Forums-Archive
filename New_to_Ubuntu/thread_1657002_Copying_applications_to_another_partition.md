---
title: "Copying applications to another partition"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by bjanzen on 2010-12-31
Hi guys, i'm relatively new to ubuntu, i was just wondering which directory has all the applications, looking to move it to a seperate partition and automount with fstab. I've found programs in /usr/bin /bin and /sbin, any guidance would be appreciated thanks! First post on your wonderful forum.

---

### Post by cariboo on 2010-12-31
If you are going to move all the applications to a seperate partiton, I would suggest moving the complete /usr directory, as all the man pages, libraries and documentation are located in that directory. I wouldn't bother moving /bin and /sbin to seperate partitions, because on my system, the two directories take up less than 15Mb of hard drive space. I would suggest a minimum of 4Gb for the /usr partition just in case.

---

### Post by iShurtugal on 2010-12-31
I completely backed up my system to new partitions for a new install and this, [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving), came in very helpful. Just do what It says, but substitute home for usr.

---

### Post by bjanzen on 2010-12-31
Would it be possible to have /home along with /usr on this partition. I have /home on it already, it is ntfs. Thanks for the quick replies.

---

