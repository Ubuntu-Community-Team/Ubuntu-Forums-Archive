---
title: "Can You Change Partition Size?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by PuddingKnife on 2009-03-15
Hi. I currently dual-boot Windows XP with Ubuntu.  The only reason I do this is because I play WoW.  I recently decided to upgrade to Wrath of the Lich King, which is a 15gig install file (!).

The only problem is, I have 6 gigs of free space on my XP partition.  On the Ubuntu side of things, I have 85 gigs free of 117.


Is there a way to increase the size of my XP partition by 10 or 12 gigs?

---

### Post by got_milk? on 2009-03-15
> **PuddingKnife said:**
> Hi. I currently dual-boot Windows XP with Ubuntu.  The only reason I do this is because I play WoW.  I recently decided to upgrade to Wrath of the Lich King, which is a 15gig install file (!).

The only problem is, I have 6 gigs of free space on my XP partition.  On the Ubuntu side of things, I have 85 gigs free of 117.


Is there a way to increase the size of my XP partition by 10 or 12 gigs?

Yes, if you use GParted on your Live CD you can shrink the Ubuntu partition and use that space to increase the Windows partition.

Before you do that though, it is recommended to defragment your Windows partition before doing any changes to the partition.

---

### Post by sgosnell on 2009-03-16
Defragging the Windows partition would be good, but it might not be practical.  When drives get close to full, they don't always have the space necessary to put the temp files.  It can take forever even if it's possible.  I wouldn't try to make a Windows partition smaller without a complete defrag, but making it larger shouldn't be a problem.  I would try to do the defrag, but if it stalls or the defrag utility complains, I would quit and just do the resize.

---

### Post by Gannon8 on 2009-03-16
Try using jkdefrag. It has an option to move everything to the front of the disk for partitioning, and as far as I know I do not think it uses temporary files (though 6 gigs should be good enough).

---

### Post by sgosnell on 2009-03-16
The files still have to be moved around.  Defrag on a Windows drive is not a pretty thing, and it sometimes moves the same file several times, especially if you tell it to compact the files in addition to defrag.

---

### Post by ramjet_1953 on 2009-03-16
The "Golden Rule" when re-sizing partitions is to do it with a stand-alone partition tool that boots from a CDROM.

You wouldn't try to change a tyre on a car that is being driven, would you?
So do not try to change partitions on a drive that is mounted.

Regards,
Roger :D

---

### Post by sgosnell on 2009-03-16
Well, yes a CD or a USB stick.  I don't think we were suggesting otherwise, but the defrag needs to be done while Windows is running.  After the defrag, you certainly want to boot from something other than the HDD you're going to resize, or you probably won't like the results.

---

### Post by PuddingKnife on 2009-03-16
Thanks for the replies!

Still feeling a little confused and uneasy about this process, but Im gathering this is what needs done:

1. defrag my Windows partition (if I can)
2. pop in the Ubuntu Live CD
3. ?
4. Windows partition is bigger!  Ta-daa


So gparted is on the Live CD, and I can use it to resize my Windows partition?  And this will not harm the files on either partition?

Once the Live CD is in the cd drive, I restart.  But then how do I access gparted?

---

### Post by carml on 2009-03-16
Yes,Gparted is on the LiveCd,you should find it under System->Administration.If isn't there make a search into the forum,it's a already answered question,I'm sorry if so,but I haven't got a Livecd near me; and finally yes it shouldn't harm your PC,a backup it's recommended only for scruple ):P .

---

### Post by PuddingKnife on 2009-03-16
Ok, I appreciate everyones patience with me.

So I have successfully defragged the XP partition.  I booted with the Live CD in the drive, and ran it that way.

I went to System > Administration > Partition Manager (or some such thing) and gparted started up and recognized both partitions.  But now Im a bit confused as to what to do now.  

As I stated, I wish to expand the size of my XP partition (which will decrease the size of my Ubuntu partition, right?) ..

So what do I put in the "Free Space Preceding" box?
Or the "New Size" and "Free Space Following" boxes?  

Id like to take 20 gigs from Ubuntu and give it to XP.

Im being very careful not to mess anything up, so I havent done anything besides check out the gparted program a little bit.

---

### Post by Elfy on 2009-03-16
It all depends on how the partitions are laid out as to how you go about this, if you used a default ubuntu install it is likely that the linux partitions are inside an extended partition. You need to resize in the correct order - resize logical, resize extended, resize primary. Also it is likely that partitins will need to be moved - or if possible resize from the correct side.

