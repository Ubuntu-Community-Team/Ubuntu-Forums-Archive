---
title: "Boot problem - Vista/Ubuntu Dual Boot Machine"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by cr42yr1ch on 2009-01-15
Firstly sorry for having to post this, I have found a lot of similar problems by searching but I need some help interpreting the "fdisk -l" output and my grub menu.ls file.

I have been running a Vista Home Premium 32bit system (Dell Dimension 9200) from a RAID1 pair of 320Gb hard disks with no problems. This drive is split into two partitions, the operating system C: drive and the recovery partition as the D: drive. I have recently bought a separate 750Gb and installed it as a non-RAID drive and formatted it to NTFS in Vista with no problems.
 
I then installed Ubuntu 8.10 i386 on the new 750Gb drive on a new 50Gb xfs3 partition. Installation seemed to go fine and grub was installed as the bootloader.
 
The first few boots with the new installation repeatedly gave the same grub error; "error 21" which I believe means disk not found, and no operating system would boot. After the first three or so boots this error stopped appearing and grub loaded as expected.
 
Now on boot (as expected, the new 750Gb disk is the first in the bios drive boot order) Ubuntu loads via grub with no problems. However if I access the grub menu the only operating system listed is Ubuntu, Vista is not on the list. Using my bios to select the boot drive as the RAID1 320Gb pair (where Vista is installed) simply results in grub loading - Vista is still not on the list.
 
In Ubuntu I can check which drives are available via "fdisk -l" (see result attached at the end of the message). This (to my untrained eye) seems fine, ie. no loss of partition or format information.
 
I need to be able to boot into Windows and I need access to all the data from the RAID pair - I only did a critical file backup before Ubuntu installation because I wasn't expecting any problems when installing onto a different hard disk. I hope you can help!
 
***some more info***
The RAID hard disk pair are in SATA0 and 1
The CD/DVD drive is in SATA2
The new 750Gb hard disk is in SATA3
 
***result of "fdisk -l" in Ubuntu***
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       77826   614594560    7  HPFS/NTFS
 
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
Disk /dev/sdb doesn't contain a valid partition table
 
Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc83d59b1
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       81918   658005311    7  HPFS/NTFS
/dev/sdc2           81919       91201    74565697+   5  Extended
/dev/sdc5           81919       90817    71481186   83  Linux
/dev/sdc6           90818       91201     3084448+  82  Linux swap / Solaris
 
Disk /dev/sdd: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         976     7839698    b  W95 FAT32
 
***copy of /boot/grub/menu.ls***
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
timeout		3
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
 
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
# kopt=root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
 
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
 
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/vmlinuz-2.6.27-7-generic
root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
 
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/vmlinuz-2.6.27-7-generic
root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
 
title		Ubuntu 8.10, memtest86+
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Bucky Ball on 2009-01-15
```
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
```Your menu.lst has given you a clue. Stick this at the bottom, change the title to vista (or whatever) and uncomment. This is mine. Should work for you if your install is on hd0,0 (first drive, first partition). Paste it into menu.lst and see how you go ... :

