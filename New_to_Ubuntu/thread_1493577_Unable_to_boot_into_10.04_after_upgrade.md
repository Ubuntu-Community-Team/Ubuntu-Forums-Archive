---
title: "Unable to boot into 10.04 after upgrade"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by EldinTheMaster on 2010-05-26
I just upgrade my Ubuntu 9.10 to 10.04. The installation went well, and when it was finished, the computer reset.
 
I came to a menu that I always come to (although I don't know why, I can't remember what I did to make it appear) that looks like this:
 
 
GNU GRUB version 1.97~beta4
 
then, inside a box, is a number of selections:
 
__________________________________________________
 
Ubuntu, Linux 2,6,32-22-generic
Ubuntu, Linux 2,6,32-22-generic (recovery mode)
Ubuntu, Linux 2,6,31-21-generic
Ubuntu, Linux 2,6,31-21-generic (recovery mode)
Windows Vista (loader) (on /dev/sda1)
__________________________________________________
 
 
I usually pick the top selection. however, when I rebooted after installing 10.04, that selection, and the (recovery mode) below it, show this error:
 
 
__________________________________________________
 
error: you need to load the kernel first.
 
press any key to continue
__________________________________________________
 
 
if I try to use the 31-21 selections (regular and recovery), I come up with some incomprehensible text, and the following:
 
 
__________________________________________________
 
[ 1.682405] Kernel panic - not syncing: VFS: Unable to mount root fs on unkno
wn-block(8,1)
__________________________________________________
 
 
note that it actually does cut off "unkno" and go to the next line.
 
Help please? I'm a total newb at this and would really like to get this working. Thanks!
 
Also, the long lines do not actually appear on the screen, I just added those to seperate the regular words from the computer words.

---

### Post by Yanno on 2010-05-26
I guess Lucid is a pretty good one.It's stable...That's weird U've got this problem however...Try to install it from a CD or DVD,upgrading may bring you a lot of trouble.Hope that good!

---

### Post by Peter09 on 2010-05-26
Sanity Check 
                 - you have no other bootable media in the machine (CD or USB)?
                 - are you using a two disk or Raid configuration?

---

### Post by EldinTheMaster on 2010-05-26
@Yanno: I've never had an Ubuntu cd... Don't they cost money or something?
 
@Peter09: No, there's absolutely no media whatsoever connected to the computer. And what exactly is a two-disk or Raid configuration? I don't know what those... are...

---

### Post by ScottinSoCal on 2010-05-26
> **EldinTheMaster said:**
> @Peter09: No, there's absolutely no media whatsoever connected to the computer. And what exactly is a two-disk or Raid configuration? I don't know what those... are...

RAID = Redundant Array of Independent Disks
It's a way to make two or more hard drives appear to be one drive to your computer. There are ways to do this in hardware, with disk controllers (which require the right drivers to be installed) or through software, which introduces a whole new mess of problems, because each type of software creates it a slightly different way.
To make it more complicated, RAID comes in several different flavors: RAID 0, RAID 1, RAID 0/1, RAID 5 are probably the most commonly used. 
RAID 0 takes (usually) two disks and makes them one large disk with the data striped across them. It gives you faster read speed. 
RAID 1 takes (usually) two disks and makes them one disk, with the data duplicated on each drive. It gives you full data redundancy, so nothing is lost. 
RAID 0/1 takes (usually) four disks and creates two striped sets, each a duplicate of the other. It gives you increased read speed as well as data redundancy.
RAID 5 takes three or more hard drives, stripes the data across X-1 of them, and uses the last to store data that allows the RAID to be rebuilt if one drive fails. So if you build a RAID 5 array from six disks, each 500 GB, you would wind up with one drive of 2.5 TB (5 x 500 GB), and if a drive failed, you could pull it, replace it, and bring the array back up to rebuild all the lost data that was on the failed drive. Because it's more expensive and the benefits to it are mostly only useful on a system that has to stay up at all times, it's mostly businesses that use RAID 5. Gamers and heavy home users tend to prefer RAID 0 or 0/1, for the increased performance.
No matter what kind of RAID you build, your computer will still see it as one hard disk. If you have the right drivers and/or software loaded. If you don't, your computer won't see anything it can recognize or use.

---

### Post by EldinTheMaster on 2010-05-26
I do not know which of those I use. Is there some way I can find out? Will it help fix my computer?

---

### Post by Peter09 on 2010-05-26
You could try using the supergrub rescue disk

[http://www.supergrubdisk.org/forum/index.php?topic=494.0](http://www.supergrubdisk.org/forum/index.php?topic=494.0)

---

### Post by Peter09 on 2010-05-27
Or you could look at this thread
 
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by dillandriskell on 2010-05-27
Hey Eldin, I had a similar problem and found an easy fix. I'm not sure if it'll work for you but it's worth a shot I'm sure.

Every time I turned my computer off and turned it back on, it would get stuck at the loading screen, forcing me to dirty shut down. As it turned out, if I left my computer off for a good minute or two, and then turned it on it worked fine. I'm guessing it has something to do with the RAM clearing? 

Anyways, my suggestion is to try letting your computer sit for a good five minutes or so before attempting to turn it on again. Hope that helps.

---

