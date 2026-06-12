---
title: "resizing linux for linux"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-17
Hello friends

Could you help me on how to resize Linux with GParted for second Linux os ?
Thanks

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
I don't fully understand your query, but I'll make some assumptions and attempt an assist anyway.
First, you'll need either a live CD or live USB, as you can't resize a mounted partition. I don't know how much harddrive space you have, but I'd say you would be fine for allotting 10 Gb per system partition and then allocating the rest for storage. You might also consider migrating your home folder to a separate /home partition while you're at it. Look [here](http://www.psychocats.net/ubuntu/separatehome) for a how to.[I]
[/I]

---

### Post by kansasnoob on 2009-12-17
You can hack it up a gazillion ways:

[ATTACH]140249[/ATTACH]

Notice that all 5 linux OS's are sharing one swap and each has it's own /home.

---

### Post by manny43 on 2009-12-17
i need to know how mib for logical partition how much for extended and how much for primary is here that im confused

---

### Post by kansasnoob on 2009-12-17
Post the output of:

```
sudo fdisk -l
```

If you have only one drive it'll probably be designated as sda like this:

```
Disk **[COLOR="Red"]/dev/sda[/COLOR]**: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       12215    15374173+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17870     6160896   83  Linux
/dev/sda12          17871       19457    12747546   83  Linux
/dev/sda13          12216       13046     6674976   83  Linux
/dev/sda14          13047       14879    14723541   83  Linux

Partition table entries are not in disk order

```
If so also post the output of:

```
sudo parted /dev/sda print
```

Of course if yours is something other than sda change that appropriately, or if you have more than one drive (ie: sda and sdb) post the results of both.

As you can see in this example it's simply more human readable and partitions are in actual order:

```
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext4
14      107GB   122GB   15.1GB  logical   ext4
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3
```

---

