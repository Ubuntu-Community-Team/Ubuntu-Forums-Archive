---
title: "External Harddrive Issues :("
date: 2008-12-14
forum: New to Ubuntu
---

### Post by kevn3k on 2008-12-14
Hi everyone,

I've got a 1TB external harddrive that I'm using to keep a bunch of things on, namely video files so I can watch them on my PS3.  Because I want to use it on my PS3, I need to keep the filesystem as FAT32.  However, the last time I used my harddrive, I had to disable EHCI support in order for it to work properly.  Now, I'm getting a problem where it's mounted on the first go, but all of my files are missing!  Navigating in the harddrive in the GUI shows my folders, but no contents at all.  The harddrive still shows a size of 1TB with 627GB free when I check in the GUI (right click, properties, and look at the pie chart), but when i do sudo fdisk -l, I get this

```
Disk /dev/sdc: 7761 MB, 7761575424 bytes
255 heads, 63 sectors/track, 943 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda22130c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(121600, 254, 63)

```

Which is blatantly wrong.  Any ideas?  If it's any difference, I'm in 8.04

---

### Post by kevn3k on 2008-12-14
Also, whenever i try to use fsck.vfat /dev/sdc1, i always get this message

```
Read 32 bytes at 317241996288: Input/output error
```

This happens regardless of whether i tack on -a or -y at the end or not :(

---

### Post by kevn3k on 2008-12-14
Okay, just to keep updating things, I've tried hooking the harddrive up to a Windows system, and it sees the drive just fine, as well as the files.  So that's a plus, at least if worst comes to worst, I can always just back everything up into a Windows computer at work.

Now, after doing that, I tried plugging it back into my machine and fdisk recognized it as being 1TB instead of ~7-8GB.

However, now I can't see the file folders when I use nautilus to access the drive.  Also, if i go to /media/MrT and do the bash command 'ls', i get this output:

```
ls: cannot access TV_Shows: Input/output error
ls: cannot access tmnt: Input/output error
ls: cannot access Animaniacs: Input/output error
ls: cannot access Dilbert: Input/output error
ls: cannot access Movies: Input/output error
ls: cannot access Reboot: Input/output error
ls: cannot access MrTMusic: Input/output error
Animaniacs  Movies    Planet Earth HD  $recycle.bin               tmnt
Dilbert     MrTMusic  Reboot           System Volume Information  TV_Shows

```

I don't know what's causing this though.  Also, the output of dmesg|tail is this: 

```
[ 2022.812133] FAT: Filesystem panic (dev sdc1)
[ 2022.812134]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2022.812175] FAT: Filesystem panic (dev sdc1)
[ 2022.812177]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2031.193002] FAT: Filesystem panic (dev sdc1)
[ 2031.193008]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2031.193025] FAT: Filesystem panic (dev sdc1)
[ 2031.193026]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2031.193037] FAT: Filesystem panic (dev sdc1)
[ 2031.193039]     fat_get_cluster: invalid cluster chain (i_pos 0)

```

Any ideas?

---

