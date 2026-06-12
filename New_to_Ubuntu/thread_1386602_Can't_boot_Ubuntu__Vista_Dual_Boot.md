---
title: "Can't boot Ubuntu / Vista Dual Boot"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by KronosQ on 2010-01-20
Hello,
Firstly, I'd like to say I'm new to Ubuntu/Linux, so I probably won't be able to understand too much techno-babble ;)

Okay, so.
I just installed Ubuntu 9.10, using a CD installer, onto my laptop which already had Vista on it. Installation seemed to go fine, it booted me into Ubuntu after that. But then when I restarted my computer it didn't give me a choice on which OS to boot into (automatically booted me into Vista).

I solved this by using EasyBCD 1.7.2 ([using this guide, following the "Vista before Linux" instructions]("http://neosmart.net/wiki/display/EBCD/Linux")). 
When restarting, I now get an option of booting into Vista or Linux. The Vista option boots me into Vista perfectly. 
The Linux option goes through a bunch of text, then stops at a point saying,

"GRUB4DOS 0.4.3 2007-06-14, Memory: 614K/1917M, CodeEnd: 0x3EF2C",
then some other text about pressing tab for options and stuff.
It now allows me to input text, and pressing tab brings up a list of commands.

It's here that I have no idea what to do, so any help would be appreciated!

Thanks.

---

### Post by presence1960 on 2010-01-20
I would get rid of Easy BCD there is no need for it. You can put GRUB on the MBR of your hard disk and boot both Vista & Ubuntu. First though I need some more info from you. I need to see your setup & boot process so I can give precise, detailed instructions to get your dual boot up & running.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by KronosQ on 2010-01-20
Here's the RESULTS.txt.
Thanks for helping.

```


============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x428a62ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   209,256,996   206,182,949   7 HPFS/NTFS
/dev/sda3         379,056,128   390,715,391    11,659,264  17 Hidden HPFS/NTFS
/dev/sda4         209,262,690   379,053,674   169,790,985   5 Extended
/dev/sda5         209,262,753   372,049,334   162,786,582  83 Linux
/dev/sda6         372,049,398   379,053,674     7,004,277  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54A2839AA2837F6C" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="CCF28A13F28A01C6" LABEL="S3A6456D002" TYPE="ntfs" 
/dev/sda3: UUID="941CA7E01CA7BC1C" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="8a4d0325-db21-4599-a48f-1c5e9e7d9dd5" TYPE="ext4" 
/dev/sda6: UUID="678bd81f-683c-4cdd-9b80-a6d86b75ebd2" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
find --set-root --ignore-floppies /boot/grub/menu.lst 
configfile /boot/grub/menu.lst 
 
# All your boot are belong to NeoSmart!
=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8a4d0325-db21-4599-a48f-1c5e9e7d9dd5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=678bd81f-683c-4cdd-9b80-a6d86b75ebd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by presence1960 on 2010-01-20
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
[COLOR="Red"]sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab[/COLOR]
sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

```

Your ubuntu install failed- see sda5 above- it is not a complete install. Uninstall Easy BCD first and let the ubuntu installer put GRUB on the MBR. Reinstall using the Live CD. When you get to the partitioner window choose manual option (see pic below). Then highlight the sda5 partition and click change. Choose ext3 or ext4 on "use as", tick the format box and at mount point use the drop down box to choose /

When you get to the Ready to install window (see 2nd pic below) Click the advanced button and choose /dev/sda. Continue with the install.

proceed with the install.

---

### Post by KronosQ on 2010-01-20
I did what you said to do, but I don't think it did much.
I uninstalled EasyBCD, but when starting my laptop up, it went through the same process as it did with EasyBCD and before I reinstalled Ubuntu.

I ran the boot info check again, and it looks like the same as before.
And it sounded like my laptop had a hard time going into the "try ubuntu without any changes" option tihs time.
Did I do something wrong, or is there just something special wrong with my laptop?

```


============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x428a62ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   209,256,996   206,182,949   7 HPFS/NTFS
/dev/sda3         379,056,128   390,715,391    11,659,264  17 Hidden HPFS/NTFS
/dev/sda4         209,262,690   379,053,674   169,790,985   5 Extended
/dev/sda5         209,262,753   372,049,334   162,786,582  83 Linux
/dev/sda6         372,049,398   379,053,674     7,004,277  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54A2839AA2837F6C" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="CCF28A13F28A01C6" LABEL="S3A6456D002" TYPE="ntfs" 
/dev/sda3: UUID="941CA7E01CA7BC1C" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="a58dbd11-80c5-44e4-8846-5055377cb2b8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="678bd81f-683c-4cdd-9b80-a6d86b75ebd2" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
find --set-root --ignore-floppies /boot/grub/menu.lst 
configfile /boot/grub/menu.lst 
 
# All your boot are belong to NeoSmart!
=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a58dbd11-80c5-44e4-8846-5055377cb2b8 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=678bd81f-683c-4cdd-9b80-a6d86b75ebd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

I kind of want to fstab my laptop :|

---

### Post by _H3MLOCK on 2010-01-21
Does the installation finish successfully?

---

### Post by presence1960 on 2010-01-21
your install is not complete again. Here is what my Linux looks like from my boot info script output:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
[COLOR="Red"]
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab
[/COLOR]
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:  
``` 

