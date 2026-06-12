---
title: "&quot;No root file system is defined&quot;"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Chapati on 2009-02-10
Hey everyone,

I installed Ubuntu 8.10 onto a flash drive earlier, and it boots up perfectly. I am currently writing this thread that you are reading from inside ubuntu in fact.

However, I get a problem when I try to install the system. The installer gets to step 4 and I can't go on. The pic below shows what happens when I click the Forward button.

[IMG]http://img23.imageshack.us/img23/9172/errorau0.png[/IMG]

Any help would be appreciated.

---

### Post by easybake on 2009-02-10
When you are installing you have to tell the program where to put the files. 

Under the Manual partitioning option,
Select your blank partition and you have to choose "/" from the drop down menu. / = root. You are probably going to need to create a swap area too. Just create a small 2 gig partition. Select the 2 gig partition and choose swap space from the drop down menu.

---

### Post by Chapati on 2009-02-11
Ok, I managed to get it working.

However, in the process, I either;

A) created a partition over the previous Windows partition.
B) completely erased the entire contents of the hard drive.

Hrmm, is there any way to tell which one?

---

### Post by khaos88 on 2009-02-11
Hey all.. where is "Manual partitioning option"

---

### Post by easybake on 2009-02-11
> **Chapati said:**
> Ok, I managed to get it working.

However, in the process, I either;

A) created a partition over the previous Windows partition.
B) completely erased the entire contents of the hard drive.

Hrmm, is there any way to tell which one?

It's possible you could have done both.
If you created a partition over the windows partition then you most likely will see a very small amount of used space for that partition. A fresh full Ubuntu install only takes about 2.5 gigs. Windows takes around 4 gigs of space. Ubuntu installs with Ext3 format while the windows partition is going to be NTFS.

If you completely erased the harddrive, partitions and all, then you should only see one large harddrive section in ext3 format.

> **khaos88 said:**
> Hey all.. where is "Manual partitioning option" 

During the install process... on the step that has the options "use guided, use entire disk, and manual" those aren't the exact words but they are close. I think it's around step 3 or 4.

---

### Post by feral1939 on 2009-02-12
> **easybake said:**
> When you are installing you have to tell the program where to put the files. 

Under the Manual partitioning option,
Select your blank partition and you have to choose "/" from the drop down menu. / = root. You are probably going to need to create a swap area too. Just create a small 2 gig partition. Select the 2 gig partition and choose swap space from the drop down menu.

Hi,  I am having the same root problem as "chapati" and I tried your solution but still get the "No root file system" window.  I don't know what to do next to try to proceed with the installation but for a person who is not very computer savvy,  I am getting that frustrated that I feel like chucking the Ubuntu CD in the trash and putting up with the rubbishy Vista OS. It would be a great help to me and I daresay some others if a comprehensive pdf of installation instructions was made and perhaps there would be a lot less questions posted. BTW, I tried to install it on my 'D' drive but the partitioner put it on my 'C' drive, huh???

---

