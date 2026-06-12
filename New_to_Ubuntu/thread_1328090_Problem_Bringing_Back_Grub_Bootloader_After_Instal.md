---
title: "Problem Bringing Back Grub Bootloader After Installing Win7 and WinXP"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2009-11-16
Ey guys I have a computer that used to be dual-boot XP and Ubuntu. I reformatted the XP partition and divided it into two and installed XP and then Windows 7 on it. After installing XP, I followed this advice(courtesy of ajmorris):

> 
hi there,
This is very normal. The installation of your Windows XP system, re-installs the XP bootloader into your MBR, and replaces GRUB. All that is required, is a re-install of grub.

So, boot up any linux media you have, i.e an ubuntu live cd etc, and do the following:

1) sudo grub
2) find /boot/grub/stage1
3) root (hd#,#)
(where #,# are the numbers that step 2) spits out
4) setup (hd0)
5) quit
6) sudo reboot


..from this thread: [http://ubuntuforums.org/showthread.php?t=1032213](http://ubuntuforums.org/showthread.php?t=1032213)

And everything worked fine, then I installed Windows 7 and the Windows Bootloader took over again and only allowed me to select Windows 7 or Windows XP. Then I performed the same procedure but this time at step #2 it says that the file is not found. I tried "stage2" "stage3" and "stage" to no avail. So what would do I do now? Thanks in advance!

---

### Post by realzippy on 2009-11-16
Which ubuntu version??

---

### Post by StunnerAlpha on 2009-11-16
> **realzippy said:**
> Which ubuntu version??

8.10, but I am using a 8.04 Live CD. Thanks for asking.

---

### Post by realzippy on 2009-11-16
Try the supergrubdisc to restore your grub easily:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by StunnerAlpha on 2009-11-16
Thanks man. You happen to recommend any way? I checked it out and there are tons of options to choose from. I am leaving the country for a trip tomorrow morning so I really need to get this done ASAP so if you could guide me to which method would be fastest/easiest, that would be great and thank you!

---

### Post by StunnerAlpha on 2009-11-16
I ended up doing it this way:  

========================== 

GRUB solution (on its own)

Find the partition where GRUB stage1 it is.

grub>find /boot/grub/stage1
grub>find /grub/stage1

Output from these commands might be:

  (hd0,1)
  (hd0,3)

Let's suppose that you want to restore GRUB from second partition on first hard disk (hd0,1).

Just type these commands:

grub>root (hd0,1)

which prompts:

Filesystem type is ext2fs, partition type 0x83

and then:

grub>setup (hd0)

which prompts:

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

Now you can reboot your machine with the reboot command.

grub>reboot

==========================

from: [http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub](http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub)

And it did everything without any hiccups. Now I have my old GRUB bootloader screen, but when I select Ubuntu 8.10,kernel 2.6.27-15-generic I get this error: "Error 17: Cannot mount selected partition". So... how would I fix that?

---

### Post by realzippy on 2009-11-16
suggestion:

[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/supergrubdisk_0.9677.iso](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/supergrubdisk_0.9677.iso)

---

### Post by louieb on 2009-11-16
> **StunnerAlpha said:**
> ...Now I have my old GRUB bootloader screen, but when I select Ubuntu 8.10,kernel 2.6.27-15-generic I get this error: "Error 17: Cannot mount selected partition". So... how would I fix that?

You change menu.lst to point to right partition. Guess your Win installs did something to the partition table. Take a look.

Pleas follow the  [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  it should help you figure it out. If you want - please put the results.txt in your next post and I'll take a look.

---

### Post by StunnerAlpha on 2009-11-16
Thanks for the link realzippy, unfortunately that .iso image connot be read and I cannot burn it. :(

louieb- thanks for the reply, I'll post the results.txt right away.

Thank you all!

---

### Post by StunnerAlpha on 2009-11-16
RESULTS.txt:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15821581

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,643,999   112,643,937   7 HPFS/NTFS
/dev/sda2         112,644,096   573,454,335   460,810,240   7 HPFS/NTFS
/dev/sda3         573,456,240   617,185,169    43,728,930  83 Linux
/dev/sda4         617,185,170   625,137,344     7,952,175  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1054 MB, 1054605312 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2059776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0217934c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,059,775     2,059,713   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F86CDC316CDBE900" TYPE="ntfs" 
/dev/sda2: UUID="EE68C08068C048D3" TYPE="ntfs" 
/dev/sda3: UUID="96f7c2f8-241c-41ba-bc0c-62fc202ee188" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="2b1a6886-0139-4d50-a9f6-0f53ff443c06" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="ATT1GB" UUID="2CCB-7A33" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/ATT1GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sda3/boot/grub/menu.lst: ===========================

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root





=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=2b1a6886-0139-4d50-a9f6-0f53ff443c06 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 296.2GB: boot/grub/menu.lst
 296.1GB: boot/grub/stage2
 296.1GB: boot/initrd.img-2.6.24-23-generic
 296.2GB: boot/initrd.img-2.6.24-23-generic.bak
 296.2GB: boot/initrd.img-2.6.27-14-generic
 296.2GB: boot/initrd.img-2.6.27-15-generic
 296.2GB: boot/vmlinuz-2.6.24-23-generic
 296.2GB: boot/vmlinuz-2.6.27-14-generic
 296.1GB: boot/vmlinuz-2.6.27-15-generic
 296.2GB: initrd.img
 296.2GB: initrd.img.old
 296.1GB: vmlinuz
 296.2GB: vmlinuz.old

```
Thanks again.

Edit: Killer script by the way.

---

### Post by louieb on 2009-11-16
There it is:   change [COLOR=Red] (hd0,1)[/COLOR] to [COLOR=Red](hd0,2)[/COLOR]  Grub legacy starts numbering partitions starting fom zero. Ubuntu was in partition #2 now its in #3. (will have to make the same change in several places - all in file /boot/grub/menu.lst) 

```
title        Ubuntu 8.10, kernel 2.6.27-15-generic
[COLOR=Red]root        (hd0,1)[/COLOR]
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-15-generic
quiet
```

---

### Post by StunnerAlpha on 2009-11-16
> **louieb said:**
> There it is:   change root (hd0,1) to root (hd0,2)  Grub legacy starts numbering partitions starting fom zero. Ubuntu was in partition #2 now its in #3. (will have to make the same change in several places) - file /boot/grub/menu.lst 

```
title        Ubuntu 8.10, kernel 2.6.27-15-generic
[COLOR=Red]root        (hd0,1)[/COLOR]
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-15-generic
quiet
```

Ok, wait, so how would I change the root to (hd0,2)? Would I just do this?
```

1) sudo grub
2) find /boot/grub/stage1
3) root (hd0,2)
4) setup (hd0)
5) quit
6) sudo reboot 

