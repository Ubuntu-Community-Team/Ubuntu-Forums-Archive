---
title: "Resizing NTFS Partition without loosing data"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by guru boy on 2010-06-13
Greetings,
I installed Ubuntu nearly a month back just to give it a try, now I am permanently switching to it, and accidentally my windows partition was also corrupted but the Data Partition is still accessible now i want my Windows Fat drive and Data's NTFS 40 GB file-system to be merged in current Installation of Ubuntu, but my Ubuntu is in 20 GB space and so i can not swap full 36 GB data from 
data drive to Ubuntu,please tell me such a way that i may merge this NTFS Drive to ext without loosing data.

Regards
Guru

---

### Post by bruno9779 on 2010-06-13
I would get an external HDD. (it is a very good idea to have backups, right?, so you are eventually gonna need one)

1 back up the NTFS partition to the external HDD.

2 boot an ubuntu live CD (your partitions cannot be mounted while you move/resize)

3 go to Gparted and delete the NTFS partiton.

4 in Gparted resize the ext partiton of your choice to use the space freed up by deleting the NTFS partition

5 remove the liveCD and reboot

6 copy your files from the external HDD

---

### Post by zaphod777 on 2010-06-13
you can install a program called gparted that will allow you to resize partitions. However I think you will get the best results if you copy tour data off to a USB drive then delete the Windows partitions and resize the Ubuntu partition. 

> sudo apt-get install gparted

It will then show up under system -> administration -> gparted

---

### Post by Metrop021 on 2010-06-13
ah i went through pretty much the exact same thing, there's a few ways to do it... this is one option (the one i used) that doesnt include an external hdd but is time consuming:

1. Boot up ubuntu on a live CD.

2. Open the file manager and move as much of your data as you can fit onto your ubuntu partition.

3. Then shrink the windows/ntfs partition down as much as you can.

4. Then expand the ubuntu partition as much as you can.

5. Repeat 2 to 4 until instead of shrinking the windows/ntfs, you can just delete it.

---

### Post by warfacegod on 2010-06-13
A thought to consider. using a separate partition on your HDD as your /home can be a real life saver. Virtually all of your user settings will be put their hidden alongside your personal data. If, at some point, you render Ubuntu broken and it cannot be fixed, a fresh install with have your settings, F.F. bookmarks/add-ons, Compiz setup, etc. already set to go. The only thing left for you to do is remove and install the programs and packages you do and don't want. (Not to mention your data being safe as could be if your OS fails.) The entire process usually takes me under an hour.

---

### Post by guru boy on 2010-06-13
Hi all 
Thank you for such quick response, 
I already came up with External HDD Idea but I need to buy it :p

i would prefer the Metrop021's way, however It seems it is risky to perform this operation, as I am just a new user.

Thank you all for reply
Regards
Guru Boy

---

### Post by warfacegod on 2010-06-13
There is always a degree of risk involved in messing with partitions. Most of that can be reduced by paying close attention and asking for advice when unsure.

---

### Post by jmore9 on 2010-06-13
Download gparted live cd, burn it to cd .  Then boot into the gparted system and you will have a GUI with all the partition tools for resizing, deleting, and what not.  Just be carefull and check at least 3 times on what you want to do to make sure you do not make a mistake.  The GUI is easy to use.

---

### Post by diablo75 on 2010-06-13
> **jmore9 said:**
> download gparted live cd, burn it to cd .  Then boot into the gparted system and you will have a gui with all the partition tools for resizing, deleting, and what not.  Just be carefull and check at least 3 times on what you want to do to make sure you do not make a mistake.  The gui is easy to use.

+1

---

### Post by Jakiejake on 2010-06-13
> **jmore9 said:**
> Download gparted live cd, burn it to cd .  Then boot into the gparted system and you will have a GUI with all the partition tools for resizing, deleting, and what not.  Just be carefull and check at least 3 times on what you want to do to make sure you do not make a mistake.  The GUI is easy to use.

