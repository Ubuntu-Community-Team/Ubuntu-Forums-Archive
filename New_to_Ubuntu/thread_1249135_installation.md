---
title: "installation"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by crazylinux on 2009-08-25
Hi Teachers here,

I am a novice. I have a PC with wndows xp with two partitions C & D both in NTFS. C (has free space) contains windows and  D is the recovery partition. I want to install ubuntu. I think i should  partition C drive to form new partition E: and install ubuntu there.

1. How can I partition C drive using partition magic 8 to insatall linux. 

1. should i convert the partition to FAT32 where i will install linux. should be active, logical or extended partition.


  Please explain everything in detail with steps. i will be grateful to you.

Regards

---

### Post by FreezWay on 2009-08-25
the cd will partition for you. it will create E

---

### Post by nhasian on 2009-08-25
hello,

actually linux doesnt use drive letters, and if you install ubuntu in its own partition it will use EXT3 or EXT4 filesystem.  (dont worry it can still read your windows fat32 and ntfs filesystems).  if you are not familiar with partitioning drives, you may want to consider using wubi instead:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by lisati on 2009-08-25
**Important:**
[LIST=1]
[*]Backup your important data. As much as we don't like to admit it, things sometimes go wrong,
[*]If you are able, make a backup of your recovery partition. Many computers come with software preinstalled to help you with this.
[*]Whatever you do, if you want to keep your Windows & recovery partitions, **do not** use the "Guided - use entire disk" partitioning option
[/LIST]

---

