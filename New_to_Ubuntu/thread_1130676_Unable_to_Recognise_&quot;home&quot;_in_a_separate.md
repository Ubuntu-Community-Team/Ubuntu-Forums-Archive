---
title: "Unable to Recognise &quot;/home&quot; in a separate partiiton"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by yessriram on 2009-04-20
Hi. i am not exactly a nube, and have been with the family for about 3+ years. 

have the 8.10 installed. have been breaking my head with the following problem:

(a) suddenly discovered system unwilling to boot properly. after a decent effort at trouble shooting have discovered that the OS is not booting because  "/home", installed in separate partition is not being recognised

(b) ran gparted from LiveCD which recognised all partitions but did not recognise /dev/sda7 where /home exists.

(c) when i boot the system in recovery mode and run "blkid", i see all other partitions with the UUIDs except /dev/sda7.

(d) contents of /etc/fstab pertaining to the partiiton reads:

#/dev/sda7
UUID=813d7216-e737-474f-a825-42314714f74a  /home     ext3    relatime  $



Requesting someone to help me trouble shoot further and understand whats the problem. 
(a) is it that the partition is corrupted?
(b) is yes, then how do i recover data? forensic tools- which ones will work best?
(c) if not, whats the best course of action. 

warm regards & thanks.
Sriram

---

### Post by tarps87 on 2009-04-20
Fstab still supports mounting by device name so changing the entry to this should get you back up and running.

```

#UUID=813d7216-e737-474f-a825-42314714f74a
/dev/sda7  /home     ext3    relatime  $

```

What do this commands return?
```
sudo vol_id -u /dev/sda7
```
```
ls -l /dev/disk/by-uuid/
```

If the isn't an entry in either of these you will have to create a new UUID. Unfortunately the only way I remember how to create a UUID is by formatting the drive. I know there is a way to set it without formatting the drive, just not how to do it.

---

### Post by mikechant on 2009-04-20
> (b) ran gparted from LiveCD which recognised all partitions but did not recognise /dev/sda7 where /home exists.

What exactly does gparted show? Free space? Maybe you could post a screenshot?

---

### Post by mikechant on 2009-04-20
> Unfortunately the only way I remember how to create a UUID is by formatting the drive. I know there is a way to set it without formatting the drive, just not how to do it.

To set the UUID of an ext2/3/4 partition to a given value:

```
sudo tune2fs -U uuidvalue /dev/yourdevname
```

---

### Post by tarps87 on 2009-04-20
> **yessriram said:**
> 
(b) ran gparted from LiveCD which recognised all partitions but did not recognise /dev/sda7 where /home exists.


I miss read this as did recognise, what did gparted say about the partition, also does fdisk -l show any thing```
sudo fdisk -l
```

Assuming it is ext3, this will generate a random UUID on the drive.
```
sudo tune2fs -U random /dev/sda7
```
I would recommend trying this after we have sorted out why the drive can not be seen

---

### Post by tarps87 on 2009-04-20
> **mikechant said:**
> What exactly does gparted show? Free space? Maybe you could post a screenshot?

> **mikechant said:**
> To set the UUID of an ext2/3/4 partition to a given value:

```
sudo tune2fs -U uuidvalue /dev/yourdevname
```

How dare you beat me twice :)

---

### Post by yessriram on 2009-04-20
Thanks a lot tarps87 and mikechant for your responses. was in fact worried that i wasn't receiving a feedback for sometime. guess i should blame the time zones for the delay. here goes...

(a) executed command "vol_id -u /dev/sda7" in the cli as root.
reply reads "/dev/sda7: unknown volume type"

(b) executed command "ls -l /dev/disk/by-uuid/"
reply:
"total 0
lrwxrwxrwx 1 root root 10 Apr 21 2009 0ef7d076-c39b-4b6f-a5d0-bb781f76a358 -> ../../sda8
lrwxrwxrwx 1 root root 10 Apr 21 2009 488EBoC58EBOACB6 -> ../../sda3
lrwxrwxrwx 1 root root 10 Apr 21 2009 ################# -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 21 2009 ################# -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 21 2009 ################# -> ../../sda5
lrwxrwxrwx 1 root root 10 Apr 21 2009 ################# -> ../../sda6
"

