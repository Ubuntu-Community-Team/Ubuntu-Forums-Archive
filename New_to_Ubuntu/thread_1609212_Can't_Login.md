---
title: "Can't Login"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by livelong on 2010-10-30
Have been receiving message at startup that the disk has only few free MBs left now free space on my ubuntu 9.10 patrition is 0 and the system has refused to login. Can any one tell me which directories should be moved or deleted using Live CD to free up some space. I already used autoclean command and synaptic package manager to clean extra/broken repositories while I was able to login.
 
Any suggesstions will be highly appreciated.

---

### Post by ubhi on 2010-10-30
Boot from live CD
Mount your Ubuntu Partition
then check for space using 
#df -h
& then remove unwanted files from maximum used partition

---

### Post by livelong on 2010-10-30
Thank for reply,
Is it a terminal command you talking about? and how can I know that the files I am deleting are not system files. I am new to ubuntu so sorry if am asking too much.

---

### Post by ubhi on 2010-10-30
first of all just check the output of df -h command 
then go to mounted partition
& then check if you have some unwanted file saved by you not by system,
like in your /home/user/Desktop or /home/user/Document directories
and if you can Login then you can follow mention guide as well

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by livelong on 2010-10-30
what should I expect after the df -h command, I mean would it show the free space available on filesystem.??

---

### Post by ubhi on 2010-11-03
you always ask question
df -h
give you the free & used space on your disk...

---

