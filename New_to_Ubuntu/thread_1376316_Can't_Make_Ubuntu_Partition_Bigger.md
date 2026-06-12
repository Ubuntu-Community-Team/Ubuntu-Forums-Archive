---
title: "Can't Make Ubuntu Partition Bigger"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2010-01-09
Hi. Using Gparted from the LiveCD, I just deleted Windows because it was unnecessary and I wanted to make my Ubuntu partition bigger. However, I can't increase the size of Ubuntu, even though there is a lot of empty space there. What do I do?

---

### Post by talsemgeest on 2010-01-09
> **LegendarySandwich said:**
> Hi. Using Gparted from the LiveCD, I just deleted Windows because it was unnecessary and I wanted to make my Ubuntu partition bigger. However, I can't increase the size of Ubuntu, even though there is a lot of empty space there. What do I do?
Unfortunately you cannot resize a partition when it is in use, which is basically whenever your computer is on. However, you can do it from the ubuntu live cd, because the hard drive is not used. You may have to turn off the swap partition, which you can do from inside gparted.

---

### Post by mapes12 on 2010-01-09
```
sudo fdisk -l
```

and post the output back here.

---

### Post by talsemgeest on 2010-01-09
> **mapes12 said:**
> ```
sudo fdisk -l
```

and post the output back here.
Shouldn't need to do that, as long as there is free space after the partition. :)

---

### Post by mikewhatever on 2010-01-09
Can you elaborate on the nature of the problem. What happens exactly when you try resizing?

---

### Post by LegendarySandwich on 2010-01-09
> **talsemgeest said:**
> Unfortunately you cannot resize a partition when it is in use, which is basically whenever your computer is on. However, you can do it from the ubuntu live cd, because the hard drive is not used. You may have to turn off the swap partition, which you can do from inside gparted.
I am using the LiveCD; how do I turn off the swap partition?
> **mikewhatever said:**
> Can you elaborate on the nature of the problem. What happens exactly when you try resizing?
It only lets me make the memory bigger by eight megabytes, instead of around 70 gigabytes, which was my Windows partition.

---

### Post by talsemgeest on 2010-01-09
> **LegendarySandwich said:**
> I am using the LiveCD; how do I turn off the swap partition?

Right-click your swap partition in gparted, and turn it off there. Also, a screenshot of what you are trying to do will show us more clearly what you are trying to do.

---

### Post by mikewhatever on 2010-01-09
LS, you should post the output of <sudo fdisk -l> or a screenshot of gparted window. It could be that the Ubuntu partition is a logical one, while the unallocated space is not inside the extended partition.

---

### Post by SecretCode on 2010-01-09
> **mikewhatever said:**
> LS, you should post the output of <sudo fdisk -l> or a screenshot of gparted window. It could be that the Ubuntu partition is a logical one, while the unallocated space is not inside the extended partition.

Exactly what I was thinking.

---

### Post by LegendarySandwich on 2010-01-09
Hmm, okay, but I'll have to load the LiveCD which takes forever.

---

### Post by SecretCode on 2010-01-09
If you think you're going to do this more than once :) I recommend the PartedMagic CD - boots in considerably less than forever and includes gparted and all the important command line tools.

---

### Post by LegendarySandwich on 2010-01-09
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1         578     4642753+   b  W95 FAT32
/dev/sda3           10025       19457    75770572+   5  Extended
/dev/sda5           19068       19457     3132643+  82  Linux swap / Solaris
/dev/sda6           18799       19067     2160711   82  Linux swap / Solaris
/dev/sda7           10025       18797    70469059+  83  Linux

Partition table entries are not in disk order

```And...[U]


[http://i279.photobucket.com/albums/kk156/legendarysandwhich/Screenshot-1.png](http://i279.photobucket.com/albums/kk156/legendarysandwhich/Screenshot-1.png)

[/U]And SecretCode, thanks for the tip, I'll look into that.

---

### Post by mikewhatever on 2010-01-09
Well, as you can see, your linux partitions are logical, while the unallocated space used to be a primary partition, outside of the extended partition. What you want to achieve is feasible, but I'd recommend creating another linux partition, and using the unallocated space for backup and storage.

---

### Post by talsemgeest on 2010-01-09
> **LegendarySandwich said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1         578     4642753+   b  W95 FAT32
/dev/sda3           10025       19457    75770572+   5  Extended
/dev/sda5           19068       19457     3132643+  82  Linux swap / Solaris
/dev/sda6           18799       19067     2160711   82  Linux swap / Solaris
/dev/sda7           10025       18797    70469059+  83  Linux

Partition table entries are not in disk order

```And...[U]


[http://i279.photobucket.com/albums/kk156/legendarysandwhich/Screenshot-1.png](http://i279.photobucket.com/albums/kk156/legendarysandwhich/Screenshot-1.png)

[/U]And SecretCode, thanks for the tip, I'll look into that.
Ok, what you will first need to do is resize the logical partition (/dev/sda3), then resize your ubuntu partition (/dev/sda7) to fill the newly created free space. It will take a while, as it needs to move all your data to a different part of the hard drive.

---

### Post by SecretCode on 2010-01-10
> **talsemgeest said:**
> Ok, what you will first need to do is resize the logical partition (/dev/sda3), then resize your ubuntu partition (/dev/sda7) to fill the newly created free space. **It will take a while**, as it needs to move all your data to a different part of the hard drive.
As in, several hours if not longer!

> **mikewhatever said:**
> Well, as you can see, your linux partitions are logical, while the unallocated space used to be a primary partition, outside of the extended partition. What you want to achieve is feasible, but I'd recommend creating another linux partition, and using the unallocated space for backup and storage.
This would be quicker, and there's no real need to have all the space in one partition.

Another point: you have two swap partitions. This is not necessary and you could merge them into one.

---

### Post by talsemgeest on 2010-01-10
> **SecretCode said:**
> As in, several hours if not longer!


It all depends on the amount of data on the partition, and the speed of the hard drive. A similar operation on my machine takes 20 minutes at the most.

---

