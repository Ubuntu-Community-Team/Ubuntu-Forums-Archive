---
title: "dual boot problem"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by A3z on 2010-01-07
When booting to Ubuntu from the OS list in XP, I get this message:

Try (hd0,0): FAT16: No WUBILDR
Try (hd0,1): NTFS5:2
Try (hd0,2): FAT32: No WUBILDR
Try (hd0,2): invalid or null
Error while reading MBR of drive hd(0,1)
Try (fd0): invalid or null
Error: Cannot find GBLDR in all devices.


I've got windows xp on my internal hdd 100gig and i got ubuntu on my external 320 gig. I'm guessing hd0,0 is xp, my large partition on external is hd0,1, and ubuntu is hd0,2.

I hope someone can help me because I'm fairly new to this.

---

### Post by kansasnoob on 2010-01-07
Well that's showing some Wubi stuff but you say you have Ubuntu on a separate drive. To give us a much clearer picture post the results of The Boot Info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by A3z on 2010-01-07
This is what I got:


============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   145,950,524   145,838,070   7 HPFS/NTFS
/dev/sda3         145,950,525   156,232,124    10,281,600  db CP/M / CTOS / ...


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00095ebe

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   603,562,049   603,561,987   6 FAT16
/dev/sdc2         603,562,050   625,137,344    21,575,295   5 Extended
/dev/sdc5         603,562,113   624,125,249    20,563,137  83 Linux
/dev/sdc6         624,125,313   625,137,344     1,012,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0A1F" TYPE="vfat" 
sda2: UUID="889841F49841E174" TYPE="ntfs" 
sda3: LABEL="DellRestore" TYPE="vfat" 
sdc1: UUID="C47C95F37C95E08A" LABEL="New Volume" TYPE="ntfs" 
sdc5: UUID="419bd849-5ae1-4b9c-9ad8-257295a32f6b" TYPE="ext4" 
sdc6: UUID="d9440497-9ddf-4ed9-b497-29eabfbfb81b" TYPE="swap" 

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
/dev/sdc5 on /media/419bd849-5ae1-4b9c-9ad8-257295a32f6b type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /TUTag=ZYGDS9 /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=ZYGDS9-BAK 
C:\wubildr.mbr = "Ubuntu" 

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=419bd849-5ae1-4b9c-9ad8-257295a32f6b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=d9440497-9ddf-4ed9-b497-29eabfbfb81b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 309.0GB: boot/initrd.img-2.6.31-14-generic
 309.0GB: boot/vmlinuz-2.6.31-14-generic
 309.0GB: initrd.img
 309.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by kansasnoob on 2010-01-08
Well, what I can see here:

> => No boot loader is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdc

That of course will keep you from booting anything.

This is also of slight concern:

> =======Devices which don't seem to have a corresponding hard drive==============

sdb

But I'd consider that a minor issue, just curious if a drive has been removed or something.

