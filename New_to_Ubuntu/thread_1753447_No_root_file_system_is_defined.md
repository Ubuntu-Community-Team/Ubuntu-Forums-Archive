---
title: "No root file system is defined"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by jrnsr on 2011-05-09
Ubuntu 11.04 on new HP g6 with AMD 64. I can't abandon Windows because of 3D CAD programs. I'd like to install dual operating systems leaving Win7 and prefer not going WUBI under Windows. There's a new 350 Gig hard drive and probably won't use 1/10th of it, so could easily allocate 100Gb to Ubuntu.  Boots off CD but hits installation error message NO ROOT FILE SYSTEM IS DEFINED.  I've read other writeups on this but am very reluctant to mess with partitions for fear of wiping out Windows files.

---

### Post by Hedgehog1 on 2011-05-09
Here are the basic steps for manually installing Ubuntu as a dual boot with Windows.

 ** Please size your partitions and select the drive letters that fit your system. In your case, the second 350gig drive is your likely install drive, so your partitions may be /dev/sdb2, /dev/sdb3 & /dev/sdb4 (instead of /dev/sda5, /dev/sda6 & /dev/sda7 as shown in the pictures below).** 


Using gparted from the LiveCD/LiveUSB, create 3 partitions your drive where you want to install Ubuntu:

1) ext4 '/' (20-30 gigs)
2) Linux swap  (Swap size is 'Size of RAM' + 10%)
3) ext4 '/home' (as much disk space as you can spare)

Here is what the allocation screen looks like when installing:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]



***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-09
> **jrnsr said:**
> Ubuntu 11.04 on new HP g6 with AMD 64. I can't abandon Windows because of 3D CAD programs. I'd like to install dual operating systems leaving Win7 and prefer not going WUBI under Windows. There's a new 350 Gig hard drive and probably won't use 1/10th of it, so could easily allocate 100Gb to Ubuntu.  Boots off CD but hits installation error message NO ROOT FILE SYSTEM IS DEFINED.  I've read other writeups on this but am very reluctant to mess with partitions for fear of wiping out Windows files.

The second picture in the above post is where the root partition is defined, by the way:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

***The Hedge***

:KS

---

### Post by jrnsr on 2011-05-09
Thank you very much for the step by step!

---

### Post by Closed Account on 2011-10-13
Thanks Hedgehog1! You are a life-saver.

---

### Post by liviusbr on 2012-03-27
Hi, 

Having slightly different issue : I already have windows 7 installed with 5 partitions.
One is dedicated just for ubuntu. Is there any chance that I can install ubuntu on this one without shrinking/repartitioning ?

Thanks,

Liviu

---

### Post by saidii89 on 2012-05-15
a lot of users faced such problem and the solution to it is pretty simple
 
make sure that the partition file system [you wish to install linux, ubunto or backrack on it] is ext4, ext3 or ext2 [not fat32 or ntfs]
 
then mount "/" on it, how? easy: 
1- on the installation process press [change] on the partition you wish to use
 
2- make sure [do not use this partition] scroll is not chosen, scroll to ext4, ext3 or ext2
 
3- and on "mount" field write "/"
 
4- when clicking ok then next a message will appear saying something like [swap area was not defined, do you wish to continue or choose a swap area? because bla bla bla..], click "ok" and continue or click "go back" and choose another partition and click change, on the file system scroll choose [swap] and click ok and next
 
this will solve both "no root file system is defined" and the "swap area" message, if you still get the swap area message then on step 4 mount "/swap" to the partition
 
**AND THIS SOLVES IT!**
 
every time anyone need solutions don't hesitate to search for help
 
ask me if you need something and I can help I will do it, I don't log to forums a lot, I found this thread while searching on google and I copied this answer to all the threads with the same problem, so If you need contact here it goes ->

 [http://www.twitter.com/saidii89](http://www.twitter.com/saidii89)
 [http://www.facebook.com/saidii89](http://www.facebook.com/saidii89)
 [http://www.formsrping.me/saidii89](http://www.formsrping.me/saidii89)
 [http://www.saidi-theory.blogspot.com]("http://www.saidi-theory.blogspot.com/")
 
brought to you by Sa'eed Awad
[Saidi Theory Solutions] by Sa'eed Awad

---