```
title           Windoze Vista - Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

I am assuming the raid1 is not going to get in the way ...

---

### Post by cr42yr1ch on 2009-01-15
Ok, I'm at work at the moment but I'll give it a go tonight, thanks for the quick reply! As you said I wouldnt expect the RAID to matter as it is bios controlled.

Not sure if it actually matters but my boot drive order is not what I expected, it is actually the RAID1 pair first, then the CD/DVR drive, then the new 750Gb. Is there any affect this could have?

---

### Post by Bucky Ball on 2009-01-15
When you get home, open a terminal and paste this is:

```
sudo blkid
```... then copy and paste/post the result, please. This will let us know how Ubuntu has organised things.

hd0 = sda; hd1=sdb

hd0,0 = sda1; hd0,1 = sda2

hd1,0 = sdb1 

Etc ...

... if you get my drift. If you can identify which is your ntfs vista partition from the 'sudo blkid' command, you can work out what the hd?,? should be in your menu.lst .

---

### Post by caljohnsmith on 2009-01-15
It sounds like you still have Grub installed to the MBR of your RAID array, and that's why you still get Grub when you switch your BIOS to boot the RAID array. Also, when you boot your Ubuntu drive, that makes the Ubuntu drive (hd0) on start up, so to boot your Vista install, Vista would have to be on either (hd1) or (hd2). Bucky Ball's entries for Vista using (hd0) will only work if you boot Grub from your RAID array, but I would think you would want to instead boot Grub from your Ubuntu drive; if you do that, you could then restore a Windows MBR to your RAID array so you can boot straight into Vista when you set the BIOS to boot the Vista RAID array. That way your drives will be independent of each other when it comes to booting. Does that sound like what you might want? If so, how about trying the following entries for Vista in your menu.lst:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
And by the way, to modify your menu.lst you can do:
```
gksudo gedit /boot/grub/menu.lst
```
Probably the first Vista entry above will work, but the second entry is for completeness since it's hard to predict how Grub "sees" your RAID array on start up. How about giving the above entries a shot, boot your Ubuntu drive on start up, and let me know exactly what happens when you try the Vista entries in the Grub menu. We can work from there if you want.

---

### Post by cr42yr1ch on 2009-01-15
Ok...

**Bucky Ball**: I tried adding the following to the grub boot list:

title           Windoze Vista - Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

this didn't bring up windows, but did bring up some kind of windows-themed diagnostics menu offering "Test Memory" "Test System" and "Exit". Exit reboots, I didn't try the other two.

sudo blkid returns the following:

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0813" TYPE="vfat" 
/dev/sdc1: UUID="2088C9D188C9A61E" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc5: UUID="9e3b3fe1-a7a4-4620-a865-3b7d16f09d91" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="2a0f6488-07ca-44dc-a806-07e49c29ff50" 
/dev/sdd1: UUID="A68C46008C45CC0D" TYPE="ntfs" 

I assume /dev/sdd1 is the vista partition; /dev/sdc5 with the label "new volume" is the ntfs partition of the 750Gb disk Ubuntu is on.

**caljohnsmith**: Getting the hard disks as separate as possible like you described would be ideal.

I tried adding the following to the grub boot list:

title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

This didn't bring up windows, both options give the error "BOOTMGR is missing, press Ctrl+Alt+Del to restart."

Thank you both for your help, I would be lost without it!

---

### Post by caljohnsmith on 2009-01-15
After looking at your fdisk output more carefully, I missed the fact that Vista is most likely on the third partition instead of the first partition (sorry I wasn't paying better attention), so how about instead trying:
```
title       Windows Vista (hd1)
rootnoverify     [COLOR="Blue"](hd1,2)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     [COLOR="Blue"](hd2,2)[/COLOR]
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Also, it would be good to mark one of your partitions as bootable on your Ubuntu drive in order to prevent problems with your BIOS booting the drive, so how about doing:
```
sudo sfdisk -A1 /dev/sdc
```
Then reboot, be sure to set your BIOS to boot the Ubuntu drive first, and let me know exactly what happens when you try the two Vista entries above. We can work from there if you want.

---

### Post by cr42yr1ch on 2009-01-15
I did this "sudo sfdisk -A1 /dev/sdc", updated menu.lst and then rebooted.

Trying to boot directly from the new 750Gb Ubuntu drive gives the error "BOOTMGR is missing, press Ctrl+Alt+Del to restart."

Booting from the RAID setup brings up grub;

title       Windows Vista (hd1)
rootnoverify     (hd1,2)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

Gives "Error 22: No such partition"