Anyway I can see that you have Win XP on sda2 (it also appears to contain a Wubi install but I'm not concerned with that now):

> sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

You also have Ubuntu on sdc5 (which I think you said is an external drive):

> sdc5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.10
Boot files/dirs: /etc/fstab

Anyway I'd first suggest getting the Windows mbr back on sda. That can be accomplished using your Windows restore/installation discs like this:

[http://www.ehow.com/how_5095077_recover-mbr-windows-xp.html](http://www.ehow.com/how_5095077_recover-mbr-windows-xp.html)

Or I actually prefer using an Ubuntu Live CD and in terminal **(Please copy-n-paste all commands)**:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Note: If you're using a Live USB or an installed version of Ubuntu I also like to remove lilo so it doesn't cause boot problems later on:

```
sudo apt-get remove lilo
```

**Note: I should know how we're working on this, that is are you using a Live CD, live USB?**

Anyway that should get Windows booting, we don't care if the Wubi install works right now or not.

Next we need to get grub working in Ubuntu, I prefer we try grub2 at first. Just so you have some idea what we're doing you can look here if you like:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

What you need to do is boot the Ubuntu Live CD and from Terminal run these commands to mount and chroot the Ubuntu OS and fix things:

```
sudo mount /dev/sdc5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
df -H
```

Then the first thing we need to find out is if package management is working right so lets try to update the package list (you'll notice that we don't need sudo while chroot):

```
apt-get update
```

If that appears to spit any errors at all I should know before proceeding, in fact lets check something:

```
apt-cache search grub
```

That should spit out a fairly long list like this:

> lance@lance-desktop:~$ sudo apt-cache search grub
gfxboot - bootlogo creator for gfxboot compliant boot loaders
grub - GRand Unified Bootloader
grub-doc - Documentation for GRand Unified Bootloader
libaal-dev - Reiser4's application abstraction library
libreiser4-dev - Reiser4's filesystem access and manipulation library
memtest86+ - thorough real-mode memory tester
bootcd - run your system from cd without need for disks
brdesktop-artwork-grub - Brazilian Debian Pure Blend - grub theme
dfsbuild - Build Debian From Scratch CD/DVD images
ggz-grubby - GGZ Gaming Zone: chat bot with the ability to play games
ggz-kde-client - GGZ Gaming Zone: advanced core client for KDE
gptsync - GPT and MBR partition tables synchronisation tool
grub-choose-default - Control Grub Default through a GUI
grub-disk - GRUB bootable disk image (dummy package)
grub-invaders - multiboot compliant kernel game
grub-splashimages - a collection of great GRUB splashimages
grub2-splashimages - a collection of great GRUB2 splashimages
grubutil-win32 - GRUB win32 boot images
libtext-markdown-perl - Markdown and MultiMarkdown markup languages library
libtext-typography-perl - markup ASCII text with correct typography for HTML
octave-outliers - outliers detection function for Octave
python-markdown - text-to-HTML conversion library/tool
sa-exim - Use spamAssassin at SMTP time with the Exim v4 MTA
startupmanager - Grub and Splash screen configuration
sugarplum - an automated and intelligent spam trap/cache-poisoner
yaird - Yet Another mkInitRD
**grub-common** - GRand Unified Bootloader, version 2 (common files)
**grub-pc** - GRand Unified Bootloader, version 2 (PC/BIOS version)
grub-coreboot - GRand Unified Bootloader, version 2 (Coreboot version)
grub-efi - GRand Unified Bootloader, version 2 (dummy package)
grub-efi-amd64 - GRand Unified Bootloader, version 2 (EFI-AMD64 version)
grub-efi-ia32 - GRand Unified Bootloader, version 2 (EFI-IA32 version)
grub-emu - GRand Unified Bootloader, version 2 (emulated version)
grub-firmware-qemu - GRUB firmware image for QEMU
grub-ieee1275 - GRand Unified Bootloader, version 2 (Open Firmware version)
grub-linuxbios - GRand Unified Bootloader, version 2 (dummy package)
grub-rescue-pc - GRUB bootable rescue images, version 2 (PC/BIOS version)
grub2 - GRand Unified Bootloader, version 2 (dummy package)


I highlighted the two packages we're concerned with. If you don't see those then we'll be stuck for the moment so I'll need to see the output of:

```
cat /etc/apt/sources.list
```

However if you did see those packages just proceed:

```
mv /boot/grub /boot/grub_old
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub grub-common
```

```
apt-get install grub-pc
```

```
grub-install /dev/sdc
```

```
update-grub
```

Wait until it says "done", you'll notice it doesn't find Windows, that's OK for now.

If all appeared to succeed then we'll exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Now, if your system BIOS is set correctly (that is to try and boot first from CD, then USB, then Hard Drive) you should be able to boot Ubuntu with the external drive plugged in, and Windows if the external is not plugged in.

The first time you boot into Ubuntu on the external drive you'll need to go to terminal and run:

```
sudo update-grub
```

Wait until it says done and you should see that it finds Windows.

Note: If you need more help regarding the BIOS settings I'll be around.

---

### Post by A3z on 2010-01-08
I got some error messages, and some of the commands didn't work.


root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-pc has no installation candidate


and

grub-install: command not found


So I stopped from there to see if you can help ;)


It won't let me install grub-pc

---

### Post by kansasnoob on 2010-01-08
What did it show when you ran:

```
apt-get update
```

and:

```
apt-cache search grub
```

---

### Post by A3z on 2010-01-08
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Reading package lists... Done



and 




root@ubuntu:/# apt-cache search grub
memtest86+ - thorough real-mode memory tester

---

### Post by kansasnoob on 2010-01-08
I need to see the output of:

```
cat /etc/apt/sources.list
```

That's why I said:

> 
Code:

apt-cache search grub

That should spit out a fairly long list like this:

Quote:
lance@lance-desktop:~$ sudo apt-cache search grub
gfxboot - bootlogo creator for gfxboot compliant boot loaders
grub - GRand Unified Bootloader
grub-doc - Documentation for GRand Unified Bootloader
libaal-dev - Reiser4's application abstraction library
libreiser4-dev - Reiser4's filesystem access and manipulation library
memtest86+ - thorough real-mode memory tester
bootcd - run your system from cd without need for disks
brdesktop-artwork-grub - Brazilian Debian Pure Blend - grub theme
dfsbuild - Build Debian From Scratch CD/DVD images
ggz-grubby - GGZ Gaming Zone: chat bot with the ability to play games
ggz-kde-client - GGZ Gaming Zone: advanced core client for KDE
gptsync - GPT and MBR partition tables synchronisation tool
grub-choose-default - Control Grub Default through a GUI
grub-disk - GRUB bootable disk image (dummy package)
grub-invaders - multiboot compliant kernel game
grub-splashimages - a collection of great GRUB splashimages
grub2-splashimages - a collection of great GRUB2 splashimages
grubutil-win32 - GRUB win32 boot images
libtext-markdown-perl - Markdown and MultiMarkdown markup languages library
libtext-typography-perl - markup ASCII text with correct typography for HTML
octave-outliers - outliers detection function for Octave
python-markdown - text-to-HTML conversion library/tool
sa-exim - Use spamAssassin at SMTP time with the Exim v4 MTA
startupmanager - Grub and Splash screen configuration
sugarplum - an automated and intelligent spam trap/cache-poisoner
yaird - Yet Another mkInitRD
grub-common - GRand Unified Bootloader, version 2 (common files)
grub-pc - GRand Unified Bootloader, version 2 (PC/BIOS version)
grub-coreboot - GRand Unified Bootloader, version 2 (Coreboot version)
grub-efi - GRand Unified Bootloader, version 2 (dummy package)
grub-efi-amd64 - GRand Unified Bootloader, version 2 (EFI-AMD64 version)
grub-efi-ia32 - GRand Unified Bootloader, version 2 (EFI-IA32 version)
grub-emu - GRand Unified Bootloader, version 2 (emulated version)
grub-firmware-qemu - GRUB firmware image for QEMU
grub-ieee1275 - GRand Unified Bootloader, version 2 (Open Firmware version)
grub-linuxbios - GRand Unified Bootloader, version 2 (dummy package)
grub-rescue-pc - GRUB bootable rescue images, version 2 (PC/BIOS version)
grub2 - GRand Unified Bootloader, version 2 (dummy package)
I highlighted the two packages we're concerned with. If you don't see those then we'll be stuck for the moment so I'll need to see the output of:

Code:

cat /etc/apt/sources.list



---

### Post by A3z on 2010-01-08
I did have what you had highlighted. 

but here you go:

root@ubuntu:/# cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted

---

### Post by kansasnoob on 2010-01-08
Would you also post the output of:

```
df -H
```

Oh, you are working from a live CD right?

---

### Post by A3z on 2010-01-08
Yes.

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdc5               11G   2.2G   7.7G  23% /mnt

---

### Post by kansasnoob on 2010-01-08
OK I wanted to be sure we were in the right place. We are.

That sources.list is totally hosed for some reason, that's probably why you had no grub or grub2 files installed.

Have you ever used the text editor Nano?

Also are you in the USA?

I need to make you a correct sources.list so you can get the proper packages and I need to know what server to use.

---

### Post by A3z on 2010-01-08
Never used Nano and I am in the USA.

---

### Post by kansasnoob on 2010-01-08
Well you're going to learn how to use nano!

Give me a few minutes. I have faith in you.

---

### Post by A3z on 2010-01-08
Haha okay :)

