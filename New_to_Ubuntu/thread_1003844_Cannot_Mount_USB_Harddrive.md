---
title: "Cannot Mount USB Harddrive"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by kevn3k on 2008-12-06
Hi all,

I know this topic has been beaten to death, but I don't see anyone who's been having exactly my problem.  I have a 1 TB Maxtor External Harddrive that I've formatted to FAT32 so that I can use it to play movies/music etc... on my PS3.  I had it working fine in Linux and it works in Windows there, too.  BUT!  Every time I plug the harddrive into a Windows computer, I'm unable to re-mount it into my Ubuntu machine!  It won't do anything!  I really don't want to reformat it again :(  I have a good amount of files on there now.  For the record, I'm running Ubuntu 8.04.

So here's what happens:

When I plug in the harddrive, I get a message saying "Cannot mount volume.  You are not privileged to mount the volume 'Mr T'."  So I hit "OK".

Then, I do sudo fdisk -l and get this output (I haven't included the output for the other internal drives)

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda22130c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    b  W95 FAT32

```

So, obviously, it's recognized as W95 FAT32 for the filesystem.  So I try
```
sudo mount /dev/sdc /media/MrT
```
(and, yes, the directory /media/MrT has been created already)

I am then told to specify the filesystem type, so I type in
```
sudo mount -t vfat /dev/sdc /media/MrT
```

and I get 

```
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

the output for dmesg | tail is

```
[ 3644.512341] FAT: invalid media value (0xb9)
[ 3644.512347] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 3666.903138] FAT: invalid media value (0xb9)
[ 3666.903143] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 3703.628091] FAT: invalid media value (0xb9)
[ 3703.628097] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 4067.870962] FAT: invalid media value (0xb9)
[ 4067.870968] VFS: Can't find a valid FAT filesystem on dev sdc.
[ 4667.586619] FAT: invalid media value (0xb9)
[ 4667.586625] VFS: Can't find a valid FAT filesystem on dev sdc.

```

Does anybody know what's going on?  I could really use a hand here!  I can use my 8GB memory stick with both Windows and Ubuntu systems just fine, but this harddrive is really becoming quite a pain in the neck!

---

### Post by Duck2006 on 2008-12-06
When you remove it from windoze do you do safe remove?

---

### Post by kevn3k on 2008-12-06
Yeah, forgot to mention, I always use the Safe Remove option in Windows, and I'm still having this issue :(

---

### Post by Duck2006 on 2008-12-06
These may help.

[http://ubuntuforums.org/showthread.php?t=48126](http://ubuntuforums.org/showthread.php?t=48126)
[http://ubuntuforums.org/showthread.php?t=921679](http://ubuntuforums.org/showthread.php?t=921679)

---

### Post by kevn3k on 2008-12-06
Thanks Duck!  Those worked great!  The sudo modprobe -r ehci_hcd worked beautifully!  It changed the fdisk -l output to the following:

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda22130c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    b  W95 FAT32

```

Which doesn't look too different except for the device is now listed as /dev/sdc1 instead of /dev/sdc!  and then the mount worked fine.  Thanks so much!

---

### Post by kevn3k on 2008-12-06
On a related note, does anyone know of a way I can get that to happen every time I plug in the device?  I know I'd have to add it to fstab, but what about the modprobe command? Will that need to be incorporated?  If so, how?

---

### Post by Duck2006 on 2008-12-06
No you shouldn't have to do it every time you boot, give rebooting a try and see if it works.

---

### Post by kevn3k on 2008-12-06
Alright, I'll try that later, I'm studying for my finals right now.  I realize that doing that command removes the USB 2.0 controller from the equation, which is fine, it just means the transfer is going to take forever (about 10 more hours).  Does anybody happen to know how I can get this to work with EHCI support again?  1TB of space to fill at a 1MB/sec is almost enough to make me cry, hahaha.

---

