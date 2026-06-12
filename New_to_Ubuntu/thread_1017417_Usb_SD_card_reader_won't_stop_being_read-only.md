---
title: "Usb SD card reader won't stop being read-only"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by mrblondeisback on 2008-12-21
So I've got a usb card reader for my micro sd card, and I'm having a lot of difficulty modifying it.  I tried mounting it via the terminal with sudo mount vfat /dev/sdc1 /media/disk1 but that just makes it crash when I open it, and when I let HAL mount it, it mounts to /media/Kingston, so I did a chown and chmod but it wouldn't let me, kept saying it's read only.  Here's my output of ls -la /media if that's any help...

```
mrblonde@TeleTranOne:~$ ls -la /media
total 56
drwxr-xr-x  6 root     root      4096 2008-12-20 23:17 .
drwxr-xr-x 21 root     root      4096 2008-12-02 16:32 ..
lrwxrwxrwx  1 root     root         6 2008-01-13 04:59 cdrom -> cdrom0
drwxr-xr-x  2 root     root      4096 2008-01-13 04:59 cdrom0
drwxrwx---  4 root     mrblonde  4096 2008-11-17 01:16 disk
drwxrwxrwx  2 mrblonde mrblonde  4096 2008-05-24 17:05 disk1
-rw-r--r--  1 root     root       173 2008-12-20 23:17 .hal-mtab
-rw-------  1 root     root         0 2008-12-20 22:50 .hal-mtab-lock
drwx------  8 mrblonde root     32768 1969-12-31 16:00 Kingston
mrblonde@TeleTranOne:~$ 

```

I just wanna put music on my phone.  Any help would be just wonderful!

---

### Post by gn2 on 2008-12-21
Something to try:
Press Alt & F2 then type: gksudo nautilus

Then plug the usb card reader in, letting it mount as /media/Kingston

Nautilus file browser will open with admin privileges, you should now be able to drag and drop your music into /media/Kingston

Remember to close Nautilus after you're finished.

---

### Post by mrblondeisback on 2008-12-21
No, didn't work.  Still keeps saying the filesystem is read-only.  It's FAT32, dunno if that makes a difference.

---

### Post by gn2 on 2008-12-21
Have you tried re-formatting it, or deleting the partitions on it and creating new ones?

---

### Post by mrblondeisback on 2008-12-21
I will try, but the phone has to format the thing, so I imagine it's going to be the same issue.  I know it worked on a windows computer, so it's not like the card is bad or anything.  I'll just delete all the partitions and format it again though, just to make sure.  Thanks for all the help, too.

---

### Post by gn2 on 2008-12-21
Do you have a USB cable for the phone?

---

### Post by mrblondeisback on 2008-12-21
Somewhere, but I've tried that before.  The phone doesn't act like a card reader, I get nothing with the usb cable.  It's an LG Chocolate, one of the newer (but not newest anymore, I think) models.

---

### Post by mrblondeisback on 2008-12-21
Fsck I reformatted it to ext3 to see if that would work and now it won't mount at all. Effin A.  Here's what I got:

```
mrblonde@TeleTranOne:~$ sudo mount -t ext3 /dev/sdc1 /media/Kingston/
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mrblonde@TeleTranOne:~$ dmesg | tail
[  198.386207] sd 8:0:0:0: [sdc] Write Protect is off
[  198.386207] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  198.386207] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  198.387780]  sdc: sdc1
[  198.392947] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[  198.393088] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  271.866858] VFS: Can't find ext3 filesystem on dev sdc1.
[  377.266214] VFS: Can't find ext3 filesystem on dev sdc1.
[  549.642341] EXT3-fs error (device sdc1): ext3_check_descriptors: Inode bitmap for group 0 not in group (block 65788)!
[  549.647625] EXT3-fs: group descriptors corrupted!

```

Also, I tried it with a different microSD card, and that one works, no problem.  It's just much smaller.  So is my big card just messed up or something?  It's pretty new, and I could read everything on it, and it worked like 4 days ago on a windows machine.  Ugh.  Frustrating.  But at least I can put music on this other smaller card.

---

### Post by stalkingwolf on 2008-12-21
It would appear that your computer is reading the card like a preburned CD
Try,  when the file browser opens it should show an icon on your desktop.
Right click it , select permissions, make sure/ change permissions to read/write.  You may have to open a terminal and navigate to this card ,
then CHOWN.

Sorry my instructions may not be exact.

---

### Post by mrblondeisback on 2008-12-22
It doesn't let me chown.  every time I do, it just says "Filesystem is read-only."

---

### Post by mcnesium on 2009-01-29
same issue here. whats the matter with this? my buddy whos card it is said "this is because of your freaky operating system. i'll do it with my windows laptop, there it works." sux... :/

---

