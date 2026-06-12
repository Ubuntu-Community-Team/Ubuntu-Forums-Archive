---
title: "ubuntu no longer boots"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by UT_Libertarian on 2010-09-23
The other night, we had a power bump.  next morning, mouse was unresponsive, so i restarted the computer.  Mouse still not responding, so i restarted again.  now I get a message on the screen stating:

gave up waiting for root device  common problems:5d09ab3a426

boot args (cat /proc/cmdline)
 -check rootdelay= (did the system wait long enough?)
 -check root= (did the system wait for the right device?)
- missing modules (cat /proc/modules; ls /dev)

alert! /dev/disk/by-uuid/ba958946-21c1-486b-856f-f5d09ab3a486 does not exist  Dropping to a shell

Busybox v1.13.3(ubuntu 1:1.13.3 - 1ubuntu7)built-in shell (ash) Enter help for list of commands

(initramfs) _

pretty new to Linux
not real sure , but i think its version 9.04

---

### Post by Ronok on 2010-09-23
hi,

(I should say that I am also a beginner with using the Terminal)

But to Help others better help you, 
could you post here the out put of:

CODE:

**uname -a**

and

**lshw -C cpu -sanitize**

Thanks

---

### Post by UT_Libertarian on 2010-09-23
> **Ronok said:**
> hi,

(I should say that I am also a beginner with using the Terminal)

But to Help others better help you, 
could you post here the out put of:

CODE:

**uname -a**

output:
**Linux (none) 2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 ... i686 unknown**

and

**lshw -C cpu -sanitize**

output:
**/bin/sh: lshw: not found**


Thanks

except for more date/time, that's all I got

---

### Post by UT_Libertarian on 2010-09-23
In actuality, have 9.10 installed, can boot from 9.04 CD, but won't let me update-initramfs because booted from read-only media.

AARRGGHH!!

---

### Post by sandyd on 2010-09-23
> **UT_Libertarian said:**
> The other night, we had a power bump.  next morning, mouse was unresponsive, so i restarted the computer.  Mouse still not responding, so i restarted again.  now I get a message on the screen stating:

gave up waiting for root device  common problems:5d09ab3a426

boot args (cat /proc/cmdline)
 -check rootdelay= (did the system wait long enough?)
 -check root= (did the system wait for the right device?)
- missing modules (cat /proc/modules; ls /dev)

alert! /dev/disk/by-uuid/ba958946-21c1-486b-856f-f5d09ab3a486 does not exist  Dropping to a shell

Busybox v1.13.3(ubuntu 1:1.13.3 - 1ubuntu7)built-in shell (ash) Enter help for list of commands

(initramfs) _

pretty new to Linux
not real sure , but i think its version 9.04
things that could have hapenned.
1. power bump caused partition corruption
2. power bump caused partition table corruption
post output of
```

sudo fdisk -l
sudo blkid

```from livecd.

---

### Post by bradleypariah on 2010-09-23
(never mind after seeing above post)

---

### Post by UT_Libertarian on 2010-09-23
output from sudo fdisk -l

disk /dev/sda: 120.0 GB (blah blah)
etc, etc.

Device        boot     start   end       blocks               Id  System
/dev/sda1      *            1  14419    (whole bunch)    83   Linux
/dev/sda2             14420  14593    1397655             5   Extended
/dev/sda5             14420  14593    1397623+          82  Linux Swap / Solaris

seems odd that sda2 and sda5 both list same numbers.....

---

### Post by UT_Libertarian on 2010-09-23
output from (whatever the 2nd one was)

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="ba958946-21c1-486b-856f-f5d09ab3a426" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="98542203-08ef-4b6c-a9a9-09cdeeaf1715" TYPE="swap"
/dev/ramzswap0: TYPE="swap"

hope I got it right...

---

### Post by JKyleOKC on 2010-09-23
Not at all odd when you know what's happening, but agreed that it certainly looks suspicious at first glance.

For historical reasons, dating back to the early 1980s, the main partition table of any hard drive can have only four entries. That's all the space that was allowed in the original design, and ever since then it's been necessary to keep the same design for compatibility.

However before the design was even 10 years old, systems had grown to the point where more than four partitions were desireable. The solution was to invent an "extended" partition entry for the main table, that simply points to an additional table elsewhere on the drive that can hold more entries. A drive can have only one extended partition, but this extended partition can hold as many additional partitions as you want to create and have space for on the drive.

