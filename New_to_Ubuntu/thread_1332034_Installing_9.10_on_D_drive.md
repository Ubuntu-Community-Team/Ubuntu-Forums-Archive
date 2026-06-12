---
title: "Installing 9.10 on D drive"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by gladaseya on 2009-11-19
First I need to admit that I'm in the right place, absolute beginners.

I have ubuntu 9.10 and want to install it on my, aging, Toshiba laptop.  It came with xp home edition.  A while back, I split the drive into C and D drive, using D for file storage only.  I cleaned D drive and put the CD in and started the installation.  So far so good.

I got to the "where to put it" (my words) and that's where I ran into trouble.  The options were "side by side" or advanced.  When I looked at the side by side option, it showed three partitions.  I selected advanced and opted to put it on D and got a message about no root, something.  At that point I chickened out and quit.  

Any suggestions on a "best" procedure for installing 9.10 on D?

gladaseya

---

### Post by egalvan on 2009-11-19
Do you intent to use all of the space on "D" drive for Linux?

If so, then you need to remove the "D" drive.
Not just erase it, you need to remove it totally, so that there is only one drive, the "C" drive left.

Linux cannot install on Microsoft-style partitions,
in other words, the partitions must be Linux-style,
formatted for a partition that is usable by installer...
ext3, for example.
And the installer will not "see" a Windows partition as "free"space...
it must be **empty**, non-existent.

Either use the disk management tools under Windows,
or boot the LiveCD, choose "make no changes".
then use Partition Editor to erase the second partition.

Then install Linux, and choose the "side-by-side" method

---

### Post by Locke_99GS on 2009-11-19
When using some space for Linux, you MUST have at least one partition with the mountpoint /

---

### Post by 3rdalbum on 2009-11-19
In the installer where you specify partitions manually, you need to set the 'mount point' to /

/ is the root file system.

Also tick the 'Format?' box for that partition, and set the filesystem type to Ext4.

---

