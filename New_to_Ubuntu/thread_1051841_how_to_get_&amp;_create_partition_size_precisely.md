---
title: "how to get &amp; create partition size precisely?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-27
I'm trying to clone the OS partition to another harddrive of a different size as the original. GParted provides an impresize size of the partition such as "32.63GB", whereas I'm trying to create a new partition of exactly the same size. It does tell me the number of sectors in the old partition but I can't directly use that number to create the new partition in GParted. 

What tools should I use to achieve this?

---

### Post by mcduck on 2009-01-27
> **anon0 said:**
> I'm trying to clone the OS partition to another harddrive of a different size as the original. GParted provides an impresize size of the partition such as "32.63GB", whereas I'm trying to create a new partition of exactly the same size. It does tell me the number of sectors in the old partition but I can't directly use that number to create the new partition in GParted. 

What tools should I use to achieve this?

you could use fdisk (although it's not for those afraid of command-line..)

---

### Post by talsemgeest on 2009-01-27
> **anon0 said:**
> I'm trying to clone the OS partition to another harddrive of a different size as the original. GParted provides an impresize size of the partition such as "32.63GB", whereas I'm trying to create a new partition of exactly the same size. It does tell me the number of sectors in the old partition but I can't directly use that number to create the new partition in GParted. 

What tools should I use to achieve this?
Gparted on the live cd (the partition editor in the menu, not the one used in the installer) has the option to select the partition size in mb. That should be as precise as you need. :)

---

### Post by anon0 on 2009-01-27
> **talsemgeest said:**
> Gparted on the live cd (the partition editor in the menu, not the one used in the installer) has the option to select the partition size in mb. That should be as precise as you need. :)

The problem is how do you know many megabytes the old partition is? And is that precise enough for RAID1? I would think for RAID1 the two partitions have to be exactly the same size, so wouldn't there be problems if there are fractional differences?

So how do we use fdisk to:
1) get the precise size (in bytes perhaps) of a partition, and
2) create a new partition of the same size?

---

### Post by rafaelsousa on 2009-01-27
But you want to resize an existent one?
I think cfdisk is more than enough to do so.

cfdisk is a curse-based tool that uses fdisk to create partitions.

The command is:

```
cfdisk
```

---

### Post by talsemgeest on 2009-01-27
> **anon0 said:**
> The problem is how do you know many megabytes the old partition is? And is that precise enough for RAID1? I would think for RAID1 the two partitions have to be exactly the same size, so wouldn't there be problems if there are fractional differences?

So how do we use fdisk to:
1) get the precise size (in bytes perhaps) of a partition, and
2) create a new partition of the same size?
I believe with raid, you must have blank disks as it changes the format of the hdds themselves. In setting up raid1, it should also allow you to create the partition of the same size. (BTW, how are you going to set up raid, with fake raid (ie, motherboard/bios setup), hardware raid or software raid (alternate install cd)?

---

### Post by anon0 on 2009-01-27
> **rafaelsousa said:**
> But you want to resize an existent one?
I think cfdisk is more than enough to do so.

cfdisk is a curse-based tool that uses fdisk to create partitions.

The command is:

```
cfdisk
```

Well it's not ideal for me to resize the OS partition unless it's safe and easy to do so. Cfdisk talks about changing cylinder and head parameters which don't exactly sound fool-proof.

I'm basically just asking how to clone the partition exactly on another drive.

---

### Post by hyper_ch on 2009-01-27
use this:
```

sfdisk -d /dev/sdX | sfdisk /dev/sdY 

```
that will make the same partitions.

---

### Post by anon0 on 2009-01-27
> **hyper_ch said:**
> use this:
```

sfdisk -d /dev/sdX | sfdisk /dev/sdY 

```
that will make the same partitions.

is that a disk-wide operation? What if the source disk is larger than the target disk?

---

### Post by anon0 on 2009-01-27
I found out that "sudo parted /dev/sdXY unit B print" will provide the number of bytes in the partition.

Also parted's mkpart can apparently create a new partition with a certain number of bytes or sectors. However when I did it the result is a sector or two different from the original, not sure why.

---

### Post by caljohnsmith on 2009-01-27
Anon0, how about first posting:
```
sudo fdisk -lu
```
And please identify the source partition and the destination drive.

---

### Post by hyper_ch on 2009-01-27
> **anon0 said:**
> is that a disk-wide operation?
yes

> **anon0 said:**
> What if the source disk is larger than the target disk?
never tested... but if target is bigger it doesn't matter...

---

### Post by anon0 on 2009-01-27
> **caljohnsmith said:**
> Anon0, how about first posting:
```
sudo fdisk -lu
```
And please identify the source partition and the destination drive.

Sure let's say source is /dev/sdb1 as follows:
```
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fee2fee
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       166015710   234436544    34210417+  fd  Linux raid autodetect

```

While target is /dev/sda as follows:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe545ed40

```

---

### Post by caljohnsmith on 2009-01-27
Do you want the destination partition to start at the beginning of the sda drive? I ask because the source partition sdb1 actually starts about 85 GB into the sdb drive. If you would like the destination partition to start at the beginning of the sda drive, how about doing:
```
echo '63,68420835,fd,*' | sudo sfdisk --no-reread -fuS /dev/sda -N1
```
That should create an unformatted partition on your sda drive exactly the same size as the sdb1 partition (about 34 GB). Then reboot, and post the new output of:
```
sudo fdisk -lu
```
And if that shows your new sda1 partition OK, you can copy the sdb1 partition to sda1 with:
```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/sdb1 of=/dev/sda1 statusinterval=10 bs=10M conv=notrunc
```
Let me know how that goes or if you run into problems.

---

### Post by anon0 on 2009-01-27
thanks caljohnsmith. I actually tried parted again and got it to create the partition in the middle, just to test things out (it's interactive so it's less cryptic). This time it worked because last time I forgot a simple arithmetic: the end sector should be starting position + size of the source partition - 512 bytes, since the starting sector is a part of the partition. Also I noticed that 1GB=10^9 not 1024^3 here.

---

### Post by Ericyzfr1 on 2009-01-27
If you make a boot disk with g4l, it will give you all the infos you need on that partition.

---

