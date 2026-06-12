---
title: "need clonezilla help - how to  clone to a smaller HD"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-15
hi,
I am trying to clone my Ubuntu 165 Gig HD to a smaller 35 Gig HD.
My 165 HD has about 30 gigs on it.
When I try to clone disk copy to disk copy the clone fails.
When I try to clone partition to partition I get a message that says I should use the "-C" option to override the larger source
partition.
 Can anyone tell me how to do this?

Thanks

---

### Post by seawolf167 on 2011-06-15
You have to resize the source partition so that it fits on the smaller drive (i.e. the source partition is now *smaller* than your destination drive, then image only that partition using [Clonezilla]("http://www.clonezilla.org"). Once the partition has been imaged, go to your destination drive and restore that partition to the smaller hard drive. You may need to [reinstall GRUB]("https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files") when you are done.

---

### Post by s1baker on 2011-06-15
I thought that I could force the 165 source to clone to the 35, as long as the source HD had less data on it that the target HD

---

### Post by seawolf167 on 2011-06-15
> **s1baker said:**
> I thought that I could force the 165 source to clone to the 35, as long as the source HD had less data on it that the target HD

If you can find a program that can do this let me know! No disk clone software I've ever used can clone to a smaller drive without doing the steps I previously listed.

---

### Post by howefield on 2011-06-15
From the Clonezilla FAQ

> Why Clonezilla can _NOT_ image from a large drive to a smaller drive ?
It's not easy to implement such a feature, since Clonezilla now is a partition "imaging" tool, by "imaging", it means clonezilla actually does not know the files themself, clonezilla just knows where the used blocks are. Because of this reason, the target partiton size must be equal or larger than the original one so that clonezilla can restore the used blocks on that partition. If the target partitioin size is smaller, then it will go wrong.
Unless Clonezilla has file-based function in the future. Maybe... 

---

### Post by s1baker on 2011-06-15
so, I use gparted to make a 30 gig partition and clone this. Then I might need to reinstall the Grub to the target HD. Correct?

Also, if I take my 165G target and make a 35 G partition on it, and then have a second partition on it, when I download data how do I determine how to download the data on the second partition. Is it like a d: or e: drive in Windows XP?

---

### Post by howefield on 2011-06-15
> **seawolf167 said:**
> If you can find a program that can do this let me know! No disk clone software I've ever used can clone to a smaller drive without doing the steps I previously listed.

I believe Acronis True Image can do it, but to be honest, the only sensible way to do it is as you described.

---

### Post by seawolf167 on 2011-06-15
> **s1baker said:**
> so, I use gparted to make a 30 gig partition and clone this. Then I might need to reinstall the Grub to the target HD. Correct?

Yea, use Gparted and resize the source partition so it is smaller than your destination drive. The reason you'll need to reinstall grub is because you will be imaging the partition, and that won't include the MBR, which will need to be reinstalled. No worries though, because reinstalling Grub is super easy - just follow the link I posted earlier.


> **s1baker said:**
> Also, if I take my 165G target and make a 35 G partition on it, and then have a second partition on it, when I download data how do I determine how to download the data on the second partition. Is it like a d: or e: drive in Windows XP?

You can always resize your partition back to the full disk later if you'd like to. By default, Firefox downloads go to your ~/Downloads folder. You can, however, format and mount your new partition and use it as a "data" drive. This can be accomplished by formatting it in Gparted, then adding the appropriate /etc/fstab entry. When you get to this step if you decide to make this so-called "data" partition, post back and we can help you add the correct entry.

---

### Post by s1baker on 2011-06-15
I will try this and post back later. I think I will try to gparted my 165 to a 30 partition and clone this, then reset the 165 back to the full size. Will post back later.
I will probably need help in reinstalling the Grub.
Also, Is there a way to determine which grub I will need to reinstall on the target HD? Do I need to reinstall the one that is on there now ( Ubuntu 10.10 is on the target ), or a different version?

---

### Post by seawolf167 on 2011-06-15
It will be GRUB2 (not legacy) since you are using Ubuntu 10.10

---

### Post by s1baker on 2011-06-15
when I tried to create a new partition on my HD I received a message that "all of the data would be erased"
So how do I create a smaller partition?

I have on the source HD ( that I am trying to partition to a smaller size so that I can clone it to a smaller HD ) a big 148 gig partition and a little tiny 2 Gig swap partition that is at the end ( or right hand side of the gparted screen ). When I select the 148 partition and select "create a new partition" I get the message about all data will be erased.

---

### Post by seawolf167 on 2011-06-15
You DO NOT want to create a new partition. You want to RESIZE you current partition.

Repeat: do not create a new partition. Resize it to a size smaller than your destination drive.

---

### Post by s1baker on 2011-06-15
when I select the large partition and try to select "resize" the "resize" selection is ghosted out

---

### Post by Jahid65 on 2011-06-15
you can use fsarchiver from live cd (if it installed in cd)
assume your root partition is in /dev/sda1. now mount another partition (not the root).
write this code in terminal as root to create a archive.
```
fsarchiver savefs /media/backup/gentoo-rootfs.fsa /dev/sda1
```if you have 4 cores then you can use this code
```
fsarchiver -j3 -o savefs /media/backup/gentoo-rootfs.fsa /dev/sda1
```to restore the archive
```
fsarchiver restfs /media/backup/gentoo-rootfs.fsa id=0,dest=/dev/sda1
```after restoring partition, you have to restore grub.

I have used fsarchiver with my opensuse root partition. It works fine.

---

### Post by seawolf167 on 2011-06-15
> **s1baker said:**
> when I select the large partition and try to select "resize" the "resize" selection is ghosted out

In order to resize a partition it needs to be unmounted - since this is your / partition, in order to unmount and resize the partition you'll need to boot up off a live cd (i.e. put in your original ubuntu installation cd and select the "Try Ubuntu Without Installing" option - then open GParted and resize)

---

### Post by s1baker on 2011-06-15
I used my install ISO disk to gparted my 165 HD to as small as it could go and when I tried to use clonezilla to clone it, it still would not let me do it. I think the 35G HD is just to little. I will have to just keep the programs on the 35G HD current manually,
program by program. 
But anyway, I think I have lost the GRUB on the 35G HD, as I can't get it to boot and my main 165G HD doesn't show it as available as sdb1. How to I install the GRUB II on it?

---

### Post by s1baker on 2011-06-15
Otherwords, when I try to boot up my little 35G HD, now I get
a black screen, like the old MS DOS command prompt window that says:

Error: Unknown Filesystem
Grub Rescue >

---

### Post by seawolf167 on 2011-06-15
Take a look at the [steps in this link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery%20Using%20the%20Ubuntu%20Alternate/Install%20CD").

---