As you can see, your /dev/sda2 is an extended partition. Think of it as simply a container for additional "logical" partitions (the other three possible in the main table are now called "primary" ones). The /dev/sda5 partition is a logical partition within sda2, and the listing shows that it takes up the entire extended partition so the numbers for both are the same.

Since you still have two entries available in the main table, it would have been possible to create both partitions as primaries -- but in order to allow for possible future changes to your system, the Ubuntu installers always create an extended partition and place at least one logical partition inside it. The convention throughout Linux for numbering partitions within a drive is to use 1 through 4 for primaries or extended, and start logicals at 5. That's why you don't have an sda3 or sda4 in your table.

All very logical, but without knowing the history it can be very confusing!

---

### Post by UT_Libertarian on 2010-09-23
That pretty much made sense, but do NOT ask me to repeat it, in English.....(grin)

---

### Post by fslezak on 2010-09-23
Looks like SDA1 is the partition you run off.

Follow these steps:

1. Boot grub.
2. Press "C"
3. Type in root(hd0 
4. Hit the TAB button
5. Whatever partition has the ext3 heading, select that partition
6. With that partition number in mind, add this to the root(hd0 statement: [I]<the number you selected>)
[/I]7. Press enter.
8. Now type in "kernel /boot/vmlinuz**-**2.6.31-22-generic root=/dev/sda1 ro quiet" without the quotes!!!
9. Press enter
10. Type in "initrd /boot/initrd.img-2.6.31-22-generic" without the quotes!!!
11. Press enter
12. Finally: Type in boot and press enter!!!

Try to see if you can fix your system through this.

---

### Post by sandyd on 2010-09-23
> **UT_Libertarian said:**
> output from sudo fdisk -l

disk /dev/sda: 120.0 GB (blah blah)
etc, etc.

Device        boot     start   end       blocks               Id  System
/dev/sda1      *            1  14419    (whole bunch)    83   Linux
/dev/sda2             14420  14593    1397655             5   Extended
/dev/sda5             14420  14593    1397623+          82  Linux Swap / Solaris

seems odd that sda2 and sda5 both list same numbers.....
alright. partition table looks ok.
Time to check disks...
```

sudo fdisk  -f -p
```

---

### Post by UT_Libertarian on 2010-09-23
> **fslezak said:**
> Looks like SDA1 is the partition you run off.

Follow these steps:

1. Boot grub.
2. Press "C"
3. Type in root(hd0 
4. Hit the TAB button
5. Whatever partition has the ext3 heading, select that partition
6. With that partition number in mind, add this to the root(hd0 statement: [I]<the number you selected>)
[/I]7. Press enter.
8. Now type in "kernel /boot/vmlinuz**-**2.6.31-22-generic root=/dev/sda1 ro quiet" without the quotes!!!
9. Press enter
10. Type in "initrd /boot/initrd.img-2.6.31-22-generic" without the quotes!!!
11. Press enter
12. Finally: Type in boot and press enter!!!

Try to see if you can fix your system through this.

Fuzzy on the "boot grub" thing, unless that happens to mean "fix dinner"...

---

### Post by UT_Libertarian on 2010-09-24
> **UT_Libertarian said:**
> Fuzzy on the "boot grub" thing, unless that happens to mean "fix dinner"...

OK, got grub booted.

now the root(hd0 is giving me grief.....

---

### Post by UT_Libertarian on 2010-09-24
> **fslezak said:**
> Looks like SDA1 is the partition you run off.

Follow these steps:

1. Boot grub.
2. Press "C"
3. Type in root(hd0 
4. Hit the TAB button
5. Whatever partition has the ext3 heading, select that partition
6. With that partition number in mind, add this to the root(hd0 statement: [I]<the number you selected>)
[/I]7. Press enter.
8. Now type in "kernel /boot/vmlinuz**-**2.6.31-22-generic root=/dev/sda1 ro quiet" without the quotes!!!
9. Press enter
10. Type in "initrd /boot/initrd.img-2.6.31-22-generic" without the quotes!!!
11. Press enter
12. Finally: Type in boot and press enter!!!

Try to see if you can fix your system through this.

Got grub booted.
Pressed "C"
Typed root (hd0,1)  when I hit TAB, got some help message.....

---

### Post by UT_Libertarian on 2010-09-24
> **UT_Libertarian said:**
> Got grub booted.
Pressed "C"
Typed root (hd0,1)  when I hit TAB, got some help message.....

**Finally got it working.**   Thanks for your help!

---

