---
title: "Ubuntu Installer Problems"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Whisp3r on 2010-12-10
Argh. I'm about ready to kill Ubuntu. 

I had Ubuntu 9.04, loved it to death. Since support ended, I decided to go ahead and upgrade to 10.04. I have two drives, a 1TB and 2TB drive. The 2TB drive is new and has all my files backed up to it. 

The 1TB drive is my primary OS drive, and has a 500GB NTFS partition with Windows XP and a 500GB partition where my Ubuntu resides. I'm not a fan of Windows, but I need to use it for work once and a while. 

I backed everything up, boot off the Windows XP disk, ran FIXMBR and FIXBOOT and was able to log into Windows no problem. Fired up GParted, resized the whole 1TB to NTFS. Rebooted to windows, no problem. And thus began the problems...

I attempted to install Ubuntu 10.04 as a dual boot next to Windows. Most of the installation goes through and then I receive a Error Code 5 and it crashes. 

I rebooted to GParted and found my entire 1TB drive is now listed as "unallocated." However, when I boot off the 1TB drive, the Windows partition boots fine. GParted, nor the Ubuntu Installer, see the Windows partition. GParted sees the entire drive as unallocated space, yet the Windows section boots up fine. 

I have already tried fixboot and fixmbring again. How do I get my HD to show the NTFS space again?

---