Exactly what I was about to say [http://gparted.org/](http://gparted.org/)

---

### Post by -kg- on 2010-06-13
> **guru boy said:**
> Hi all 
Thank you for such quick response, 
I already came up with External HDD Idea but I need to buy it :p

i would prefer the Metrop021's way, however It seems it is risky to perform this operation, as I am just a new user.


There's another little bit of space you can use.

How big is your (corrupted?) Windows partition?  If it is of any size at all (and since it's already corrupted and you intend to make the full switch to Ubuntu), you could delete that partition and make a new one, or, if the partition itself is not corrupted, you could erase everything in it and use that space to store part of the data in it.  That would decrease the time necessary to copy the data, resize the partitions, and copy data again until the partition was empty.

Now the caveat:

Have an [Ultimate Boot CD]("http://www.ultimatebootcd.com/") burned and handy before you start.  When you delete a partition from a hard drive, the partitioning scheme is changed, and the partition number of every drive after it will change.

If your Windows drive is sda1, your data drive is sda2, and your Ubuntu root partition sda3, then when you delete your sda1 drive, your data partition will become sda1 and your root partition will become sda2.  The same thing will happen when you delete the data partition.  If your Ubuntu partitions are Logical partitions, then this won't change, as the Extended partition is a form of Primary partition, and the Logical partitions then count up from sdb5.  However, the UUID of that partition, once you move and expand it, will.

At any rate, it is likely that you won't be able to boot to Ubuntu after these operations.  You will need to repair GRUB.  The UBD *should* enable you to boot to Ubuntu, and from there you should be able to repair GRUB by issuing the "update-grub" command from the terminal. (I may be wrong on this...can anyone confirm?)

At any rate, be advised that you may (most likely) be unable to boot back into the installation.  You will (likely) need to repair GRUB from that point before you can reboot normally into the installation (that, or reinstall, if you wish).  I just wanted to advise you of this so that you don't panic.

It ***would*** be a really good idea to get that external hard drive, though.  It makes every such operation much easier, with little possibility of data loss.  And it makes a handy space to store things that you don't use much, or that you want a backup copy of.

---

### Post by warfacegod on 2010-06-14
Deleting an OS partition can make your system unbootable, I've done it myself so I confirm this.

However, I've never noticed the partition letters change so I can't confirm that. I'm not saying it doesn't happen, just that I don't know.

---

### Post by rewyllys on 2010-06-14
> **-kg- said:**
> There's another little bit of space you can use.

How big is your (corrupted?) Windows partition?  If it is of any size at all (and since it's already corrupted and you intend to make the full switch to Ubuntu), you could delete that partition and make a new one, or, if the partition itself is not corrupted, you could erase everything in it and use that space to store part of the data in it.  That would decrease the time necessary to copy the data, resize the partitions, and copy data again until the partition was empty.

Now the caveat:

Have an [Ultimate Boot CD]("http://www.ultimatebootcd.com/") burned and handy before you start.  When you delete a partition from a hard drive, the partitioning scheme is changed, and the partition number of every drive after it will change. . . .

Or you could follow my "lazy man's" way of handling this problem.  

My laptop's 60GB hard drive came with a 55GB Windows partition and a 5GB manufacturer's "restore OS" partition.  When, a year ago, I decided to experiment again with Linux, this time with Ubuntu, my first modification was to shrink the Windows partition to 25GB, shift the "restore OS" partition to immediately after the Windows partition, and create a 30GB Ubuntu space after the "restore OS" partition.  The Ubuntu space consisted of a 2GB swap partition and a 28GB root partition that also contained my home directory.

After 9 months or so of using Ubuntu, I needed more room for it.  I tried to shrink the Windows partition further but accidentally damaged it.  Since I was already essentially prepared to abandon Windows, I decided to do so.  But being lazy, I avoided the partition-renumbering problem (which I was aware I could face). I simply: (a) shrank what had been the damaged 25GB Windows partition to a 50MB partition, and formatted it ext3; (b) shrank the 5GB "restore OS" partition to 50MB, and formatted it ext3; and (c) enlarged the Ubuntu space to 59.9GB.  

Thus the partition numbers remained the same, and I had no need to fiddle with GRUB.  Yes, I've wasted 0.1GB of storage space, but I don't mind that.

Note 1:  I actually divided the 59.1GB Ubuntu space into a 2GB swap partition followed a  20GB root partition followed by a 27.9GB home-directory partition, a separation that I've seen widely recommended and that makes a lot of sense to me.  But that did not affect the numbering of the first three partitions, which I wanted to avoid in order not to have to change GRUB.  

Note 2:  Since then I've learned that, for fastest operation, I should have placed the swap partition at the very end of the physical drive.  I'll do that the next time I need to make a major change.

---

### Post by -kg- on 2010-06-14
> **warfacegod said:**
> Deleting an OS partition can make your system unbootable, I've done it myself so I confirm this.

However, I've never noticed the partition letters change so I can't confirm that. I'm not saying it doesn't happen, just that I don't know.

I can confirm it, mainly because I do all my partitioning manually.  The confirmation of drive letter changes will come from the message we sometimes get from the "fdisk -l" command, "Partitions are not in disk order."  This is because the partitions are not numbered according to their order on the disk, but the sequence of their creation.  My recent experience with this:

Upon wishing to upgrade to Lucid, I decided a little partition "house cleaning" was in order.  I had earlier created a separate /boot partition in one of my little "experiments" and I wanted to eliminate it and increase my available space.

I deleted it and, considering I was going to do a clean installation, I also deleted the root partition and recreated it using the entire space that I gained by deleting the /boot partition.  This is much faster than trying to expand the existing partition.  I also expanded the /home partition after having shrank and moved another partition to give /home room.

I installed, and all was well, so I decided to do updates to my other installations (Fedora and OpenSUSE).  Fedora went well (it's on sda), but when I tried to boot into OpenSUSE (on sdb, along with my Ubuntu partitions) it would not boot.  It hung, giving the message, "looking for sdb11".

As it turns out, while the Ubuntu GRUB installation found OpenSUSE's GRUB Stage 1 (installed in the OpenSUSE partition), OpenSUSE was looking for its subsequent GRUB stages in sdb11, which no longer existed.  I had installed OpenSUSE last, and created its partition after all the other partitions on sdb.  When I had deleted Ubuntu's /boot partition, this changed OpenSUSE's partition number to sdb10.  Then when I deleted Ubuntu's root partition, it changed it to sdb9.

Now, when I recreated the partition for root, instead of changing the OpenSUSE partition back to sdb10, it remained sdb9 and the new root partition was assigned sdb10, due to its order of creation.  I confirmed all this through Gparted and the "fdisk -l" command.  I had to do several back flips with a 1 1/2 twist to get OpenSUSE back up again. :p

> Or you could follow my "lazy man's" way of handling this problem.

Yes, if you have the room, that's certainly an option, and if I had ***_followed my own advice_*** (i.e., ***think*** about what you're doing before doing it!) I certainly would have done it in a similar fashion.  With 240 GB of internal HD space and 1 TB of external, I certainly could have wasted a few MB to preserve my partitioning scheme! ](*,)

You live, and you learn.

---