title       Windows Vista (hd2)
rootnoverify     (hd2,2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

Gives "Error 13: Invalid or unsupported executable format"

---

### Post by caljohnsmith on 2009-01-15
OK, I guess I was confused, because I thought you were able to boot the Ubuntu drive since you said in your first post:
[QUOTE=cr42yr1ch]Now on boot (as expected, the new 750Gb disk is the first in the bios drive boot order) Ubuntu loads via grub with no problems.[/QUOTE]
So probably what happened is even though your BIOS was set to boot the Ubuntu drive, your BIOS may have skipped over it and booted your RAID array instead since none of the partitions on the Ubuntu drive were marked bootable at the time. The fact that you get a "BOOTMGR missing" error now when trying to boot the Ubuntu drive is actually a good sign, because that means your BIOS must be booting the Ubuntu drive now that your first NTFS partition is marked as bootable. So probably all you need to do is install Grub to the MBR (Master Boot Record) of your Ubuntu drive, and hopefully that will get the Ubuntu drive booting as expected:
```
sudo grub
grub> root (hd2,4)
grub> setup (hd2)
grub> quit
```
Then reboot again, and let me know if the Ubuntu drive boots OK, and also whether booting Vista from the Grub menu works or not. We can work from there.

---

### Post by Bucky Ball on 2009-01-15
Thought the Vista partition would be hd(3,0) as it is on sdd1 ...

/dev/sdd1: UUID="A68C46008C45CC0D" TYPE="ntfs" 

... from sudo blkid.

---

### Post by caljohnsmith on 2009-01-15
> **Bucky Ball said:**
> Thought the Vista partition would be hd(3,0) as it is on sdd1 ...

/dev/sdd1: UUID="A68C46008C45CC0D" TYPE="ntfs" 

... from sudo blkid.
His sdd drive is only 8 GB, so I think that is maybe his USB stick. :)

---

### Post by Bucky Ball on 2009-01-15
> **caljohnsmith said:**
> His sdd drive is only 8 GB, so I think that is maybe his USB stick. :)

Gotcha. Cheers. :)

---

### Post by cr42yr1ch on 2009-01-16
Ah, yes, sorry guys I have an 8gb flash disk!

I have now installed grub on hd (2,4), and got the following:

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

Ill try booting!

---

### Post by cr42yr1ch on 2009-01-16
Looks like a step in the right direction, as I am posting this from Windows! (or arguably a step in the wrong direction lol).

Grub now loads from the 750Gb Ubuntu drive, and selecting the following option from the list booted Vista with no obvious problems (apart from an NTFS consistency check on the NTFS partition of the repartitioned Ubuntu drive).

```
title       Windows Vista (hd1)
rootnoverify     (hd1,2)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```

Again I'm off to work now but ideally I would like, as caljohnsmith said, to get the two drives independent, ie. (if I understand correctly!) remove grub from the RAID MBR.

Thank you so much! Its not often that I actually miss seeing Vista :D

*edit* and Ubuntu also loads from grub hapily when booted this way.

---

### Post by caljohnsmith on 2009-01-16
Great, glad to hear that worked OK. :) About restoring a Windows MBR to your RAID array, if you have a Vista Install CD, you can do it from the command line of the Vista CD with:
```
bootrec /fixmbr
```
If you don't have a Vista Install CD, you could instead install a Windows equivalent MBR to your RAID array by doing the following in Ubuntu:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then try booting your RAID array again and let me know what happens. We can work from there if necessary, but most likely using either of the above methods should be all it takes to boot directly into Vista again when booting the RAID array.

---

### Post by cr42yr1ch on 2009-01-16
Cool that looks good! I won't try it just yet though, it is about 2am here and I've had a few! I will let you know tomorrow how it goes :) Thank you again for your help, you have been a pleasure to work with!

---

### Post by cr42yr1ch on 2009-01-17
I don't have a Vista install CD (It came pre-loaded, and I'm not sure where the restore disks are!). I installed lilo and updated the hda MBR. Now trying to boot Vista straight from the RAID hard disk gives the error "BOOTMGR is missing, press Ctrl+Alt+Del to restart."...

