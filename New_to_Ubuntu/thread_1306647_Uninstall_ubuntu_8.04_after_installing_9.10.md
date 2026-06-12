---
title: "Uninstall ubuntu 8.04 after installing 9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by nishanvincent on 2009-10-30
Hi Guys, I really need some help to uninstall ubuntu 8.04.
I am using ubuntu 8.04 and windows vista with dual boot for long time now. I recently installed ubuntu 9.10 into my laptop using the CD. But now the ubuntu 8.04, 9.10 and windows vista, 3 operating system in the laptop. All I need is some advice how to uninstall ubuntu 8.04 from my laptop.
I would really appreciate if someone can help.
Thank You.

---

### Post by phillw on 2009-10-30
Hi.

Are you triple booting (i.e. you have access to all 3 o/s on boot time ?)

Phill.

---

### Post by nishanvincent on 2009-10-30
Yes Phill, I have triple booting currently and have access to all 3 o/s while booting. I want to remove the older ubuntu 8.04 version.

Nishan

---

### Post by nishanvincent on 2009-10-31
Hey guys can some help me to uninstall ubuntu 8.04, I have already explained the issue in my earlier post.

---

### Post by yeats on 2009-10-31
If you don't need to preserve anything (files, etc.) from the 8.04 partition, this *should* be as simple as running gparted and deleting/reformatting the 8.04 partition.  You'll need to be sure which partition is the correct one to remove, and that partition cannot be mounted when you do it.

---

### Post by kansasnoob on 2009-10-31
The most helpful thing for us would be to see a screenshot of gparted, so first install gparted in your new Karmic:

```
sudo apt-get install gparted
```

Then you'll find it in System > Administration.

If you take the screenshot from your running Karmic we'll be able to see which partitions are mounted, so we should be able to see which partitions can be deleted.

---

### Post by Zoot7 on 2009-10-31
Depending on how the partitions are set up the best thing to do would be just to delete the partition housing Hardy, and resize Karmic into the remaining space using Gparted.
Beware resizing the Vista partition - if you resize it with gparted (Or anything else other than the inbuilt Vista partitioner - which is useless) the bootloader has to be re-installed using the setup disk. Then that'll involve re-installing grub to the MBR, bit of a pain all thanks to Vista.
But if Vista is at the start or end of your disk, you'll be fine.
Actually can you post the output of
```
sudo fdisk -l
```

---

### Post by nishanvincent on 2009-10-31
Hey guys, thanks very much for all your suggestion. As suggested, I have put the output --> sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54065e39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   83  Linux
/dev/sda2   *        1020        5394    35142187+   6  FAT16
/dev/sda3            5395        5419      200812+  83  Linux
/dev/sda4            5420        9729    34620075    5  Extended
/dev/sda5            5420        6053     5092573+  8e  Linux LVM
/dev/sda6            6989        9609    21053151   83  Linux
/dev/sda7            9610        9729      963868+  82  Linux swap / Solaris
/dev/sda8            6054        6941     7132828+  83  Linux
/dev/sda9            6942        6988      377496   82  Linux swap / Solaris

Partition table entries are not in disk order

Hope u guys can give me some advice based on the above.

---

### Post by nishanvincent on 2009-10-31
I have attached the screenshot from my running karmic, hope u can give me some idea how to move ahead.
Thanks you guys.

> The most helpful thing for us would be to see a screenshot of gparted, so first install gparted in your new Karmic:

Code:

sudo apt-get install gparted

Then you'll find it in System > Administration.

If you take the screenshot from your running Karmic we'll be able to see which partitions are mounted, so we should be able to see which partitions can be deleted.

---

### Post by Zoot7 on 2009-10-31
Hardy looks like it's on the /dev/sda6 partition and it's swap looks to be on /dev/sda7 so I'd say delete those two, move the swap to the end and grow Karmic's ext4 partition into it. Click apply to carry out those actions.
Bear in mind you'll need to boot off a liveCD to grow Karmics partition as you won't be able to do so if it's mounted, it's not necessary, but there's no use having unallocated space on your hard drive. ;)

Then after that's finished, run
```
sudo update-grub
```

That should get rid of the Hardy entries in your Boot Menu.

---

### Post by nishanvincent on 2009-10-31
Here is it, output of df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             6.7G  2.8G  3.6G  44% /
udev                  245M  296K  244M   1% /dev
none                  245M  300K  244M   1% /dev/shm
none                  245M   88K  244M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw

> One last thing I forgot to get you to post the output of:
Code:

df -h

Sorry.

That'll let us know which one of those partitions is Hardy. 

---

### Post by Zoot7 on 2009-10-31
My bad. I didn't realize the mount points were shown in Gparted.

I'm slow today. :p

---

### Post by nishanvincent on 2009-10-31
Hi dude, I tried to delete using gparted both logged in Karmic and through live cd. It give the following message.

Unable to delete /dev/sda6!
Please unmount any logical partitions having a number higher than 6

Any idea how to delete this.

---

### Post by Zoot7 on 2009-10-31
Your swap partition was more than likely already mounted, right click on the swap and select "Swap-off", or in short make sure anything with the key icon is unmounted.
Then try and delete those two partitions, it should work then.

---

### Post by nishanvincent on 2009-10-31
I did all this deletion and allocating the space to ext4 using the live CD. But now the issue is if I run the -- sudo update-grub, its showing me this error message.
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

I cant login to the system since there is not grub menu now. I can login only by live CD.

---

### Post by Zoot7 on 2009-10-31
> **nishanvincent said:**
> I did all this deletion and allocating the space to ext4 using the live CD. But now the issue is if I run the -- sudo update-grub, its showing me this error message.
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

I cant login to the system since there is not grub menu now. I can login only by live CD.
So you can't Ubuntu now at all!? Are you sure you didn't delete karmics partition /dev/sda8 ?
It looks like you might have...

---

### Post by kansasnoob on 2009-10-31
> **nishanvincent said:**
> I did all this deletion and allocating the space to ext4 using the live CD. But now the issue is if I run the -- sudo update-grub, its showing me this error message.
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

I cant login to the system since there is not grub menu now. I can login only by live CD.

Just running "update-grub" from the live CD shouldn't work.

What happens when you actually try to reboot?

If it fails you'd have to mount and chroot from the live CD, but if that's necessary I first need to see the new output of:

```
sudo fdisk -l
```

---

### Post by nishanvincent on 2009-11-01
I am sure I did not delete the karmic partition. However I will send you the details soon, by end of day. Now I am at work, thanks anyways for all your help.

---

### Post by nishanvincent on 2009-11-01
Hey All u guys who suggested me with your expertise, thankx a lot.
I was not able to figure out what to do so at last I deleted all the partition except widows and reinstalled karmic. So all is fine now.
thankx once again to all of your out here.
regards,
Nishan

---

