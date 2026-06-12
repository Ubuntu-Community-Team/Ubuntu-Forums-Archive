---
title: "Reinstalling ubuntu as a second system"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Samemax on 2010-07-19
Because of some problems I want to reinstall ubuntu. Now I have windows, ubuntu jaunty and koala in my boot-menu. I'd like to keep windows but to delate jaunty and koala and instead of them install lynx. I assume during the installation, I'm going to be asked if I want to replace / overwrite the partitions used now by the two former versions of ubuntu without doing something to the windows-partition. Am I right? Something more I should know?
Thank you very much for answering.

---

### Post by ajgreeny on 2010-07-19
You are more or less right.

When you get to the partitioning part of installing, choose manual partitioning, I can't remember the actual wording of the option, but it will be pretty obvious.  That will take you to a tabular version of your current partitions.  Just choose the old ubuntu partitions and delete them all to make unallocated space, then install ubuntu into that space.

It may actually be easier to use gparted from the live CD and delete your old partitions that way first, then you can either make new partitions for root, swap and /home, or just let the installer use the space without partitioning ahead of the install.  Once you have a separate /home, you will see what a great advantage it is when you need to reinstall next time, so I strongly recommend it.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Backup everything important to you first.

---

### Post by Samemax on 2010-08-01
Thank you very much for your help!!!
Greetings!

---