---

### Post by caljohnsmith on 2009-01-17
> **cr42yr1ch said:**
> I don't have a Vista install CD (It came pre-loaded, and I'm not sure where the restore disks are!). I installed lilo and updated the hda MBR. Now trying to boot Vista straight from the RAID hard disk gives the error "BOOTMGR is missing, press Ctrl+Alt+Del to restart."...
A "BOOTMGR missing" error means the MBR successfully booted a partition with a Vista boot sector, but the partition is missing Vista's bootmgr boot loader. I think we're going to need more info about your setup at this point, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Vista booting problem might be.

---

### Post by cr42yr1ch on 2009-01-17
Looks like fun!
FYI I have an internal USB card reader which is presumably being seen as sde, sdf, sdg and sdh (it is recognised as 4 drives in windows).

```
============================= Boot Info Summary: ==============================

 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Drive sdg does not have a valid partition table.
 => Drive sdh does not have a valid partition table.
 => Lilo is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112640    21084159    10485760    7  HPFS/NTFS
/dev/sda3        21084160  1250273279   614594560    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 3 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


sfdisk -V /dev/sdb:


sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/sdb: unrecognised partition table type

sfdisk: no partition table present.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc83d59b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1316012669   658005311    7  HPFS/NTFS
/dev/sdc2      1316012670  1465144064    74565697+   5  Extended
/dev/sdc5      1316012733  1458975104    71481186   83  Linux
/dev/sdc6      1458975168  1465144064     3084448+  82  Linux swap / Solaris

sfdisk -V /dev/sdc:

/dev/sdc: OK

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

Drive sdg: _____________________________________________________________________

fdisk -lu /dev/sdg:

sfdisk -V /dev/sdg:

/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading

Drive sdh: _____________________________________________________________________

fdisk -lu /dev/sdh:

sfdisk -V /dev/sdh:

/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0813" TYPE="vfat" 
/dev/sdc1: UUID="2088C9D188C9A61E" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc5: UUID="9e3b3fe1-a7a4-4620-a865-3b7d16f09d91" TYPE="ext3" 
/dev/sdc6: UUID="2a0f6488-07ca-44dc-a806-07e49c29ff50" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rich/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rich)

=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91

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

title       Windows Vista (hd1)
rootnoverify     (hd1,2)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9e3b3fe1-a7a4-4620-a865-3b7d16f09d91
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=9e3b3fe1-a7a4-4620-a865-3b7d16f09d91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=2a0f6488-07ca-44dc-a806-07e49c29ff50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc5/boot: ==================================

total 11956
drwxr-xr-x  3 root root    4096 2009-01-17 01:35 .
drwxr-xr-x 20 root root    4096 2009-01-15 00:17 ..
-rw-r--r--  1 root root  507665 2008-10-24 09:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root     512 2009-01-17 01:35 boot.0800
-rw-r--r--  1 root root   91364 2008-10-24 09:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-15 20:31 grub
-rw-r--r--  1 root root 8180489 2009-01-15 00:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 09:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 09:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 09:29 vmlinuz-2.6.27-7-generic

=============================== sdc5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-15 20:31 .
drwxr-xr-x 3 root root   4096 2009-01-17 01:35 ..
-rw-r--r-- 1 root root    197 2009-01-15 00:17 default
-rw-r--r-- 1 root root     45 2009-01-15 00:17 device.map
-rw-r--r-- 1 root root   8108 2009-01-15 00:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-15 00:17 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-15 00:17 installed-version
-rw-r--r-- 1 root root   8712 2009-01-15 00:17 jfs_stage1_5
-rw-r--r-- 1 root root   4548 2009-01-15 20:31 menu.lst
-rw-r--r-- 1 root root   4407 2009-01-15 19:33 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-15 00:17 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-15 00:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-15 00:17 stage1
-rw-r--r-- 1 root root 121460 2009-01-15 00:17 stage2
-rw-r--r-- 1 root root   9556 2009-01-15 00:17 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 6e 00  3f 00 ff 00 3f 00 00 00  |......n.?...?...|
00000020  08 b7 01 00 80 00 29 13  08 d7 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sda2

00000000  97 49 cc dc fc 0d de f3  5b 54 45 70 a0 0f 47 74  |.I......[TEp..Gt|
00000010  79 11 e5 ab a0 0b 8d b5  3c 82 3f ea 73 6d 74 88  |y.......<.?.smt.|
00000020  62 a3 c3 89 0b 1e 3c 06  03 a1 63 bd 31 b6 40 8d  |b.....<...c.1.@.|
00000030  ad e2 3f 7f 94 fc 34 f2  17 e9 f7 46 fe 7d fd f7  |..?...4....F.}..|
00000040  b7 8f 92 56 3a cc 7f 5e  7b 33 8e 72 e2 51 9a 28  |...V:..^{3.r.Q.(|
00000050  0e ee a3 d7 ef c0 2b ce  c5 c6 e8 85 6d eb bc 86  |......+.....m...|
00000060  d8 82 64 bc c1 1c 93 70  56 2c a0 0c d5 8f 92 1f  |..d....pV,......|
00000070  8e eb 10 a8 eb f8 2b da  5b 28 2a 02 e0 bc fb 51  |......+.[(*....Q|
00000080  9a 31 21 7d 11 7f e3 09  dc a4 c8 4d de da ed 3a  |.1!}.......M...:|
00000090  c9 66 1e 2b 51 6c a0 d2  a7 e6 52 44 66 c8 4c 50  |.f.+Ql....RDf.LP|
000000a0  0c 31 25 ae 67 46 97 77  5c 33 29 4d 8e 94 90 97  |.1%.gF.w\3)M....|
000000b0  f8 49 f3 7b ba 78 03 71  87 bc 0d 55 a2 9b 21 64  |.I.{.x.q...U..!d|
000000c0  ac cc e8 e4 7b ee 07 c7  55 92 f2 8b 8a b7 7b 8b  |....{...U.....{.|
000000d0  55 77 77 6c 36 9a 6b e7  b9 fb 62 26 25 3e 4e de  |Uwwl6.k...b&%>N.|
000000e0  1a c8 af 53 70 4c 49 d8  a4 cd dd b4 54 b2 3f 31  |...SpLI.....T.?1|
000000f0  18 dc 7d 8d a8 a0 7b 7a  9f 7c 40 3f 3d 3c 8c c1  |..}...{z.|@?=<..|
00000100  63 ef a3 88 5e fc cb 3f  a5 1c 8d 31 cb e4 77 63  |c...^..?...1..wc|
00000110  81 c1 90 89 cd f0 4f d5  fd 97 59 35 90 3f f3 53  |......O...Y5.?.S|
00000120  cd 3d da 17 7e 8a c6 e6  4e c0 b7 fb ed d8 b9 cd  |.=..~...N.......|
00000130  76 be 18 13 06 dd 6f 4f  ab e9 74 ac c9 85 22 97  |v.....oO..t...".|
00000140  9c 55 63 e3 2e 79 0c e6  9e 1e ad 6b 47 88 cf 6a  |.Uc..y.....kG..j|
00000150  c1 c6 a3 d7 28 f2 01 c8  6c 2f c0 fd cb e6 7e a5  |....(...l/....~.|
00000160  4f 3e a8 1d 70 72 3c d9  8c ce e7 4f b6 a0 32 91  |O>..pr<....O..2.|
00000170  8d 97 ff 14 07 21 61 2b  8b eb 9e 53 5e 80 fe 35  |.....!a+...S^..5|
00000180  ba df 8e e6 d5 72 3b 7e  4b c5 0e 68 4e 72 75 23  |.....r;~K..hNru#|
00000190  89 9d a1 c7 f9 8e d3 8d  06 25 61 57 12 0e 25 51  |.........%aW..%Q|
000001a0  b8 42 69 72 6a 77 aa 82  36 04 cb 89 37 6c f2 01  |.Birjw..6...7l..|
000001b0  01 f5 37 28 fe 2a 3c 91  5e 24 86 95 e0 58 ce a5  |..7(.*<.^$...X..|
000001c0  36 ba d8 26 13 7a 40 7e  21 fa da 86 01 d2 bc 97  |6..&.z@~!.......|
000001d0  8c f3 58 06 46 45 3e e0  92 07 59 7c af 2b be 0b  |..X.FE>...Y|.+..|
000001e0  d5 3f 2b ec c5 db 93 6b  8b 8c c0 b2 4a f7 77 6b  |.?+....k....J.wk|
000001f0  0b 55 09 f6 b3 e0 58 88  f7 5e 4f 11 41 c9 12 75  |.U....X..^O.A..u|
00000200

Unknown BootLoader  on /dev/sda3

00000000  a3 72 83 70 fb 99 f7 88  f5 d8 d1 22 df 0c 24 2c  |.r.p......."..$,|
00000010  d3 9a 22 30 22 e1 e5 fc  90 89 52 09 3f 84 e1 42  |.."0".....R.?..B|
00000020  90 31 db 09 61 a7 88 96  e8 7c 18 d1 d5 f6 4c 1d  |.1..a....|....L.|
00000030  a4 b7 b8 d2 3d 49 83 63  41 2e e5 71 9a 2e 70 53  |....=I.cA..q..pS|
00000040  a2 6e 28 55 71 95 8e d1  d8 18 ac b4 68 46 91 85  |.n(Uq.......hF..|
00000050  fb 87 e0 ec fb 46 82 9d  4f 30 3d b5 04 f9 6c 35  |.....F..O0=...l5|
00000060  47 41 6b 5c 01 58 a3 7e  23 d4 70 63 d5 ce 08 c6  |GAk\.X.~#.pc....|
00000070  06 6a 2c 0c 66 cb c8 97  38 88 ea fd 38 68 4f c4  |.j,.f...8...8hO.|
00000080  d8 80 ee 8b 09 84 76 34  b3 5a c2 50 c1 34 27 3c  |......v4.Z.P.4'<|
00000090  23 58 43 29 ac b7 06 49  85 67 19 c9 3c 4c 23 e5  |#XC)...I.g..<L#.|
000000a0  b5 b1 05 cc 0e c4 20 c8  32 38 2f 11 eb 1c c4 ed  |...... .28/.....|
000000b0  85 12 f0 d2 ce 23 6b 3c  37 b3 d8 6d cb dc a2 c2  |.....#k<7..m....|
000000c0  48 85 64 8e 68 79 1b d3  47 57 72 50 ad a7 e9 f4  |H.d.hy..GWrP....|
000000d0  98 d2 1e 8e 6b 78 82 98  5a 6d c9 fc 25 70 64 e4  |....kx..Zm..%pd.|
000000e0  7a e6 dc e5 62 1d e7 aa  81 17 d6 21 39 dc 97 f5  |z...b......!9...|
000000f0  a9 19 6a 11 8c de d5 45  cb d6 cc 8f 04 5f 56 08  |..j....E....._V.|
00000100  e5 06 45 19 b5 bf 21 8f  1f 41 f9 77 ad 54 a5 4c  |..E...!..A.w.T.L|
00000110  06 24 26 11 f1 ba d6 2d  32 86 16 f8 78 06 20 14  |.$&....-2...x. .|
00000120  99 68 10 3c 5d 3e a9 5f  f8 a9 58 4a 5d ef ab da  |.h.<]>._..XJ]...|
00000130  3a 82 3a 89 3f 54 31 bb  86 e1 e4 7f 81 4a df 15  |:.:.?T1......J..|
00000140  c3 6a b3 be 68 66 42 9e  0f 8b 00 39 e4 ec cc 98  |.j..hfB....9....|
00000150  29 60 56 8b 18 8e 09 50  52 a1 52 77 58 89 af 45  |)`V....PR.RwX..E|
00000160  d3 06 8a 38 0c 43 04 50  2d 0c a7 8c cf 8b 16 38  |...8.C.P-......8|
00000170  30 92 69 dc 3c e4 5c 32  44 68 54 91 c2 71 a6 78  |0.i.<.\2DhT..q.x|
00000180  9d cb fa 2f d3 0d e6 84  70 c7 75 a8 4d 39 ec 13  |.../....p.u.M9..|
00000190  d0 33 50 39 cb fc 94 55  0f 2d 9d 19 90 bd e8 75  |.3P9...U.-.....u|
000001a0  74 d8 7d 57 b4 f5 61 26  1e 8e 44 d1 07 1c 40 ae  |t.}W..a&..D...@.|
000001b0  70 e3 3b 9e 91 b7 38 ea  1d 33 b1 87 8b 92 ba a0  |p.;...8..3......|
000001c0  3c 5c dc 55 25 63 92 1a  ee 5d bd 7e bc 45 5d cb  |<\.U%c...].~.E].|
000001d0  24 50 e6 b6 54 a1 30 9d  c1 4f e8 78 0b 59 55 47  |$P..T.0..O.x.YUG|
000001e0  91 17 f9 57 ff d9 38 9f  94 66 ea 78 43 b0 31 9a  |...W..8..f.xC.1.|
000001f0  8b 3b c0 a0 77 ef ce 62  2e f1 38 a1 70 b0 6a 32  |.;..w..b..8.p.j2|
00000200


