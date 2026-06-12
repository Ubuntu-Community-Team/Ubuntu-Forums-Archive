---
title: "Grub Rescue: no such device"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Zipherroc on 2010-12-07
Hey, I've been having major trouble with my bootloader.  I installed (through windows) the 10.10 wubi version of Ubuntu, and everything worked just fine when I first logged in, but after I ran updates, it updated my grub (probably to grub 2) and it asked me to check off which hard drives to put it on, and as I didn't know any better I checked all of them.  
When I restarted Grub Rescue came up with the error message as follows:
```
error: no such device: a678f9e1-7c1d-4d6d-982a-ec4ce6ca2903
grub rescue>
```
I've looked all over the forums and seen this problem come up, but nothing has helped me solve it.  I've used the windows CD to rewrite the MBR on the first two hard drives, and fiddled with a few other things, including the BIOS, but I think I've probably made the problem worse.

I decided to run through drs305's **Grub Rescue Prompt Megathread**, and the recommendation is run *meierfra's* boot info script.  I did this and now I need help interpreting it.  

There is an error message in the WUBI section below (SDC1), but I'm not sure what it means.  SDA, SDB, and SDC are the hard drives.  SDD and SDE are an external hard drive and USB stick respectively that were attached at the time.  

I was thinking of reinstalling GRUB 2 next.  Is this a good idea?

Here's RESULTS.TXT:  Any help would be much appreciated!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,001,849    40,001,787   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,001,849    40,001,787   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   120,085,874   120,085,812   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 82.0 GB, 81963515904 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32    15,753,214    15,753,183   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a678f9e1-7c1d-4d6d-982a-ec4ce6ca2903   ext4                                     
/dev/sda1        F40C20BC0C207C2C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        08C88904C888F0EC                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3ED00256D0021535                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        AC0222050221D4DC                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        CC1C-1C01                              vfat       FIRESTICK                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/FIRESTICK         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by bcbc on 2010-12-07
See this link [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Problem #1, Solution #1 or #2.

Note, if you choose to reinstall the Windows bootloader, do not mess with the bootsector (fixboot) you just need the bootloader in the MBR (xp:"fixmbr" or vista/7:"bootrec.exe /fixmbr")

---

### Post by wilee-nilee on 2010-12-07
Do you have a XP install disc to reload the MS bootloader to the MBR?

Do you have a Ubuntu disk to load a compatible bootloader to the MBR?

I just noticed bcbc posted with a great link asking the same basic info yeah for everybody.;)

---