### Post by ku5165 on 2009-02-10
if you use a windows computer and take of read only, ive heard it works...just my 2cents, ive had the problem and it somehow fixed when i did something like that

---

### Post by drhiii on 2009-02-17
I have the same problem.  Was working fine in 8.04.  All removable media was able to read and write.  On upgrading to 8.10, all removable media is mounted as read-only.  I cannot change perms, ownership, nuttin.  This as su.  

Help anyone?  Am searching around for a solution and see it mentioned, but no solution offered so far.  

Help?

---

### Post by dogeatery on 2009-03-30
I'm having this same problem but only with my MiniSD card reader.  And it only happens sometimes, choosing randomly when it wants to be difficult.  chown doesn't work, gksudo nautilus doesn't work, nothing.  Making it weirder, when I go into the file properties and look at permissions, the boxes are checked for read, write and execute.

Both my computers do this, both run Mint but one runs Hardy and one runs Intrepid.

Surely there's a fix?

---

### Post by drhiii on 2009-03-30
> **dogeatery said:**
> I'm having this same problem but only with my MiniSD card reader.  And it only happens sometimes, choosing randomly when it wants to be difficult.  chown doesn't work, gksudo nautilus doesn't work, nothing.  Making it weirder, when I go into the file properties and look at permissions, the boxes are checked for read, write and execute.

Both my computers do this, both run Mint but one runs Hardy and one runs Intrepid.

Surely there's a fix?

It seems to have something to do with how the version of Ubuntu "sees" the media, as to whether it is healthy, or corrupted.  Lazy Windows is lazy, did I mention lazy... about how it looks at this media.  Am not an engineer, but on some media sticks that are not read, I finally found that Ubuntu considered it to be corrupted and recommended dosfck to fix the corruption.  Problem became... some of the media was considered not fixable.  So it was left to flap in the wind.

I have yet to find a reasonable solution, but at least I think it has to do with when the media is read, and it sees what it considers to be a filesystem corruption, it will not mount it.  dosfck is as close as I have come to resolving this, but it is far from perfect.  I wish Ubuntu was a bit more descriptive about what it sees as the problem, and reports on it.

---

### Post by dogeatery on 2009-03-30
drhiii, thanks for the reply.  The card mounts, reads and executes, but it doesn't allow me to write any new files to the disk.  I can even delete files from the disk!

Perhaps I should mention that I use it with a Nintendo DS flash card.  Not sure if that makes a difference or not, but it was working just fine even earlier today in my Hardy install and has been working for the four months since I bought it.

---

### Post by drhiii on 2009-03-30
> **dogeatery said:**
> drhiii, thanks for the reply.  The card mounts, reads and executes, but it doesn't allow me to write any new files to the disk.  I can even delete files from the disk!

Perhaps I should mention that I use it with a Nintendo DS flash card.  Not sure if that makes a difference or not, but it was working just fine even earlier today in my Hardy install and has been working for the four months since I bought it.

As mentioned prior... I believe it is because Ubuntu sees the card's file system as corrupted.  Try to use   dosfsck -a -v /dev/sdb1   and replacing the device with where the card is mounted.  Oh, you need to unmount it before  running this.  If you need deeper instructions, let me know.  This is not guaranteed to work, but it did repair and then allow one of the cards I had to be read.  Two others were considered to be not repairable.  Another way is to place them in a Windows machine, and run chkdsk or something else against it, and then eject the disk carefully.  I think it's because Ubuntu (and I mean the filesystem under it, not Ubuntu itself) sees the disk as corrupted usually because it sees the disk as having been removed without closing it, something like that.  

These are obviously not technical explanations... just something I have observed.  The better thing is to swear off anything Windows related.  I have nothing but trouble every time I get near a Windows machine, and so do a lot of my friends and associates.

---

### Post by dogeatery on 2009-03-30
Thanks drhiii.  I think I misunderstood your previous post (thinking that you misunderstood *my *previous post)

I've backed up the drive's contents (it'll let me copy/paste files from the device) and then ran your command after unmounting the device.  PROBLEM SOLVED! :KS

For anyone else with this problem the command, again, is:

[QUOTE]dosfsck -a -v /dev/sdb1[/QUOTE}

Just replace the /dev/sdb1 with your device's mountpoint

---

### Post by drhiii on 2009-03-30
> **dogeatery said:**
> Thanks drhiii.  I think I misunderstood your previous post (thinking that you misunderstood *my *previous post)

I've backed up the drive's contents (it'll let me copy/paste files from the device) and then ran your command after unmounting the device.  PROBLEM SOLVED! :KS

For anyone else with this problem the command, again, is:

[QUOTE]dosfsck -a -v /dev/sdb1[/QUOTE}

Just replace the /dev/sdb1 with your device's mountpoint


Cool.  Glad it worked.  It rescued one of two external devices I had, so at least yours was in the positive group.  Very good.

---