=============================== StdErr Messages: ===============================

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
/dev/sdg: No medium found

sfdisk: cannot open /dev/sdg for reading
/dev/sdh: No medium found

sfdisk: cannot open /dev/sdh for reading
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: sda1/??: binary operator expected
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: sda1/üëe?ïe?p.ïe?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/üëe?ïe?p.ïe?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/eïçh.*é?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/eïçh.*é?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/?èe?ïmï.ë?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/?èe?ïmï.ë?: binary operator expected
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: sda1/e°*pâ?.êe?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/e°*pâ?.êe?: binary operator expected
boot_info_script_011.sh: line 663: [: sda1/m9à?: binary operator expected
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
boot_info_script_011.sh: line 663: [: too many arguments
Disk /dev/sdb doesn't contain a valid partition table
me type
```

---

### Post by caljohnsmith on 2009-01-17
It looks like the problem is that the boot flag was moved from the third partition to the second partition in your RAID array. How about doing:
```
sudo sfdisk -A3 /dev/sda
```
Then reboot your RAID array and let me know what happens. We can work from there.

---

### Post by cr42yr1ch on 2009-01-17
It booted Vista fine straight from the RAID disk, grub loads fine from the Ubuntu disk and can boot either Ubuntu or Vista. Excellent! I will keep an eye on it for any unexpected behaviour, but apart from that a perfect fix, and thank you very much!

*edit* Is there a way to mark this thread as a resolved problem?

---

### Post by Ptero-4 on 2009-01-17
Use the thread tools menu to mark it as solved.

---

### Post by caljohnsmith on 2009-01-17
Great, glad you can boot either the Vista RAID array or the Ubuntu drive. Unfortunately the "marked as solved" feature for threads has been disabled until further notice from the admins because of all the database problems they've been having. Anyway, cheers and have fun with Vista and Ubuntu. :)

---

### Post by Bucky Ball on 2009-01-17
Excellent work, both of you! Have fun exploring. :)

---

