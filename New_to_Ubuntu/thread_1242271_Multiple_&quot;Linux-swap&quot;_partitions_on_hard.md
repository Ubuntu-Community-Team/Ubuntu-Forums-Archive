---
title: "Multiple &quot;Linux-swap&quot; partitions on harddrive"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by CaptAmerica on 2009-08-17
I had installed Ubuntu several days ago, and, long story short, I accidentally deleted some important system files via nautilus. So I tried many methods of recovery, and then decided the easiest way is to just wipe Ubuntu from my harddrive and install it again.

Using the Gparted Live CD, I deleted the Ubuntu partition (ext3) but not the Linux-swap partition. By deleting the Ubuntu partition I gained 6.2gb of unnallocated data, which I would use for my reinstallation of the OS, and this is where the problems begin.

Installing from the Ubuntu 9.04 Live CD, I specified to install using the empty space on my harddrive, the 6.2gb. Now that I have the OS installed, I see that the new Ubuntu partition is less than 3.0gb. Browsing with Gparted again, I see that there is no unallocated data anywhere, so I don't know where that extra 3.2gb went. Second, since I never deleted the Linux-swap partition from my first Ubuntu installation, I now have two of them, one is about 500mb and the other is about 100mb.

Here is my full list of partitions as displayed in Gparted:

/dev/hda1         ntfs
/dev/hda2         extended
    /dev/hda6     ext3
    /dev/hda7     linux-swap
    /dev/hda5     linux-swap


I've already transfered 1.0gb from my ntfs partition (Windows XP) to ext3 so I have some memory for Ubuntu, but I need to know if I should delete one of the two linux-swap partitions, and how to recover the 3.2gb memory that has been lost. Any help would be much appreciated.8-)

---

### Post by nhasian on 2009-08-17
while linux can use multiple swap files, you probably dont need two of them.  

i would boot off the live cd, and delete the swap partition closest to your linux partition.  then simply extend the ext3 partition to recover the unused disk space.

dont manipulate mounted volumes with gparted.  you must do this from the liveCD boot disc.

---

### Post by prvteprts on 2009-08-17
Multiple swap partitions work fine, although as nhasian has pointed out, most of the time there is no point in having two. In my case, though, I do have two swap partitions. Anyway, my suggestion is the same: make sure to delete the swap adjacent to the partition you want to install Ubuntu on and then expand the partition to cover the newly freed space. I think the partition must also be before (to the left of) the swap you should delete.

---

### Post by CaptAmerica on 2009-08-17
Thanks for your help, much appreciated. One problem though, I can not modify partitions from the Live CD because I get an error "No partition set to /root" or something akin to that. How do I set a partition as /root?

---

### Post by Bartender on 2009-08-17
You need to build a GParted LiveCD.  Go here:

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

click on the "stable", and download the .iso.  You create a bootable CD from that .iso same as you created your Ubuntu install CD.  Boot from the CD, click OK to several screens that ask about keyboard and graphics (the defaults almost always work but you might have to choose "safe mode" for the graphics if the defaults don't work for you) and you'll get to a map of your partitions.  Since none of the partitions are mounted you won't get that error message that you refer to.

Your Windows partitions will be identified as ntfs.  Right-click on a partition, check the "Delete" button, then apply the change.  Wipe out all the Linux partitions.

If it were me, when I was done deleting Linux partitions I'd create one extended partition that encompassed all the unallocated space.  But you could create a primary ext3 or ext4 partition from the unallocated space if you don't have a lot of primary Windows partitions.

After you've applied your changes, you can get out of GParted and pop in your Ubuntu CD.  The rest should be familiar to you.

EDIT:  I see from your first post that Ubuntu's already inside an extended partition.  That makes things simpler.  Delete hda5, hda6, and hda7 partitions but keep the extended partition.  You could probably try deleting the extra swap and resizing partitions but I suggested wiping them all out and starting over because it'd be good practice to install Ubuntu again.

---

### Post by egalvan on 2009-08-17
First, by deleting (at random) one of the two swap partitions,
you run a 50/50 chance of deleting the one that your current install is referencing in fstab and initrd-img, among other places.

You can regenerate these references, or you can check the UUID of the current swap, then delete the other one.

```
sudo blkid
```

will give you the UUID...

here is mine as an example

```
ernest@gx280:~$ sudo blkid
/dev/sda1: UUID="805424F85424F318" TYPE="ntfs" LABEL="gx280-xp" 
/dev/sda5: UUID="0933d680-d893-40fa-a01d-3c819f0b2ea3" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="3119f61a-7ab2-4b91-b9c8-44fa795dfae5" SEC_TYPE="ext2" TYPE="ext3" 
**/dev/sda7: TYPE="swap" LABEL="swap" [COLOR="Red"]UUID="7f9f938e-90da-4c2d-a75a-bd680b97aa4e"[/COLOR] **
/dev/sdb1: LABEL="750-data1" UUID="ea49cca2-75fc-4082-a4d7-4bc040df5d8b" TYPE="ext3" 

```

The red UUID is what you are looking for.
[I]
 This is the one that MY system is referencing...
yours will be different....
[/I]
delete the one that YOUR system is NOT referencing.

Note... I use the LABEL method, instead of UUID... 
easier for ME to read, understand and remember... :)

---

### Post by egalvan on 2009-08-17
Using the graphcical gparted, can you post a screenshot of your partitions?


Note, I use PartedMagic LiveCD for partition work...
I much prefer it's interface...

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by PGScooter on 2009-08-17
are both swaps being used?
what is the output of
```
cat /proc/swaps
```
?

---

