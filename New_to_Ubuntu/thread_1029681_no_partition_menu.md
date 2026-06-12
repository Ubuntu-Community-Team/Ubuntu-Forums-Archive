---
title: "no partition menu"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by poisondart on 2009-01-03
I am trying to install ubuntu that I bought from Best Buy.  It was going OK after I clicked the Install icon until step 4.  I got a notice that "no file system is defined, please correct this from the partition menu".  This is an older computer(2003) that had a bad hard drive, so I put a new one in that was completely empty.  I get no partition menu, no option to "guided--use entire disk or resize master partition" HELP, I can't get past step 4, and I really want to try linux.:confused.

---

### Post by kestrel1 on 2009-01-03
Try booting up the live CD & use System - Administration - Partition Editor or open a terminal & type:
```
sudo gparted
```
see if you get a result.
Is the new HD seen in the BIOS?

---

### Post by ash369 on 2009-01-03
Hey are you creating a SWAP partition?

If not you need to create one it should be about x2 the amount of your RAM.

---

### Post by Michael.Godawski on 2009-01-03
hi,

I assume you have inserted the new drive correctly?

I would try out the application gparted to see if the drive is recognized. It should be on the Live CD (I guess somewhere in the System section, do not remember quite well now)
or you can download it from here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Elfy on 2009-01-03
Use the manual option to create your partitions.

You need at least 1 linux and 1 linux swap partition. YOu could though make a /home partition as well - could be useful if you need to reinstall.

You don't say how big the drive is nor how much swap you have so it's hard to guess at partition sizes. 

But at a guess I would do

linux (ubuntu defaults to ext3) - 12GB
linux swap - assuming you don't want to hibernate/suspend and RAM is greater than 1GB - 512Mb linux-swap
linux - remainder of drive

But if the drive is not very big forego the /home

You need to give 2 of these mountpoints in the edit partition menu

the 12Gb partition - mountpoint of /
the other linux partition mountpoint of /home
swap will take care of itself.

Alternatively you can use the partition editor in the system admin menu to do the same thing before starting the install and then just deal with the mountpoints during the install procedure.


Edit - check that the jumpers are set correctly on the hdd - and that it is recognised in BIOS

---

### Post by poisondart on 2009-01-03
It's an 80GB hard drive, and I have no idea how to partition it. I downloaded gparted, but don't what to do with it, as I still get the same message. Obviously I installed the hard drive correctly, or I would not be talking to you on this computer.  I just need to figure out how to get to the partition menu so I can define a root file system.

---

### Post by Elfy on 2009-01-04
> **poisondart said:**
> It's an 80GB hard drive, and I have no idea how to partition it. I downloaded gparted, but don't what to do with it, as I still get the same message. Obviously I installed the hard drive correctly, or I would not be talking to you on this computer.  I just need to figure out how to get to the partition menu so I can define a root file system.

Reading you first post it seemed to at least 2 of us that the drive wasn't installed correctly - we have no way of knowing whether you're posting from the pc which has a problem.

What OS does it have at the moment that you are able to post here - is it windows? How many hdd's does the machine have installed?

Boot the livecd and opena terminal from the Apps/Accessories menu, paste this command in and then paste the output to a new post here please.

[code]sudo fdisk -l[code]

If you are running windows then how much space to do you want to use for ubuntu?

---

### Post by kestrel1 on 2009-01-04
If the drive is installed correctly you shouldn't have any problems installing Ubuntu, as it should be recognised by Gparted.

---

