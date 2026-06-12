---
title: "Grub does not load"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by IronArjen on 2011-07-19
Following an upgrade I could enter normally into Grub and Ubuntu, then I clicked on something, my screen went weird. I had my desktop open but not one clicked worked. Reset and now it says:

SYSLINUX 3.63 Debian 2008-07-15 EBIOS Copyright (C) 1994-2008 H. Peter Anvin #all on one line
boot:

What can I do? Install and hope both my windows partition and my Unbuntu-data are OK?  

v10.4 64 bit

Obviously I am not sure whether the upgrade is related but it appears as too much of a coincidence.

---

### Post by Joris Donders on 2011-07-19
You can do a Grub repair via the LiveCD. Actually you've got to reinstall this. 

It's a lot to explain so I think you better refer to the Wiki first on how to perform this action. 

With booting up the LiveCD you can save your data first before doing anything permanent. Choose try ubuntu on boot. 

An external USB harddrive would be very handy at that point for saving data first.

---

### Post by IronArjen on 2011-08-03
Mmm, finally I managed to download the liveCD. It does not login to the gui, it goes to the terminal. Any idea? Will put separate post as well..........

---

### Post by Blasphemist on 2011-08-03
It sounds like you are having a video issue now that this threads first 3 posts can help with. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

As you use that to get to where you can boot the live cd, please download and run the boot info script and post it's results here in code tags. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by IronArjen on 2011-08-04
It appeared that I had an error on my harddisk which prevented reaching the grub. Quite troublesome since it took me a while finding out what the cause was. Couldn't mount my disk on a second machine etc etc. Lesson for me is as follows: Severa problem: run 

sudo fsck /dev/sd..

in which .. indicate which disk and partition you require. If you dont know run:

sudo fdisk -l 

and you ll get something like:

omitting empty partition (5)

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe74ee74e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18155   145830006    7  HPFS/NTFS
/dev/sda2           18156       36483   147212642+   5  Extended
/dev/sda3           35757       36483     5839596   82  Linux swap / Solaris
/dev/sda5           18156       35036   135588864   83  Linux
/dev/sda6           35037       35756     5782528   82  Linux swap / Solaris

In the above the NTFS is a windows partition, my Ubunta was sda5.

Checking for errors on the hard drive might as such prevent a lot of troublesome searches.

---

