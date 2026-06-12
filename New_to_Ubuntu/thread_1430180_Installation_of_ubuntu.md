---
title: "Installation of ubuntu"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by msidhard on 2010-03-15
I have 80gb internal hard disk . It has two drives c:,d:. Both are 40gb each. I have windows xp in c drive. And my important documents in d drive. I want to install ubuntu in dual boot  with xp. I have a idea to delete the d drive and make it in to two partitions. And i want to install ubuntu in one drive. And leave other as common between xp. If i do it the new common partition i created , wont be seen in windows. I want the new partition which i create while installation of ubuntu, should be seen and accessed through windows without any problem

---

### Post by finku on 2010-03-15
Although I don't like this much, you might like to try out [http://wubi-installer.org/](http://wubi-installer.org/) should be easier for you to achieve what you need using that tool without effecting your current installation.

---

### Post by overlord.gaurav on 2010-03-15
Or you can make the two partitions...one on which you install ubuntu and leave the other one as it is. Once when you are on ubuntu you can install 'gparted' and format the leftover space as NTFS, which you'll be able to access from both...windows and ubuntu.

---

### Post by CompyTheInsane on 2010-03-15
If you intend to install Ubuntu on an ext3 or ext2 partition instead of ext4, you can consider checking out the [ext2fsd driver](http://www.ext2fsd.com/) for Windows XP if you want to be able to access the Ubuntu partition from within XP.

---

### Post by msidhard on 2010-03-15
Thanks guys. But how do i activate the newly created partition other than one in which i installed ubuntu in windows. Like using partition magic or some thing else

---

