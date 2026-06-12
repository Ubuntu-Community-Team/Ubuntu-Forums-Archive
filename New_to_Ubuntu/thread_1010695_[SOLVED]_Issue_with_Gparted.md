---
title: "[SOLVED] Issue with Gparted"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-14
I am not sure if I have another option or not. I tried this code "sudo gparted" and I got this. 
(gpartedbin:6333): Gtk-WARNING **: cannot open display: A similar ERROR occured also while I was trying to boot from a gparted boot disk. I am using an old Riva TNT2 AGP card.



Apparently gparted does not like my video card. Any suggestins? Other than switching video cards...

---

### Post by pshootr on 2008-12-14
I tryed a methed mentioned in another thread and here is what I got.


Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Now what do I do? DZamn newbies lol  Thanks for any suggestions.

---

### Post by Michael.Godawski on 2008-12-14
hi pshootr, 
two questions:

What do you want to do with Gparted? and
Are you able to boot with the LiveCD? because, when I remember correctly, there is also Gparted on the Live Session.

---

### Post by Bachstelze on 2008-12-14
You should do

```
gksudo gparted
```

The errors will also appear, but you can safely ignore them.

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> hi pshootr, 
two questions:

What do you want to do with Gparted? and
Are you able to boot with the LiveCD? because, when I remember correctly, there is also Gparted on the Live Session.

First of all I would like to thank you for your intrest in helping me. As far as better aiding you in your attemp, I would say that I have used dban as a second resorce after a failure trying to boot from a gpated disk.  Having that said, I have used dban to "blank" the drive. In other words, I did not choose to do a full wipe....
Anyhow, now that I have blanked the drive. What is my next step to make this drive usable?

---

### Post by pshootr on 2008-12-14
> **HymnToLife said:**
> You should do

```
gksudo gparted
```

The errors will also appear, but you can safely ignore them.

"safely" Thank you.

UPDATE: 
(gksudo:6772): Gtk-WARNING **: cannot open display:

This still occurs. How shall I ignore this?

---

### Post by Michael.Godawski on 2008-12-14
> Anyhow, now that I have blanked the drive. What is my next step to make this drive usable? 	

If you have a blank drive and you hopefully want to install Ubuntu on it, just download the latest version of it ( intrepid 8.10) and begin the installation; there is a step called partitioning which will create the needed type of partitions for Ubuntu.

If you have other ideas in mind please let us know.

---

### Post by pshootr on 2008-12-14
I have a server install on a 4 gig drive. No problem. I am trying to add a storage drive. Hence the drive I am working on.
Sorry for not being more clear from the start.
BTW Just hand over the beans!

---

### Post by pshootr on 2008-12-14
Yoohoo. Dont go to sleep on me now :KS

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> If you have a blank drive and you hopefully want to install Ubuntu on it, just download the latest version of it ( intrepid 8.10) and begin the installation; there is a step called partitioning which will create the needed type of partitions for Ubuntu.

If you have other ideas in mind please let us know.

I do have another idea. How about you suggest a method other than Gparted to do this from the server?
BTW my sever IS intrepid.

---

### Post by iKonaK on 2008-12-14
> **pshootr said:**
> I do have another idea. How about you suggest a method other than Gparted to do this from the server?
BTW my sever IS intrepid.

1 > fdisk -l (to list available drives/partitions)
2 > umount /dev/sdx1 (unmount the partition you want to touch)
3 > fdisk /dev/sdx (you'll have a list of commands)

hope it helps...
EDIT: "sudo su" - first, so you would have root powers ;)

---

### Post by Michael.Godawski on 2008-12-14
So you have a server install with only  command line interface?

then try this command:
```
sudo mke2fs -j /dev/sdb
```This will create a ext3 partition.

```
sudo mkfs.msdos /dev/sdb
```This will create a fat32 partition.

edit: corrected the ext3 command sry.

---

### Post by pshootr on 2008-12-14
> **iKonaK said:**
> 1 > fdisk -l (to list available drives/partitions)
2 > umount /dev/sdx1 (unmount the partition you want to touch)
3 > fdisk /dev/sdx (you'll have a list of commands)

hope it helps...
EDIT: "sudo su" - first, so you would have root powers ;)

Thanks KonaK. The disk I am trying to format is not mounted yet.
 I will try fdisk /dev/sdx.exmp

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> So you have a server install with only  command line interface?

then try this command:
```
sudo mke2fs -t vfat /dev/sdb
```
This will create a ext3 partition.

```
sudo mkfs.msdos /dev/sdb
```
This will create a fat32 partition.

Ok, I will check out these options as well. Thank you for the tips. I am ubutuholic at this point, so don't take any erasional comments personaly. :lolflag:

---

