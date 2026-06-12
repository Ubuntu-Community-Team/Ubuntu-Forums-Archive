---
title: "Need Help with Partitions.."
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Codix121 on 2009-09-23
Well the problem happened, because originally I had windows/linux...
well I eventually turned full linux...and I'm not sure what I did wrong,
but I now have Jaunty installed on my first harddrive (/dev/sda) which consist
of 80 GB...I'm running out of space, I have a second harddrive which is 115gb (/dev/sdb), when I try to access my second harddrive, it's under "115.1 GB Media" and apparently when i click on it, and open it, it's a bunch of linux files... As if linux is installed on it? Which might be a previous installation of linux on my second harddrive.

Anyone know how I can wipe my second harddrive clean or how I can use it just for storage, I have alot of video and music files that are taking up space and I have gparted but not sure how to basically wipe my second harddrive clean without affecting my first harddrive and current installation of ubunut. Thanks!

---

### Post by community nerd on 2009-09-23
Open gparted, right click on the drive and click format.

---

### Post by Codix121 on 2009-09-23
Just did that my harddrive is now empty but I can't access it from my (sda), the "115.gb Media" folder is gone, any way to resize my 80gb (sda) harddrive to add the now, "unallocated 115.gb" or anyway to turn it into a media harddrive so I can put stuff in there?

---

### Post by mikewhatever on 2009-09-23
You obviously need to format the unallocated space now. Use gparted again.

---

### Post by nhasian on 2009-09-23
i'll bet your larger hard disk is faster than your smaller one.  In the future when you want to say... do a fresh install of Ubuntu Karmic Koala 9.10 with the ETX4 filesystem you'll want to use the faster hard disk.  :)

---

### Post by Codix121 on 2009-09-24
I should of stated that I'm a newbie at this :(
Ok so in Gparted, I select Create New Partition Table ..I'm assuming,
What are the settings, ext2,ext3,linux-swap? which one and free space
preceding...and after, I'm sorry I'm really new to all this...

I'd appreciate the guidance thank!

---

### Post by Codix121 on 2009-09-24
So after some digging I finally found it has to be ext3 primary...
but only one problem...when I tried to do that,it keeps giving me an error,
doesn't say the error just doesn't seem to work and I tried with fdisk but it had some kind of "superblock" error and said there was no valid mount point (dev/sdb1). I'd really appreciate some help.

---

### Post by mikewhatever on 2009-09-24
Try deleting sdb1 and recreating it, ext3 file system, no unallocated space before or after.

---

### Post by Codix121 on 2009-09-24
I did and it just gives me some kind of error? It says I can't turn
into ext3, I added a screenshot of the error.

```

Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sdb.

```

This is the main error I'm getting from the console while running Gparted,
Not sure if there's anyway to fix it.

---

### Post by natravis on 2009-09-24
The message seems pretty straightforward. Did you try to reboot after making the first set of changes? If not, do so. Also, you can use gparted from a LiveCD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) or use gparted from the Ubuntu Live CD (open it CD, "Try without any changes" and then open gparted from the Desktop). Using any of those ways will allow you to change the partition info for the second drive. I also recommend switching at some point (perhaps now) to have Ubuntu on your faster drive (which  the larger presumably is, if it is newer). You could make two partitions on the second drive, move your data over to the secondary partition, install ubuntu to the first, then wipe first drive and use it as your data storage. Best practices for backup will have at least 2 locations though (meaning at least one primary (ie your 2nd partition of bigger drive) and one secondary (your 80gb drive), although that is unlikely to happen in some situation (like mine ... 2TB drives nearly full and no money to buy a double of that kinda storage).

Also as a rule, when you are opening a graphical app from the terminal, you should be using gksudo instead of plain ol' sudo. Explanation here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

