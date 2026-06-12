---
title: "delete vista hidden partition?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by cairnzi on 2011-01-09
hi folks, can some kind soul tell me how to remove/delete my vista hidden partition? it takes up nearly 10Gb and i'm never going to use it again,i'm running 10.04 at the moment,many thanks.

---

### Post by CaptainMark on 2011-01-09
Are you sure its not needed, it could contain critical files which may stop your system booting? If your sure then from ubuntu go to the system menu > Administration > GParted select the partition and unmount then delete it from there, you can expand other partitions to use the space easily or make a new one from there. Just make sure you defragment any windows partitions before changing their size to reduce chance of complications

---

### Post by cairnzi on 2011-01-09
@CaptainMark, sorry i should have said gparted does not see the hidden partition? any ideas would be great, thanks.

---

### Post by CaptainMark on 2011-01-09
in a terminal type ```
sudo fdisk -l
```does it appear there? anmd if so what is it you wish to do with the free space once youve removed it?

---

### Post by cairnzi on 2011-01-09
here is what i get with sudo fdisk -l



```
sk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0a65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      498688   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2              63       12162    97184769    5  Extended
/dev/sda5              63       12162    97184768   83  Linux
```

---

### Post by CharlesA on 2011-01-09
The partition setup looks fine except for the "Partition 1 does not end on cylinder boundary." part.

You've got a partition for swap and one for the Linux install.

I don't see anything for Windows.

---

### Post by cairnzi on 2011-01-09
@CharlesA, yeah i noticed that aswell but i no there is a hidden partition as gparted only see's 93.66Gb and as you can see from the output it does not give me the whole of my hard drive, any ideas how to get all my hard drive space back?

---

### Post by CharlesA on 2011-01-09
If it's a true 100GB drive, then there will always be some "wasted space" due to how hard drive manufactures calculate drive space (1,000,000 = 1 MB) instead of using binary bits (1,048,576 = 1 MB)

See [here]("http://en.wikipedia.org/wiki/Megabyte").

---

### Post by Verbeck on 2011-01-09
1 gigabytes = 1 073 741 824 bytes
100 000 000 000 bytes (how they calculate 100 gb) divided by 1 073 741 824 bytes[B] = 93.132257462
[/B]

edit: late again

---

### Post by cairnzi on 2011-01-09
@CharlesA,Verbeck cheers, just thought i had a bit of my HDD missing lol, many thanks.

---

