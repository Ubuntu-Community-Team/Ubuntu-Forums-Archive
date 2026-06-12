---
title: "How do I move the Grub menu to another drive"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by RandomP on 2009-11-17
Just a pretty straight forward question, how do I move the grub menu to hd0?

For some reason my Grub menu is on hd1.

The story is that I wiped the hard drive that windows was on and reinstalled windows. I tried restoring my grub menu the way I usually did after I restored windows from my recovery partition, but it seems that it is stored on my Ubuntu drive.

---

### Post by kansasnoob on 2009-11-17
Can you boot Ubuntu now?

---

### Post by RandomP on 2009-11-17
Only if I unplug the hard drive Windows XP is on. (I have windows and Ubuntu stored on different hard drives)

---

### Post by kansasnoob on 2009-11-17
Then we'll have to work from the Live CD, so leave both drives plugged in, then boot the Live CD choosing Try Ubuntu without changes to disc.

Once you're on the Live Desktop post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

We can mount and chroot the Ubuntu partition and do what needs to be done.

---

### Post by RandomP on 2009-11-17
Will do, but right now I can't since I am using a public computer.

---

### Post by Dirtpile on 2009-11-17
Does the GRUB menu appear or does it boot straight into Ubuntu?
 
If it does go into your BIOS and switch the boot priotrity of you drives so your Ubuntu disk is the first one to boot.
 
After doing that you'll have to map the drives in menu.lst
```
 
sudo gedit /boot/grub/menu.lst

```
 
Change the entry for the windows partition to:
title              Windows XP (if this line reads NT/2000/XP leave it that way)
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
 
That should get you working again.

---

### Post by melrokz on 2009-11-17
1. boot from the ubuntu cd and 
2. double click the drive with Ubuntu 
3. try this command in a terminal:

```
sudo grub-install hd0 --root-directory=/media/disk
```

---

### Post by RandomP on 2009-11-17
> **Dirtpile said:**
> Does the GRUB menu appear or does it boot straight into Ubuntu?
 
If it does go into your BIOS and switch the boot priotrity of you drives so your Ubuntu disk is the first one to boot.
 
After doing that you'll have to map the drives in menu.lst
```
 
sudo gedit /boot/grub/menu.lst

```
 
Change the entry for the windows partition to:
title              Windows XP (if this line reads NT/2000/XP leave it that way)
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
 
That should get you working again.
I would rather not switch the priority of my drives.

---

### Post by kansasnoob on 2009-11-17
Just FYI where I was headed with this was, look at the output of fdisk -l, we'll imagine it's like this:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bffde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bffde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2678        3763     8723295   83  Linux
/dev/sdb2            3764       19457   126062055    5  Extended
/dev/sdb5           14880       15032     1228941   82  Linux swap / Solaris


In a simple example like that you can see that sda is the Windows drive and sdb is the Linux drive.

Furthermore you can easily see that sdb1 is the Ubuntu / (aka: root) partition. 

Sometimes in more complex partitioning schemes you either must simply know your own computer or if you get computers dropped in your lap like I do the Boot Info Script will usually help me sort out what I need to know:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Anyway, in this example, we know that sdb1 is Ubuntu / so we want to mount and chroot sdb1:

```
sudo mount /dev/sdb1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo chroot /mnt
```

You'll notice the shell prompt changes from $ to #, the # indicates you are root so no sudo is needed for the following commands. Just to be sure I am where I want to be I always like to run:

```
df -H
```

and:

```
cat /etc/issue
```

Anyway the next command I was going to ask you to run once we were chroot in your Ubuntu was;

```
grub-install -v
```

Which will simply display the grub version number, 0.97 is legacy grub and 1.9* is the new grub2.

If this is legacy grub I'd do this:

```
grub-install /dev/sda
```

Then to be sure it worked:

```
grub
```

Which will drop you into a grub shell, then:

```
find /boot/grub/stage1
```

Which will provide an output like (hd1,0) which you'll need to use in the next step:

```
root (hd1,0)
```

You see I've used (hd1,0) from the "find" command, then I use only the (hd1) part of that:

```
setup (hd1)
```

Which should produce an output like this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Then, hopefully all said yes and succeeded so:

```
quit
```

And you should be done except for exiting the chroot and unmounting sdb1, that's coming after the grub2 example:

If it's grub2 it's easier:

