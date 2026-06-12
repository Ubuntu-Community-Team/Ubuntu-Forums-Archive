---
title: "Program like Norton Ghost"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by TechDragon on 2011-01-17
Currently I am using UBCD4win to launch Ghost 11 and image computers to a networked location.

I cant seem to get ghost 11 to work with wine.

Is there an alternative that would work on a live usb? that works similar I am trying to create a toolset for myself and my co workers that will help us to fix windows machines, IE Ghost, Antivirus, Antispyware, cleaner, etc

any suggestions on those would also be appreciated.

---

### Post by davidmohammed on 2011-01-17
try clonezilla - great imaging tool that works in many different environments and hardware.

---

### Post by wilee-nilee on 2011-01-17
Probably a good consideration.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by friv_livs on 2011-01-17
To satisfy all your partitioning, recovery, system testing, and backup needs,

[HTML]http://sourceforge.net/projects/partedmagic/[/HTML]

---

### Post by TechDragon on 2011-01-17
i have looked at clonezilla but it appears to be its own bootable live cd can it work from inside of ubuntu?

I am wanting to utilize the Live USB Ubuntu with the persistent drive folder option.

I have everything but this ghost "style" of application

---

### Post by davidmohammed on 2011-01-17
this [thread]("http://ubuntuforums.org/showthread.php?t=1216081") should help you.

---

### Post by wilee-nilee on 2011-01-17
> **TechDragon said:**
> i have looked at clonezilla but it appears to be its own bootable live cd can it work from inside of ubuntu?

I am wanting to utilize the Live USB Ubuntu with the persistent drive folder option.

I have everything but this ghost "style" of application

I'm personally that familiar with its use, but others are.:)

---

