---
title: "Root question a la noob"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by holadebob on 2010-03-16
I am confused about how the root directory is used in the structure of the Ubuntu system. First of all I have two hard drives, one is a 40 gig that I put the system root on when I installed Jaunty. 
The root directory shows these stats:
/dev/sda1  /  ext3  36.7Gib Total, 51.2MiB Free, 0 Avail, 36.6GiB Used. 100% in use.

The other drive (160 GiB) looks like this:
/dev/sdb2  /home        ext3      55GiB total, 46.6GiB Free 16% used
/dev/sdb5  /media/disk  fuseblk   70.9GiB total, 39.2GiB Free 44% used
/dev/sdb7  /use/local   ext3      19.1GiB total 18.9GiB Free 0% used. 

I am confused because the root directory shows no space available, and it also includes the files from media, which is referring to the sdb5 media drive. I understand from the web that the root directory is the top directory and contains all files. Apparently when I directly load files into the sdb5 partition (the other hard drive partition), it also goes into the media folder in the root directory. So how do I keep things separate so that my sda1 drive doesn't get filled up with duplicates. I installed Jaunty after reading as much as could understand, and most advice was to use about 20 GiB for the root, so I just used my 40 Gig drive thinking, ah that's great with room to grow and it separates my files in case of disaster I could recover easier. 

Hope you can understand this - it's clearly confusing to me. :)

Throw it at me and chuckle - I'm ready.

---

### Post by lidex on 2010-03-16
What is the output of :
```
sudo fdisk -l
```

That's a terminal command (small L, not 1). "Applications>Accessories>Terminal"
Supply your user password when prompted.

---

### Post by undecim on 2010-03-16
Your root directory will not get any duplicate files. Filesystems are mounted to a folder, so if you have /dev/sda5 mounted to /media/disk, then the folder /media/disk will display the files on /dev/sda5. If you umount /dev/sda5, then /media/disk will be empty, because /media/disk on /dev/sda1 is empty.

It looks to me though that you need to make space on your root partition, otherwise you may be having problems soon, since you have no space. Have you been installing a lot recently?

---

### Post by holadebob on 2010-03-16
Lidex - here's the printout..

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41774177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71be71be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            7296       19456    97683232+   5  Extended
/dev/sdb2               1        7295    58597056   83  Linux
/dev/sdb5           10200       19456    74356821    7  HPFS/NTFS
/dev/sdb6            9829       10199     2979994+  82  Linux swap / Solaris
/dev/sdb7            7296        9828    20346259+  83  Linux

Undecim -- I have been doing a bit of installing, trying out stuff and uninstalling, so that fills up root? Well, I will attack that problem. And thanks for the comment about the media, the disk was mounted and I didn't know that it's files would show up in root like that. I guess that's what they mean about "mounted" eh? :)

Thanks again

---

### Post by lidex on 2010-03-16
As I suspected, and undecim points out. It's a weird (to me) partitioning scheme - what led you to that? :-k

---

### Post by holadebob on 2010-03-17
Please tell me what is wrong with my partitions. I read and read lots of info on partitioning, and when it came down to actually doing it, I followed a composite of stuff that I'd read. The actually manual process of setting partitions was a little confusing to me, and It also wouldn't let me include a strange 8 mb block of sdb into a partition, so I just went with the flow. Someone advised that many small partitions are better than one big one, so that's why the use of the user partition. I have the one part of the sdb drive partitioned with NTFS, because I have some windows files that wouldn't go on the ubuntu formatted drives.
Please give me a recommendation as to what to do.
Thank you

---