```
grub-install /dev/sda
```

If that produces any errors:

```
grub-install --recheck /dev/sda
```

```
update-grub
```

Now regardless of whether it was legacy grub or grub2 we need to exit chroot and unmount so:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

And if you're ready to reboot:

```
sudo reboot
```

Clear as mud???????????

---

### Post by RandomP on 2009-11-17
Well now, that is informative...

Here are the commands I usually went through when grub disappeared:

```

sudo grub
root (hd0,0)
setup (hd0)
exit

```

This time though, hd0,0 did not work, so I tried hd1,0
This is more or less exactly what it gave me:
> Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done. 

The problem is, Grub is still gone.

---

### Post by kansasnoob on 2009-11-17
Did you do the very first step though:

```
grub-install /dev/sda
```

That determines which drive grub gets installed on.

---

### Post by kansasnoob on 2009-11-17
Or maybe I should see your fdisk -l.

---

### Post by RandomP on 2009-11-17
Sorry, I am still on a public computer.

---

### Post by kansasnoob on 2009-11-17
> **RandomP said:**
> Sorry, I am still on a public computer.

Oh, I thought you had actually tried that.

Just be sure to substitute the proper numbers and such based on the output of your fdisk -l.

---

### Post by RandomP on 2009-11-18
Alright, I am home and have started up with the liveCD.

here are the contents of my fdisk-l:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         705     5662881    b  W95 FAT32
/dev/sda2   *         706       30401   238533120    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c6635f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9568    76854928+  83  Linux
/dev/sdb2            9569        9729     1293232+   5  Extended
/dev/sdb5            9569        9729     1293201   82  Linux swap / Solaris
```

---

### Post by RandomP on 2009-11-18
Ran into a problem. 

Did everything said on the other page to do after looking at fdisk-l, it all worked, so I unmounted and rebooted. 

The first thing I noticed, Grub is still gone.

Ideas, suggestions?

---

### Post by kansasnoob on 2009-11-18
Does it just boot straight to Windows? Or Ubuntu? Or nothing?

The easiest thing for me is if you just post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I will be turning in for some shut-eye directly though.

---

### Post by RandomP on 2009-11-18
Here's the text it gave me:

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,325,824    11,325,762   b W95 FAT32
/dev/sda2    *     11,325,825   488,392,064   477,066,240   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c6635f9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   153,709,919   153,709,857  83 Linux
/dev/sdb2         153,709,920   156,296,384     2,586,465   5 Extended
/dev/sdb5         153,709,983   156,296,384     2,586,402  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="PRESARIO_RP" UUID="275F-17CE" TYPE="vfat" 
/dev/sda2: UUID="1AE8DAA7E8DA8105" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sdb1: UUID="7806267b-4498-4fc4-937e-36e11a1f9086" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="81e13515-4a94-46dc-8172-f1271b732644" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7806267b-4498-4fc4-937e-36e11a1f9086 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7806267b-4498-4fc4-937e-36e11a1f9086

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		7806267b-4498-4fc4-937e-36e11a1f9086
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7806267b-4498-4fc4-937e-36e11a1f9086 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		7806267b-4498-4fc4-937e-36e11a1f9086
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7806267b-4498-4fc4-937e-36e11a1f9086 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7806267b-4498-4fc4-937e-36e11a1f9086
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7806267b-4498-4fc4-937e-36e11a1f9086 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7806267b-4498-4fc4-937e-36e11a1f9086
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7806267b-4498-4fc4-937e-36e11a1f9086 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7806267b-4498-4fc4-937e-36e11a1f9086
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=7806267b-4498-4fc4-937e-36e11a1f9086 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=81e13515-4a94-46dc-8172-f1271b732644 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  63.4GB: boot/grub/menu.lst
  68.8GB: boot/grub/stage2
  62.2GB: boot/initrd.img-2.6.28-11-generic
  22.5GB: boot/initrd.img-2.6.28-16-generic
  62.1GB: boot/vmlinuz-2.6.28-11-generic
  22.4GB: boot/vmlinuz-2.6.28-16-generic
  22.5GB: initrd.img
  62.2GB: initrd.img.old
  22.4GB: vmlinuz
  62.1GB: vmlinuz.old
```

---

### Post by RandomP on 2009-11-18
Solved it. I found a tutorial from the Ubuntu site:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

