---
title: "Beginner makes a big OOPS!!"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by ttandaj on 2010-03-22
Ok, so my 15 yo son decides to load Ubuntu onto his secondary drive allowing for a dual boot option. Unfortunately, he accidentally loads it onto his primary drive instead. Problem is, he now cannot access the windows files since the new os created a new file format...I think? 

Anyway, does anyone know of a way to recover those windows files? My son has stuff on there from when he was pretty young, and we would really hate to lose everything. Thanks!!--Terri

---

### Post by Kenny_Larsen on 2010-03-22
Hi,

Unfortunately if he has re-partitioned the drive and installed ubuntu over it then the data is almost certainly all lost. 

Wait for someone else more knowledgeable to confirm it before you do anything (including using the machine).

Although it is no help now, it's often the hard reminder we all need to back-up everything regularly.

Kenny

---

### Post by Calash on 2010-03-22
If he overwrote the drive there is nothing that can be done.  

Best way to tell is to type the following command into the terminal (Applications-Accessories->Terminal)

sudo fdisk -l

It will ask you for a password.  This is the password of the account you are on in Ubuntu.  Just type it, you will not see any feedback until you press the Enter key.  You should get a bunch of information back.  Use the mouse to highlight all the lines, then Right-Click and select Copy.  Paste the information here and we may be able to tell you more about what is going on.


The output will be a listing of all the partitions on your computer. With luck one of them will say NTFS or FAT...that may mean the data was not overwritten, but moved aside.

---

### Post by dyingsun on 2010-03-22
That IS a big oops!

If your son has installed it onto the primary drive, it is *possible* that the installation has taken over a portion of the free space on that drive. Calash's fdisk command should reveal that. Which *could* mean that the Win partition is still, more or less, ok. The problem is fragmentation - if the disk was not defragged under Windows before installing Ubuntu, you could come up with some errors.

It *may* be possible to recover some files, but your actual Win install is probably cactus.

However if he has overwritten the whole partition, then the files will probably be unrecoverable.


The best option might be to farewell the Windows installation, and just let Ubuntu have its wicked way with your whole system!

---

### Post by Jerry N on 2010-03-22
No sweat - just restore your files from your backup.  You do have backups of those files don't you?

Jerry

---

### Post by TriBlox6432 on 2010-03-22
:popcorn:

If they had backup, they wouldn't be asking.  

I never backed up any of my info until I lost 6 years of school work and pictures.  Now I always back up to an external drive and to the cloud :p

---

### Post by halitech on 2010-03-22
before you do anything else SHUT DOWN THE SYSTEM!

the more you do on the system, the less likely you are going to be able to recover anything. Use another computer to download the desktop cd unless that was what your son used to do the install. Once downloaded (if needed) burn and boot from the desktop/Live cd. 

Once the Live cd has loaded, use Synaptic to install testdisk and use it to scan the drive. If anything is recoverable, testdisk should find it. If testdisk doesn't find anything then the data is gone.

---

### Post by k3lt01 on 2010-03-22
> **dyingsun said:**
> It *may* be possible to recover some files, but your actual Win install is probably cactus.I said that once and another Aussie had to translate it. Cactus is Strine (Aussie English) for no good.

---

### Post by Calash on 2010-03-22
> **halitech said:**
> before you do anything else SHUT DOWN THE SYSTEM!

the more you do on the system, the less likely you are going to be able to recover anything. Use another computer to download the desktop cd unless that was what your son used to do the install. Once downloaded (if needed) burn and boot from the desktop/Live cd. 

Once the Live cd has loaded, use Synaptic to install testdisk and use it to scan the drive. If anything is recoverable, testdisk should find it. If testdisk doesn't find anything then the data is gone.


A good idea, but we need to know what drive has been altered and what remains.  Will fdisk run from the LiveCD with valid results??  Been a while since I tried that.

---

### Post by halitech on 2010-03-22
> **Calash said:**
> A good idea, but we need to know what drive has been altered and what remains.  Will fdisk run from the LiveCD with valid results??  Been a while since I tried that.

yes, sudo fdisk -l will list all drives and partitions wither they are mounted or not.

---

### Post by asmoore82 on 2010-03-22
Some, if not all, of the files are definitely still there and retrievable.
But **for best results you must shut down the machine immediately**!!

What you need is a *"data carving"* utility.
You have to run it on the drive but from another OS on a 2nd drive.

A quick search of the Ubuntu Repos turns up a program called `scalpel`
I've never used this tool before myself,
but I have had success with this on several occasions: [http://www.restorer2000.com/](http://www.restorer2000.com/)

---

### Post by Calash on 2010-03-23
> **halitech said:**
> yes, sudo fdisk -l will list all drives and partitions wither they are mounted or not.

Bah,,,I should have known that.  Not sure what I was thinking yesterday.  Thank you for the correction.

To the OP, as noted boot into the LiveCD and then run the command I listed to show us the output.  From there testdisk will be the next step provided the drive has actually been overwritten.

No guarantees here, but it is the best chance you have to get the data back.

---

