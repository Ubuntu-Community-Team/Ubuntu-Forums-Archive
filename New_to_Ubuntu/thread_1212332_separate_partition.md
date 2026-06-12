---
title: "separate partition"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by dbquick on 2009-07-13
I have a drive with a c partition for windows and a f partition I just did a reformat on.  I have vista on my c partition and want to put ubuntu 9.04 on my f partition.   What will happen when I put my ubuntu intall in?  Will it give me the option to put ubuntu on my f drive, put in a dual boot scenario, so it won't mess up vista?  Thank you in advance.

---

### Post by 73ckn797 on 2009-07-13
The install will see the Windows partition and since you have an unused partition it should ask whether you want to install there. Any choices will be yours to make. It will not show up under Ubuntu as drive "F" unless that is the label you have given it. If the partition is the only other one on the disk and if you have only a single hard drive it typically will show as:
sda1 (Windows partition) and sda2 (the free partition). The installation will create a smaller partition for a swap space. The install will format the partition as ext3 but you can designate others if you want. You should go with the recommended format the install gives.

---

### Post by bodhi.zazen on 2009-07-13
Yes you will be able to dual boot 

Just be sure to understand Linux partitions first and do not install into the wrong partition.

See :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by camaron1 on 2009-07-13
Remember to choose manual install though

---

### Post by dbquick on 2009-07-13
Thanks you guys  You have sure cleared things up.  when I first put the disc in.. I ran it so it wouldn't hurt windows and I am going to like it.  I've gone as far as I want to go with windows, and I am really good at reinstalling it.  Thanks for your help.

---

### Post by renbla on 2009-07-13
> **dbquick said:**
> I have a drive with a c partition for windows and a f partition I just did a reformat on.  I have vista on my c partition and want to put ubuntu 9.04 on my f partition.   What will happen when I put my ubuntu intall in?  Will it give me the option to put ubuntu on my f drive, put in a dual boot scenario, so it won't mess up vista?  Thank you in advance.


Normally for my XP, YES ;)

---

### Post by Bartender on 2009-07-13
The OP would not need to use manual install if he has an empty partition that Ubuntu can recognize and use.  "Guided" would work just fine for a basic installation.  By "basic" I mean no separate /home partition.  I believe that Ubuntu would create an extended partition, then two logical partitions inside the extended partition.  One for the OS, and one for swap.  That means the new logical partitions would be recognized as sda5 and sda6.

---

