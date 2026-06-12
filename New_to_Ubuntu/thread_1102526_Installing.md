---
title: "Installing"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Zach.Town on 2009-03-21
Summarized version of this post at the bottom, looking for some quick help.
________________
I'm installing Ubuntu again, I'm in the LiveCD at the moment and I have a partition of my drives set up ( C:/ and Z:/) I want to format everything off of the C partition and put ubuntu on it but I'm frankly confused as to what option to select and where to put the little dragging bar.

[http://i42.tinypic.com/xmpflz.png](http://i42.tinypic.com/xmpflz.png)

That's what it look like at the moment, anyone care to do like a quick paint edit or something? I'm installing off of a USB also so it might be shown in this menu.
________________

tl;dr?
I want to put ubuntu on C and leave my partition Z untouched.

This is what it looks like [http://i42.tinypic.com/xmpflz.png](http://i42.tinypic.com/xmpflz.png)

---

### Post by PukingPenguin on 2009-03-21
As you may know, the C: and Z: designations are Windows terminology. No other system uses it, including Ubuntu. 
The true state of your hard drive appears to be that you have six, not two, partitions. It isn't clear from your post whether or not you know what is on the partitions, and I suspect that hosing your C: partition will result in eradicating Windows, which is OK, if that's what you intend...

---

### Post by Zach.Town on 2009-03-21
I know on my Z:/ there is my movies and stuff, I also have a flashdrive plugged in so that could be a drive (i'm installing Ubuntu from it). I basically just want to wipe everything except for what's on the Z. I know that I will loose windows. I'm ready to loose that.

If you can tell from the picture what is what, C will be the biggest partition (the one I want to format, along with anything else) and Z will be the second largest, the only one that I want to keep.

---

### Post by SunnyRabbiera on 2009-03-21
I am sure if these are indeed different partitions then the Ubuntu should be able to just install on C and leave Z alone, of course thats in windows terms for you.

---

### Post by Zach.Town on 2009-03-21
C and Z are legitimate partitions. I was dualbooting ubuntu and windows 7 for awhile now I'm going to have just ubuntu, but I still want Z as a separate drive and untouched.

And yes I know C and Z and that stuff is not used outside of windows.

---

### Post by Zach.Town on 2009-03-21
bump.

---

### Post by GSF1200S on 2009-03-21
> **Zach.Town said:**
> bump.

Please open a terminal on the LiveCD and post the results of the following command:

```
sudo fdisk -l
```

After this, Ill be able to tell you what partitions to erase/format/install on. This said, I really hope you are ready for Linux. Its great, but it may be a bit frustrating trying to learn it. I suggest a dual boot setup which is nearly as easy, and That will let you run Linux or Windows whenever you want.

Back to the OP, Linux designates drives/partitions in a different way than windows. Windows is C:/ D:/ etc.. Here is just an idea of the difference.

Windows      Linux
C:/          /dev/sda1

Once I get the output from that command I can explain it further..

---

### Post by Zach.Town on 2009-03-21
I've had dualboots and such, I feel like I'm ready. I got some people helping me :) lemme boot back into livecd and post that.

---

### Post by Zach.Town on 2009-03-21
I'm installing from a USB.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x53535353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16424   131925748+   7  HPFS/NTFS
/dev/sda2           16425       30401   112270252+   5  Extended
/dev/sda5           28179       30302    17060998+  83  Linux
/dev/sda6           30303       30401      795186   82  Linux swap / Solaris
/dev/sda7           16425       27694    90526212    7  HPFS/NTFS
/dev/sda8           27695       28178     3887698+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x3ba29c02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7872     2015216    6  FAT16

---