### Post by Zipherroc on 2010-12-07
I have tried running the XP fixboot and fixmbr, in c: and d: (I guess they'd be sda and sdb).  Still goes to the same message.

I just tried the lilo thing for SDA, and restarted and it went to the same prompt (error, no such device etc, grub rescue).

I think SDA is the windows install, but I also think that SDB has one too, because I used to be able to choose either when it was just windows.

Also my boot order in BIOS has **Other Boot Device: Onboard ATA100 Boot**, placed before **IDE Hard Drive: Maxtor 6Y060L0**.  Maybe this has something to do with it?

Any more ideas?

---

### Post by Zipherroc on 2010-12-07
Oh and if I reverse the order in BIOS so that IDE Hard Drive is first, then the new error message is as follows:

NTLDR is missing
Press Ctrl+Alt+Del to restart

---

### Post by bcbc on 2010-12-07
Whatever you do, don't reinstall grub2. that will make things MUCH worse.

You need to fixmbr on both /dev/sda and /dev/sdb. Changing the boot order doesn't work, because you need to boot the drive with the Windows XP boot partition on it first.

Run the bootinfoscript again and let's see where you're at.

---

### Post by Zipherroc on 2010-12-07
OMG!!!  I ran Lilo again on SDA and then on SDB and I just got the bootloader menu with two windows and one Ubuntu option!  It's loading XP as we speak.  If it loads Ubuntu ok, should it be ok now, or should I uninstall it or install some patch?  You have no idea how this problem's been plaguing me for the past week.  THANKYOUTHANKYOUTHANKYOU!

---

### Post by bcbc on 2010-12-07
> **Zipherroc said:**
> OMG!!!  I ran Lilo again on SDA and then on SDB and I just got the bootloader menu with two windows and one Ubuntu option!  It's loading XP as we speak.  If it loads Ubuntu ok, should it be ok now, or should I uninstall it or install some patch?  You have no idea how this problem's been plaguing me for the past week.  THANKYOUTHANKYOUTHANKYOU!

Sweet...
I suspect Ubuntu will boot. If not, post back and we can try some more stuff.

Avoid all updates to packages grub-pc and grub-common in the future.

---

### Post by molave on 2010-12-28
I'm a longtime Windows user (but not an admin) and was trying Ubuntu for the first time. Just now I downloaded and used the Wubi installer (it said 10.04). I was able to install it, but after following the prompt to update some needed files, I encountered exactly the same problem.

I know nothing about fixboots or bootloaders or MBR or Lilo or SDA or SDB. None of the forum pages I've visited provides a clear solution, apart from reinstalling XP, that I could actually understand. 

At least one forum thread states that this bug was fixed already, but apparently not. 
[https://bugs.launchpad.net/wubi/+bug/541607](https://bugs.launchpad.net/wubi/+bug/541607)

At this point all my work and all my data are locked up behind a command prompt that says grub rescue and takes no input. 

This is kind of upsetting, because the Ubuntu download page mentioned nothing about any bugs that could end so disastrously for Linux noobs like me. It's not like I did anything irresponsible during the installation process. I just followed instructions. To the letter, in fact... 

Actually, now I'm quite upset. 

Can anybody help?

Thank you.

I'm thinking this is not very good for evangelizing Ubuntu to regular Joes like me.

---

### Post by bcbc on 2010-12-28
> **molave said:**
> I'm a longtime Windows user (but not an admin) and was trying Ubuntu for the first time. Just now I downloaded and used the Wubi installer (it said 10.04). I was able to install it, but after following the prompt to update some needed files, I encountered exactly the same problem.

I know nothing about fixboots or bootloaders or MBR or Lilo or SDA or SDB. None of the forum pages I've visited provides a clear solution, apart from reinstalling XP, that I could actually understand. 

At least one forum thread states that this bug was fixed already, but apparently not. 
[https://bugs.launchpad.net/wubi/+bug/541607](https://bugs.launchpad.net/wubi/+bug/541607)

At this point all my work and all my data are locked up behind a command prompt that says grub rescue and takes no input. 

This is kind of upsetting, because the Ubuntu download page mentioned nothing about any bugs that could end so disastrously for Linux noobs like me. It's not like I did anything irresponsible during the installation process. I just followed instructions. To the letter, in fact... 

Actually, now I'm quite upset. 

Can anybody help?

Thank you.

I'm thinking this is not very good for evangelizing Ubuntu to regular Joes like me.

I couldn't agree more. I emailed the ubuntu release manager and requested exactly that - a warning - or pulling the bad update. Or pulling wubi. I didn't get a response. So - you can complain here, but that does nothing. Try writing to canonical.  

Anyway... about your problem. Your computer is normal - just the bootloader is broken. So if you have XP, put in your XP disc or a windows repair disc, and then boot from it and go to a repair command prompt and enter: fixmbr. ([http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true))

That's the fix.
If you have an ubuntu cd you can also use lilo.
The wubi megathread details this (you're looking at Problem #1) [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by oldfred on 2010-12-28
Wubi runs inside the NTFS windows partition. So it relies on windows to boot.

Did you follow the links in post #2 to the wubi mega thread on solutions.

You need to install either the windows boot loader from a windows repair disk or you can install from a Ubuntu or any other Linux liveCD a part of Lilo that goes into the MBR. That part of lilo works just like the windows boot loader in that it just jumps to the active partition (boot flag).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by molave on 2010-12-28
Thanks for the reply Bcbc. Really helps calm down someone in my shoes, who's been hitting the panic button for several hours now.

I guess it wouldn't be rocket science to figure out the solutions you suggested. It's just that all those unfamiliar terms made matters much worse. 

And like I said, I've tried a lot of open source betas in my time---Mozilla, Source Forge, PHP, MySQL, Drupal, SETI@home, whatever---but Ubuntu has the dubious honor of shooting everything on my system to sh** so fast, it practically made my heart stop. 

Now to try solutions 1 *and* 2 and hope *something* takes. 

Btw, I really might give Canonical a piece of my mind. I gotta find out first, tho, if they actually listen to their community. 

Cheers!

---

### Post by molave on 2010-12-28
> **oldfred said:**
> Wubi runs inside the NTFS windows partition. So it relies on windows to boot.

Did you follow the links in post #2 to the wubi mega thread on solutions.

You need to install either the windows boot loader from a windows repair disk or you can install from a Ubuntu or any other Linux liveCD a part of Lilo that goes into the MBR. That part of lilo works just like the windows boot loader in that it just jumps to the active partition (boot flag).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)


Will do that oldfred, thanks much. Rolling up my sleeves now... Oh wait, heavy sigh first: *heavy sigh*

:)

---

