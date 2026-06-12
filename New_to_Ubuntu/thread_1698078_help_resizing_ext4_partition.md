---
title: "help resizing ext4 partition"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by bestron on 2011-03-01
[B]My ext4 partition where I installed ubuntu 10.10 has run out of space and I wanted to resize it

I used the win 7 tool in shrinking an ntfs partition so I now have an allocated space that I wanted

but of course win didn't recognize the ext4

then inserted the live CD so that I can resize the partition unmounted 
I used Gparted to do it but it has put a maximum size which is its actual size now, I can only shrink it

what to do to enlarge it?:confused:
[/B]

---

### Post by jeremyjjbrown on 2011-03-01
Can you describe your partition table?

Open a terminal and type

```
sudo fdisk -l
```

lower case l not #1

and post the results...

---

### Post by turtle153 on 2011-03-01
Not sure it will help, but I prefer using the GParted on my computer installation. Installing it onto the computer runs much faster than off a CD

---

### Post by bestron on 2011-03-01
here's the output of the command u gave me

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000efe4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       11632    93326336    7  HPFS/NTFS
/dev/sda3           12546       35891   187516928    7  HPFS/NTFS
/dev/sda4           35891       60802   200097793    f  W95 Ext'd (LBA)
/dev/sda5           35891       59235   187516928    7  HPFS/NTFS
/dev/sda6           60304       60802     3998720   82  Linux swap / Solaris
/dev/sda7           59236       60304     8580096   83  Linux

Partition table entries are not in disk order

```

If u ask me, yes I've had problems with my hard disk before.

> I prefer using the GParted on my computer installation. Installing it onto the computer runs much faster than off a CD

this wont work, I want to resize the working partition

---

### Post by jeremyjjbrown on 2011-03-02
I really doubt you need ~4 gb of swap. You can probably shrink that down to 1gb and clear out 3gb of space. Many people say equal your swap with your memory but I don't think that's true anymore. Especially if you don't leave a lot of apps and files open when you hibernate. You can check your memory right before you hibernate if you like. Just enter "free -m" in a terminal to see the memory usage in mb. If you want to check your virtual memory you can use "vmstat". I've installed Ubuntu on over a dozen machines and I never use more than 1gb of swap anymore. I've never had a problem because of it. Not even once.

---

### Post by slooksterpsv on 2011-03-02
Ok, so someone please correct me if I'm wrong (which I may be), but where the Cylinders for the drive are at the end for Ubuntu, the only way to resize is to reinstall Ubuntu correct?

Cause resizing can only go larger on the drive so from cylinder 59236 on up, and not dip down below 59236 without redoing the partitions for Ubuntu.

Again, correct me if I'm wrong.

The other option you have is you can move your files (like documents downloads pictures music videos) onto your windows partition, use pysdm to have it automatically mount your windows drive at boot, and have symbolic links to your user folders on the windows drive.

The benefit to that is any files you need are like they're in the respective directories, but on a different drive. If you want to do something like that, I can help you out.

That's how I do it on my computer downstairs (dual-boot windows and Ubuntu)

---

### Post by bestron on 2011-03-02
well then, if I free 3 gigs from my swap partition I still have the same problem : unallocated space which I can't use to resize the ext4 partition that has a maximum size

@[slooksterpsv]("http://ubuntuforums.org/member.php?u=38762") I'm not so good in dealing with partitions excuse me but I can't get the idea of the cylinders thing, so if you can explain a little

and if moving files to windows partitions works good and can be undone, yes help me out

---

### Post by jeremyjjbrown on 2011-03-02
I don't see any unallocated space on that partition table. You have to have create unallocated space next to the partition you want to grow before you can grow it. The maximum size of an ext4 partition is bigger than the largest HD in the universe. It's only limit is the space you leave for it.

Is the area that is occupied by sda4 and sda5 the space that you cleared from windows? Are you storing files on that partition? Perhaps the WIN7 tool made the space and them partitioned it. If that is the space you wanted to add to ubuntu you have to delete sda4 and 5 in gparted and use the space to grow sda7. Make sure you don't need that partition because once you delete it is is hard as hell to get the info back. Backup everything you can before you do it.

If those partitions contain data you want to keep you can also clear space by deleting the swap in Gparted and then growing the EXT4 Linux partition next to it. Then recreating the swap from what you leave.

---

### Post by bestron on 2011-03-02
so you are saying that I can't move the unallocated space?
I do have this space but I've taken it from that 89 gigs partition and it's next to it

here's the gparted graph and the win tool graph if that helps

I'm nearly sure that there's something wrong with that disk, but it works fine

[IMG]http://img97.imageshack.us/img97/2136/screenshotop.jpg[/IMG]


[IMG]http://img856.imageshack.us/img856/6474/capturem.png[/IMG]

---

### Post by jeremyjjbrown on 2011-03-02
OK So you want to use the 7gb of unallocated.

There are two problems with this. 

1. it is not next to the ext4 you want to add to.

2. it is not on the extended partition (sda4) that holds the logical partition sda7 you want to grow.

you have two obvious choices.

1. shrink sda5 and grow sda7 
2. delete swap and grow sda7 and recreate swap

---

### Post by bestron on 2011-03-02
-then the 7.0 unallocated gbs has no use and I have to return them to sda2, did I get it right?

-what's the meaning of this 1.02 mb of unallocated space that appear in gparted but not in windows tool
will it merge with the space that results from deleting the swap?

sorry if I bored you, but I really am a beginner !

---

### Post by jeremyjjbrown on 2011-03-02
Using the 7gbs would mean moving a lot of stuff around and is not what I would want to do.

The small 1mb is an area that is reserved on the disk to store things like the sector table. The table of contents that the disk uses to read itself.

Stick with it your are learning! I also learned from people here and from banging my head against the keyboard ;)

Good Luck

---

### Post by tharunkumarkmr on 2011-04-26
> **jeremyjjbrown said:**
> Can you describe your partition table?

Open a terminal and type

```
sudo fdisk -l
```lower case l not #1

and post the results...



Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d8010

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38149   306425856   83  Linux
/dev/sda2           38149       38914     6142977    5  Extended
/dev/sda5           38149       38914     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4   *           1         246     1974240+   6  FAT16
Partition 4 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 200, 19)

---