---

### Post by kansasnoob on 2010-01-08
OK here's the sources.list I want you to use:

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe


Here's another copy in code tags:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
#deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe

```

You can use whichever one is easier for you to work with, I assume you know how to copy-n-paste real well?

Anyway nano is kind of different but we can't really use Gedit in a chroot so you'll have to run:

```
nano /etc/apt/sources.list
```

[ATTACH]142946[/ATTACH]

Looks scary huh? It's not really, at least you can paste into it.

Anyway in this case you just need to press the arrow down key to get to the bottom of the list and then use the Backspace key to wipe out that little bit of a sources.list, then come back here and copy-n-paste that new list in there.

Then to save it press and hold Ctrl and while holding Ctrl press the x key, then release both keys.

Then at the bottom you'll see it say "Save modified buffer?. You need to press y for yes, then it will say at the bottom "File name to write", so just press Enter.

Then just to double check and see if it looks right run the command:

```
cat /etc/apt/sources.list
```

If it looks good try:

```
apt-get update
```

Unless it spits a bunch of errors resume with:

```
apt-get install grub-pc
```

```
grub-install /dev/sdc
```

```
update-grub
```

And the rest in post #4.

I'll be right here.

---

### Post by A3z on 2010-01-08
It says permission denied when I save it.

---

### Post by kansasnoob on 2010-01-08
> **A3z said:**
> It says permission denied when I save it.

You didn't exit the chroot did you?

You still need to be root as indicated by the # prompt in terminal.

---

### Post by A3z on 2010-01-08
How do I get back to root?

---

### Post by kansasnoob on 2010-01-08
Well in order that I can help you better (because I can't see at your end) please lets start over by:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then go back to post #4 and begin with (note: when you ran the last command if it spit any errors this might fail, but I need to see):

```
sudo mount /dev/sdc5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