All sounds a bit complicated - but it's not, to me it sounds like it could take a long time.

To let us help you with the ins and outs it would be good to know how your partitions are laid out - open a terminal, run this command and post the result here please

```
sudo fdisk -l
```

---

### Post by PuddingKnife on 2009-03-16
> **forestpixie said:**
> It all depends on how the partitions are laid out as to how you go about this, if you used a default ubuntu install it is likely that the linux partitions are inside an extended partition. You need to resize in the correct order - resize logical, resize extended, resize primary. Also it is likely that partitins will need to be moved - or if possible resize from the correct side.

All sounds a bit complicated - but it's not, to me it sounds like it could take a long time.

To let us help you with the ins and outs it would be good to know how your partitions are laid out - open a terminal, run this command and post the result here please

```
sudo fdisk -l
```


Wow, that does seem rather complicated :o  Ok, ran the command and this is what comes up:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3276    26314438+   7  HPFS/NTFS
/dev/sda2            3277       19457   129973882+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris
/dev/sda6            3277       18711   123981574+  83  Linux
/dev/sda7           18712       19084     2996091   82  Linux swap / Solaris

Partition table entries are not in disk order


What do I do with this information?

---

### Post by PuddingKnife on 2009-03-16
Bueller?   


[SIZE="1"](shameless, I know)[/SIZE]

---

### Post by PuddingKnife on 2009-03-17
bump for help

---

### Post by PuddingKnife on 2009-03-17
ehh .. Im just going to try it and see what happens.  My WotLK 10 day trial is quickly burning away.  Anyone reading want to give some last second advice?  

I already defragged, Ill run gparted off the Live CD, try to figure out what to put in the "Free Space Preceding/Following" boxes and boot into XP two times to make sure it works.  Am I missing anything?

---

### Post by Elfy on 2009-03-17
To be able to resize the xp partition (sda1) you will need to do it in this order

shrink - sda6
shrink - sda2
expand - sda1

You will also need to have the unallocated space NEXT to sda1 before you can expand it - it might be that you need to move partitions to be able to do that if you are not able to resize from the left.

---

### Post by mikechant on 2009-03-17
Running gparted from live CD:
1/ If any partitions show with a 'lock' icon in gparted, right click on them and select 'unmount' or for swap partitions 'swapoff'. There should be no lock icons showing now.

2/ Resize sda6 by moving its start point up by 20Gb (you can just drag the start point in gparted's resize function.
3/ Apply this change.
4/ Move the sda5 partition up so it ends at the start of sda6 (the Gparted move function allows you to just drag partitions around).
5/ Apply this change.
6/ Resize sda2 by moving its start point to match the start of sda5 (this moves the free space out of the extended partition so it is logically next to the primary partition sda1)
7/ Apply this change.
8/ Now you have you free space in the right place, and you can resize sda1 by dragging its end point to fill the free space.
9/ Apply this change.

You *can* do multiple operations at once before applying but I wouldn't recommend it. Repartitioning is best done in the most cautious way possible.

Some of these operations may take a very long time, particularly item 2/ which may take several hours at worst.
Don't interupt the operations or you will almost certainly lose data.
Windows may do a lengthy file system check when you boot it next.

If you can back up anything crucial before doing this I would strongly recommend it.

---

### Post by PuddingKnife on 2009-03-17
Thanks, that seems like a very helpful post.

However, I think I have resigned myself to the fact that this is way over my head, and Im thinking 'to hell with it' at this point.  

It would almost seem easier to just buy an external hard drive, load XP onto it, and play WoW that way.  Which I might end up doing.  I really dont feel like backing up 20 days worth of music, an endless assortment of personal photos, etc onto DVDs just to make a partition a different size.

At first it seemed like a routine sort of job, but this has turned into something I perceive beyond my ability. Oh well.

:(

---

### Post by mikechant on 2009-03-22
> It would almost seem easier to just buy an external hard drive, load XP onto it, and play WoW that way. Which I might end up doing. I really dont feel like backing up 20 days worth of music, an endless assortment of personal photos, etc onto DVDs just to make a partition a different size.


Of course, if you had an external drive, you could back everything up to that and redo your partitions from scratch with no risk of data loss.
But maybe still a bit more hassle than you want...

---

