---
title: "Wipe windows on sda1"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Mike V on 2011-03-30
I switched my wife to Ubuntu about six months now and now that she has not booted on Windows since almost five, I will finally get rid of the Windows partition to recover my hd space, here is my setup:

```

mike@laptop:~$ sudo fdisk -lu
[sudo] password for mike: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   112642047    56320000    7  HPFS/NTFS
/dev/sda2       112644094   234440703    60898305    5  Extended
/dev/sda5       112644096   151703551    19529728   83  Linux
/dev/sda6       151705600   171235327     9764864   83  Linux
/dev/sda7       232488960   234440703      975872   82  Linux swap / Solaris
/dev/sda8       171237376   187621375     8192000   83  Linux
/dev/sda9       187623424   208103423    10240000   83  Linux
/dev/sda10      208105472   232486911    12190720   83  Linux

Partition table entries are not in disk order
mike@laptop:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=112640000, Id= 7, bootable
/dev/sda2 : start=112644094, size=121796610, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=112644096, size= 39059456, Id=83
/dev/sda6 : start=151705600, size= 19529728, Id=83
/dev/sda7 : start=232488960, size=  1951744, Id=82
/dev/sda8 : start=171237376, size= 16384000, Id=83
/dev/sda9 : start=187623424, size= 20480000, Id=83
/dev/sda10: start=208105472, size= 24381440, Id=83


```

sda1  = Windows Vista
sda5  = /home (Ubuntu)
sda6  = Ubuntu (Maverick)
sda8  = Arch
sda9  = openSUSE (Celadon)
sda10 = Fedora (Laughlin)
sda7  = swap

What I would like to do is remove windows and resize the ex-Vista partition into 4 smaller ones (10Gigs aprox) to test out more distros and the rest hopefully add it to home...

It's possible to just use gparted and erase Vista and create the partitions as I want? will grub be erased and need reinstallation?
What about logical/extended issues?

Thanks for any advice...

Regards

---

### Post by uRock on 2011-03-30
If you delete those partitions from within your Ubuntu install, then you only have to run the following command for grub to see that Windows is no longer there.```
sudo update-grub

```

---

### Post by Mike V on 2011-03-31
I deleted the windows partition and ran the command you gave me:

```

sudo update-grub

```

but unfortunately nothing happens, I also ran:

```

sudo grub-install /dev/sda

```

and

```

grub-install --recheck /dev/sda

```

But it didnt work either, I have open gparted and the hard drive is not bootable, I have not restarted but it does not have the flag :(

here is the output of fdsik:

```

mike@laptop:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       112644094   234440703    60898305    5  Extended
/dev/sda5       112644096   151703551    19529728   83  Linux
/dev/sda6       151705600   171235327     9764864   83  Linux
/dev/sda7       232488960   234440703      975872   82  Linux swap / Solaris
/dev/sda8       171237376   187621375     8192000   83  Linux
/dev/sda9       187623424   208103423    10240000   83  Linux
/dev/sda10      208105472   232486911    12190720   83  Linux

Partition table entries are not in disk order
mike@laptop:~$ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=112644094, size=121796610, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=112644096, size= 39059456, Id=83
/dev/sda6 : start=151705600, size= 19529728, Id=83
/dev/sda7 : start=232488960, size=  1951744, Id=82
/dev/sda8 : start=171237376, size= 16384000, Id=83
/dev/sda9 : start=187623424, size= 20480000, Id=83
/dev/sda10: start=208105472, size= 24381440, Id=83

```

any further suggestions?

Thanks

---

### Post by Dutch70 on 2011-03-31
That's because you can only have 4 primary partitions. Anything numbered sda1 thru sda4 is your primary partitions. You'll have to make 3 primary's, 1 extended which counts as your 4th primary. Then you can make a little over 60 logical partitions inside the extended partition.

A pic of your hdd from Gparted would be very helpful.
Here's mine, it's still under construction. :)

Edit: Is you're computer not booting after you deleted windows???

---

### Post by Mike V on 2011-03-31
I haven't checked because I do not see the boot flag as before so I did not want to try since I only have a 7.10 CD right now and that have grub1.

Here is the screenshot

---

### Post by Mike V on 2011-03-31
Already solved, just checked the boot flag and rebooted and everthing went fine.

---

### Post by Dutch70 on 2011-03-31
Well that's good news.

You do know that you can only make 2 more partitions with your set up right? That 43.95GB of unallocated space can only be split into 2 partitions.

Unless you can extend the left side of your extended partition to take up that unallocated space. I've never thought that was possible, but I've never tried it either. Can't hurt to try.

---

### Post by Mike V on 2011-04-01
Will create a backup this weekend and try, I will report back next week XD

regards

---

### Post by Mike V on 2011-04-20
> **Dutch70 said:**
> Well that's good news.

You do know that you can only make 2 more partitions with your set up right? That 43.95GB of unallocated space can only be split into 2 partitions.

Unless you can extend the left side of your extended partition to take up that unallocated space. I've never thought that was possible, but I've never tried it either. Can't hurt to try.

Hi, sorry for the late reply, it was possible to claim all the space to the left.
I deleted Natty (in sda1) and grow the extended partition all the way to the left  claiming the +50GB, now I can create as many partitions as I want to test different distros.

Regards

---

