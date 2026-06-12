---
title: "Partitioning pen drive and installing Linux"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by siteregsam on 2010-04-24
Hi,

   I recently bought a 8Gb pen drive. I wish to partition it and install Pen Drive Linux in it. I want to know whether it is possible to partition the pen drive into two 4Gb partitions, one to have for data transfer(a fat file system) and other for installing Linux(an ext file system). And the partition in which i am installing Linux should not be accessed in windows so that no one will delete the linux installation files(i hope ext type partitions will not be recognized in windows). 

 And if partitioning pen drive into two(one as ext file type and other as fat) is possible then i wish to know whether viruses in windows will have access to the Linux partition when the pen drive is mounted in windows.


Thanks in advance....

---

### Post by ed-koala on 2010-04-24
Two things I do know ...

1.  Windows can't see any ext partitions.

2.  Windows viruses can't hurt Ubuntu.

---

### Post by siteregsam on 2010-04-24
Thanks [ed-koala]("http://ubuntuforums.org/member.php?u=397691"), is there any tutorial as how to partition pen drive. Can i do it with partition magic or some other partitioning tools?

Though it may be a silly question, but i wish to know Partitioning and installing an OS in a pen drive will do any harm to life time of pen drive?

---

### Post by tuberculo on 2010-05-27
Use Gparted.

---

### Post by geet89 on 2010-05-27
windows viruses aint do nothing to ubuntu FTW

---

### Post by srs5694 on 2010-05-27
Be aware that Windows treats removable media, including USB flash drives, as "superfloppies," meaning that Windows will only access the first partition definition it finds. This means that you should make your data exchange partition (FAT or NTFS) the first partition on the disk (probably /dev/sda1) and put Linux on the second partition (probably /dev/sda2, or perhaps use a logical partition, /dev/sda5, for it).

Edit: Oh, wait, /dev/sda will probably be your hard disk, so make those partition identifiers /dev/sdb1, etc., or maybe even /dev/sdc1 or whatever. The third character after "/dev/" indicates which disk device it is, and that will depend on how many other disks are installed and the order in which they're detected.

---