(c) altered the /etc/fstab as suggested to
"#UUID=813d7216-e737-474f-a825-42314714f74a
/dev/sda7  /home     ext3    relatime  $"

upon subsequently booting up, the system boots upto the login screen and once i enter the password, i get the following message:

"Your home directory is listed as: '/home/yessriram' but it does not appear to exist. Do you want to log in with / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."

This is exactly the same thing that's been happening since the problem started.

(d)executed command "fdisk -l"
Result as follows:
Disk /dev/sda: 120.0 GB, ########### bytes
255 heads, ## setors/ track, #### cylinders
Units= cylinders of 1065*512= ###### bytes
Disk identifier= ###########

Device    Boot    Start           END      Blocks      Id     System
/dev/sda1  *          1           ###      ######       7      HPFS/NTFS
/dev/sda2          ####           ###      ######       7      HPFS/NTFS
/dev/sda3          ####           ###      ######       7      HPFS/NTFS
/dev/sda4          ####           ###      ######       5      Extended
/dev/sda5          ####           ###      ######       b      W95 FAT32
/dev/sda6  *       ####           ###      ######       83     Linux
/dev/sda7          ####           ###      ######       83     Linux
/dev/sda8          ####           ###      ######       82     Linux swap/ Solaris

Partition table entries are not in disk order"

(e) booted with LiveCD and ran gparted.
output reads: "Partition=/dev/sda7, Filesystem= Unknown, Label= _____, Size= 16.14 GiB, Used- Nil, unused- Nil, Flags= _____"

sorry, cant post the screenshot coz i am on a different machine and the machine with the problem is what we are discussing. :)

My Analysis:
Guys, I seem to feel that the partition exists (since fdisk seems to identify it correctly) but it is not being recognised. now i cant see to understand why there should be a different output from gParted and from fdisk. is it that fdisk works at a different level!!

should i try and force a uuid onto this partition now? my gut feel is that it will still not accept it. there seems to be something at a lower layer which is creating some problem. this is just my view.

request:
simplest solution is to reformat and do a re-install. i do have some info that i would like to retrieve but thats ok. primary reason i dont want to do this is coz i think i want to figure out what could have happened.
so... any help will be welcome.

regards.
sriram

---

### Post by tarps87 on 2009-04-21
It appears that the partition is there by it is corrupt, fdisk is listing the partition but doesn't list any information on it which is why there is a difference between fdisk and gparted.

As fdisk can see it I don't believe it is a partition table error.

My suggestion would be to run fsck on the partition
```
sudo fsck /dev/sda7
```
If this does not work try
```
sudo fsck -t ext3 /dev/sda7
```

This may fix or revile the problem, but won't tell us why I occurred.
So causes could be:
Moving partitions around
Improper shutdown/power failer
Dyeing hard drive, i.e. dead sectors

If you choose to reformat I suggest that you run the fsck on the partition after to see if it picks anything up.


hope this helps

---

### Post by supererki on 2009-04-21
well there is a backup superblock, and its location depends on a block size used. 
If 1 KB blocks are used, the backup superblock is in block 8193; if 2 KB blocks are used, it is in 16384; and, if 4 KB blocks are used, you can find it in 32768. By running the e2fsck -s 8193 command for example, you may be able to repair a file system that cannot be mounted anymore by using its backup superblock.

---

### Post by yessriram on 2009-04-21
Hey Thanks a ton tarps87.
Solved.:D

Ran "sudo fsck /dev/sda7"
went thru a lot of "yes" for inode errors and multiply-claimed blocks.
finally got out and then rebooted again. the systems working fine.

Thanks a ton guys.

supererki- request you to give me a link to literature about whatever you have riten about.  have dont it budone it without really understanding what i have done. so wold be gratefl if you could give me some links to reading material.

regards & thanks again.
sriram

---

### Post by tarps87 on 2009-04-21
That's ok.
You may want to change fstab back to using the UUID.
I believe supererki's post is describing effectively what fsck has done for you. If fsck couldn't fix the problems using e2fsck may have helped.
It just a shame we can't tell why it happened.

---

