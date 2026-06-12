---
title: "Can't fit"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by akelsall on 2009-10-28
I'm trying to figure out why I can't fit a 9G file onto a USB
(formated at FAT32) onto a 16G flash card (I formatted it FAT32 
so I can use it on both a Windows and Linxu system). 

I've attempted this twice, and both times it dies after roughly 4Gig is transferred (giving the error message shown below). Any ideas
why it's unable to copy a 9Gig file onto a flash card that had all 16 Gig free (and still shows 12G available)????

/media/disk$ cp /windows/WinXP.vdi  .
cp: writing `./WinXP.vdi': File too large

/media/disk$ df -h /dev/sdb1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              16G  4.1G   12G  27% /media/disk

/media/disk$ ls -lh /windows/WinXP.vdi
-rwxr-xr-x 1 hiker hiker 9.3G 2009-10-28 14:00 /windows/WinXP.vdi

Here's how it's being mounted by the system (output is from the *mount* command:

/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)

---

### Post by Gazneth on 2009-10-28
Fat 32 has a file size limit of 4 GB per individual file. One way around this is to use compression such as RAR and break your file into several pieces. Other than that I would recommend a more modern file system like Ntfs or ext3. Ubuntu reads and writes Ntfs just fine.

---

### Post by Jazzy_Jeff on 2009-10-28
> **gazneth said:**
> fat 32 has a file size limit of 4 gb per individual file. One way around this is to use compression such as rar and break your file into several pieces. Other than that i would recommend a more modern file system like ntfs or ext3. Ubuntu reads and writes ntfs just fine.

+1

---

### Post by H3l0 on 2009-10-28
he hit the nail on the head.

---

### Post by lavinog on 2009-10-28
> **akelsall said:**
> 
/media/disk$ cp /windows/WinXP.vdi  .
cp: writing `./WinXP.vdi': File too large



I would be curious what windows says when during this operation.
Maybe Ubuntu can be a leader by giving a better error message like: "File size exceeds FAT32 limit."

---

### Post by akelsall on 2009-10-28
> **Gazneth said:**
> Fat 32 has a file size limit of 4 GB per individual file. One way around this is to use compression such as RAR and break your file into several pieces. Other than that I would recommend a more modern file system like Ntfs or ext3. Ubuntu reads and writes Ntfs just fine.

Thanks Gazneth. That explains what's happening. Now I have a related issue. I ran gparted and it does not provide an option to format as ntfs. Neither does mkfs. Any ideas? here's the output when I enter **mkfs** followed by the TAB key:

someone@somewhere:/media$ mkfs.
mkfs.bfs       mkfs.ext2      mkfs.ext4      mkfs.minix     mkfs.reiserfs  
mkfs.cramfs    mkfs.ext3      mkfs.ext4dev   mkfs.msdos     mkfs.vfat  

thanks,

Andy

---

### Post by lavinog on 2009-10-28
you can format it as ext3 if you are not planning to use it on windows computers.

---

### Post by 3rdalbum on 2009-10-29
> **akelsall said:**
> Thanks Gazneth. That explains what's happening. Now I have a related issue. I ran gparted and it does not provide an option to format as ntfs. Neither does mkfs.

You need the *ntfsprogs* package from the repositories.

---

### Post by akelsall on 2009-10-29
> **3rdalbum said:**
> You need the *ntfsprogs* package from the repositories.

That's the program I needed! I just upgraded to 9.04 and forgot to re-install ntfsprogs. 

I failed to mention that I did indeed need to use it on a Windows machine (I'm backing up my VirtualBox .vdi file onto my wife's PC. Shhhhhh don't tell her   :lolflag:

Thanks to all those who tried to help, and a big thanks to 3rdalbum!!

Andy

---

### Post by lavinog on 2009-10-29
compressing the image into a split volume would have worked also:
```

7z a -v2g archive.7z filetoarchive

```
-v2g means split up into 2g files

---

