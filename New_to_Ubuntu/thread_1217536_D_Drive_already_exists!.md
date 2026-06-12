---
title: "D Drive already exists!"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Rob.T on 2009-07-19
Hi ... I am new to the forum, and I am a complete Linux newbie.  I decided to install Ubuntu 9.04 next to my operating system so I could dual-boot.  It did not work, and the reason seems to be that it attempted to create a new D partition, and I already have a D drive on another disk.  After it finished, there was a new partition on the disk containing the D drive.  Changing the letter on the D drive would be the simplest solution, but I have a lot of stuff on other partitions that are linked to files on that drive, so that is not an option.  Does anyone have any suggestions?
Thanks!!

---

### Post by ugm6hr on 2009-07-19
Did you install a true dual-boot or with Wubi inside Windows?

If the former, you should be able to use fs-driver to relabel the Ubuntu drive to Z: (or something else out of the way).

[www.fs-driver.org/](www.fs-driver.org/)

---

### Post by Rob.T on 2009-07-19
Hi ... I am trying to install a true dual boot, but I can't cause Ubuntu sets up on my D drive.  I want to create a new partition on the disk containing the C: Drive.

I have downloaded fs-driver.  Could I impose on you to (briefly) walk me through the installation steps?  E.G. ... do I install Ubuntu 1st or fs-driver 1st?

Thanks

---

### Post by lavinog on 2009-07-19
Is the D drive a 2nd physical drive?
The D letter is just how windows labels partitions. Linux doesn't care if a drive is the C, D,E...etc

Can you explain in more detail what part isn't working?
Is the grub boot menu not showing?

---

### Post by ugm6hr on 2009-07-20
I'm confused too.  It sounded like you had 1 HD with partitions, but now it sounds like you have 2 HDs with partitions.

Boot Ubuntu and post the output of:
```
sudo fdisk -l
```

Then let us know what you want the HD partitions to look like without using confusing terms like D drive, which is merely a label for a partition, not a HD.
i.e. use Linux naming structure. e.g. partition sda1 on HD sda etc

As for fs-driver, just install it in Windows.  It is pretty self-explanatory when you run it. It allows you to access the Ubuntu partition from Windows, and allows you to select a drive letter manually (e.g. Z: or U: for Ubuntu), which would free up the letter D: to be assigned to your previous "D drive")

---

### Post by Rob.T on 2009-07-20
Hi ... sorry if I wasn't clear.  The D Drive on my computer is actually a separate disk.  One disk is the C drive (with the operating system) and the other is the D drive.  When I tried to install Ubuntu before, it stuck the installation at the end of the disk with the D drive.  When I booted up, no grub boot menu.
Cheers, Rob

---

### Post by ugm6hr on 2009-07-20
So where do you want to install Ubuntu?  Or is it already installed?

---

### Post by Rob.T on 2009-07-20
Hi ... I have not had a chance to try a reinstall yet.  I would like to place it on the same disk as my operating system - the C drive.
Thanks

---

### Post by ugm6hr on 2009-07-21
Have you already created a partition / spac on HD for it?

What version of Windows do you have?

Overall, I would recommend resizing the Windows partition (from GParted if XP; from Vista if Vista), then using GParted to create appropriate partition(s), then using the manual install option to select where to install to.

It is helpful to know how much HD space you intend to give to Ubuntu to decide how to plan partitions.  Also, how much RAM do you have?

---

### Post by Rob.T on 2009-07-21
Hi
I have not created a partition on the C disk yet.  I had planned to allot around 30 Gigs to the Ubuntu partition.  I have 2 Gig of RAM.
Thanks!!

---

### Post by 3rdalbum on 2009-07-21
Okay, well, Ubuntu doesn't use Windows' "drive letters" naming scheme; so your idea that "it tried to create a D drive but I already have a D drive" is not correct.

The Ubuntu installer should give you the option to resize the partition on the drive that you know as the C drive. If it doesn't, then it's possible that the drive has files scattered all over it, so much so that the last couple of gigabytes actually contain files. If you defragment the disk from within Windows, you should get the option in the Ubuntu installer to resize the partition on the "C drive".

---

### Post by lavinog on 2009-07-21
> **3rdalbum said:**
> 
The Ubuntu installer should give you the option to resize the partition on the drive that you know as the C drive.

like ugm6hr mentioned, you should really use vista's partition manager to resize the partition if it is a vista partition. Otherwise you could mess up your vista install.

---

### Post by egalvan on 2009-07-21
> **ugm6hr said:**
> 
If the former, you should be able to use [COLOR="Red"]fs-driver[/COLOR] to relabel the Ubuntu drive to Z: (or something else out of the way).

[**www.fs-driver.org/**](**www.fs-driver.org/**)


Remember the following limitation...[www.fs-driver.org/](www.fs-driver.org/)
this causes Windows to ask "drive not formated... format drive?"

(quote is from the fs-driver web-site)
[B] Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. [/B]

---

### Post by Rob.T on 2009-07-25
Okay ... first of all, sorry that I keep talking "Windows".  I realize the terms I use are not appropriate for a Linux OS ... unfortunately at this point they are the only ones I know.  When (if) I get Ubuntu installed, I will be able to use the appropriate terms.
 
I went through the installation process again, and everything seemed to go fine.  I successfully partitioned the disk containing the XP OS, and Ubuntu seemed to insall OK.  But as the computer was shutting down, I got a whole ,list of error messages that went by too fast for me to read, and when the computer restarted, it went directly into Windows ... no grub boot menu.  According to the Computer Manager in Windows Administrator, the disk has been successfuly partitioned and the other partitions are Linux.
 
Oh yeah ... and when I installed fs-driver, it seemed to install okay, but it is nowhere to be found on my system.
 
The disk has recently been defragged, so that should not be an issue.
 
Sorry .. I know I must be doing something really simple wrong!
 
Thanks!!

---

### Post by lavinog on 2009-07-25
Did you install ubuntu on the master or the slave drive?
In otherwords: If you pull the 2nd hd (the D drive) out of your computer, should you be able to boot into both windows and ubuntu?

---

### Post by Rob.T on 2009-07-25
I installed it on the master ... its on the same disk as XP.  If this was the only disk in the computer, I should be able to boot both.

---

### Post by lavinog on 2009-07-25
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

boot from the live cd
open a terminal
type:
```

sudo grub

```
then you should have a grub> prompt
```

find /boot/grub/stage1

```
It should return something like root(hd0,#) or (hd0)
Use whatever it says in the next line:
```

root (hd0,#)

```
then the next line writes grub to the mbr:
Note: The instructions say to use (hd0,#), but I find it doesn't work with dualbooting with XP.
```

setup (hd0)
quit

```

After that reboot and see if it works.
Make sure you watch for it, by default you only get a 2 second message saying press ESC to change boot.

---

### Post by animesh1988 on 2010-02-17
Hi,

I am new to Ubuntu, I have it installed on a 55 GB drive and windows on a 20 GB drive, I was wondering how do I use the remaining space on the D drive (apart from the Ubuntu install).. Please reply asap!

Thanks 
Animesh

---

### Post by lavinog on 2010-02-17
> **animesh1988 said:**
> Hi,

I am new to Ubuntu, I have it installed on a 55 GB drive and windows on a 20 GB drive, I was wondering how do I use the remaining space on the D drive (apart from the Ubuntu install).. Please reply asap!

Thanks 
Animesh

Please start a new thread.
By hijacking a thread you are only going to get confusing answers as users try to answer the OP's question and not yours.

When you start a thread, please be specific when describing your issue.  Which drive is the D drive.
You can resize partitions with gparted using the live cd.

---

