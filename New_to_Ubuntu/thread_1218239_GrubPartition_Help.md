---
title: "Grub/Partition Help"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Bobrm2 on 2009-07-20
When upgrading from 8.10 to 9.04 I caused myself alot of problems. 
   
   How do I take a screen shot of GRUB? 
 
   Second: How can I repair the "Partition table entries are not in disk order"?
 
   Third, don't believe I need all the "Partitions(?) under /dev/sda2; and have a complaint that indicates only part of sda5, 6, 7, 8, and 9 are in SDA2 (huh)? 

Really getting confused so I'll quit and hope someone can help. Thank you.

Bob


file:///home/bob/Desktop/72009.png

bob@bob-desktop:~$ sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedb1edb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1107     8891946   83  Linux
/dev/sda2            1693       14593   103627282+   5  Extended
/dev/sda3            1108        1692     4699012+  83  Linux
/dev/sda5            6930        6954      200812+  83  Linux
/dev/sda6            6955       13004    48596593+  83  Linux
/dev/sda7           13005       13126      979933+  82  Linux swap / Solaris
/dev/sda8            1693        6929    42066139+  83  Linux
/dev/sda9           13127       13434     2473978+  83  Linux

Partition table entries are not in disk order

---

### Post by Bobrm2 on 2009-07-20
Here is my GParted file.

---

### Post by dlmarti on 2009-07-20
Not sure I understand the problem.

You have a bunch of partitions, most of which are too small to be of any use, who made them and what are they for?

---

### Post by zerhacke on 2009-07-20
How many times did you reinstall Ubuntu?

---

### Post by Het Irv on 2009-07-20
> **Bobrm2 said:**
> Here is my GParted file.

To get GRUB post your menu.lst file

In the terminal type ```
gedit /boot/grub/menu.lst
```

Since thats gonna be a long file, use [pastebin.com]("http://www.pastebin.com")

---

### Post by ajgreeny on 2009-07-20
How did you upgrade?  I suspect what you did is another install without overwriting the original, but I may be wrong.  However, as dimarti says, you have far more partitions than you need and it will probably be better to backup and start again, but before that, can you tell us, if you know, where all your own docs and music and videos etc etc are on the file system?  Perhaps you have a separate /home partition, which in theory makes life easier when you upgrade from distro to distro, or version to version.

With ubuntu running as you always have it and making certain all your files are where you expect in /home, run the command ```
mount -l -t ext3
```This will show which partitions are in use and needed for your current properly working (I assume so at any rate) ubuntu install.  We can then mount the others and check what is in them and if necessary delete them, and then add the free space to other partitions.

For your grub menu.lst file just copy the bottom part of the text file (/boot/grub/menu.lst) where the menu itself starts and copy it here.  We don't need all the general configuration from the top.

---

### Post by Bobrm2 on 2009-07-20
Exacty, and I don't how to see just what they contain. As, to how many times I reinstalled JJ 9.04 I will try to remember the sequence, it's been a while.  

  First I attempted to download directly over 8.10 that failed. 
  Then, with a slow burn ISO downloaded and installed to sda1, it's the one I am currently on and is confirmed by:

 ob@bob-desktop:~$ mount -l -t ext3
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) [Ubuntu 9.04]
bob@bob-desktop:~

   Lastly I had XP on it's own partition and I replaced it with JJ 9.04 (I don't know why) and in grub it's there in top position, but gparted doesn't indicate in what partition.

---

### Post by Bobrm2 on 2009-07-20
Say, pastebin is ok, 