```

---

### Post by realzippy on 2009-11-16
> **StunnerAlpha said:**
> Thanks for the link realzippy, unfortunately that .iso image connot be read and I cannot burn it. :(

louieb- thanks for the reply, I'll post the results.txt right away.

Thank you all!


..because you are on windows?
LiveCD would do....

---

### Post by StunnerAlpha on 2009-11-16
> **realzippy said:**
> ..because you are on windows?
LiveCD would do....

I tried burning it with my mac. You are saying I should try mounting the image when in ubuntu with the live CD?

---

### Post by louieb on 2009-11-16
edit file /boot/grub/menu.lst  

live cd press alt+f2 - run dialog```

gksudo nautilus
``` navigate to file on hard drive open with text editor.

or faster 
grub menu  - highlight entry - press [COLOR=Red]e[/COLOR] to edit - make the change - press enter - then press [COLOR=Red]b[/COLOR] to boot.  temporary - will still have to use text editor to make change permanent.

---

### Post by StunnerAlpha on 2009-11-16
> **louieb said:**
> edit file /boot/grub/menu.lst  

live cd press alt+f2 - run dialog```

gksudo nautlius
``` navigate to file on hard drive open with text editor.

or faster 
grub menu  - highlight entry - press [COLOR=Red]e[/COLOR] to edit - make the change - press enter - then press [COLOR=Red]b[/COLOR] to boot.  temporary - will still have to use text editor to make change permanent.

AWESOME! You just made my day man, thank you so much!!! Thanks to all that chimed in and helped. 

In menu.lst I had:
```

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

```
Which are duplicates, can I delete them/comment them out? If so, which ones? All of them? Thanks.

---

### Post by louieb on 2009-11-16
There not duplicates - different kernels - just in case one has trouble. Some get rid of all but a couple - I don't bother. 

BTW: make sure to find the line 
```
# groot=(hd0,1)
```and change it too.

Have a safe trip. Lou

---

### Post by StunnerAlpha on 2009-11-16
Done and will do! You take it easy yourself Lou. Thanks again, you made my life a whole lot easier.

---