The red sda6 is 9.10, sda7 is Ubuntu 10.04 alpha2, sda8 is sabayon linux. Note the differences in the info for each partition compared to yours.

I think your disk may be bad. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to making the CD?

If that checks out did you burn the CD at a slow speed? 4x-8x is perfect.

Boot the Live CD and choose "check disk for defects and see what that says.

Your ubuntu is missing directories/files and the bootloader is not installed. Either your CD is no good or you are doing something wrong. I think it is the disk.

You also need to get rid of this file from sda2 your windows partition: /NST/menu.lst

---

### Post by KronosQ on 2010-01-21
I got the CD from a friend who has Windows 7 and Ubuntu dual-booted on his laptop, and working just fine. 

I'll check the CD for defects, and if that doesn't give any clues then I'll make my own CD.

---

### Post by KronosQ on 2010-01-21
So, the integrity check tells me there are errors in 7 files :-s

I'll try again when I get a new CD. So I may be back here next week sometime, but hopefully not.

Thanks for all your help, it's very much appreciated.

---

### Post by gnometorule on 2010-01-21
...or use a cheat, instead of geeking out before you even started :) :

I had terrible problems getting Ubuntu onto my laptop; in part because it is very old and so some native device driver support probably lacks. This killed my attempt to install Feisty Fawn as I absolutely couldn't get my ethernet and wireless running. Using an (error checked) Ubuntu boot CD crashed early in the process. Nothing seem to work for me. Until I discovered: 

[http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)

As the installation works exactly as installing a program in windows, from windows, all my really outdated drivers were simply copied over from windows (and I assume wrapped with some form of ndiswrapper functionality that wubi will have). Worked like a charm. Yes, this is version 9.04; but just, during your first update of the new system, choose to upgrade to version 9.10, which again worked like a charm. You'll get an option to dual boot at start. 

I have no idea why ***WUBI*** isn't marketed more. I am new; and maybe I am missing any significant downsides. However, if I may fathom a guess, it might be geek-pride not wanting to give in to the evil empire - in the sense that installing Ubuntu using Windows tools goes so much smoother (not to speak of uninstalling via Add/Remove Programs under Windows simply). If that's it, I'd really urge the community to reconsider as it doesn't serve those interested in Ubuntu well.

---

### Post by presence1960 on 2010-01-21
> **gnometorule said:**
> ...or use a cheat, instead of geeking out before you even started :) :

I had terrible problems getting Ubuntu onto my laptop; in part because it is very old and so some native device driver support probably lacks. This killed my attempt to install Feisty Fawn as I absolutely couldn't get my ethernet and wireless running. Using an (error checked) Ubuntu boot CD crashed early in the process. Nothing seem to work for me. Until I discovered: 

[http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)

As the installation works exactly as installing a program in windows, from windows, all my really outdated drivers were simply copied over from windows (and I assume wrapped with some form of ndiswrapper functionality that wubi will have). Worked like a charm. Yes, this is version 9.04; but just, during your first update of the new system, choose to upgrade to version 9.10, which again worked like a charm. You'll get an option to dual boot at start. 

I have no idea why ***WUBI*** isn't marketed more. I am new; and maybe I am missing any significant downsides. However, if I may fathom a guess, it might be geek-pride not wanting to give in to the evil empire - in the sense that installing Ubuntu using Windows tools goes so much smoother (not to speak of uninstalling via Add/Remove Programs under Windows simply). If that's it, I'd really urge the community to reconsider as it doesn't serve those interested in Ubuntu well.
Wubi is not intended to be a permanent installation but rather a test drive for those unwilling to partition their hard disk(s) until they are sure they like Ubuntu. Here is a [link]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/") to an interview with the developer of wubi. Note his answer to the second question. Another downfall is since most of the community members do not use wubi it is harder to get support for problems as a lot of us only have a limited understanding/experience with wubi.

---

### Post by presence1960 on 2010-01-21
> **KronosQ said:**
> So, the integrity check tells me there are errors in 7 files :-s

I'll try again when I get a new CD. So I may be back here next week sometime, but hopefully not.

Thanks for all your help, it's very much appreciated.

Here are some tips for burning a good Live CD from the iso.

1. After downloading [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso. The hashes must match exactly or the iso is corrupted. If possible download from a torrent.

2. Burn the iso as an image to CD at 4x-8x speed. Anything faster increases the likelihood of error(s). If your software will not allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder for windows.

3. When you boot the CD for the first time always select "check disk for errors". If there is even one error the disk cannot be expected to function properly. Even if it does install something will be incorrect with your install.

---

