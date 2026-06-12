---
title: "Getting Dual Boot Install on Compaq Presario?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by lolajl on 2010-07-05
Today I got Compaq Presario CQ62-231NR Notebook, which is 64bit.  I downloaded Ubuntu 10.4, 64 bit version and installed onto DVD.  Then, I booted off the DVD drive.  I want to install Ubuntu as dual boot since I want to keep Windows (need to be able to check websites in IE, FF and Win Safari).  Going through Ubuntu install, I only got 2 options:  Erase whole disk and Specify partitions (advanced).  

Here's the partitions that I have:  

Win7 - /dev/sda1, 208.7MB (69MB used)
WinVista loader - /dev/sda2, 305.1GB (26424MB used)
WinVista loader - /dev/sda3, 14.7GB (12574MB used)
none listed - /dev/sda4, 108.4MB (33MB used)

So, what can I do to get that dual boot option?

---

### Post by mike555 on 2010-07-05
Looks like you have the 4 primary partition limit .... you might not be able to install without getting rid of one of those primary partitions .

---

### Post by -humanaut- on 2010-07-05
You need to shrink the Win partitions and give Ubuntu enough installation space about 80-100GB should do.

---

### Post by lolajl on 2010-07-05
> **-humanaut- said:**
> You need to shrink the Win partitions and give Ubuntu enough installation space about 80-100GB should do.


Ugghh . . . apparently I have to find a Windows CD so i can safely shrink the partitions to give Ubuntu enough room to install.

---

### Post by Miljet on 2010-07-05
And once again, what mike555 said. You already have 4 primary partitions on your disk. You are limited to a total of 4 primary partitions. So, even if you shrink your existing partitions, you still can't create any more without deleting one of the existing partitions.

You could then create an extended partition which could contain several logical partitions.

Also, you should be able to shrink Windows partitions from within Windows itself using the built-in disk tools.

---

### Post by kingbirdy on 2010-07-05
they are right. you have reached the 4 primary limit.

---

### Post by lolajl on 2010-07-05
> **kingbirdy said:**
> they are right. you have reached the 4 primary limit.


Okay . . . what about the last partition - none listed - /dev/sda4, 108.4MB (33MB used) 

Is that safe to delete?  I know almost nothing about Windows (my primary setup is OSX).

---

### Post by lkraemer on 2010-07-06
Here is one option!  Purchase a New Drive, Insert it in your Computer,
and install what you want.  You will have your existing Windows
installation to do with as you please, later.  Just swap drives, doing and
playing with whatever, until you make your final decision, which 
shouldn't take you long......

When you settle on Ubuntu, you can plug the old drive into a USB to 
IDE/SATA Converter and copy all the files/Data to Ubuntu.

If your Computer is New, and you have the option of making a set of
Restore CD's or DVD's, be sure to do that first.

It's your choice now!  For less than $50.00 you should be Dual Booting
your choices.

lk

---

### Post by lolajl on 2010-07-06
> **lkraemer said:**
> Here is one option!  Purchase a New Drive, Insert it in your Computer,
and install what you want.  You will have your existing Windows
installation to do with as you please, later.

It's a laptop, hence, only room for one drive.  And yes, I really do need to keep both Windows and Ubuntu. I don't have money to buy another laptop so I can run Windows on one and Ubuntu on the other.   But, thank you for your advice. :)

---

### Post by Miljet on 2010-07-06
It is impossible for us to know what is on sda4. You can find out by booting a live CD, mounting sda4, and looking to see what is on it.

If it is just data (photos, documents, music, etc), you can copy it to a CD and delete the partition. Then after shrinking the Windows partition, you can create an extended partition with the unallocated space. Then you can create multiple logical partitions within the extended partition. The data that you backed up can go on one logical partition, Ubuntu on another, and a swap partition on another.

---

### Post by thinkren on 2010-07-23
I just bought a Presario CQ62-225NR and am trying to resolve the same issue.  One option is to create a set of Recovery discs, then install Ubuntu over the partition currently allocated to System Recovery (D: I believe).  I'm going to try it this weekend and will report my findings.

---

### Post by leebh28 on 2010-07-23
Please try installation of ubuntu via wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by cjv8888 on 2010-07-23
I had exactly the same scenerio with a CQ42-136TU.  The last primary partition on mine contained HP tools.
I ended up copying this onto external disk, backed up the recovery partition (no 3). then deleted the HP tools partition so I can shrink the Windows partition to make room for an extended partition.

---

### Post by Pangthagerous on 2010-09-24
My brother recently bought a Compaq laptop with a similar setup and is having what I BELIEVE is the same problem. 

[http://dl.dropbox.com/u/8551896/Capture.PNG](http://dl.dropbox.com/u/8551896/Capture.PNG)

Here is a screenshot of his partition setup in the windows partition manager thinger. My question is, will deleting HP tools help him or will he still be unable to use the unallocated space because of its location in relation to the other partitions?

---

