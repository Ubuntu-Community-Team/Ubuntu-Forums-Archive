---
title: "[SOLVED] convert a logical partition to a primary one?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by uarale on 2008-12-11
I totally switched to Ubuntu some days ago, after made some changes to my hard disk. at the moment its state is as follows:

[[IMG]http://img523.imageshack.us/img523/3203/extendedgm7.png[/IMG]](http://imageshack.us)
[[IMG]http://img523.imageshack.us/img523/extendedgm7.png/1/w782.png[/IMG]](http://g.imageshack.us/img523/extendedgm7.png/1/)

Now there's a problem: one partition is still a extended one for nothing. i want to convert it to a primary. in this situation, i want sda1 and sda5 to become one and there is no extended, all partitions would be primary.

so what should i do?

---

### Post by Titan8990 on 2008-12-11
**Backup all data**

Delete the extended partition and then attempt to resize partition sda1 to use the space that deleting the extended partition created.

---

### Post by Duck2006 on 2008-12-11
You may find what you need here.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

But as far as i know you will have to delete the partition and then the extended partition to make it a primary partition.

---

### Post by caljohnsmith on 2008-12-11
It's possible to manually change a logical partition into a primary one via the command line, but I'm just curious why do you want to do that? What is wrong with leaving sda5 as a logical partition? If you really want to try it, then first please post:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda

```

---

### Post by uarale on 2008-12-11
> **caljohnsmith said:**
> It's possible to manually change a logical partition into a primary one via the command line, but I'm just curious why do you want to do that? What is wrong with leaving sda5 as a logical partition?

I just want to see what a Linux OS can do? It's amazing to know that this task can be completed in command line, cause i once thought i had to borrow a drive and copy all the data to it.

```

$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaca3aca3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        30732345   155268224    62267940    f  W95 Ext'd (LBA)
/dev/sda2       155268225   156296384      514080   82  Linux swap / Solaris
/dev/sda3              63    30732344    15366141   83  Linux
/dev/sda5        30732408   155268224    62267908+  83  Linux

Partition table entries are not in disk order

```

```
sudo sfdisk -d /dev/sda

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 30732345, size=124535880, Id= f
/dev/sda2 : start=155268225, size=  1028160, Id=82
/dev/sda3 : start=       63, size= 30732282, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 30732408, size=124535817, Id=83

```

---

### Post by caljohnsmith on 2008-12-11
To convert from a logical partition into a primary one is fortunately easy, assuming one doesn't try to exceed the max limit of 4 primary partitions; it is only if you want to convert from a primary partition into a logical partition that it takes more work. So anyway, all I did was change your partition table as follows in the attached "partition_table.txt" file:
```
# partition table of /dev/sda
unit: sectors

[COLOR="Blue"]/dev/sda1 : start= 30732408, size=124535817, Id=83[/COLOR]
/dev/sda2 : start=155268225, size=  1028160, Id=82
/dev/sda3 : start=       63, size= 30732282, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0

```
So basically I just deleted your sda1 extended partition and replaced it with the sda5 logical partition, so sda5 will become the sda1 primary partition. As always, be sure to back up any important files on the HDD before doing the following partition changes. To write the above partition table to your HDD, just download the "partition_table.txt" file to your desktop and do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
And your sda5 logical partition will now be sda1 primary partition. You can check immediately after the above command by doing:
```
sudo fdisk -l
```
To see your new partition table. Also you should be able to mount sda1 and view its contents:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
Anyway, let me know how that goes. :)

---

### Post by uarale on 2008-12-11
Hi caljohnsmith,
this is the outcome of the command
```
$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1       1913    9664    7752   62267940    f  W95 Ext'd (LBA)
/dev/sda2       9665    9728      64     514080   82  Linux swap / Solaris
/dev/sda3          0+   1912    1913-  15366141   83  Linux
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       1913+   9664    7752-  62267908+  83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1      30732408 155268224  124535817  83  Linux
/dev/sda2     155268225 156296384    1028160  82  Linux swap / Solaris
/dev/sda3            63  30732344   30732282  83  Linux
/dev/sda4             0         -          0   0  Empty
**Warning: partition 1 does not start at a cylinder boundary**
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```
I'm really worried now. After running the command, i see the disk via GParted and this is its status:
[[IMG]http://img117.imageshack.us/img117/4152/primaryyr0.png[/IMG]](http://imageshack.us)
It seems all data was deleted!!!
unfortunately, i didn't backup anything (actually, i don't have an external disk). if the data cannot recovered, i go crazy!

---

### Post by caljohnsmith on 2008-12-11
OK, go ahead and reboot your Live CD, open a terminal again, and post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. We can work from there.

---

### Post by bumanie on 2008-12-11
Unfortunately on this occasion caljonsmith made an error (which I can promise you, is rare) - when deleting or changing a logical to a primary partition, anything with in the logical partition is wiped. You could try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to restore you data. It will probably re-write the logical partition to do this. If you manage the retrieval of your data, you will have to copy the data elsewhere whilst removing the logical partition. Get testdisk live cd from the link or you can use ubuntu if it's still functional > sudo apt-get install testdisk then to start testdisk > sudo testdiskThere are instructions on the testdisk site and also [here]("http://www.users.bigpond.net.au/hermanzone/p21.html"). Good luck

---

### Post by caljohnsmith on 2008-12-11
> **bumanie said:**
> Unfortunately on this occasion caljonsmith made an error (which I can promise you, is rare) - when deleting or changing a logical to a primary partition, anything with in the logical partition is wiped.
Bumanie, that's not true about the operation that we did with sfdisk; sfdisk only changes the MBR (Master Boot Record) and the EBRs (Extended Boot Records) with the partition changes, and his operation was such that no EBRs had to be created, which is the risky process. His data has not been wiped. If we need to, we can reverse the process and reinstate his previous partition table; that is one reason why I had him post the "sfdisk -d" so that essentially we have an online backup of his previous partition table. As long as he doesn't do anything to write to the drive, we can rewrite his original partition table back to the drive if we need to. But first I want to see if it was successful, because I don't see reason yet to be alarmed.

---

### Post by uarale on 2008-12-11
guys, caljohnsmith was true and i'm happy now that my data is still there!

i changed the mount command that caljohnsmith suggested before a little (added -t ext3) and it worked like a charm. after that i can see sda1 with all the data remains. maybe only after the first mount, the system can realize a new partition i think.

i also added an entry into /etc/fstab so that sda1 can be automatacally mouted each time the computer starts.

thank you, caljohnsmith. you rocks!

---

### Post by caljohnsmith on 2008-12-11
Glad to hear that worked OK, uarale. Cheers and have fun with your Ubuntu install. :)

---

### Post by fermulator on 2009-10-01
> **caljohnsmith said:**
> to convert from a logical partition into a primary one is fortunately easy, assuming one doesn't try to exceed the max limit of 4 primary partitions; it is only if you want to convert from a primary partition into a logical partition that it takes more work. So anyway, all i did was change your partition table as follows in the attached "partition_table.txt" file:
```
# partition table of /dev/sda
unit: Sectors

[color="blue"]/dev/sda1 : Start= 30732408, size=124535817, id=83[/color]
/dev/sda2 : Start=155268225, size=  1028160, id=82
/dev/sda3 : Start=       63, size= 30732282, id=83
/dev/sda4 : Start=        0, size=        0, id= 0

```
so basically i just deleted your sda1 extended partition and replaced it with the sda5 logical partition, so sda5 will become the sda1 primary partition. As always, be sure to back up any important files on the hdd before doing the following partition changes. To write the above partition table to your hdd, just download the "partition_table.txt" file to your desktop and do:
```
sudo sfdisk --force /dev/sda < ~/desktop/partition_table.txt
```
and your sda5 logical partition will now be sda1 primary partition. You can check immediately after the above command by doing:
```
sudo fdisk -l
```
to see your new partition table. Also you should be able to mount sda1 and view its contents:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
anyway, let me know how that goes. :)

perfect solution! :-)

---

### Post by LeHomard on 2009-11-11
Hi everyone.

Unfortunately I've tried this in order to sort out a very similar issue (sda1 as an extended partition containing sda5).

I used an Ubuntu Live CD to perform the operation.

Before, sudo sfdisk -d /dev/sda gave me :
> /dev/sda1 : start=       63, size= 40965687, Id= 5
/dev/sda2 : start= 40965750, size= 83955690, Id= 7, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=124921440, size=196748055, Id= b
/dev/sda5 : start=      126, size= 40965624, Id=83

Now I have :
> /dev/sda1 : start=  2024190, size=982753272, Id=83
/dev/sda2 : start=984777462, size=128428906, Id= 7, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=1113206368, size=3956541015, Id= b

So I appears to have succeeded.

sudo fdisk -lu :
> Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe94d42ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         2024190   984777461   491376636   83  Linux
/dev/sda2   *   984777462  1113206367    64214453    7  HPFS/NTFS
/dev/sda4      1113206368  5069747382  1978270507+   b  W95 FAT32

sda5 was an ext4 partition, so I suppose that should now be sda1 (previously extended partition). sda2 is a Windows Vista NTFS partition and sda4 is a FAT32 data partition.

The problem is that now the partitions can't be mounted (tried to mount the various partitions with no success) and on startup grub says it can't find the partition it's looking for...

Does anyone know a simple way either the get it to work properly or to revert it to the previous state ? (I tried sudo sfdisk --force /dev/sda < ~/desktop/partition_table.txt with the previous partition table, still can't mount...)

Thanks.

---

### Post by darkazurka on 2010-02-14
I've now taken all backups after some 4-6 hours of "backup time devotion". Now I don't really care that much if this goes wrong, although I hope it will work.

A thread which mentions converting more than 1 logical partitions into more than 1 primary partitions(my case!): [http://ubuntuforums.org/showthread.php?t=1036239](http://ubuntuforums.org/showthread.php?t=1036239)

Maybe I should just format my harddrive. Having spent so much time taking backups, I wish that time should not go in vain. I might also try using ext4 filesystems for my new distributions.

---

### Post by meierfra. on 2010-02-14
darkazurka: Are your trying to convert a logical partition into a primary one?  If  yes, why?
Or do just want gparted to recognize your partitions?

If you would like some help,  follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt. 

Also post the output of

```
sudo sfdisk -d
```

---

### Post by darkazurka on 2010-02-15
Why I wanted to turn my 2 logical partitions into 2 primary partitions?
The reason is this: I wanted this because I believed my logical partitions were overlapping(if I remember correctly, it was fdisk that said this.) and that was the reason gparted couldn't see them.

To cut a long story short: After I took the backups, I posted here, then I considered....and decided that since I have my data safe from my backups, I'll delete all my partitions and install one distro (19GB ext4) on the first partition and Ubuntu 9.10 on the other partition (20GB ext4). 

I used a 1GB flash stick to transfer the data to another computer.(I had about 8GB of data to transfer)

---

