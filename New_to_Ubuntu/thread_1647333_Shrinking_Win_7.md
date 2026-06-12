---
title: "Shrinking Win 7"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Ziggy Coaldust on 2010-12-17
Hi. I'm new to the world of Ubuntu having just yesterday installed 10.10 via Wubi on my Win 7 system.

Looking through these forums people seem to recommend uninstalling Wubi and installing Ubuntu on a partition of its own. Now, I'll admit the prospect of shrinking partitions and potentially losing data is daunting but I'm willing to try anything once!

The question is, what would people suggest for the minimum partition size (in MB) for a Ubuntu partition?

Thanks.

---

### Post by ajgreeny on 2010-12-17
This is not simple to answer as it will depend on your current partition setup.

Win7 is often installed by OEMs with a boot partition, an OS partition and a data partition, so before giving advice it would be better to know what you already have.

From your current ubuntu can you show us the output of command in terminal ```
sudo parted -l
```That's a lower case L at the end.

When we have that info we can give you some suggestions on new partitions, but until then the only comment I would make is that for the sake of safety, you should use win7's own disk management utility to shrink the current windows partitions.  You should also defragment  windows partitions at least two times before you shrink them.  Do not try to shrink windows partitions in gparted during the install, as it can cause problems when next booting windows.

---

### Post by Mark Phelps on 2010-12-17
BEFORE you do anything else ... go into the Win7 Backup feature and use the option to create and burn a Win7 Repair CD.  That will prove invaluable later, should you need to repair the boot loader due to dual boot setup problems.

---

### Post by kansasnoob on 2010-12-17
You might find some of this info useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by seawolf167 on 2010-12-17
Before you do anything I **very highly **suggest you create a backup image of your disk in case anything goes wrong. I suggest using clonezilla and backing up to an external hard drive (just burn the live cd then follow the prompts, its easy).

[http://clonezilla.org/](http://clonezilla.org/)

After which, there are a number of programs you can use to shrink your Windows 7 partition.

[Gparted]("http://gparted.sourceforge.net/larry/resize/resizing.htm") is a good program

You can also use Windows-only programs like [Acronis Disk Director ]("http://www.acronis.com/enterprise/products/diskdirector-workstation/index.html")(non-free)

Two helpful links are (both from the Ubuntu help site):

[Windows Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot")

[Resize Windows Partition]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")

---

### Post by sandyd on 2010-12-17
[Propper way to resize windows 7]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

---

### Post by Ziggy Coaldust on 2010-12-17
Thanks for all the replies so far.

ajgreeny, the output from that command is:

> [B]Model: ATA ST3320820AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs         boot


Model: ATA Hitachi HDS72161 (scsi)
Disk /dev/sdb: 165GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7337MB  7337MB  primary  ntfs
 2      7338MB  165GB   157GB   primary  ntfs[/B]


Model: HDT72252 5DLAT80 (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ntfs


Model: ST350082 0AS (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs


Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0
has been opened read-only.



The first two (bold) drives are internal, the other two are external.

I'll be sure to backup before proceeding and have a repair disk prepared.

---

### Post by candtalan on 2010-12-17
> **sandyd said:**
> [Propper way to resize windows 7]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

A nice HowTo. However, unfortunately this does not include the installer for Ubuntu 10.10 which does not include the facility to install into the largest uncommitted space on the drive. Nor does Live CD 10.04.1, but Alternate 10.04.1 does still include it.

---

