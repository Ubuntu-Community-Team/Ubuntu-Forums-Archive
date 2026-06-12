---
title: "Mounting Partitioned Volume: Error"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by benzodiaz on 2008-12-31
Hi ubuntu,

   I was operating vista 32 bit, and repartitioned 25 GB for a linux partition.  With an 8.10 bootdisk, installed ubuntu to largest free space in the gui type installer.
   Ubuntu works perfect, but the sda2 partition with windows on it cannot be mounted.

Places>Computer> 132.6GB Media

Cannot mount volume.

Unable to mount the volume.

Details>
$MFTMirr does not match $MFT(record 1). Failed to mount '/dev/sda2': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then rebbot into Windows TWICE. The usage of the /f parameter is very impertant! If you have SoftRAID/FakeRAID the you must activate it and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

I cannot dual boot neither, since I just need to backup some files and reformat again with a 80 GB linux partition and 20 GB windows. The menu grub only opts linux boots and memtest.

I originally used the disk manager in windows to create the free space for linux.

Let me know if there's anything i can help with.

Thank you,

I tried this based on other posts:

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       16128   129470460    7  HPFS/NTFS
/dev/sda3           16129       19457    26740192+   5  Extended
/dev/sda5           16129       19314    25591513+  83  Linux
/dev/sda6           19315       19457     1148616   82  Linux swap / Solaris
hawk@Back-hoe:~$ sudo mkdir /mnt/dev/sda2
mkdir: cannot create directory `/mnt/dev/sda2': No such file or directory
hawk@Back-hoe:~$ sudo mkdir /mnt/sda2
hawk@Back-hoe:~$ sudo mount -t ufs/dev/sda2/mnt/sda2

I tried ntsffix as root but it gave me the same errors.

I reckon that during the ubuntu 8X install that I messed with the partitions.
Further reckonin' makes me think of ditching the filesystem and reformatting the drive again with a proper partition an dual boot with vista, just for the odd compatibility.

Last calls?

---

### Post by blueridgedog on 2009-01-02
Your logic seems perfect to me, and infact you have done all the research that most people helping you might have done.  

You may be able to get data off of the partition with your Vista boot disk.  Can the Vista boot disk in recovery mode see the NTFS partition?

---