### Post by Hippytaff on 2010-12-10
For info so the people who know more than me can help you out, it would be useful is you could boot from Livecd. Go to this link [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Download the script and run it. Then post the RESULTS.TXT here (in code tags #)
 
It will show what is what an what is where etc. :-)

---

### Post by Whisp3r on 2010-12-10
To further complicate things...

I did go into GParted command line, and ran fdisk on /dev/sda, and it shows /dev/sda1 as a NTFS along with the failed installation from the Ubuntu Installer (Ext4, swap, and linux). So GPArted's GUI shows nothing, but fdisk does. 

Help! :(

---

### Post by Hippytaff on 2010-12-10
The best way to get help is to post the Results.txt of the script I gave the link for. Then people can see exactly how everything is regarding partitions, mbr, grub, fstab etc etc

---

### Post by amjjawad on 2010-12-10
> **hippytaff said:**
> the best way to get help is to post the results.txt of the script i gave the link for. Then people can see exactly how everything is regarding partitions, mbr, grub, fstab etc etc


+1

---

### Post by Whisp3r on 2010-12-10
Well, I downloaded the script onto my LiveCD desktop and tried to run it. It tells me Permission Denied. I tried to run it sudo, and it says "command not found." Next suggestion? :(

*sigh* 

I downloaded the new GParted CD and ran it, and it can see my NTFS partition now. Yet, when I run the Ubuntu installer, it doesn't see the NTFS partition and just wants to wipe the whole drive.

---

### Post by Rubi1200 on 2010-12-10
The other thing to look at is this:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

However, as both Hippytaff and amjjawad have requested, please post the results of the script as it will really help us troubleshoot the problem.

Thanks.

---

### Post by Rubi1200 on 2010-12-10
> **Whisp3r said:**
> Well, I downloaded the script onto my LiveCD desktop and tried to run it. It tells me Permission Denied. I tried to run it sudo, and it says "command not found." 

*sigh* 

I downloaded the new GParted CD and ran it, and it can see my NTFS partition now. Yet, when I run the Ubuntu installer, it doesn't see the NTFS partition and just wants to wipe the whole drive.
If the script is on the Desktop try running it with the alternate command given in the instructions.

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> Well, I downloaded the script onto my LiveCD desktop and tried to run it. It tells me Permission Denied. I tried to run it sudo, and it says "command not found." 

*sigh* 

I downloaded the new GParted CD and ran it, and it can see my NTFS partition now. Yet, when I run the Ubuntu installer, it doesn't see the NTFS partition and just wants to wipe the whole drive.

1) Have you checked [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")? 
2) You need to run that script while you're booting from the LiveCD/USB. Instructions are included here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Whisp3r on 2010-12-10
Yes, I verified the MD5SUM on both my 10.04 and 10.10 disks. I also have tried reburning both CDs at the lowest speeds possible. 

Here are the results of my boot_info. I did remove the 2TB drive for safety's sake.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       1953523640 sectors, but according to the info from 
                       fdisk, it has 1953536066 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,536,129 1,953,536,067   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA9C46379C45FDF7                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Thank you for all your help thus far.

---

### Post by Hippytaff on 2010-12-10
I can't see ubuntu here, is it a Wubi install or a real partition? (ie did you install ubuntu with an exe file?)

---

### Post by Whisp3r on 2010-12-10
There is no Ubuntu there. I eliminated the bad Ubuntu install with GParted and resized the whole disk NTFS. 

All that is on the drive is a NTFS partition (the whole drive). 

The problem is Ubuntu's installer does not see the NTFS partition and thus wants to write onto the whole disk.

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> Yes, I verified the MD5SUM on both my 10.04 and 10.10 disks. I also have tried reburning both CDs at the lowest speeds possible. 

Here are the results of my boot_info. I did remove the 2TB drive for safety's sake.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       1953523640 sectors, but according to the info from 
                       fdisk, it has 1953536066 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,536,129 1,953,536,067   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA9C46379C45FDF7                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```Thank you for all your help thus far.

sda which is HDD1 (1TB) has ONLY ONE partition which is sda1 and it's NTFS.

In order to install Ubuntu, you need to create at least 3 more partitions:
Root
Home (recommended but not a must)
Swap

You have only one Primary Partition (sda1). You need to resize/shrink it.

Are we ok so far?

---

### Post by Whisp3r on 2010-12-10
Yes yes, I get that. 

The problem is the Ubuntu installer does not see the NTFS partition, so when I go to install Ubuntu for dual boot, my options are:

Write to the whole disk
Write my partitions manually, but I still don't see sda1.

---

### Post by amjjawad on 2010-12-10
[This]("http://www.facebook.com/album.php?aid=40578&id=154937727857763") might help you ;)

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> The problem is the Ubuntu installer does not see the NTFS partition, so when I go to install Ubuntu for dual boot, my options are:


I strongly recommend to use GParted first to prepare your HDD, then you could carry on with installation.

[U][B]Edit:
[/B][/U]Please note that, if you're going to shrink your Windows Partition (which is the only way to carry on with this as long as you don't want to use sdb - HDD2), you MUST:
1- Backup Windows File
2- Clear the temp, cookies and the unused files (CCleaner)
3- Use Defragment
4- Shrink it with GParted (LiveUSB is faster than LiveCD).

---

### Post by Whisp3r on 2010-12-10
I understand I need to use GParted. fdisk sees the sda1 NTFS partition.

GParted does not. See the attached screen shot from my LiveCD. If I reboot right now, the NTFS partition with fdisk sees will run and boot right into Windows. 

I can't format the drive for dual boot, if GParted doesn't see the partition to begin with... I'm guessing the NTFS partition is missing a flag to make it visible or such?

Results of:
```
ubuntu@ubuntu:~/Downloads$ sudo fdisk -ul /dev/sda1

Disk /dev/sda1: 1000.2 GB, 1000204853760 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525105 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4      2692939776  2692991410       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> I understand I need to use GParted. fdisk sees the sda1 NTFS partition.

GParted does not. See the attached screen shot. 

I can't format the drive for dual boot, if GParted doesn't see the partition to begin with...

If my memory still functioning correctly, I guess GParted can't read your Partition Table. I've read about that a month ago or so. Can't really remember how the other guy managed to fix it.

I'm waiting for my other friends to share their opinions :)

---

### Post by Rubi1200 on 2010-12-10
Are you able to boot Windows normally from that drive, sda?

Please take a look at the link I provided in a previous post:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

The other problem that i have heard about is BIOS not being able to recognize newer, larger drives. It might be worth checking that angle.

This is also perhaps part of the problem:
> Boot sector info:  According to the info in the boot sector, sda1 has 
                       1953523640 sectors, but according to the info from 
                       fdisk, it has 1953536066 sectors.

---

### Post by kansasnoob on 2010-12-10
I notice in your Gparted screenshot there is a yellow triangular warning emplem. If you highlight that space and then just right click and select Information what does it say?

**Note: don't make any changes just yet!**

It might also be helpful to see the output of:

```
sudo parted /dev/sda print
```

I'm also curious what disc you used here:

> I backed everything up, boot off the Windows XP disk, ran FIXMBR and FIXBOOT and was able to log into Windows no problem. **[COLOR="Red"]Fired up GParted, resized the whole 1TB to NTFS.[/COLOR]** Rebooted to windows, no problem.

I've had some problems with newer versions of Gparted so you may need to try an older disc. I have a stand-alone Gparted disc, version 0.4.6-1.iso, that just seems to work when other versions don't.

---

### Post by Whisp3r on 2010-12-10
Yes, if I boot the computer straight off the hard drive, it goes straight into windows with no problems.

Both GParted info and the parted command read the same:

"Can't have partition outside of the disk!"

When I run fdisk and ask it to "verify the partition table", this is my response:

> 
Partition 1 does not end on a cylinder boundary.
Partition 2 does not end on a cylinder boundary.
Partition 3 does not end on a cylinder boundary.
Warning: partition 2 overlaps partition 3.
Remaining 251534693 unallocated 512 byte sectors.


Since it should only have 1 partition.. I'm guessing something is majorly fubared with my table?

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> "Can't have partition outside of the disk!"

I'm searching in google and I found some related topics to the same issue.

From what I read so far, I guess your Partition Table is messed up. However, I'm not sure how to fix that without formatting the whole drive.

Edit:
I'm reading this: [http://ubuntuforums.org/archive/index.php/t-1413012.html](http://ubuntuforums.org/archive/index.php/t-1413012.html)

---

### Post by kansasnoob on 2010-12-10
OK I've experienced that also and following this guide helped me:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

However, I'm not proficient enough with that procedure to be of much help.

If in doubt be patient and someone with more experience will almost surely help you. A quick Google search provided another example:

[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

Do you understand that?

---

### Post by Whisp3r on 2010-12-10
Yes, I understand. I went ahead and ran TestDisk on the drive to see if that would find any problems. During the partition search, it located numerous deleted partitions. I went ahead and re-wrote the partition table to include only the NTFS, and GParted can now see Ubuntu. I have other issues now, but that's for another thread. Thanks for all your help. :)

---

### Post by amjjawad on 2010-12-10
> **Whisp3r said:**
> Yes, I understand. I went ahead and ran TestDisk on the drive to see if that would find any problems. During the partition search, it located numerous deleted partitions. I went ahead and re-wrote the partition table to include only the NTFS, and GParted can now see Ubuntu. I have other issues now, but that's for another thread. Thanks for all your help. :)

Glad you managed to fix it :)

You could use this thread if it's related to installation.

Good luck :)

---

### Post by Spyderkid on 2010-12-10
Go into CMOS if you have it on your computer nd have a look at the hard drives see if there mounted nd things like that

---

