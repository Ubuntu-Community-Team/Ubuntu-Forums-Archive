---
title: "Installation"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Aruar on 2010-11-10
Hi, about a month ago I installed Ubuntu on an old computer.  I made a liveCD and everything went smooth.  For a couple hours now i've been trying to install it on my main desktop which has windows 7.  

When I try to boot from the CD it says that there is no file system median and stops.  Ive been searching online for awhile now and have been unable to find a solution to the problem.  Trying to boot inside windows doesnt work either.  It says to run chkdsk and restart, which I did.

---

### Post by sandyd on 2010-11-10
> **Aruar said:**
> Hi, about a month ago I installed Ubuntu on an old computer.  I made a liveCD and everything went smooth.  For a couple hours now i've been trying to install it on my main desktop which has windows 7.  

When I try to boot from the CD it says that there is no file system median and stops.  Ive been searching online for awhile now and have been unable to find a solution to the problem.  Trying to boot inside windows doesnt work either.  It says to run chkdsk and restart, which I did.

a)how are you burning the iso file? IN windows 7, you can just right click the iso, and ill burn it correctly. Its a common mistake that people make, burning the actual .iso onto the disc.

b) and a warning, you might want to follow these instructions [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)
because windows 7 will sometimes complain if you resize its partitions.

oh, and welcome to my 3000th post.
only 501 posts to go until I get a custom usertag.

---

### Post by Aruar on 2010-11-10
I will try and burn another disc.  Ive already made two and have used with two different burning programs, both burnt as images.  Ive also mounted it to a virtual drive and tried doing it like that with no luck aswell.  

I can load into the screen with check the disk, try first, install etc... then I go to install and if gives me this :

[COLOR=DarkOrange]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)

No median with file system available.


[/COLOR]

---

### Post by Aruar on 2010-11-11
Note, the cd works on different computers.

---

### Post by The Cog on 2010-11-11
Now here's a funny thing. If you google for "No median with file system available" (including the quotes), you get a single search result, which is this thread. So it's not a common problem that you have.

I wonder if you have strange CD drive hardware that the on-CD linux can't read. It may be worth making up a bootable USB installer stick and trying that.

---

### Post by Mark Phelps on 2010-11-11
You sure the error message isn't "medium" not "median"?

Also, if this is a PC preinstalled with Win7, it's possible that it already has the 4-primary-partition limit, in which case, the Ubuntu installer has no place to install TO.

To check that out, boot from the LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one) and post the results back here.

If fdisk reports no disks found -- that's a very different problem.

---

### Post by Aruar on 2010-11-11
Yes, it is "medium" heh.  I have 2 hard disk, one with 2 partitions and one with only 1 partition.  

And I couldnt figure out how to open the terminal...  Selecting any of the options from the menu gives me that previous error.

---

### Post by sandyd on 2010-11-11
> **Aruar said:**
> Yes, it is "medium" heh.  I have 2 hard disk, one with 2 partitions and one with only 1 partition.  

And I couldnt figure out how to open the terminal...  Selecting any of the options from the menu gives me that previous error.

might be bad cdrom drive.

swap it out and try another one.

---

