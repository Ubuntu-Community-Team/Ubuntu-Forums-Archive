---
title: "How do I make an exact clone of a drive using dd?"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by daimaru on 2010-04-02
Hi I wanted to make a 1to1 copy of my newly installed windows 7 partition. (just so I can roll back to a previous state) --> just installed all  the necessary programs and wanted a clone of this disk so I can restore it. 

I would be restoring to the same harddisk partition as it resides on now.
What I though I would do after a bit of googling is 

My partitons:
```

sudo fdisk -l

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2fbe2fb

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sdc3           12750       60801   385977690    f  W95 Ext'd (LBA)
/dev/sdc5           12750       15299    20482843+  83  Linux
/dev/sdc6           15300       21674    51207156   83  Linux
/dev/sdc7           21675       21929     2048256   82  Linux swap / Solaris
/dev/sdc8           21930       34678   102406311    7  HPFS/NTFS
/dev/sdc9           34679       60801   209832966    7  HPFS/NTFS

```/dev/sdc8 is my windows 7 partition. MBR and grub are on /dev/sdc

Now to backup i thought to use 
```

sudo dd if=/dev/sdc8 of=/media/storage/backup.img bs=4096

```If i want to restore my win 7 partition in the future I would do: **[COLOR=Red] ( do I have to format the drive before I do this ? )[/COLOR]**
```

sudo dd if=/media/storage/backup.img of=/dev/sdc8

```my question : Is this at all right? I have no idea if i should try it or not. I made a backup image already, but I am not sure if everything will work once I copy that image back to the /dev/sdc8 device. 

2nd question : is there a way to speed up dd command? It seems to have to do with the bs= byte size option. The bigger the faster. Is there a way to set the byte size as big as my win 7 partition and then having dd run super fast? If so how do i determine the exact byte size I have to use? (34678 - 21930)*(16065 * 512) = 104855869440   ???
```

sudo dd if=/dev/sdc8 of=/media/storage/backup.img bs=104855869440

```would the above make dd run extra fast or does this not work at all?

Any help is appreciated. Thx

---

### Post by SoloSalsa on 2010-04-02
You have the general in/out command correct.  You should not have need to reformat the disk or partition.  At a later date when you restore the image, the worst that could happen is the bootloader might not correctly point to your Windows 7 partition.  There are ways to fix that (for Windows only and for multiple OS) if it ever occurs.  If you only restore Windows to its current state, and everything else on the disk has not changed, then there should be no problem when you restore: dd will cover over everything in the partition, making a reformat unnecessary.

You have a very good question about byte size.  When someone who knows replies, then I will learn the answer, too.

---

### Post by daimaru on 2010-04-02
thanks for the reply. yeah the byte size thing seems important, when running dd without it I guess it goes with a very low byte size and my read write speed is at around 5mb/sec which would take ages to copy a 100gb or larger partition. Using bs=4096 I got 34mb/sec using bs=8192 gave me 36mb/sec... 

so larger seems to be better. But the question remains if when choosing a too big byte size and my partitions byte size is not dividable by this number that maybe the copying wont work?

---

### Post by srs5694 on 2010-04-02
The "bs" option is better interpreted as "block size," not "byte size." AFAIK, changing its value will not speed up the operation.

What *can* speed up the operation is using ntfsclone rather than dd. This program backs up only the used sectors on an NTFS partition. It's installed as part of the ntfsprogs package. Type "man ntfsclone" for details. There are some examples at the end of the man page, such as:

```

ntfsclone --save-image --output backup.img /dev/hda1

```This is what you'd want to use, changing /dev/hda1 to /dev/sdc8 in your case. You'd presumably want a separate backup of /dev/sdc1, too, since it must be involved in your Windows boot process, and perhaps /dev/sdc9, depending on what it holds.

Edit: Oh, and please note that Windows may not be bootable when you restore it, depending on where it's restored. (If you change the first sector of the partition, you'll have problems.) Windows 7 seems to be *very* hard to restore to bootability when this happens; I've never succeeded, despite having followed two or three "sure-fire" procedures I found on the Internet.

---

### Post by oldfred on 2010-04-02
To add to the caveats that srs5694 made. Your windows partition is in sdc8 which is a logical partition. You are booting thru a primary partition and some of the key boot files have been moved to the primary partition. Your win7 will not boot on its own.

Only one or two of the people who post here have been able to get a windows to boot from an extended partition after users deleted the primary boot partition or wanted to separtely boot the extended partition. Windows says its not possible but whatever it is not easy.

If they are both primary partitions, then two copies of windows can easily be split or repaired to boot separately. 

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by daimaru on 2010-04-03
thanks for the replies. I'll take a closer look at the ntfsclone program. As to the difficulty of getting bootloader back. I was not planning on clearing the MBR I just want to replace the existing partition with an image of that partition form an earlier date. 

sdc8 is win7 somewhere i got winXP and of course ubuntu. When I installed win 7 it of course assumed that only windows exists on this planet and wiped my MBR to include winxp and win7 . So I reinstalled grub 2 and got all the stuff there. I am guessing that the grub stuff is installed in the first block of the sdc disk. So if I replace the sdc8 win7 patition with an older image of that partition it should be ok right? 

well thanks anyways I guess I'll just have to give it a try. And see what happens. I am hoping it will work and thanks again for the ntfsclone suggestion , will save loads of time if I dont have to copy all the empty sectors.

---

