---
title: "more gparted help"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by KevNice on 2009-01-27
I re-installed Windows Vista on a partition I created after resizing my /storage partition. I made it an ntfs file type because that was the only one that would allow me to install Vista.

I have since run out of space on the Vista partition, and want to add more space. I bit off more of the /storage partition to free up 15 GB. 

However, it won't let me resize the ntfs partition. There is even a caution sign next to it, and it tells me that gparted doesn't recognize this file type. I am afraid the only choice I have is to delete the partition and create a whole new one, re-installing everything.

Is there a way to resize the partition?

---

### Post by caljohnsmith on 2009-01-27
How about opening a terminal and posting the output of:
```
sudo fdisk -lu
```
Also, for whichever partition is Vista, how about also posting:
```
sudo mount /dev/sdaX /mnt && ls -l /mnt
```
And replace sdaX with the Vista partition.

---

### Post by KevNice on 2009-01-28
> **caljohnsmith said:**
> How about opening a terminal and posting the output of:
```
sudo fdisk -lu
```

Here is the readout:
[CODE}
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2        62171550   243127709    90478080   83  Linux
**/dev/sda3   *      160650    62171549    31005450    7  HPFS/NTFS**
/dev/sda4       274566976   312578047    19005536    5  Extended
/dev/sda5       307339515   308881754      771120   dd  Unknown
/dev/sda6       274566978   305877599    15655311   83  Linux
/dev/sda7       305877663   307323449      722893+  82  Linux swap / Solaris

[/CODE]

In case it's unclear, the Vista partition is a boot (*)
> **caljohnsmith said:**
> 
Also, for whichever partition is Vista, how about also posting:
```
sudo mount /dev/sdaX /mnt && ls -l /mnt
```
And replace sdaX with the Vista partition.

and I get:

```
sudo mount /dev/sda3 /mnt && ls -l /mnt
fuse: mount failed: Device or resource busy

```

what do you think?

---

### Post by GepettoBR on 2009-01-28
IIRC gparted doesn't resize NTFS partitions, but Vista does. If you shrink the /storage in gparted and then stretch the NTFS partition in Vista, it'll probably work. Since you can't resize a mounted partition, Vista will probably schedule the task for the next boot and do it.

note: I haven't done any partitioning in Vista, but:
a)I know that Vista has a built-in partitioner
b)The behavior I described is compatible with every 3rd-party pertitioner I've ever used in XP.

---

### Post by caljohnsmith on 2009-01-28
Which is the storage partition? Is it sda2? Because it looks like you shrunk sda2 from the end, and yet the Vista partition comes before the beginning of sda2. Therefore, you would need to shrink the beginning of sda2 in order to add space onto the sda3 Vista partition. Also, please post:
```
sudo umount /dev/sda3
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda3
sudo mkdir /tmp/sda3 && sudo mount /dev/sda3 /tmp/sda3 && ls -l /tmp/sda3
```

---

### Post by KevNice on 2009-01-30
Thank you for your replies.

Caljohnsmith, you were right in that I needed to take the space off the front of storage and not the end, and that was the whole problem. Unfortunately, while playing with it I accidentally formatted my Ubuntu partition!!! I re-installed it, got the partitions how I wanted, and am now re-configuring Ubuntu from square one again...

Thanks though!

---

