---
title: "[SOLVED] Resizing an extended partition"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by rlogan on 2008-12-09
Hi all

I have looked through the forums for an answer to this one but it all appears to be something that we can't do at the moment.

On our laptop we have 4 partitions, sda1 is the vista recovery area, sda2 is effectively the c drive (ntfs) partition , sda3 is data partition for windows (ntfs) and sda4 is the Ubuntu partition. I have made some space in front of sda4 but I am unable to relocate the start of the partition with qparted when running from a live cd. 

sda4 being an extended partition is broken down into sda5 is the ext3 Ubuntu partition and sda 6 is the swap partition.

If anyone has any thoughts or suggestions on increasing the size of the extended partition I would gratefully accept them.

If all else fails I guess the last option is a clean install but what a hassle.

Many thanks

Richard

---

### Post by stevoo on 2008-12-09
This will be a length process, so 
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

but it could end up screwing a lot of things ... so backup what ever is important on an external disk !

---

### Post by rlogan on 2008-12-09
Thanks for taking the time to reply, it is appreciated !!!

I see what you mean, it is quite lengthy to say the least. I must admit I am concerned about trying to change the extended partition. But I guess if all else fails there is always a clean install.

Will check out the process properly tomorrow when I can suss it out some more when I am not so tired.

I have also contemplated getting a bigger drive for this machine, as 80gb doesn't go far these days. If that was to happen would make it a Ubuntu boot only and keep the old hard drive in case I need a warranty job.

Cheers

Richard

---

### Post by bumanie on 2008-12-09
Personally, I don't think you need to go to the lengths as described in that article. If you have space next to the extended partition, from a gparted live cd you should be able to enlarge the extended partition with the 'slider tool' and then enlarge the ubuntu partition within the extended partition later. That is what will take the time, as it contains a filesystem the extending process is slow. I am sure I did this some time ago and did not have to 'jump through hoops' to get it done. But do back up important files first - partitioning can go wrong. You cannot delete the extended partition without getting rid of the filesystems contained within - so don't try that!

---

### Post by mikechant on 2008-12-09
Given that you're running from the live CD this should be very easy. I'd use Gparted rather than qparted (on the System->Admin menu as 'partitioning'). 
The only thing that might cause a problem is that the swap partition will be in use by the live CD. This will show up as a 'lock' icon against the swap partition in Gparted. Just right-click on this partition and select swapoff. Next you should be able to stretch the extended partition, sda4, to the left to take up the free space. That should be a very quick operation since no data moving is involved.
Now sda4 should contain free space followed by sda5 and sda6and you can do anything you need - create extra logical partitions or move/extend the existing ones. But note that moving a partition with data in (such as sda5) can take a long time, and must not be interupted if you want to avoid data loss.

---