### Post by BbUiDgZ on 2011-01-17
PING (Partimage Is Not Ghost) -- Backup and Restore Disk Partitions
[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

built from the "linux from scratch" book

---

### Post by Mark Phelps on 2011-01-17
> **TechDragon said:**
> i have looked at clonezilla but it appears to be its own bootable live cd can it work from inside of ubuntu?

IF you're talking about the ability that a lot of MS Windows apps that allows full partition backup/imageing while running MS Windows on the same partition, then NO -- that feature is NOT available in any of the Linux-based products.

Why? Because the Linux utilities do not allow you to image them while they are mounted (i.e., in use).

Instead, you have to boot OUTSIDE of the Linux OS in order to do the imaging.

You can, however, "install" CloneZilla to your hard drive so you can boot from that and image your Linux partitions.  I know because this is how I image MY Linux partitions.

Instructions on how to do that are available at the CloneZilla website in their FAQs.

---

### Post by CodeToad on 2011-01-17
Google PartImage and you'll find lots of instructions on use, including how to create bootable USB drives. Or just grab a copy of the Ultimate Boot CD (UBCD) -- I believe it's already part of the boot and is loaded with lots of other useful tools.

---

### Post by steve7777777 on 2011-01-17
> **CodeToad said:**
> Google PartImage and you'll find lots of instructions on use, including how to create bootable USB drives. Or just grab a copy of the Ultimate Boot CD (UBCD) -- I believe it's already part of the boot and is loaded with lots of other useful tools.

Partimage does not support ext4

see the "Limitations" section:  [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by lykwydchykyn on 2011-01-17
I use g4l, but it's also a live-bootable sort of thing.  I believe there is a way to "hot clone" a Linux system by using rsync with a few specific excludes (/proc, /dev, and /sys?), but I don't know of a snazzy tool to do it automatically.

---

### Post by OzzyFrank on 2011-01-17
Personally, I agree with the suggestion of CloneZilla. It's easy to use, and has all the options you could wish for, from backing up partitions to image files, to complete drive cloning. It shouldn't have the limitations of PartImage.

---

### Post by BbUiDgZ on 2011-01-17
> **bbuidgz said:**
> ping (partimage is not ghost) -- backup and restore disk partitions
[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

built from the "linux from scratch" book
> **codetoad said:**
> google partimage and you'll find lots of instructions on use, including how to create bootable usb drives.
:d

---

### Post by LewRockwellFAN on 2011-01-17
Edited to remove a totally idiotic assertion utterly divorced from reality. I'd delete the post if I could. /me tips hat to [davidmohammed]("http://ubuntuforums.org/member.php?u=600258") in appreciation for catching it.

---

### Post by HermanAB on 2011-01-18
Well, there is always Data Definition(dd) and Netcat (nc).  With those two, you can copy anything to anything and they are part of the Knoppix distro for example.

---

### Post by davidmohammed on 2011-01-18
> **LewRockwellFAN said:**
> I concur that Clonezilla is great. But, as far as I know, it's purely a DOS program and does not run directly under a linux as OP indicated he wanted. You could probably get it to run under a DOS emulator under a linux. I believe it is "shipped" with DR DOS but I bet you could get it to work under other similar DOSes. I don't think I'd put a lot of effort into making it work under a DOS emulator if it didn't work right off the bat though if you could make do with the native-to-linux program mentioned above or for that matter, alternately, use DOS programs for the rest of the utilities you want on your repair drive and just use DR DOS or Free DOS.

You must be mistaking this for something else - clonezilla uses maverick for its base image...  nothing to do with DOS

---

### Post by pl@yer on 2011-01-18
If you decide to use dd first off be careful! 

Second make a zero file, this will compress to nearly nothing. dd does not care if it is copying blocks of data that have been deleted months ago and so it will make an image that is bigger than needed. 

If you make a zero file then delete it, when you bzip your image it will shrink nicely. 
```

dd if=/dev/zero of=./someunusedfilename;rm -rf ./someunusedfilename

```

Also note that dd will copy the boot record and everything else unless you skip ahead the right number of blocks. The nice thing about dd is that it is usually real easy to find. The not so nice part is that it does what you tell it to do.
Also note that you should not run dd on a mounted device. 
 :)

---

### Post by presence1960 on 2011-01-18
> **Mark Phelps said:**
> IF you're talking about the ability that a lot of MS Windows apps that allows full partition backup/imageing while running MS Windows on the same partition, then NO -- that feature is NOT available in any of the Linux-based products.

Why? Because the Linux utilities do not allow you to image them while they are mounted (i.e., in use).

Instead, you have to boot OUTSIDE of the Linux OS in order to do the imaging.

You can, however, "install" CloneZilla to your hard drive so you can boot from that and image your Linux partitions.  I know because this is how I image MY Linux partitions.

Instructions on how to do that are available at the CloneZilla website in their FAQs.

+1

That is what I have set up on my machines. At the GRUB menu I just choose clonezilla. Works great!

---

### Post by Mark Phelps on 2011-01-18
> **BbUiDgZ said:**
> :d

You're wasting folks time referencing PING.  I used that back in the days when Linux filesystems defaulted to Ext3.  But when Ext4 came along, PartImage quit working -- along with PING.  So, I moved over to Clonezilla.

Doesn't matter what websites or books you cite -- PartImage does NOT work with Ext4, and last time I checked with their website, they indicated no plans to do so.

---

### Post by LewRockwellFAN on 2011-01-18
> **davidmohammed said:**
> You must be mistaking this for something else - clonezilla uses maverick for its base image...  nothing to do with DOS

You are, of course, correct. It hit me later, I was thinking of The Ultimate Boot Disk. Darn, I was hoping to get back here and edit that post and remove the evidence of my idiocy before anyone caught it. *sigh*

---

### Post by BbUiDgZ on 2011-01-27
> **Mark Phelps said:**
> You're wasting folks time referencing PING.  I used that back in the days when Linux filesystems defaulted to Ext3.  But when Ext4 came along, PartImage quit working -- along with PING.  So, I moved over to Clonezilla.

Doesn't matter what websites or books you cite -- PartImage does NOT work with Ext4, and last time I checked with their website, they indicated no plans to do so.

Ok, consider me told off

PING doesn't support EXT4! sorry to anyone who downloaded it ](*,)
look [HERE](http://sourceforge.net/projects/partitionman/)

---

