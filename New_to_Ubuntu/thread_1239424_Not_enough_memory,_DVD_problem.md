---
title: "Not enough memory, DVD problem"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by RichardLi on 2009-08-13
Hi all, I'm new to Linux and Ubuntu so please use easy terminolgy. Thanks in advance.
 
For three days, I used the Live DVD (burned by myself with Infrarecorder, checked), and loved it. So yesterday, I went ahead and installed Ubuntu. 
 
All was fine, until time came to install Flash (for Youtube) - it said there was not enough memory! Strange... it then popped up with the security updates (I assume it is automatically checking), that I needed to install, also, not enough memory! The updates required ~300 mb, and according to the error it informed me I only had 100 mb, despite I had divded the Windows memory in half, half for Linux, half for Windows.
 
Looking on Google, people said you can resize the partition if you boot by Live DVD, and use qpartition - makes sense. So trying to boot to Live DVD, the screen froze! The DVD was spinning, but no movement on the screen. Okay, perhaps just a small problem... I forced the computer off via power button, and tryed it again, same problem! I once again forced the computer off, and this time I attempted to check the DVD for defects - same result!
 
If anyone can help with either resizing the partitions without Live DVD or what is wrong with the DVD, please let me know!
 
Info:
Laptop is Dell Inspiron 1525, 32 bit Vista (bad model, I might note, I do not recommend)
Ubuntu version 9.04 
Installed per instructions on Ubuntu website ([https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto))
 
Thanks!
 
Richard

---

### Post by Mark Phelps on 2009-08-13
First off, you're confusing memory with disk space.  You use partitioning tools to allocate disk space, not memory.

As an alternative to GParted, try Parted Magic.  It's available on the distrowatch.com webpage and I've read of situations where it worked when GParted did not.

---

### Post by raymondh on 2009-08-13
Richard,

```
df -h
```

from terminal will tell you size allocations and remaining space in/for your ubuntu install.

Use a liveCD and in live session, access and use Gparted to resize for you. Remember to make sure all pertinent partitions are unmounted.  Rt. click on partition and if presented with option to unmount, do so.  For swap, select swapoff.  

You can also download/burn the latest [gparted]("http://gparted.sourceforge.net/"). Good tool to have.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Good luck.  Back up your files.  There are no guarantees.

Raymond

---

### Post by RichardLi on 2009-08-13
Mark, thanks, you're right. Could I use Parted Magic during normal use of Ubuntu (not Live CD) since it would be changing the partitions? I read you can not use Qparted unless you were using Live session, which I have trouble with now.
 
Raymond, I recieve this
Filesystem Size Used Avail Use% Mounted on
/dev/sda6 2.3G 2.3G 0 100% / (<- Is this Linux?)
tmpfs 1003M 0 1003M 0% /lib/init/rw
varrun 1003M 96K 1002M 1% /var/run
varlock 1003M 0 1003M 0% /var/lock
udev 1003M 188K 1002M 1% /dev
tmpfs 1003M 508K 1002M 1% /dev/shm
lrm 1003M 2.4M 1000M 1%/lib/modules/2.6.28-11-generic/volat
ile
overflow 1.0M 16K 1008K 2% /tmp
/dev/sr0 699M 699M 0 100% /media/cdrom0
 
Can you help me understand this information?
As said in my first post, I cannot use Live CD/Live Session.
 
I might add, that all settings are gone (ie appearance, wireless, etc) as though I'm in Live Session even though I have installed and run the real Ubuntu now.
 
Thanks for the fast response.
 
Richard

---

### Post by raymondh on 2009-08-13
Yes, that arrow is your linux root (/) where your system files reside.

The 2.3GB install happens when we forget to use the slider or..... we did use the slider but something went wrong/different during the install that it defaulted to 2.3GB.  

Back up your vista files.

We need space.  See this [link]("http://ubuntuforums.org/showthread.php?t=1122670") (try the 5 minute guide or section J. Gain just a bit of space) then try to use the liveDVD (in live session) about resizing.