### Post by caljohnsmith on 2008-12-09
I agree with Bumanie and Mikechant, I don't think you need to go through all those manual steps described in that linked tutorial; using Ubuntu's partition editor gparted (System > Admin > Partition Editor) from the Live CD should work fine. One thing you should be aware of is that when you resize your Ubuntu/swap partitions, the UUIDs will change. So before doing the resizing, I would recommend opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo blkid
```
And copy the UUIDs of your Ubuntu/swap partition to some safe place, then do your partition resizing, and then for the Ubuntu ext2/ext3 partitions you can do:
```
sudo tune2fs -U "<original Ubuntu UUID>" /dev/sdXY
```
Just copy/paste the original UUID into that command above and change sdXY to the Ubuntu partition. Then for the swap partition:
```
sudo swapoff -a
sudo mkswap -U "<original swap UUID>" /dev/sdXY
```
And replace sdXY above with the swap partition. By restoring the original UUIDs of the Ubuntu/swap partitions, you won't have to mess with changing your /etc/fstab, /boot/grub/menu.lst, regenerating the initrd images, etc. afterwards to reflect the new UUIDs. Anyway, let us know how it goes. :)

---

### Post by rlogan on 2008-12-10
> **bumanie said:**
> Personally, I don't think you need to go to the lengths as described in that article. If you have space next to the extended partition, from a gparted live cd you should be able to enlarge the extended partition with the 'slider tool' and then enlarge the ubuntu partition within the extended partition later. That is what will take the time, as it contains a filesystem the extending process is slow. I am sure I did this some time ago and did not have to 'jump through hoops' to get it done. But do back up important files first - partitioning can go wrong. You cannot delete the extended partition without getting rid of the filesystems contained within - so don't try that!

Thanks for the reply !!!

I have been using gparted in an attempt to change partition size but with no luck.

Yeah it takes time to say the least, no the first time I have shuffled partitions and prob won't be the last on the laptop.

I wasn't going to delete the extended parition, thats a no no.

Thanks for your help

Cheers 

Richard

Many thanks

---

### Post by rlogan on 2008-12-10
> **mikechant said:**
> Given that you're running from the live CD this should be very easy. I'd use Gparted rather than qparted (on the System->Admin menu as 'partitioning'). 
The only thing that might cause a problem is that the swap partition will be in use by the live CD. This will show up as a 'lock' icon against the swap partition in Gparted. Just right-click on this partition and select swapoff. Next you should be able to stretch the extended partition, sda4, to the left to take up the free space. That should be a very quick operation since no data moving is involved.
Now sda4 should contain free space followed by sda5 and sda6and you can do anything you need - create extra logical partitions or move/extend the existing ones. But note that moving a partition with data in (such as sda5) can take a long time, and must not be interupted if you want to avoid data loss.

Will give this a go tomorrow, cheers for the suggestions

Will let you know how I go !!!

Many thanks

Richard

---

### Post by rlogan on 2008-12-10
> **caljohnsmith said:**
> I agree with Bumanie and Mikechant, I don't think you need to go through all those manual steps described in that linked tutorial; using Ubuntu's partition editor gparted (System > Admin > Partition Editor) from the Live CD should work fine. One thing you should be aware of is that when you resize your Ubuntu/swap partitions, the UUIDs will change. So before doing the resizing, I would recommend opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo blkid
```
And copy the UUIDs of your Ubuntu/swap partition to some safe place, then do your partition resizing, and then you can do:
```
sudo tune2fs -U "<desired UUID>" /dev/sdXY
```
For the Ubuntu and swap partitions to restore their original UUIDs. Just copy/paste the original UUID into that command above and change sdXY to the Ubuntu/swap partition, and then you won't have to mess with changing your /etc/fstab, /boot/grub/menu.lst, etc. afterwards to reflect the new UUIDs. Anyway, let us know how it goes. :)



Thanks for the reply !!!

Will take your suggestion on board and give it a whirl. Will let you know what goes.

My only questions is what is a UUID ? Sorry for my ignorance !!!

Many thanks

Cheers

Richard

---

### Post by caljohnsmith on 2008-12-10
> **rlogan said:**
> Thanks for the reply !!!

Will take your suggestion on board and give it a whirl. Will let you know what goes.

My only questions is what is a UUID ? Sorry for my ignorance !!!

Many thanks

Cheers

Richard
UUID is an acronym for "Universally Unique IDentifier"; linux assigns each of your partitions a UUID to more easily keep track of which partition is which. One of the reasons for doing this is because your Ubuntu partition might originally be on sdb5 for example, but then when you add another HDD to your setup, all of the sudden Ubuntu is on sdc5; using UUIDs prevents problems from happening in those situations since the Ubuntu partition UUID won't change when you add a new HDD. You might also want to see this [web page on UUIDs]("https://help.ubuntu.com/community/UsingUUID") at the Ubuntu help website for a little more info. :)

---

### Post by Xenokite on 2008-12-10
> **caljohnsmith said:**
> I agree with Bumanie and Mikechant, I don't think you need to go through all those manual steps described in that linked tutorial; using Ubuntu's partition editor gparted (System > Admin > Partition Editor) from the Live CD should work fine. One thing you should be aware of is that when you resize your Ubuntu/swap partitions, the UUIDs will change. So before doing the resizing, I would recommend opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo blkid
```
And copy the UUIDs of your Ubuntu/swap partition to some safe place, then do your partition resizing, and then you can do:
```
sudo tune2fs -U "<desired UUID>" /dev/sdXY
```
For the Ubuntu and swap partitions to restore their original UUIDs. Just copy/paste the original UUID into that command above and change sdXY to the Ubuntu/swap partition, and then you won't have to mess with changing your /etc/fstab, /boot/grub/menu.lst, etc. afterwards to reflect the new UUIDs. Anyway, let us know how it goes. :)

i'm going to try this i have a lot of space but yet the OS is stating i'm out.

---

### Post by rlogan on 2008-12-10
Hi all

All sorted here, big thanks to Bumanie, Mikechant and caljohnsmith for all of your help.

Turning off the swap did the trick, so partition resized. The sudo blkid and sudo tune2fs -U "<desired UUID>" /dev/sdXY were not needed, but was a really good suggestion to be safe and sure than to be a little reckless. Once resize was completed with gparted I just turned swap back on all is a source of joy now.

Will now read up on UUID's !!!

Thanks to all of you who helped, you guys are awesome !!!

Cheers

Richard

---

