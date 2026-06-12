---
title: "Disk full message"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ryoji on 2009-12-23
I f this is a really stupid question, I apologize. Just dual booted Ubuntu 9.10 over a Windows XP install on a 120G HD using the default side by side partition set up by the Ubuntu install disk. Everything works great (aside from some issues with flv videos like youtube). Computer shows the HD as 2 drives both with 50+ gigs each. The Ubuntu half shows 5.5G used and the rest open. But last night I went to download some pictures and video off my camera and got a warning box saying the disk was almost full! How can that be? Any help would be appreciated and use small words as I am very new to linux.

---

### Post by muteXe on 2009-12-23
can you do a 'sudo fdisk -l' please?
(that's a little L not a one)

---

### Post by ryoji on 2009-12-23
How do I show you what I get?

---

### Post by Merk42 on 2009-12-23
Open a terminal (Applications > Accessories > Terminal), then enter ```
sudo fdisk -l
``` one that is done, then just select all, copy, and past in a response here.

---

### Post by ryoji on 2009-12-23
Here's what I get:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b231b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6743    54163116    7  HPFS/NTFS
/dev/sda2            6744       14593    63055125    5  Extended
/dev/sda5            7562       14300    54130986   83  Linux
/dev/sda6           14301       14593     2353491   82  Linux swap / Solaris
/dev/sda7            6744        7519     6233157   83  Linux
/dev/sda8            7520        7561      337333+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe0d2e0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5169    39077608+   7  HPFS/NTFS

---

### Post by mapes12 on 2009-12-24
> **ryoji said:**
> Here's what I get:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b231b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6743    54163116    7  HPFS/NTFS
/dev/sda2            6744       14593    63055125    5  Extended
[B]/dev/sda5            7562       14300    54130986   83  Linux
/dev/sda6           14301       14593     2353491   82  Linux swap / Solaris
/dev/sda7            6744        7519     6233157   83  Linux
/dev/sda8            7520        7561      337333+  82  Linux swap / Solaris[/B]

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe0d2e0d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5169    39077608+   7  HPFS/NTFS

I'm not sure how you've done it but it looks to me as if you have set up two sets of partitions for Ubu. Notice as well that sda7 has the same start block as the main Extended partition sda2 = not good.

I would burn myself a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), boot from it and try and reconfigure those partitions from the GParted GUI.

---

### Post by Akavashi on 2009-12-24
I wouldn't worry about playing around with GParted too much, unless you've got files you wanna save. Reinstall from scratch so you don't get any more issues. 
And just so you know, you only need 1 Partition for Swap space (about 2gb is more than sufficient), and if you want a separate partition for extra space in Ubuntu, I'd advise mounting it under /home... as you can save that when you reinstall Ubuntu later on. 

Remember that the main drive you install Ubuntu on is mounted with / .

And just so you don't tear your hair out with youtube videos, mp3's or any video files for that matter, install the ubuntu-restricted-extras package by typing in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mapes12 on 2009-12-24
> **Akavashi said:**
> I wouldn't worry about playing around with GParted too much, unless you've got files you wanna save. Reinstall from scratch so you don't get any more issues. 
And just so you know, you only need 1 Partition for Swap space (about 2gb is more than sufficient), and if you want a separate partition for extra space in Ubuntu, I'd advise mounting it under /home... as you can save that when you reinstall Ubuntu later on. 

Remember that the main drive you install Ubuntu on is mounted with / .

And just so you don't tear your hair out with youtube videos, mp3's or any video files for that matter, install the ubuntu-restricted-extras package by typing in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```Those partitions will still need sorting out. If you go down the reinstall route you can select "Manual" when you get to the partitioning stage and reconfigure them from there. However, in my experience the GParted GUI is easier to understand and use.

Remember to backup your windoze stuff just in case. 

Here's a good resource for setting up a dual boot system: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

and this is also worth looking at: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

:popcorn:

---

### Post by JKyleOKC on 2009-12-24
> **mapes12 said:**
> Notice as well that sda7 has the same start block as the main Extended partition sda2 = not good.This is normal for an extended partition that has anything inside it. Keep in mind that an extended partition is a "container" for other partitions; its starting block will be the same as that of the first partition it contains, and its ending block will be the same as the last (or of the unallocated space, if it's not all in use). Think of it as a box that holds several smaller boxes...

I'd also be very cautious about recommending changes in partitioning to a newcomer; it's all too easy to thoroughly mess up a disk structure!

---

### Post by QLee on 2009-12-24
[QUOTE=JKyleOKC]
I'd also be very cautious about recommending changes in partitioning to a newcomer; it's all too easy to thoroughly mess up a disk structure![/QUOTE]

Well, from what was shown, the partitioning is already out of order, presumably from some previous partitioning changes. I do agree with JKyleOKC.

ryoji needs to be careful and be sure to understand what you are going to do before you give any commands or do any clicking. Come back to the forum and verify what you are going to attempt before trying it. There will be no big problems if you are careful.

---

### Post by falconindy on 2009-12-24
> **mapes12 said:**
> I'm not sure how you've done it but it looks to me as if you have set up two sets of partitions for Ubu. **Notice as well that sda7 has the same start block as the main Extended partition sda2 = not good.**

I would burn myself a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), boot from it and try and reconfigure those partitions from the GParted GUI.
Its expected behavior that the first logical partition in an extended partition shares the same start block with its parent (the extended partition). Notice that sda8 starts right after sda7, which is then followed by sda5 and sda6. All 4 of these partitions are inside the extended partition definition, just as intended.

Also, partitions being "out of order" isn't a big deal at all. Why has no one asked for the output of 'df -h' yet?

---

### Post by QLee on 2009-12-24
[QUOTE=falconindy]Its expected behavior that the first logical partition in an extended partition shares the same start block with its parent (the extended partition). Notice that sda8 starts right after sda7, which is then followed by sda5 and sda6. All 4 of these partitions are inside the extended partition definition, just as intended.[/QUOTE]

And, JKyleOKC already explained this.

[QUOTE=falconindy]Also, partitions being "out of order" isn't a big deal at all. Why has no one asked for the output of 'df -h' yet?[/QUOTE]

None of the posts I saw suggested that it was a big deal.

It does however, suggest that perhaps the OP has followed some advice previously, some advice that perhaps was not fully understood.

[QUOTE=falconindy]Why has no one asked for the output of 'df -h' yet?[/QUOTE]
I can't speak for others but I didn't ask because I don't kneed to know, you may troubleshoot in any manner you choose.

---