The liveDisc (and it's gparted) will do.  Better yet is a liveCD of gparted or partition magic.

Good luck.

---

### Post by RichardLi on 2009-08-13
Hi, thanks! I looked at the link, it is good, but I want more than "just a bit" because it looks like I will be using Linux a lot.
 
So there is apparently a problem with my Ubuntu Live Disk, which causes it to freeze if I choose anything on the boot screen, so I can't use qparted. However I happened to have a copy of openSuse and tryed that to see if it was an issue with my harddrive - it wasn't. And then I realized openSuse had YaST/Expert Partitioner, so can I use that instead of qparted? - and how? Thanks!
 
Richard

---

### Post by raymondh on 2009-08-14
> **RichardLi said:**
> Hi, thanks! I looked at the link, it is good, but I want more than "just a bit" because it looks like I will be using Linux a lot.
 
So there is apparently a problem with my Ubuntu Live Disk, which causes it to freeze if I choose anything on the boot screen, so I can't use qparted. However I happened to have a copy of openSuse and tryed that to see if it was an issue with my harddrive - it wasn't. And then I realized openSuse had YaST/Expert Partitioner, so can I use that instead of qparted? - and how? Thanks!
 
Richard

Richard,

I just re-read the thread.  

You can use whatever partition editor you choose.  Even Vista's.  I advocate gparted because that is what I am used to.  The goal is to size down from somewhere and use that space to size up Ubuntu.

I'm sorry, I do not know, nor have tried YaST.

For your reference:

[http://www.novell.com/documentation/sled11/sled11_deployment/?page=/documentation](http://www.novell.com/documentation/sled11/sled11_deployment/?page=/documentation)

Good luck.

---

### Post by RichardLi on 2009-08-14
Hi, thanks again. Do you know what's going on with my DVD? YaST feels difficult to use, so I might prefer qparted. Thanks for everything.
 
Richard

---

### Post by raymondh on 2009-08-14
> **RichardLi said:**
> Hi, thanks again. Do you know what's going on with my DVD? YaST feels difficult to use, so I might prefer qparted. Thanks for everything.
 
Richard

Free us some disk space. Even just a little bit.

Can't say what's going on with the DVD.  It could be a DVD turning bad or something with your DVD drive (dirty head, etc.), or even Ubuntu not mounting the cd drive.

Could you go into windows ..... download [CDBurnerXP]("http://cdburnerxp.se/") (or any free cd burner) ..... download [gparted]("http://gparted.sourceforge.net/") ..... burn iso image to a cd-r (as slow as possible) .... and then exit windows and try the newly burnt CD in ubuntu.  

If you are able to write/burn and then see it function in ubuntu, then you know your DVD is bad.  If able to write/burn but not run in ubuntu, then look towards Ubuntu.  If not able to write nor run, then probably the drive itself.

Good luck.

---

### Post by RichardLi on 2009-08-14
Alright I've booted successfully onto GParted Live. It looks easy enough to use, but I don't want to do anything mediocre. Could you provide some instruction on how to use it, which one to adjust? I see these partitions -
/dev/sda1 fat 16 DellUtility
/dev/sda2 ntfs Recovery
/dev/sda3 ntfs OS
/dev/sda4 extended
/dev/sda6 ext3
/dev/sda7 linux-swap
unallocated
/dev/sda5 fat32 Mediadirect
 
Looking at this tutorial: [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
I find it interesting I don't have a Windows partition?
 
Thanks!
 
Richard

---

### Post by raymondh on 2009-08-14
> **RichardLi said:**
> Alright I've booted successfully onto GParted Live. It looks easy enough to use, but I don't want to do anything mediocre. Could you provide some instruction on how to use it, which one to adjust? I see these partitions -
/dev/sda1 fat 16 DellUtility
/dev/sda2 ntfs Recovery
/dev/sda3 ntfs OS
/dev/sda4 extended
/dev/sda6 ext3
/dev/sda7 linux-swap
unallocated
/dev/sda5 fat32 Mediadirect
 
Looking at this tutorial: [http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
I find it interesting I don't have a Windows partition?
 
Thanks!
 
Richard

Sda3 is where windows resides.

Richard, can you post a screenshot of gparted's output.  It helps visualize.  Or, access a terminal (from the liveCD) and type/post back output of

```
fdisk -l
```

That'll show your current HD set-up.

1.  What is the unallocated space and how much?

You need to expand root. And you need to take space from somewhere. Ubuntu root (/)...sda6... is in a logical partition inside an extended (sda4) whch means we have to enlarge the extended partition first and grow root from there.

_Assuming there is no unallocated space right now ... or its' size is unuseable_:

Back up your files.

Booting from the liveCD and using gparted in a live session.  First make sure sda3, sda4, sda5 and probably sda6 are unmounted by rt. click on each partition and if given the option to unmount, do so.  Also, for swap (sda7), select swapoff. You will know it is mounted by either a key sign or you have a greyed-out option to resize.

1.  Click on the windows partition (sda3) and resize/shrink windows
2.  Click on the extended partition (sda4) to resize and grab slider to enlarge (to the left) to take up the space vacated by windows.
3.  Click on the root partition (sda6) and either:
- move the whole partition to the left border of the now enlarged extended and then, grab the right side and enlarge or,
- grab the left side and enlarge.
This all depends whether you have to move sda5 or not.  Cannot see exactly where it resides inside the extended without a visual output of gparted.
4.  Review and apply.  It will take a while.

Assuming the unallocated space has room (say 20GB or more), we'll have to do another method.

***Sometimes, it is better to cut losses (so to speak) and start all over again and re-install.  As it is a new installation, a re-installation can go faster as well as have less risks of moving data (as opposed to moving/enlarging).  Your choice.  I can also post a guide for your review if you so desire to re-install.***

Post back if you need clartifications or want to re-do.

Reading materials for you:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck.

---