### Post by plucky on 2008-12-14
From a terminal you can use the mkfs.ext3 command to create a linux file system on the disk.

```
sudo mkfs.ext3 /dev/sdb1
``` to create an ext3 file system.


See **man mkfs** for other options.

Good Luck

---

### Post by pshootr on 2008-12-14
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2444624 inodes, 9770670 blocks
488533 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
299 block groups
32768 blocks per group, 32768 fragments per group
8176 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

 Ummm, did I do good?

---

### Post by Michael.Godawski on 2008-12-14
Which command did you use?
run```
sudo fdisk -l 
```to check what new partition you have created?
By the way I have corrected my first command for creating ext3, sry.

---

### Post by pshootr on 2008-12-14
Ok, tryed this

 sudo mkfs.ext3 /dev/sdb
mke2fs 1.41.3 (12-Oct-2008)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2444624 inodes, 9770670 blocks
488533 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
299 block groups
32768 blocks per group, 32768 fragments per group
8176 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 32 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


$ sudo fdisk -l

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by pshootr on 2008-12-14
Does that mean I am ready to mount?

sudo mount /dev/mount/path/sdb

Will this do it?

<Disk /dev/sdb doesn't contain a valid partition table>

This is what I find unsatisfactory...

---

### Post by Michael.Godawski on 2008-12-14
We are almost there:

run 

```
sudo fdisk /dev/sdb
```
then 
a (for add)
1 (partition number)
then let it cover the entire disk, simply accept default start & end.
w (write and exit)

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> We are almost there:

run 

```
sudo fdisk /dev/sdb
```
then 
a (for add)
1 (partition number)
then let it cover the entire disk, simply accept default start & end.
w (write and exit)

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c08ec43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1           0    0  Empty

Edit: Attention---->Partition 1 does not end on cylinder boundary.

<then let it cover the entire disk, simply accept default start & end.>

This part does not seem to take place..

---

### Post by Michael.Godawski on 2008-12-14
wow, 
I am learning too, it is fun with you because you have a separate drive, so we can make all this dangerous stuff without consequences.

once again, this time it should work

```
sudo fdisk /dev/sdb
```
**n(for add)**
1 (partition number)
then let it cover the entire disk, simply accept default start & end.
w (write and exit)

---

### Post by pshootr on 2008-12-14
LOL yes fun indeed. Thanks for your patronage...:popcorn:

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> wow, 
I am learning too, it is fun with you because you have a separate drive, so we can make all this dangerous stuff without consequences.

once again, this time it should work

```
sudo fdisk /dev/sdb
```
**n(for add)**
1 (partition number)
then let it cover the entire disk, simply accept default start & end.
w (write and exit)

<<Invalid partition number for type `1'>>
Command action
   e   extended
   p   primary partition (1-4)

Guess I should choose "e"

---

### Post by pshootr on 2008-12-14
Ok, looks we may have done it. 

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c08ec43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    5  Extended

How does this look?

PS if you want to have some fun. Install another drive for file serving. :) hehe

---

### Post by Michael.Godawski on 2008-12-14
The difference between "primary" and "extended" is simply that there can be a max of 4 primary partitions, and a lot of extended, so if you're going to have more than 4 partitions on one drive, use extended for the excessing.

edit: looks not bad :)
try to move some files to it, and do some work to see if it really works

---

### Post by pshootr on 2008-12-14
Correct me if I'm wrong, but is would seem that we have succeeded. Thank you very very much for your help. You :guitar:

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> The difference between "primary" and "extended" is simply that there can be a max of 4 primary partitions, and a lot of extended, so if you're going to have more than 4 partitions on one drive, use extended for the excessing.

Ah, So I really should have chosen primary for this drive being that it only has 1 partition?

---

### Post by Michael.Godawski on 2008-12-14
> Ah, So I really should have chosen primary for this drive being that it only has 1 partition?     Well if everything is working leave it as it is. The drive is not that big with 40 GB so you probably won't add more partitions to it.

You are welcome.

---

### Post by pshootr on 2008-12-14
> **Michael.Godawski said:**
> Well if everything is working leave it as it is. The drive is not that big with 40 GB so you probably won't add more partitions to it.

Yeah sounds good for now. I have to delete the newly created partition (which I am unsure how to do rite now) in order to change it to primary...

Unfortunatly I must go to bed now.. I hope you realize how much I appreciate your help tonight. Thanks alot bud..

---

### Post by pshootr on 2008-12-14
I will have to configure samba to test the server, once I do, I will update this thread. Thanks again bro.

---

### Post by Michael.Godawski on 2008-12-14
No problem; it's my job:p.

When you run sudo fdisk /dev/sdb
and then press m you get to the help menu, which lists all possible options.
d is for deleting partitions.

---