And everything after it (note: I added df -H), and this time I want to see the full output from terminal like this:

> lance@lance-desktop:~$ sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for lance: 
root@lance-desktop:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
dpkg-divert: rename involves overwriting `/sbin/initctl.distrib' with
  different file `/sbin/initctl', not allowed
root@lance-desktop:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@lance-desktop:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              8.8G   3.3G   5.1G  40% /
none                   8.8G   3.3G   5.1G  40% /sys
none                   1.1G   295k   1.1G   1% /dev
none                   1.1G   295k   1.1G   1% /dev/shm
none                   8.8G   3.3G   5.1G  40% /var/run
none                   8.8G   3.3G   5.1G  40% /var/lock
none                   8.8G   3.3G   5.1G  40% /lib/init/rw
none                   8.8G   3.3G   5.1G  40% /var/lib/ureadahead/debugfs
root@lance-desktop:/# apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_US               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Translation-en_US   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_US                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,392kB]    
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [7,947B]          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [658kB]                  
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,269B]         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,442kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,110kB]            
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [197kB]           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [123kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages              
Fetched 11.0MB in 34s (319kB/s)                                                
Reading package lists... Done
root@lance-desktop:/# 


Of course you probably still won't get a long output from running "apt-get update" like that so then you'll have to nano the sources.list as described above, but I really need to see the full output of terminal to see what's up.

I know you can't just copy-n-paste the results of what's going on in nano but I just tried that here to be sure I made no typos and it's working for me.

---

### Post by A3z on 2010-01-08
Okay this is what im getting from the first command:

ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
umount: /mnt/dev/pts: not mounted

then the second:

ubuntu@ubuntu:~$ sudo mount /dev/sdc5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: /dev/sdc5 already mounted or /mnt busy
mount: according to mtab, /dev/sdc5 is already mounted on /mnt

says its not mounted but then says it is? or it says its busy.

---

### Post by kansasnoob on 2010-01-08
OK I think I included this link earlier:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Like it says there, "the commands below are just a string of commands connected by "space&&space" but if one part of the string fails it stops the whole process so if you encounter any failure message look at the list of individual commands below!"

> MOUNT:
sudo mount /dev/sdc5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

REMEMBER: exit

UNMOUNT:
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

Actually in that case what I do is drop just the first part of the mount script like this:

```
sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

If that still fails then I drop one more command from the front of the string like:

```
sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

etc, etc.

---

### Post by A3z on 2010-01-08
root@ubuntu:/# apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [65.9kB]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [3,405B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release [44.1kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [1,353kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [7,971B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [190kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [640kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [3,270B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [5,133kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [129kB]       
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [39.7kB]       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [77.9kB]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [18.8kB]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages [45.0kB]     
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages [14B]  
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources [12.4kB]      
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources [14B]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages [19.4kB] 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources [3,367B]  
Fetched 10.6MB in 11s (948kB/s)                                                
Reading package lists... Done


Okay I think you wanted that right?

---

### Post by kansasnoob on 2010-01-08
Something I should say is, since we've run into trouble, there is a certain skill level required for a lot of this stuff. It's taken me two years of playing to learn what I have and I still have tons of stuff to learn.

Like I realize you didn't know what a normal output from "apt-get update" should look like, and something failed in the install procedure or you would have had a proper sources.list.

Even if we manage to succeed at this we may find that other files/directories are hosed, so given your skill level and the odds at success you may be better off considering a reinstall choosing "Manual (advanced)" from the initial partitioning screen like it shows here (look where the mouse pointer is):

[http://members.iinet.net.au/%7Eherman546/p22/027.png](http://members.iinet.net.au/%7Eherman546/p22/027.png)

Then you'll end up here:

[http://members.iinet.net.au/%7Eherman546/p22/029.png](http://members.iinet.net.au/%7Eherman546/p22/029.png)

So just be sure to choose /dev/sdc5 and click on Edit Partition which will take you here:

[http://members.iinet.net.au/%7Eherman546/p22/031.png](http://members.iinet.net.au/%7Eherman546/p22/031.png)

Just be sure to choose either ext3 or ext4 as "Use as" and check the format box, and make sure the mount point is set as /. (BTW / = root.)

Then when you get to this screen:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

Be sure you click on advanced which will take you here:

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

Be certain to choose **/dev/sdc** to install grub to.

Also if you do decide to just reinstall be sure to Check disc for defects before beginning:

[http://members.iinet.net.au/%7Eherman546/p22/002.png](http://members.iinet.net.au/%7Eherman546/p22/002.png)

OTOH if you want to keep trying to fix it I'm cool with that, but I am getting really tired. I was up and down most of the night due to that power outage because I usually rely on heat lamps for my fainter goats but I had to use a kerosene heater and I had to keep checking on it so I didn't burn the place down or gas the goats.

So I kind of need to take a break until tomorrow.

---

### Post by kansasnoob on 2010-01-08
> **A3z said:**
> root@ubuntu:/# apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [65.9kB]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [3,405B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release [44.1kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [1,353kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [7,971B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [190kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [640kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [3,270B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [5,133kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [129kB]       
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [39.7kB]       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [77.9kB]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [18.8kB]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages [45.0kB]     
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages [14B]  
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources [12.4kB]      
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources [14B]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages [19.4kB] 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources [3,367B]  
Fetched 10.6MB in 11s (948kB/s)                                                
Reading package lists... Done


Okay I think you wanted that right?

Well that looks much better!

Go back to post #4 and start from:

```
apt-get install grub-pc
```

```
grub-install /dev/sdc
```

```
update-grub
```

You just might get it!

I think that sources.list change must have been saved! Even if it's just slightly hosed we can work on it with gedit, which is much easier than nano, if we get you booting.

---

### Post by kansasnoob on 2010-01-08
Just BTW you can probably tell from browsing the forum that Karmic has been a real pain the rump!

I started with Gutsy and this has been the most problematic Ubuntu I've seen!

Both Hardy and Jaunty are incredibly stable for me.

---

### Post by kansasnoob on 2010-01-08
I hope I didn't scare you into reinstalling. I think you were very close, I'm just getting tired.

I'm a bit "long in the tooth" as they say ;)

Tired old fart is more accurate.

---

### Post by A3z on 2010-01-08
I'm just going to reinstall because when i try to boot to ubuntu same thing happens in the beginning lol.

I still don't think the problem is with my ubuntu, i think its with Win XP grub/OS list or w.e its called. And i can't find my CD anywhere :/. So idk what i am going to do.

---

### Post by kansasnoob on 2010-01-08
I sat here and dozed off. Did you at least get a Windows mbr back on sda?

I'm thinking I hit you with a much too technical approach. Sorry for that.

---

### Post by A3z on 2010-01-08
Yeah

I think. lol

---

