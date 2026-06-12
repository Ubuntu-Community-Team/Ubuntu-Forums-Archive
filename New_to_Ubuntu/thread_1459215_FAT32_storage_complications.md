---
title: "FAT32 storage complications"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-21
Hi,

I want to use a couple of old HDDs as backup storage devices. One is NTFS and seems to be adequate, but Ubuntu wont give me that format option for a 2nd dev. I seem to remember FAT32 has a too limited number of sub-directories allowed or it might not handle my filenames as well as NTFS.

Must i adopt a Primary, or will Ex2/3 suffice?

Thanks

---

### Post by coffeecat on 2010-04-21
> **nnjond said:**
> One is NTFS and seems to be adequate, but Ubuntu wont give me that format option for a 2nd dev.

Are you trying to use Gparted or Disk Utility? Whatever, you need to install the package ntfsprogs to be able to create/resize NTFS partitions with either utility.

> **nnjond said:**
>  I seem to remember FAT32 has a too limited number of sub-directories allowed

You may be right - I can't remember - but the main disadvantages of FAT32 is the 4GB filesize limit and the fact that it is non-journalled and therefore more vulnerable to corruption than either NTFS or a Linux journalled FS.

---

### Post by srs5694 on 2010-04-21
If you only plan to access the drive from Linux, then I recommend you use a Linux-native filesystem, such as ext2fs, ext3fs, ReiserFS, or XFS, on *both* drives. NTFS offers no advantages over these filesystems, and several disadvantages. For instance, if you store files outside of a tarball or other carrier, NTFS won't preserve permissions, which can be very important for some files. Also, if there's a power failure or system crash, you'll need Windows to run a disk check (CHKDSK) on the disk, since Linux can't do a full disk check on NTFS.

---

