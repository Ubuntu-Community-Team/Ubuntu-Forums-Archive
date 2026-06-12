---
title: "supported file system for Ubuntu"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by IT_NERD on 2009-02-04
Hi All,

I was wondering what file system are supported under Ubuntu other than ext3, ext4 and NTFS?

Please help and thanks!

Cheers

---

### Post by howefield on 2009-02-04
This page might help a bit

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by Sorivenul on 2009-02-04
> **IT_NERD said:**
> Hi All,

I was wondering what file system are supported under Ubuntu other than ext3, ext4 and NTFS?

Please help and thanks!

Cheers
Depends. If you mean, what filesystems can Ubuntu be installed on, add ReiserFS, XFS, and JFS to your list (and subtract NTFS unless you install inside Windows using WUBI). If you are wondering what filesystems it can read, I have had no trouble with all of the above, plus HFS(+), FAT16, FAT32, and UFS (read-only by default).

---

### Post by IT_NERD on 2009-02-04
Sorivenul,

If i have an Ubuntu server on ext3, will there be an issue when windows operating systems on NTFS or FAT32 tries to accessing the files on it?

---

### Post by Sorivenul on 2009-02-04
> **IT_NERD said:**
> Sorivenul,

If i have an Ubuntu server on ext3, will there be an issue when windows operating systems on NTFS or FAT32 tries to accessing the files on it?
If you want to access it locally (on the same drive/machine) you will need [this]("http://www.fs-driver.org/"), which should also support ext3.

In general, it also depends on the kind of server you want to set up. If you are looking at a web server, then no issues should arise from the filesystems being used. Yahoo ran/runs on FreeBSD and millions of people have no problems accessing it. If you are looking at a file server for a local network, you may want to look into Samba.

---

### Post by jarvoll on 2009-02-04
Well, I don't know this from a technical standpoint, but I do know that my ext3 files have no problem being shared to my winXP computer, and I don't recall having done anything special to get it working. Thus, you can know that it's at least possible. :)

EDIT: This is using Samba to share between two different machines, btw.

---

### Post by IT_NERD on 2009-02-05
What filesystem that Ubuntu supports other than ext3 and ext4 i.e installing a Ubuntu OS on a desktop?

---

### Post by mcduck on 2009-02-05
> **IT_NERD said:**
> Sorivenul,

If i have an Ubuntu server on ext3, will there be an issue when windows operating systems on NTFS or FAT32 tries to accessing the files on it?

no. The server reads the filesystem, not the client machines.

Just like you can access any web page on any OS, even though major part of web servers are running Linux or BSD and definitely are not using any Windows filesystems.

---

### Post by Sorivenul on 2009-02-05
> **IT_NERD said:**
> What filesystem that Ubuntu supports other than ext3 and ext4 i.e installing a Ubuntu OS on a desktop?
ext4 support in the installer is only in Jaunty, though an ext3 partition can easily be converted if you install Hardy or Intrepid.

ext2, ReiserFS, JFS, and XFS should be supported for desktop installs. I have my / as ext3, and my other partitions as JFS. It's really a matter of preference. Is there something in particular you are looking for from the filesystem you choose?

---

### Post by IT_NERD on 2009-02-05
Hi Guys, 

Thanks for the replies, appreciate it. In summary, i will be able to select FAT32, NTFS, ext2, ext3, ReiserFS, JFS and XFS for installing Ubuntu desktop and as for server, the only option is ext2 or ext3.

---

### Post by perlluver on 2009-02-05
> **IT_NERD said:**
> Hi Guys, 

Thanks for the replies, appreciate it. In summary, i will be able to select FAT32, NTFS, ext2, ext3, ReiserFS, JFS and XFS for installing Ubuntu desktop and as for server, the only option is ext2 or ext3.

I have my server running on JFS, and I do believe that XFS, ext2, ext3, and reiserfs were all options.

---

### Post by Sorivenul on 2009-02-06
> **IT_NERD said:**
> In summary, i will be able to select FAT32, NTFS, ext2, ext3, ReiserFS, JFS and XFS for installing Ubuntu desktop and as for server, the only option is ext2 or ext3.
Both the Desktop and Server installs should support the same filesystems. Also note that the FAT and NTFS filesystems are not supported for install, though they can be created to share with a Windows install. Very limited support to install Linux on FAT partitions is available, though not advised. The other filesystems (ext3, JFS, ReiserFS, and XFS) are suggested because they have journaling capabilities and enhancements that Linux can't take advantage of on FAT or NTFS partitions. 

If you are installing for desktop, ext3 should be fine for most everything, with only moderate benefits from filesystems like JFS or ReiserFS. If you are dealing with a server (that will not double as a desktop) JFS is frequently recommended, though the others will work just as well for most basic needs.

---

### Post by wangsuda on 2009-02-06
> **Sorivenul said:**
> 

If you are installing for desktop, ext3 should be fine for most everything, with only moderate benefits from filesystems like JFS or ReiserFS. If you are dealing with a server (that will not double as a desktop) JFS is frequently recommended, though the others will work just as well for most basic needs.
So let me get this straight - if I install Ubuntu 8.10 on a desk/laptop as the only operating system, then ext3 format is my best bet. Correct?

---

### Post by Sorivenul on 2009-02-06
> **wangsuda said:**
> So let me get this straight - if I install Ubuntu 8.10 on a desk/laptop as the only operating system, then ext3 format is my best bet. Correct?
Sure... I don't see any reason why not to. ext3 is a stable, journaling filesystem that is well suited to everyday use. 

Most "average" users, will not have a need to use more unique, exotic, foreign, or "specialized" filesystems. Even "average" users setting up a home server would be fine using ext3 with little to no notable performance difference when compared to the other filesystems.

In short: Yes, I believe ext3 would be the "best bet" for most users.

---

### Post by wangsuda on 2009-02-06
> **Sorivenul said:**
> Sure... I don't see any reason why not to. ext3 is a stable, journaling filesystem that is well suited to everyday use. 

Most "average" users, will not have a need to use more unique, exotic, foreign, or "specialized" filesystems. Even "average" users setting up a home server would be fine using ext3 with little to no notable performance difference when compared to the other filesystems.

In short: Yes, I believe ext3 would be the "best bet" for most users.
Is ext3 the default format when installing Ubuntu 8.10?

---

### Post by Sorivenul on 2009-02-06
> **wangsuda said:**
> Is ext3 the default format when installing Ubuntu 8.10?
Yes, as far as I know.

---

### Post by wangsuda on 2009-02-06
Thank you for your help.

---

