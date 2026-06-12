---
title: "External Hard Drive won't format in Disk Utilities nor be recognized in GParted"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-03-21
When I try to format my Simpletech 500GB hard drive in GParted, I get a partition table error. I tell GParted to make a new partition table and my hard drive disappears.

In Disk Utilities when i try to format, I get this error

73722/37273723/37273724/37273725/37273726/3727done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

and 

when i try to change the partition table i get this error

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
Error: Input/output error during read on /dev/sdb
ped_disk_commit_to_dev() failed

---

### Post by byStanderone on 2010-03-21
...is your 500gb drive formatted in ext4?

---

### Post by laidback on 2010-03-21
I always make sure that the jumpers are set to slave, worth checking as it may help.

---

### Post by srs5694 on 2010-03-21
> **theweasel2345 said:**
> When I try to format my Simpletech 500GB hard drive in GParted, I get a partition table error. I tell GParted to make a new partition table and my hard drive disappears.

This is obviously a problem!

> In Disk Utilities when i try to format, I get this error

73722/37273723/37273724/37273725/37273726/3727done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 23 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

This isn't an error message; it's the normal output of the e2fsck command, which is what creates an ext2, ext3, or ext4 filesystem on a partition.

> and 

when i try to change the partition table i get this error

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
Error: Input/output error during read on /dev/sdb
ped_disk_commit_to_dev() failed

Please post the output of "sudo -l /dev/sdb". I have a hunch (no more than a hunch) that you may have a disk with 1024-byte sectors. Somebody else had a similar problem recently. It turns out that libparted (upon which GNU Parted, GParted, and many other Linux disk utilities are based) can't handle disks with that sector size. If I'm right you'll need to use fdisk to partition your disk and command-line utilities to create filesystems and otherwise manipulate it.

---

### Post by theweasel2345 on 2010-03-21
To answer all the questions...
Standerone: It was in fat32, the disk started acting up and had trouble mounting so I tried to reformat to ext4

laidback: I have no idea if the jumpers are set to slave, I never changed, or even knew about jumpers

srs5694: here is your outputs

michael@michael-laptop:~$ sudo -l /dev/sdb
[sudo] password for michael: 
sudo: /dev/sdb: command not found
michael@michael-laptop:~$ sudo -l /dev/sdb1
sudo: /dev/sdb1: command not found
michael@michael-laptop:~$ sudo ls -l /dev/sdb
brw-rw---- 1 root disk 8, 16 2010-03-21 13:54 /dev/sdb
michael@michael-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by theweasel2345 on 2010-03-21
Also I have tried to format it in fat32 and NTFS on a windows machine, and I get an error saying "failed to format the device".

---

### Post by srs5694 on 2010-03-21
Sorry about my earlier command; I left out the most important part ("fdisk")! You figured it out, though, and from your output, I can see that my hunch was wrong -- the disk seems to use 512-byte sectors. The way I see it, there are at least three possible issues:


[list]
[*]The disk hardware may be defective or incompatible with your computer's hardware.
[*]The disk may be incompatible with Linux generally, say because of a flaky driver or weird protocol implementation used by the disk interface's firmware.
[*]Some subtlety of the disk's design may be causing libparted to flake out.
[/list]


 What type of interface does the disk use? (USB? FireWire? eSATA? Something else?) Does it offer choices on that score? If you've got options, you could try using another interface; that might work around some hardware defects or general Linux incompatibilities.

If it's a libparted-specific issue, you could try using fdisk, an fdisk variant (sfdisk or cfdisk), or GPT fdisk (gdisk or sgdisk), to partition the disk. These are all command-line tools that do *not* use libparted. If you use any of them, you'll need to use mkfs or a related tool to create filesystem(s) on the partition(s) you create. For instance, if you create one big partition (/dev/sdb1), you'd type "sudo mkfs -t ext3 /dev/sdb1" to create an ext3 filesystem on the partition. If you wanted to use another filesystem (say, FAT or NTFS for Windows compatibility), you'd use a different option to -t, but it would otherwise be similar. Of course, for Windows compatibility, you could just try setting up the disk in Windows and see how Linux handles it.

---

### Post by srs5694 on 2010-03-21
> **theweasel2345 said:**
> Also I have tried to format it in fat32 and NTFS on a windows machine, and I get an error saying "failed to format the device".

Oh, I just noticed this comment. This is starting to sound like you've got yourself a defective drive, or perhaps one that's incompatible with your computer on a hardware level.

---

### Post by theweasel2345 on 2010-03-21
I was really afraid that it was defective but here is the website of it
[http://www.simpletech.com/commercial/products/simpledriveexternalpininfarina.html](http://www.simpletech.com/commercial/products/simpledriveexternalpininfarina.html)

I'll try working with it

---

### Post by theweasel2345 on 2010-03-21
I will also try this
sudo mkfs -t ext3 /dev/sdb1

---

### Post by srs5694 on 2010-03-21
> **theweasel2345 said:**
> I will also try this
sudo mkfs -t ext3 /dev/sdb1

Do this only *after* you create a partition with fdisk or some other non-libparted tool! If you try it without first creating a partition, you'll get an error message.

---

### Post by theweasel2345 on 2010-03-21
michael@michael-laptop:~$ sudo mkfs -t ext3 /dev/sdb
mke2fs 1.41.10 (10-Feb-2009)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 inodes, 122096645 blocks
6104832 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

says it is successful but disk utilities and gparted don't recognize/see it as unallocated. The disk, I guess is fried

---

### Post by srs5694 on 2010-03-22
You created a filesystem on the *whole disk,* not on a *partition.* Under those circumstances, neither fdisk nor GParted would recognize the disk. As I said, you need to partition the disk *first* and *then* use fdisk on a *partition* (e.g., /dev/sdb1, not /dev/sdb).

That said, your mkfs operation reported a warning about not being able to read block 0. That's highly suspicious, and could indicate defective hardware.

---

### Post by theweasel2345 on 2010-03-22
The HDD fails to mount after

sudo mkfs -t ext3 /dev/sdb1

i guess the disk is messed up. What a waste of $90

---

