---
title: "Creating Raid-5 Array"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by caepli on 2010-05-25
I started by creating a software raid in the ubuntu alternate install, that runs on a separated disk space than the OS. 

this is a completely clean install. The raid finished syncing and when I fdisk -l I get 
```
heinz@localhost:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdi'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      243202  1953514583+  ee  GPT

Disk /dev/md0: 26005.2 GB, 26005170487296 bytes
2 heads, 4 sectors/track, -1 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 851968 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdj'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdk'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdl'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdm'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdn'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdo'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdo: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1      243202  1953514583+  ee  GPT

```

My raid device is /dev/md0

If I try to format the partition with ntfs, I end up with

(this is using the disk utility or mkntfs /dev/md0, same output for both)

```

heinz@localhost:~$ sudo fdisk -l /dev/md0

Disk /dev/md0: 26005.2 GB, 26005170487296 bytes
2 heads, 4 sectors/track, -1 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 851968 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1   ?      822447   240553456   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/md0p2   ?   244156454   471478443   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/md0p3   ?    28216909    28216910           5   72  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/md0p4       330301441   330307927       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Problem 1 is, I don't want that many partitions! It is set to no partition so it uses the entire disk as ntfs. Problem 2, when I restart the OS It shows that the entire partition is not aligned and I can't mount anything. 

What exactly am I completely missing here?

---

### Post by skulls on 2010-08-26
Hi,

I have the same problem as you, the fdisk -l output is frightening to say the least. Even the start/end boundaries are the same (also check [http://ubuntuforums.org/showthread.php?p=9767859]("http://ubuntuforums.org/showthread.php?p=9767859") it's the same thing!!

I'm starting to suspect something is wrong with ntfs partitions in RAID arrays... It seems that either the partition is corrupt somehow, or fdisk is unable to correctly report it. Regardless of which, this is clearly an error in the system and it is not only ubuntu related (I have seen the same in Fedora forums...).

Let me know if you still have this problem, or if you have chosen to just ignore it, and have had no problems ever since..

---

### Post by srs5694 on 2010-08-26
First, the "fdisk -l" output reveals that your separate disks use the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning system rather than the older [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) system. As the output suggests, you should use another program to view or manipulate the disk's partitions. For Linux, libparted-based tools, such as GNU Parted and GParted, work; or if you prefer an fdisk-like tool, try my [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/)

Second, if you're using Linux's software RAID features, putting NTFS on the RAID device makes absolutely no sense, because Windows can't (AFAIK) read Linux's software RAID setup. If you want to use the array in both Linux and Windows, you could buy a hardware RAID controller and use it to manage the RAID duties. I *think* that Linux can read Windows' software RAID setup, too, but I'm not positive of that. If Windows doesn't need to access the array (except possibly via a network, such as through Samba), then put a Linux filesystem on the thing.

Third, in a Linux software RAID configuration, you normally create the /dev/md# device, as you've done, then put a filesystem on it, and then mount that device. If you view the device with fdisk, as you've done, you'll be trying to interpret the filesystem as if it were an MBR partition map, which is meaningless. This would be like trying to view the contents of a partition with fdisk, as in "fdisk -l /dev/sda1". Alternatively, I think I've heard of people partitioning their software RAID arrays, but I don't know much about this approach. You could also put LVM atop the RAID device.

I suggest you read the [Software RAID HOWTO](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) document.

---

### Post by skulls on 2010-08-27
Hi,

Thanks for your reply. 

Let me start with some explanation on why I needed such a setup; I was previously using EXT4 as the filesystem of choice for this RAID array, but wasn't very happy with it because of some Samba permissions problems, and also because EXT4 is not as efficient when you consider the disk space that is being used, reserved, etc. 

So I considered NTFS for a variety of reasons; first it doesn't have advanced permissions so it would not pose many problems with samba, because the main use of the RAID is to serve as a residential NAS. Second, it is quite efficient when it comes to storage allocation, almost all the disk's space is available: in a TB-level storage, even a few % makes a huge difference, we're talking maybe 10-20Gb more. The third reason is, that in case of major system failure, the disks could be read by almost any pc, because NTFS is a widely accepted format. 

Don't get me wrong, I love my linux box and I stand by my choice of not putting windows onto it, but the NTFS filesystem is pretty robust and it has some nice features that should not be underestimated, even windows 7 doesn't exploit the full potential. Just because NTFS was created by microsoft doesn't mean we should not be allowed to use it in linux..

So this is a reasonable scenario where someone would like to have a ntfs over raid in linux. The reality is that support for this type of setup is not ideal, and I firmly believe that either fdisk or mkfs or mdadm have some kind of bug in that respect, as this is easily reproducible even within a virtualised system, with small drives (I have done it with 2 500mb virtual drives, the results are the same).

In the end I figured out that ntfs is a filesystem that is not entirely supported by linux (for obvious reasons, I assume it had to be reverse-engineered). So I ended up creating a RAID and formatting it with XFS, which is reputedly very stable, can be accessed from any livecd in case of need, and does a very good job with the space allocation, almost beating NTFS. I'll see if I can fix the permissions in some other way..

As a conclusion I'll say that even with all the RAID arrays I created, destroyed, converted, and so on, none of the data was lost.. (fingers crossed!)

P.S: formatting as GPT or MBR has no effect on the fdisk problem described above, it still happens.

---

### Post by srs5694 on 2010-08-27
I realize you say you've switched away from NTFS to XFS, but I want to reply to your points so that you, as well as other readers, fully understand why using NTFS in the way you were attempting was inadvisable.

> **skulls said:**
> I was previously using EXT4 as the filesystem of choice for this RAID array, but wasn't very happy with it because of some Samba permissions problems, and also because EXT4 is not as efficient when you consider the disk space that is being used, reserved, etc.

Samba provides a large number of options that are designed to bridge the gap between Windows-style and Unix-style security. For instance, there's "force user", "force group", and "force create mode" on the share level, and "username map" on the global level. (There are many others; these just spring to mind.) I recommend you read the smb.conf man page (it's *huge*) and/or get a book on Samba, such as my [*Definitive Guide to Samba 3.*](http://www.rodsbooks.com/samba3/)

I'm not positive, but I suspect the "efficiency" issue with ext4 you've identified is simply a matter of the reserved space. Ext2, ext3, and ext4 all reserve 5% of the available disk space when you create a new filesystem, by default. This value can be changed, though, by using the -m option to mke2fs (when creating the filesystem) or tune2fs (after creating a filesystem). You can set it as low as 0%, if you like. That said, the available space reported on a new filesystem is not a perfect indicator of how many files you can store. Some filesystems are more efficient than others at storing files, particularly if they're small files. I don't know how ext4 compares to XFS or NTFS on this score, but it's conceivable you could store more files on ext4 than on XFS or NTFS, even with the default 5% reserved space for ext4. If you're storing predominantly small files (a few kilobytes), ReiserFS is the winner on this particular count; it's very efficient at cramming in small files.

> So I considered NTFS for a variety of reasons; first it doesn't have advanced permissions so it would not pose many problems with samba, because the main use of the RAID is to serve as a residential NAS. Second, it is quite efficient when it comes to storage allocation, almost all the disk's space is available: in a TB-level storage, even a few % makes a huge difference, we're talking maybe 10-20Gb more. The third reason is, that in case of major system failure, the disks could be read by almost any pc, because NTFS is a widely accepted format.

Your last point is invalidated by the fact that you're using a *Linux-only* software RAID configuration. On your setup, *only Linux can directly access the NTFS data structures!* Moving the RAID array to a Windows computer won't help; the software RAID data structures will render the NTFS data structures inaccessible to Windows. Thus, *when* (not if, when) you suffer a power outage, system crash, or similar problem that leaves the NTFS volume in a state that requires repairs, those repairs will become very difficult to make.

It is possible to make such repairs, but there are extra hurdles to overcome. I can think of two ways of recovering the data in such a scenario. Both involve extra configuration, and if you didn't happen to be set up to do it already, even an expert would require a couple of hours just to begin the process. Both will slow the actual data recovery down, too. One of these methods is to use network block devices (NBDs) to give a Windows system direct access to the device. (I'm not even 100% sure this would work; I know there's a Windows NBD server, but you'd need a Windows NBD client for this to work, and I'm not sure if such software exists.) The other method would be to run Windows in a virtual machine on the Linux box so that it can repair the disk. Of course, Murphy's Law says that a problem like this would occur at a time when you can least afford to be learning about NBDs or virtualization software.

> the NTFS filesystem is pretty robust and it has some nice features that should not be underestimated, even windows 7 doesn't exploit the full potential. Just because NTFS was created by microsoft doesn't mean we should not be allowed to use it in linux..

I don't care if NTFS can make unicorns appear and dance across my lawn; if it can't be fixed by the only OS on the computer, it's not a good choice for use on that computer. Putting NTFS in a Linux-only RAID configuration just exacerbates this problem.

> So this is a reasonable scenario where someone would like to have a ntfs over raid in linux.

It may seem reasonable, but it's not, as I've just detailed.

> The reality is that support for this type of setup is not ideal, and I firmly believe that either fdisk or mkfs or mdadm have some kind of bug in that respect, as this is easily reproducible even within a virtualised system, with small drives (I have done it with 2 500mb virtual drives, the results are the same).
...
P.S: formatting as GPT or MBR has no effect on the fdisk problem described above, it still happens.

You haven't identified a problem. I suspect you're referring to the garbled fdisk output, but as I wrote in my first response in this thread, that garbled output is because you were using fdisk on an inappropriate device. You put NTFS on /dev/md0, and fdisk is not intended to interpret NTFS, so when you use fdisk to access /dev/md0, of course it showed you nonsense. It would be like trying to load an MP3 file into a text editor.

Once again, I recommend you read the [Software RAID HOWTO](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) document, which describes how software RAID is used.

---

