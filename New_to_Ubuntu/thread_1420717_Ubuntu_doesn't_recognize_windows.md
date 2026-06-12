---
title: "Ubuntu doesn't recognize windows"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by dc10 on 2010-03-03
Hello,

I'm new to ubuntu and burned an image to a cd. I have winxp installed and after reboot, in the process of installing ubuntu, in the 4th step, Analizing disks...

- This system has no operating system.

Use the entire disk or
Do a manually partition

Why doesn't the installer recognize that winxp is installed in my computer?

What should I do?

Thank you!

---

### Post by Gone fishing on 2010-03-03
Certainly manually partition.

I'd reboot make sure XP boots OK

Then I'd start on a live CD run gparted and make sure the Windows partition is there you can then use gparted to resize the partition.

Then install ubuntu and choose the install into largest free space option

---

### Post by dc10 on 2010-03-03
I've rebooted and windows xp runned ok.

Then I rebooted again with the ubuntu cd, and runned a terminal.

$ sudo gparted

gparted said No devices were detected

It's strange :/

I don't understand why not recognize my winxp partition!

---

### Post by dc10 on 2010-03-03
Oh and some information maybe will help you:

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ cat /proc/partitions 
major minor  #blocks  name

   7        0     684016 loop0
   8        0   78150744 sda
ubuntu@ubuntu:~$ 

fdisk -l doesn't show me any partition :/

---

### Post by Gone fishing on 2010-03-03
This is very odd.

Let start with the obvious only one HD no flash disks plugged in?
If not I think I'd restart in XP and then run check the hard drive with chkdsk. 

Make sure every thing is OK then install, possibly do the partitioning with parted magic [http://partedmagic.com/](http://partedmagic.com/) or similar. Though I've never had a problem with the partitioning tool in Ubuntu

---

### Post by dc10 on 2010-03-03
That's what display chkdsk on cmd on winxp:

C:\Documents and Settings\alex>chkdsk
The type of the file system is NTFS.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.

  78140128 KB total disk space.
  12359652 KB in 38385 files.
     11484 KB in 3974 indexes.
         0 KB in bad sectors.
    111872 KB in use by the system.
     65536 KB occupied by the log file.
  65657120 KB available on disk.

      4096 bytes in each allocation unit.
  19535032 total allocation units on disk.
  16414280 allocation units available on disk.

C:\Documents and Settings\alex>

What's wrong? I don't understand.

---

### Post by audiomick on 2010-03-03
You might have more success with the alternate CD. It has a different partitioning tool in it.
The Graphic installer, i.e. the normal live CD, couldn't find one of my two Drives, but the alternate installer did. I have also seen quite a number of posts from people who had similar problems and could solve them with the alternate CD.
It is a text based installer, which looks a bit scary when you first see it, but it is not hard to manage.

---

### Post by Gone fishing on 2010-03-03
Boot up on the XP disk and try chkdsk /f

---

