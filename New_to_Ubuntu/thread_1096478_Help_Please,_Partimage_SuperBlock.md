---
title: "Help Please, Partimage SuperBlock ?"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by altech6983 on 2009-03-14
Hey guys, need your help bad. I am in the process of trying to backup my system as I have crashed it twice in the last three weeks from fooling with things I shouldn't be (or at least at this stage of my knowledge ;) ).

What I want to do is use partimage to create a image of the Ubuntu installation and that way if I do mess something up then I can just re-image it.

Here is fdisk -l results:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d6348b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda3           10200       60801   406460565    5  Extended
/dev/sda5           10200       31871   174080308+  83  Linux
/dev/sda6           31872       32844     7815591   82  Linux swap / Solaris
/dev/sda7           32845       50603   142649136    7  HPFS/NTFS
/dev/sda8           50604       60801    81915403+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdc5               2       19457   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000207286272 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34078fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS

```

This is what I am doing, I boot in to Ubuntu's live CD, then I install partimage. I use the arrow down key to get to sda5 then I hit the right arrow key. I have sda8 mounted to Backup in Ubuntu, so I type /media/Backup/backup-3-14-09.gz in the Image file box. then I hit F5 (it is set to save) then gzip is selected.

Then I uncheck the Enter Description box with the spacebar. I then choose Automatic split with the space (doesn't matter, I have also chosen the split into files size is 80000MB partition size is 73000MB) I then hit F5.

This is when I get: Error "Can't read SuperBlock" [Cancel]

I hit enter and it takes me back to the prompt.

I have searched high and low and can't find anything about SuperBlock and partimage together, tons about mounting and SuperBlock errors but nothing to help me and what baffles me is that Ubuntu mounts the partition just fine.

I would love to use partimage so I hope someone here can help but even if you can't could you suggest other programs that do the same as partimage please.

---

### Post by RetchingRabbit on 2009-03-14
Ya know, I hope this is the kind of answer yer looking for...
I don't know about partimage, but if you are just trying to copy sda8 ( I'm guessing that's your /home ?) then you can do that with a  number of other programs, very easily. 

```
rsync -av /home <target>
```Where <target> is the destination that you want the files backed up to. There are a large number of utilities built into Linux to do this sort of thing., but I tend to like rsync for this type of operation.
You can also google or man cp, tar, cpio, and dd, for starters.
:)

---

### Post by altech6983 on 2009-03-15
I have seen rsync but I am not just trying to copy my Home folder, sda8 is the location I want to backup to, and sda5 is the partition I want to backup, sda5 being / (root).

I didn't created a separate partition for home or anything like that.

If I was going to do a small non-system restore backup I would use tar, I kind of like it, I actually wrote my own tar backup script for bash (simple little script really).

What I really wanted was to have a partition image so that if it breaks then I just boot to a live CD and say, put this image on to this partition, reboot, and then everything would be like it was when I made the image.

Thanks for the suggestion though.

---

### Post by theozzlives on 2009-03-15
[Remastersys]("http://www.remastersys.klikit-linux.com/ubuntu.html")

---

### Post by altech6983 on 2009-03-15
Thanks but tried that one, loved the idea but it has a 4GB limit, if you know a way to get around that then I would love to use it.

---

