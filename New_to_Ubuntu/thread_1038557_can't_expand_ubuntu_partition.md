---
title: "can't expand ubuntu partition"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-12
well i wanted to schrink vista and expand ubuntu so i booted from live cd ran partition editor and schrunk vista by 30gb but when i go to expand my ubuntu partition it doesn't give me the option of increasing the partition please help

---

### Post by whoop on 2009-01-12
Are you sure everything is unmounted. I believe that LiveCD uses linux swap if it finds it on hard disk.
Also first resize extended then resize ext(x)

---

### Post by mamamia88 on 2009-01-12
heres what i did i booted from live cd and went to partition editor.  i then schrunk the ntfs partition by 30gb.  then i go to my ext3 partition which is ubuntu right but it won't let me increase the size only decrease the size.  am i doing this right?

---

### Post by 1packer on 2009-01-12
Is there free space next to the partition? That is the only error I can think of right away that would prevent it from expanding but not shrinking.

---

### Post by drs305 on 2009-01-12
Can you post a snapshot of the gparted setup? Otherwise post the results of:
```
sudo fdisk -l
```

Are you trying to take space from a primary partition to expand a logical one?

---

### Post by mamamia88 on 2009-01-12
i honestly have no idea what i am doing wrong here but i can't increase the size only decrease itdubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e721e72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9610    77190276    7  HPFS/NTFS
/dev/sda2           13527       14593     8570677+   7  HPFS/NTFS
/dev/sda3            9611       13526    31455270    5  Extended
/dev/sda5            9611       13359    30113811   83  Linux
/dev/sda6           13360       13526     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by whoop on 2009-01-12
> **mamamia88 said:**
> i honestly have no idea what i am doing wrong here but i can't increase the size only decrease itdubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e721e72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9610    77190276    7  HPFS/NTFS
/dev/sda2           13527       14593     8570677+   7  HPFS/NTFS
/dev/sda3            9611       13526    31455270    5  Extended
/dev/sda5            9611       13359    30113811   83  Linux
/dev/sda6           13360       13526     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

So can you increase the size of extended as I said? Then increase Linux

---

### Post by mamamia88 on 2009-01-12
> **whoop said:**
> So can you increase the size of extended as I said? Then increase Linux

no every option is greyed out when i click extended

---

### Post by sam1948 on 2009-01-12
if you running XP as well 
it might not have been shut down properly 
run it(XP) and shut down in the traditional way 
(_**not **_reset button)
Start ==> shut down
this might work
in any case do not try to change partition of a running system
run an ubuntu live cd or gparted live cd and do it from there

---

### Post by mamamia88 on 2009-01-12
running vista and thats what i did

---

### Post by whoop on 2009-01-12
Did you unmount the drive as i said before attempting to resize extended and linux?

---

### Post by minsf on 2009-01-13
so it seems you currently have about 79G in the main windows partition and about 30G in the main linux partition. it is my understanding that you want to have 49G for your main windows partition and 60G for your main linux partition, is that right? 
let's start from the first step, just shrinking windows. first be sure that the hard drive is unmounted. this is very important. if you boot with a live cd, then by default it should be unmounted. but it wouldnt hurt to run ```
sudo umount /dev/sda1
``` just to be sure that it is unmounted. similarly please unmount the other partitions with "sudo umount /dev/sda2" and "sudo /dev/sda3" etc.  
now, can you just shrink windows by 30G with gparted (the Partition Editor in ubuntu's live cd) and press apply (before you make any changes to the size of the linux partition), or are you having problems with shrinking too? of course, be sure to shrink it "from the end" and dont move it's starting point. dont forget to press "apply". after you do this, please post here the results of "sudo fdisk -l" again.

---

### Post by minsf on 2009-01-13
guys, does the live cd ever use the swap partition on the hard drive? is it safe for him to unmount it, that is to run "sudo umount /dev/sda6" or is it needed by the live cd?

---

### Post by whoop on 2009-01-13
I have unmounted all my drives when using livecd and done partitioning afterwords, it works fine. Livecd is known to use swap from disk when it detects it, but it is not necessary.

---

### Post by drs305 on 2009-01-13
It is probable that the free space is not in the extended partition (the area with the light blue border) while your linux partition is within the extended partition. You can't expand the ubuntu partition by taking freespace from outside the extended partition (the light blue bordered area). 

I partitioned a thumb drive to replicate what I think is your situation. sda2 may or may not be in the proper position but it doesn't really matter for the purposes of this post. See Screenshot-1.png

The freespace must be placed within the extended partition first. You do this by getting the freespace up against the extended partition, then expanding the extended partition to the left to include this freespace. 
See Screenshot-2.png

Once the freespace is inside the extended partition and next to the linux partition, you will be able to expand the linux partition. Here are the pix of what I am guessing is your situation. You can let us know. Again, if you can post a pic of your gparted image it would explain a lot.

---

### Post by minsf on 2009-01-14
right drs305, except it seems to me (from his fdisk -l output) that his second windows partition is at the end. that is, the /dev/sdc2 in your picture will be after the linux/extended in his gpart picture.
whoop, thanks for the info about the swap.
like you both said, it seems like he's going to have to move the expand the extended, and then expand the linux inside it.
but let's take him step by step. 
that's why i suggested that he first run "sudo umount /dev/sda*" from a live cd boot(just to be sure), then shrink the /dev/sda1 by 30G, and then post his "fdisk -l". 
then, when we see the unalocated space we can continue.

---

### Post by drs305 on 2009-01-15
minsf,

I think he has already reduced the size by 30GB. You are correct that the posted results show a primary partition at the end of the disk. There is also the statement saying that the partitions are not in order. That can be fixed from within the 'sudo fsck /dev/sda' command but I won't go there unless asked.

My last post was more or less a generic way to go about getting free space into an extended partition and then expanding a logical primary partition. I will monitor this post but will not interfere with things further so that the OP doesn't get help from too many different directions.

Thanks for assisting him/her with this.

---

### Post by minsf on 2009-01-15
i think we should consider this thread as SOLVED.

FIRST, because the original poster, mamamia, seem to have gone in different directions, as can be seen from 
[http://ubuntuforums.org/showthread.php?t=1039431](http://ubuntuforums.org/showthread.php?t=1039431)
and especially 
[http://ubuntuforums.org/showthread.php?t=1039599](http://ubuntuforums.org/showthread.php?t=1039599)
(at first i found it annoying that he hasnt closed this thread, but then i realised that the forum does not allow to mark things as "solved" in the last two days... how silly)

SECOND, because the problem seems to be solved via expanding the extended partition first and then expanding the linux inside it, as we have all agreed. (so this thread will help newbies who get it on their search in the future)

---

### Post by theozzlives on 2009-01-15
try the gparted live CD

---

