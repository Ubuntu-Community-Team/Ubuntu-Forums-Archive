---
title: "MountPointManager"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Dog walker on 2009-06-27
I'm working may way through a fresh dual-boot install of WinXP-HE and Ubuntu Jaunty and keep coming across a problem, could anyone help please?.

I have successfully installed WinXP and Ubuntu and now I am trying to rearrange my data and applications on the new partitioning scheme that I've created.

The problem I am having is that when trying to copy or move various files I'm getting this Windows error... 

***"Cannot copy MountPointManagerRemoteDatabase: Access is denied"***

From searching, I think this is something to do with the reassignment of drive letters when I re-partitioned for Ubuntu.

My PC has two internal hard drives, two external hard drives, two internal CD/DVD drives plus a 5 device multicard reader. 

Can anyone, please, tell me how to overcome this problem?

Thanks.

---

### Post by Hobgoblin on 2009-06-27
> **Dog walker said:**
> 

From searching, I think this is something to do with the reassignment of drive letters when I re-partitioned for Ubuntu.


Why would the drive letters be reassigned when you installed Ubuntu?

The best way if starting from scratch is to leave some unpartitioned space when installing Windows for your Ubuntu install.

---

### Post by Dog walker on 2009-06-27
> **Hobgoblin said:**
> Why would the drive letters be reassigned when you installed Ubuntu?

The best way if starting from scratch is to leave some unpartitioned space when installing Windows for your Ubuntu install.

One reason was to make the drive assignment more logical and to eventually allow for complete migration to Ubuntu. Another reason was to create a spare NTFS partition where I could initially share data between the two OS's. Finally amongst all the preparation I needed to move/copy data to my backup drive prior to eventually deciding on/creating the best (percieved!) scheme.

I also made an idiotic mistake as per this thread!!!:-

[http://ubuntuforums.org/showthread.php?t=1196628](http://ubuntuforums.org/showthread.php?t=1196628)

---

### Post by Hobgoblin on 2009-06-27
> **Dog walker said:**
> 
I also made an idiotic mistake as per this thread!!!:-

[http://ubuntuforums.org/showthread.php?t=1196628](http://ubuntuforums.org/showthread.php?t=1196628)

OK, I would start again then.

The Ubuntu partitions do not need drive letters in Windows.

Backup your data then boot from the Ubuntu CD.

Delete all partitions using the partition manager. (remember to click apply).

Boot from the Windows CD and install Windows to the C drive, leaving some free space for Ubuntu.

Once Windows is installed then install Ubuntu.

If you want the complicated partitioning you have gone for then do that during the Ubuntu install process, for most people one partition for / and one for /home is sufficient.

---

### Post by Dog walker on 2009-06-27
> **Hobgoblin said:**
> OK, I would start again then.

The Ubuntu partitions do not need drive letters in Windows.

Backup your data then boot from the Ubuntu CD.

Delete all partitions using the partition manager. (remember to click apply).

Boot from the Windows CD and install Windows to the C drive, leaving some free space for Ubuntu.

Once Windows is installed then install Ubuntu.

If you want the complicated partitioning you have gone for then do that during the Ubuntu install process, for most people one partition for / and one for /home is sufficient.

Thanks Hobgoblin,

I've already resolved the issue in that previous thread, I only referenced to it as one of the reasons to answer the question of why I had created a different partition structure. This is a seperate issue.

---