[http://pastebin.com/m3781f1b8](http://pastebin.com/m3781f1b8)

Thank you all for chiming in.

Bob

---

### Post by Het Irv on 2009-07-20
Okay looking at your GRUB and your Partition table, it looks like you have two OS's installed Ubuntu 9.04 in sda1, and Ubuntu 8.10 in sda8, which is part of the Logical partition sda2.  You have a SWAP partiton @ sda7, and a data partion of some sort on sda6.  

As for the errors that you described in the OP, when are you getting those?

---

### Post by ajgreeny on 2009-07-20
OK, so sda1 is your root partition for your new install of 9.04, but it looks as if you are not able at the moment, with what is mounted according to "mount", to access the 21GB of files in sda8, presumably the filesystem and /home folder files from 8.10.  If this is correct you will need to make sure any of your own files from that partition (sda8) are backed up so you can restore them to your eventual new home.  There is also a partition sda6 with a smaller amount of files and we need to find out what they are.

Open the places menu and mount all the partitions showing, one by one and you will be able to see what is in each, and copy the files you want to keep (docs, music etc etc, but not hidden config files) into a temporary folder you should make in sda6 in order to consolidate them, as you don't have enough space in your current install partition, sda1.  You can do this for all the existing partitions, just copying files from the /home/username folder in each, if there is one, to sda6.

When you have done that, unmount all the partitions you have mounted, and delete them with gparted, except for your OS partition, of course, swap, and the now fairly full sda6.  You should now just have those three partitions left, and a big unallocated space next to sda1, which you can add to your sda1 using the ubuntu live CD's gparted.  Now copy all the files in sda6 to your /home/username folder to get all your old documents back, and either leave the sda6 as a data partition, or add that also to sda1 to make a large root partition.  You can also enlarge the swap a bit if you want and perhaps move it to the end of the drive and then add the 8.8GB unallocated space to sda6, if you kept it separate, or your root partition if you didn't.

I hope that all makes sense.  It sounds a bit complicated, but it is simply moving files to free space, then removing partitions to enlarge your root and the copying files back again to the newly enlarged root, and generally cleaning up your partition system.  The numbering will still be out of order, perhaps, but with UUIDs that does not really matter too much.

Of course, if you have an external usb drive to backup everything from your /homes in the various partitions, you may decide simply to wipe the lot and start again.  It is probably what I would do, as it is so quick to install the system, particulary if using the whole disk, as you appear to be, with no dual boot to confuse things.

Good luck!  I'm sure you will get it sorted one way or the other.

---

### Post by ramnarayan on 2009-07-20
Am also wondering if you have a separate /boot partition or is your /boot part of your / (root)

if this was the case for Ubuntu 8.10 over along which you installed 9.04 then i suspect that 9.04 does not know where to find 8.10. There is a way of figuring that out.

However as a few folks have suggested - best is to back up your data (prefereably onto an external HD/ CD / DVD etc ) and then begin buy doing a clean install and doing a good partitioning scheme.

Can anyone point to a good partitioning guide.

What i do (and think is the recommended way)

make the following - separate partitions (preferably in the following order)

swap - twice your RAM (if your have 1.5 GIG ram then allote 3 gig for swap)
/boot - about  100 MB
/ (or root) depends on how much software you install 4 gig is minimum(my opinion) 7 gig is good 10 is like if you can afford it

the remaining you can make into /home - where your data is stored.

The order is so that you can at any stage take extra space from your /home and allot it to / (if need be)

In your HD you can have 3 primary partitions - of which the 3rd can be a Extended Partition under which you can have quite a few logical partitions.

But before you do all this please
1. Backup your data
2. Read a bit more about the individual processes and see help guides

---

### Post by ajgreeny on 2009-07-21
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) for an excellent partitioning guide for ubuntu, should you decide to backup and start again as I and ramnarayan seem to think might be easiest.

---

### Post by LewRockwell on 2009-07-21
> **Bobrm2 said:**
> Say, pastebin is ok, 

[http://pastebin.com/m3781f1b8](http://pastebin.com/m3781f1b8)

Thank you all for chiming in.

Bob

i think this post from yesterday means bob got it fixed

.

---

### Post by Bobrm2 on 2009-07-21
Had to be gone today, and intend to begin to backup and re-partition later this evening or tomorrow. Want to thank each of you. Hope I can handle this myself.

Best to all

Bob

---

### Post by ajgreeny on 2009-07-22
> **Bobrm2 said:**
> Say, pastebin is ok, 

[http://pastebin.com/m3781f1b8](http://pastebin.com/m3781f1b8)

Thank you all for chiming in.

Bob
Just out of interest Bobrm2, what on earth was this supposed to mean?  By the time I got to it there was nothing abiout your problem showing on it and I didn't realise you had everything sorted out.

Hope all is well with the reinstall when you get to it.  Good luck.

---

### Post by Bobrm2 on 2009-07-24
Want to thank all for your assistance. Wish to mark this closed.   Bob

---

