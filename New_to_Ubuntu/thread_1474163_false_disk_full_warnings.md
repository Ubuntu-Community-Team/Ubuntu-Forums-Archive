---
title: "false disk full warnings"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-05-05
Currently I have 170GB free in my home partition and 28 GB free in /. However every time I try to backup my 70GB of files I get disk full warning and then grsync stops. I think the mounted disks are in media and counting as used instead of as external devices. Is there a fix for this?

---

### Post by Peter09 on 2010-05-06
Do a 
```
df 
```
to show your free space for each partition.
 
The problem may be that you have enough free space in total but not enough in a particular area.

---

### Post by tropdoug on 2010-05-06
If you are getting the file sizes by using nautilus, it will not show the true size of all files, even if you have shown your hidden ones. However use this code to see the correct size of all the files on your partition.

```
df -ch
```

The -c tells df to total the files and the h presents it in human format

---

### Post by cmcanulty on 2010-05-06
I am getting size empty from gparted. True /doesn't have enogh space for the 70GB backup but I am backing up to an ext hard drive not ?
```
cmcanulty@Gateway:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             44267840  14797856  27221288  36% /
none                    508188       284    507904   1% /dev
none                    512548      6964    505584   2% /dev/shm
none                    512548       100    512448   1% /var/run
none                    512548         0    512548   0% /var/lock
none                    512548         0    512548   0% /lib/init/rw
/dev/sda3            260438464  83256032 163952912  34% /home
cmcanulty@Gateway:~$ 

```
```

cmcanulty@Gateway:~$ df -ch
df: invalid option -- 'c'
Try `df --help' for more information.
cmcanulty@Gateway:~$ 
```

---

### Post by Peter09 on 2010-05-06
I can think of three scenarios here
 
1. One you are actually backing up to a place you do not mean to back up to
2. During backup your system is trying to save a temporay file somewhere
3. You are using a 32 bit O/S which is having problems addressing a file of that size

---

### Post by Grenage on 2010-05-06
FAT32 drive, and files that might be larger than 2GB?

---

### Post by Peter09 on 2010-05-06
Ahh good one Grenage

---

### Post by cmcanulty on 2010-05-06
No file over 1 GB I am backing up to /media/ then my ext HD. I am using grsync and browsing to destination which is the ext HD every time I try to back up it stops due to full disk when I have over 100 GB free on ext HD then it unmounts disk

---

### Post by Paddy Landau on 2010-05-06
As Peter says, it's possible that the program is using a temporary file. For example, if you're using tar to back up, then it will use /tmp for the temporary file unless you tell it otherwise.

What program are you using to back up?

---

### Post by cmcanulty on 2010-05-06
grsync

---

### Post by Paddy Landau on 2010-05-07
> **cmcanulty said:**
> grsync
Thanks. I should have noticed that in your first post!

grsync is a front-end to rsync, which, to the best of my knowledge, should not have that problem.

I understand that you're backing up to an external hard drive. Is that right?

When using rsync, to avoid straying away from the file system that you're backing up, you use the option [FONT=Courier New]-x[/FONT] or [FONT=Courier New]--one-file-system[/FONT]. I've never used grsync, so I don't know how to put that option in.

I'd like you to plug in your external hard drive, and then do the command that you were given before:
```
df -h
```I'd like to see the space that you have not only on your [FONT=Courier New]/home[/FONT] partition, but also on the partition where you are trying to save your backup.

---

### Post by tropdoug on 2010-05-07
I got the wrong command before, sorry

try du -ch on the drive your wanting to backup that will show you the exact size of all files on the drive, individually and as a total

---

### Post by Paddy Landau on 2010-05-07
> **Paddy Landau said:**
> When using rsync, to avoid straying away from the file system that you're backing up, you use the option [FONT=Courier New]-x[/FONT] or [FONT=Courier New]--one-file-system[/FONT]. I've never used grsync, so I don't know how to put that option in.
I've just loaded grsync to check it out. The option is "Do not leave filesystem." Ensure that you have that ticked.

---

### Post by warfacegod on 2010-05-07
Just a thought here. Is it somehow possible that the OP is running up against the system reserve on the external? Default is 5% of the drive. If there are 100GB free and assuming its a 1 TB drive, 70 GB would be about 20 GB too much.

```
sudo tune2fs -m x /dev/sdx#
```

This will change the system reserve. The first x is the percent of the reserve so replace it with a number (I have my external set to 0. As in zero %). x# will need to be changed to match the appropriate drive. For example, my external is usually sd*b1*

---

### Post by warfacegod on 2010-05-07
The more I think about this, the more I'm convinced its the system reserve. Unless the drive is about 600 GB or less, the 5% reserve with 100 GB free is going to stop a 70 GB transfer dead in its tracks. Whether its rsync or even just a manual transfer of data.

---

### Post by Grenage on 2010-05-07
Does system reserve list reserved space as free space?

---

### Post by warfacegod on 2010-05-07
> **Grenage said:**
> Does system reserve list reserved space as free space?

It does in Nautilus and I *think* with df but I don't think gparted sees it as free. Or maybe its the other way around, I can't remember at the moment.

---

