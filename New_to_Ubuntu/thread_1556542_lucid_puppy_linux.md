---
title: "lucid puppy linux"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by DarinB on 2010-08-19
Lucid puppy linux full hard drive install on a sony laptop. hangs on shut down. have to force shut down causes f.s. check and errors. 
anybody know how to help?

---

### Post by Thryn on 2010-08-19
I actually have the same problem, but it's on an ASUS UL30a with Puppy on a thumb drive. Didn't have the problem the first time, when I made the puppy save.

---

### Post by DarinB on 2010-08-19
it is a great os but this is a big deal. 
from the live cd no problems but after i wiped out the hdd re partitioned it and created a swap partition installed pup on the hdd now i get these crashes...my experience with puppy is a bad shutdown can kill the install.
at least i am not alone.

---

### Post by lemmy999 on 2010-08-19
AFAIK Lucid Puppy is so-called because its Puppy Linux constructed using the Ubuntu repositories. As such you will probably get a much better response [[COLOR="Red"]here[/COLOR]](http://murga-linux.com/puppy)

Best of luck- Puppy is a really good distro but  with a somewhat different approach to Linux.

---

### Post by -kg- on 2010-08-19
Reading [this page from the Puppy Linux website]("http://puppylinux.org/main/index.php?file=How%20NOT%20to%20install%20Puppy.htm") might also help.

I remembered reading that it is definitely not recommended to install Puppy Linux to the hard drive.  The recommended method for max booting speed is to run Puppy from a USB flash drive.

---

### Post by Sir Jasper on 2010-08-19
Hi,

Quote: "I remembered reading that it is definitely not recommended to install Puppy Linux to the hard drive" is almost certainly not true today.

If Lucid Puppy is installed on an ext3 partition (not ext 2 or 4)then I believe the "ignore" button can be pressed and fsck will be bypassed.

There are many clever helpers on this forum, but although Puppy takes advantage of the Ubuntu repositories it has no other connection to Ubuntu so, as was already said, it will be better to raise any query in the Puppy forum.

My regards

---

### Post by jtarin on 2010-08-19
> Playdayz,01micko, WhoDo and the team produced the latest and brilliant release, Lucid Puppy version 5.1.
**_Lupu-5.1 is brilliant but is half way_**. i intend to offer its modification 'QuickSet Edition' as 'lupq'. [HERE]("http://murga-linux.com/puppy/viewtopic.php?t=58654")

---

### Post by -kg- on 2010-08-20
> **Sir Jasper said:**
> Hi,

Quote: "I remembered reading that it is definitely not recommended to install Puppy Linux to the hard drive" is almost certainly not true today.


From the following page: [http://puppylinux.org/main/index.php?file=How%20NOT%20to%20install%20Puppy.htm]("http://puppylinux.org/main/index.php?file=How%20NOT%20to%20install%20Puppy.htm"):

> Puppy is easy to use and does not require a hard disk, so the first trick that you must know is how NOT to install it to hard disk ! 

From this page: [http://puppylinux.org/main/index.php?file=Frugal%20Install%20to%20Hard%20Disk.txt]("http://puppylinux.org/main/index.php?file=Frugal%20Install%20to%20Hard%20Disk.txt"), linked to at the bottom of the previous page and containing rather complicated instructions to install Puppy to hard disk anyway:

> That's it, you can now boot Puppy using your WindowsXP hard disk! If you fail, the only problems that you must solve are any of: (1) WindowsXP needing a disk check; (3) grubinstall.exe must be re-run after the Windows disk check; (3) wrong numbering of partition, such as when the Windows install uses two partitions to boot itself.

The ultimate solution? You guessed it, DO NOT INSTALL PUPPY TO HARD DISK!

This is all obviously from the Puppy Linux website itself.  While there might be an alternate way to install it to disk elsewhere, I tend to believe and follow suggestions from the website of the distribution itself.  According to the official puppy website, it is NOT recommended to install it to the hard drive.

---

### Post by 01micko on 2010-08-20
Hello Ladies and Gents.

There are many misconceptions on what Puppy is for and how to install, or even if to install.

Now I'm a former Mandrake user. I remember when I first switched to Linux all the hoo har about how it's so difficult and nothing runs, this and that.

We are lucky in the Linux world to be blessed with so much choice.

Puppy takes that a step further by offering so many choices in build and installation type. I won't go into things in detail but you can install puppy a number of ways including the traditional full install way. As with anything, you do what suits you.

In my most humble opinion, if you are a little apprehensive about Puppy, you can try it as a live install, yes exactly that. Boot from the CD and save a 'pupsave' on your hard drive in any filesystem. Of course native Linux filesystems are best but NTFS works fine as well and FAT is supported though has it's limitations. You can still 'install' Puppy without even touching a dard drive or a flash drive by saving back to cd + or -r or dvd.

Not all the information on the Murga Puppy forum is 100% correct. It's a forum after all and each post is someone's opinion just as it is here.

Best places for info are:
[http://puppylinux.com]("http://puppylinux.com") and [http://puppylinux.org]("http://puppylinux.org")

Cheers

---

### Post by DarinB on 2010-08-25
FYI,,,,
I am using a full install of lucid puppy on a sony lap top that has 
18gb hard drive and 256 of ram. most likely a little less do to some inherent usage. I could no longer use Ubuntu due to ram requirements. 

Lucid Puppy is an amazing build for older laptops. 
I am slowly learning how to use it but now that it is based on Ubuntu and uses Ubuntu repos, is a fantastic innovation.

---

