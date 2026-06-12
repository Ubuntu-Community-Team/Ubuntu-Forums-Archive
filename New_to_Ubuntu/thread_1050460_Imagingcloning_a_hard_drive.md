---
title: "Imaging/cloning a hard drive"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Oath on 2009-01-25
Heya

Very new to ubuntu and Linux/Unix as a whole, just got so fed up with 'are you sure you want to do that?' that I decided that it was some time for some real computing again!

So far it's all going well, but I have now come to a small hitch which I am sure if VERY basic.

I would like to copy one hard drive to a new blank (larger) drive, copying all files, programs and the windows (shameful I know) installation.

Neither drive is my primary drive with my installation of ubuntu on it.

I believe what I want to do is image the drive, and there a a lot of guides to do this when the drive your imaging is the one your using and have the OS on, but I don't need it that complicated! and I'm not yet confident enough with linux to know what bits of the process need modification.

I'm sure this is a simple thing, but help would be very much appreciated!

Thanks very much for your help.


P.S. I am using ubuntu 8.10

---

### Post by uidb4056 on 2009-01-25
You can try with Clonezilla at [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by drs305 on 2009-01-25
First, welcome to the ubuntu forums.

One app I use regularly is called partimage, which images all the contents of a partition but not the free space, making it much smaller. You have to run it with the partition(s) unmounted, so you need to use the ubuntu LiveCD, gparted CD, or a systemrescueCD. If you want to run it from the liveCD you will have to enable the *universe* repository in Synaptic or Software Sources and then download it. I'd recommend making a rescue CD just to have one on hand.

Here are two references on how to use partimage:
 
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")
 
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html]("http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html")

I regularly use it to restore my ubuntu partition but there is one caveat with using it for what you want to do.

There have been some issues with the way partimage restores the partition which might effect it's use in your situation. There have been posts indicating that when partimage restores an image to a larger partition it creates the new image but fails to release the rest of the free space in the partition. So if you restore 60GB partition to a new 100GB one, your system may not recognize the extra 40GB. I believe you can manipulate the partition table to regain the space, or it may not happen if you select copy instead of restore (I don't know). It would be good to do a search of the forums of the partimage site to learn more about this issue.

Another partition copier is Clonezilla. I haven't used it and don't know its capabilities but a quick search should provide some information on it.

---

### Post by mikechant on 2009-01-26
*So if you restore 60GB partition to a new 100GB one, your system may not recognize the extra 40GB. I believe you can manipulate the partition table to regain the space, or it may not happen if you select copy instead of restore (I don't know). *

If this is the case, the simplest thing to do might be to restore to the same partition size as the backup and then expand the partition using gparted. This would ensure the filesystem was grown properly into the extra space.

---

### Post by scotty2 on 2009-01-26
I used the instructions in the following link to clone a Windows disc on to a larger disc.  I performed the copy (dd) from an Ubuntu live cd.  Remarkable simple process and no problems encountered.

[http://www.justlinux.com/forum/showthread.php?threadid=149328](http://www.justlinux.com/forum/showthread.php?threadid=149328)

---

### Post by -kg- on 2009-01-26
All the above methods will work.  I have used [Clonezilla]("http://clonezilla.org/"), and it is very easy to use.  All the operations are fairly well automated and it should work for you.  Just follow the instructions on the website.

For a very good tutorial on using Partimage and Clonezilla, as well as SystemRescue Live CD, see:

[http://www.dedoimedo.com/computers/free_imaging_software.html]("http://www.dedoimedo.com/computers/free_imaging_software.html")

---

