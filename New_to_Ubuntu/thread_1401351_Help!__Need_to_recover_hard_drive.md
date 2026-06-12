---
title: "Help!  Need to recover hard drive"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by bug67 on 2010-02-08
I installed Ubuntu X64 on a *separate* internal hard drive.  I *can* boot either in Windows 7 or Ubuntu.  However I do not want Ubuntu on the second drive.  I want my system back to the way it was before install.  I.E. no Grub, no Ubuntu.  As it is now, when I boot into Windows, I cannot see the drive with Ubuntu on it.  How do I fully recover this drive for Windows only use and eliminate Ubuntu and restore my system to the way it was?  Thanks.

---

### Post by switch10 on 2010-02-08
put in a LiveCD, go to system>administration>gparted, and reformat the partition that has Ubuntu on it to NTFS.  You will lose all data on that partition, unless you back it up.  Windows will now see it as a separate partition/disk.

---

### Post by bug67 on 2010-02-08
That didn't work!  I wiped that drive with gparted and, when I tried to re-boot, I get:

```
GRUB loading.
error: no such disk
grub rescue_>
```

Can't boot into Windows.  How do I get rid of grub altogether?

Please help.  I don't want Ubuntu on any of my hard drives.  I want to go back to the way things were before I got all froggy.

---

### Post by adam814 on 2010-02-08
You need to restore your Windows MBR.  One way to do this is to access the "Recovery Console" which is usually available on Windows install CDs.  Maybe this will help:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Specifically I believe you need to run fixmbr followed by fixboot.

If that's not a possibility you can *probably* do it one of the ways mentioned in post #10 on this thread:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

The one time I've needed to uninstall Ubuntu from a machine I restored the Windows MBR from the Recovery Console, so I know for sure that works.

---

### Post by Cheezespread on 2010-02-08
Or you could use something like SuperGrub to restore the Windows bootloader and then remove the partition allocation for Linux.

---

### Post by bug67 on 2010-02-08
Thanks guys, for all the help.  Unfortunately, all I have is the recovery disks from HP I made when I got the computer.  If I had an *actual* copy of Windows 7, resetting the MBR would probably work.  None of the options for resetting the MBR are available from the HP restore disks that I could see.  The options you guys suggested from within Ubuntu itself won't work either because I have no Internet connection when the machine is booted into Ubuntu.  

So, I am completely reformatting.  Not really a huge deal as I am meticulous about back up.  I guess, for now, my Ubuntu experience will remain in the 32 bit realm on the machine in my sig.  Thanks again!

---

