---
title: "need help on hard drive"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by sandy0594 on 2011-04-08
hey all,i have 3 drives in windows os..whenever i switch to ubuntu,my third drive is missing..why is it like that?
I installed ubuntu through windows installer wubi in the drive which is missing in ubuntu

---

### Post by mikewhatever on 2011-04-08
So, you are saying that Ubuntu is installed and runs from the drive that's missing?
Can you post the output of **df -h** from Ubuntu.

---

### Post by sandy0594 on 2011-04-08
Hey,here are the results

```


sandy@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  3.6G   12G  24% /
none                  1.7G  252K  1.7G   1% /dev
none                  1.7G  196K  1.7G   1% /dev/shm
none                  1.7G  100K  1.7G   1% /var/run
none                  1.7G     0  1.7G   0% /var/lock
/dev/sda6             173G   46G  128G  27% /host
none                   17G  3.6G   12G  24% /var/lib/ureadahead/debugfs
/dev/sdb1             3.8G   17M  3.8G   1% /media/SANDY



```

BTW,mine is a 500Gb hard disk..with 3 partitions in windows

---

### Post by mikewhatever on 2011-04-08
I should probably have also asked for the **sudo fdisk -l** output. Can you post that as well. The partition you said was missing is there, and you can access it by going to /host:
```
/dev/sda6             173G   46G  128G  27% /host
```

---

### Post by sandy0594 on 2011-04-08
Hey mike,here are the results:

```


sandy@ubuntu:~$ sudo fdisk -l
[sudo] password for sandy: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c041c04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60800   385977690    f  W95 Ext'd (LBA)
/dev/sda5           12749       38244   204796588+   7  HPFS/NTFS
/dev/sda6           38245       60800   181181038+   7  HPFS/NTFS

Disk /dev/sdb: 4018 MB, 4018143232 bytes
84 heads, 20 sectors/track, 4671 cylinders
Units = cylinders of 1680 * 512 = 860160 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4672     3923412    6  FAT16



```

Also,can u guide me how to browse through the drives in ubuntu..as i am new to it,i can't locate which drive is located where..So,is there any way in ubuntu wherein we can sort the drives as in windows

---

### Post by mikewhatever on 2011-04-08
Thanks for the outputs. As you can see, all three partitions/drives are in place, and the fourth is an extended partition.
I'm not sure what you mean by 'sort the drives as in windows', but you should be able to access sda1(Windows) and sda5 by clicking the entries in the left panel of the file browser, and sda6 by browsing to /host.

---

### Post by sandy0594 on 2011-04-08
In windows drive format is C,D,E...I mean like that and BTW,can't we make /host to be visible outside?

---

### Post by mikewhatever on 2011-04-08
As far as I know, the alphabetic notations for partitions are used by Windows only. It might be possible to emulate it in Linux, not sure how.
The /host can be added as a bookmark. To do that, browse to /host, then use Bookmarks in the menu up top.

---

### Post by sandy0594 on 2011-04-08
Oh !  anyhow,thanks for ur time Mike
have a great day!!

---

