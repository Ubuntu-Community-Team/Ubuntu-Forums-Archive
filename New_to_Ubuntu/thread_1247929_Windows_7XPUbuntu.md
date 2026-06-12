---
title: "Windows 7/XP/Ubuntu"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Nate Shoffner on 2009-08-23
I have successfully installed Windows 7, Windows XP, and Ubuntu Jaunty onto my computer.  I have GRUB as my bootloader and when it starts, it display Ubuntu and Windows 7.  I would like to be able to add Windows XP to GRUB.  How would I go about doing that.  Right now, I have to go to Windows 7 and then Windows 7's bootloader starts and I have to choose Windows XP.  Can I add an option for Windows XP in GRUB?  Thanks.

---

### Post by zvacet on 2009-08-24
You can  try [this.]("http://ubuntuforums.org/showthread.php?t=220452&highlight=triple+boot+windows")

---

### Post by Mark Phelps on 2009-08-24
> **Nate Shoffner said:**
> Can I add an option for Windows XP in GRUB?  Thanks.

Depends ...

When you install XP and then Seven, Seven puts its loader files into the XP partition; if you install Seven first and then XP, don't know where XP puts it's files, but it might put them (i.e., NTLDR) into the Seven partition.

Problem is, GRUB is only able to point you to a partition, at which point it hands off control to whichever MS boot loader has been installed in that partition.

So, using the first example, since the XP partition houses the Seven boot loader, there's no way to point GRUB to just XP.  It will launch the boot loader there, which will put up the MS Windows menu.

If you have your boot loaders installed completely separate from each other, with no duplication, then you could have two GRUB stanzas, one for each bootable partition.  But, that's the best you can do.

---

### Post by Nate Shoffner on 2009-08-25
There's no way to remove Windows 7's bootloader from the XP partition?

---

### Post by mess110 on 2009-08-25
I think it depends on the order you installed everything (that is cuz I doubt windows gives a rats *** about linux)

you should try installing the windows systems first and after that install ubuntu

Or you can just add Windows XP to grub in /boot/grub/menu.lst

---

### Post by Nate Shoffner on 2009-08-25
> **mess110 said:**
> I think it depends on the order you installed everything (that is cuz I doubt windows gives a rats *** about linux)

you should try installing the windows systems first and after that install ubuntu

Or you can just add Windows XP to grub in /boot/grub/menu.lst

I did install them in that order. :-|

And that's kind of what I've been aiming for is adding Windows XP to GRUB.  I'm just now sure how to go about doing it.

---

### Post by pedro3005 on 2009-08-25
Add this to your /boot/grub/menu.lst
```

title Windows XP
root (hd0,0) # see note
savedefault
makeactive
chainloader +1 

```
Note: this indicates where XP is installed. hd0,0 means hda1. hd0,1 means hda2, and so forth. Run 'sudo fdisk -l' to check where it all is.

---

### Post by kansasnoob on 2009-08-25
> **Nate Shoffner said:**
> I have successfully installed Windows 7, Windows XP, and Ubuntu Jaunty onto my computer.  I have GRUB as my bootloader and when it starts, it display Ubuntu and Windows 7.  I would like to be able to add Windows XP to GRUB.  How would I go about doing that.  Right now, I have to go to Windows 7 and then Windows 7's bootloader starts and I have to choose Windows XP.  Can I add an option for Windows XP in GRUB?  Thanks.

The answer is **possibly**! It can't hurt to try but we first need some info. Please post the full output of the following commands:

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by Mark Phelps on 2009-08-26
Good grief! Did nobody read what I wrote about how GRUB can only point you to a partition?  It doesn't matter what you put into the menu.lst file, it can still only point to a partition.

If the Windows boot loader on that partition has already been modified to allow selecting more than one OS, there's literally NOTHING that GRUB can do to change that.

To the OP: Need to look at your Windows partitions.  The one containing NTLDR is the XP partition; the one containing the (hidden) BOOT folder and bootmgr file is Windows 7 partition.

If ALL of these are in the XP partition, that means the following:
1) Any GRUB handoff will launch the MS Windows boot menu.
2) Pointing GRUB to the Windows 7 partition will not work because there is no bootloader there.

---

### Post by LewRockwell on 2009-08-26
> **Mark Phelps said:**
> Good grief! Did nobody read what I wrote about how GRUB can only point you to a partition?  It doesn't matter what you put into the menu.lst file, it can still only point to a partition.

If the Windows boot loader on that partition has already been modified to allow selecting more than one OS, there's literally NOTHING that GRUB can do to change that.

To the OP: Need to look at your Windows partitions.  The one containing NTLDR is the XP partition; the one containing the (hidden) BOOT folder and bootmgr file is Windows 7 partition.

If ALL of these are in the XP partition, that means the following:
1) Any GRUB handoff will launch the MS Windows boot menu.
2) Pointing GRUB to the Windows 7 partition will not work because there is no bootloader there.

Thanks Mark

.

---

### Post by Nate Shoffner on 2009-08-28
> **kansasnoob said:**
> The answer is **possibly**! It can't hurt to try but we first need some info. Please post the full output of the following commands:

```
sudo fdisk -l
``````
cat /boot/grub/menu.lst
```


```


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36b10608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9138    73400953+   7  HPFS/NTFS
/dev/sda2            9139       18276    73400985    7  HPFS/NTFS
/dev/sda3           18277       26109    62918572+   b  W95 FAT32
/dev/sda4           26110       35308    73890967+   5  Extended
/dev/sda5           26110       35247    73400953+  83  Linux
/dev/sda6           35248       35308      489951   82  Linux swap / Solaris


```

```

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## Splash image!
splashimage=/boot/grub/splashimages/triboot.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret


#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=812b09f6-c59f-4caa-b431-7450db9f11aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=812b09f6-c59f-4caa-b431-7450db9f11aa

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
# defoptions=quiet splash vga=769

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

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


title        Ubuntu 9.04
uuid        812b09f6-c59f-4caa-b431-7450db9f11aa
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=812b09f6-c59f-4caa-b431-7450db9f11aa ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04 (Recovery Mode)
uuid        812b09f6-c59f-4caa-b431-7450db9f11aa
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=812b09f6-c59f-4caa-b431-7450db9f11aa ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04 (Memtest86+)
uuid        812b09f6-c59f-4caa-b431-7450db9f11aa
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```


Sorry for the delay, I've been kinda busy lately.  I would imagine that there would be a way to remove the Windows 7 bootloader from the XP partition....

---

### Post by oldfred on 2009-08-28
I would try downloading bootinfo script
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
This will create a results.txt file and you can see if you have the windows boot.ini and /ntldr or whatever win7 needs. It will also list your boot.ini to see what is there.

this is my XP entry:
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

If you do have both loaders you then can add the stanza to menu.lst.
title        Windows 7 Ultimate, chainloader (on /dev/sda2)
rootnoverify    (hd0,1)
savedefault
chainloader +1

You may also have to edit XP's boot.ini to delete the wind7 entry.
You also have a problem in your menu.lst as your windows stanza is just above the ubuntu entries and is in the automagic area. It will get overwritten on the first update to ubuntu kernels. You need to move all windows stanza above or below the automagic area. If above put between these lines:
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by lovelife53 on 2009-09-01
I'm havin three OS'es. Ubuntu + XP + Windows 7. Can anyone tell me how to uninstall windows 7, leaving behind ubuntu n xp ??

---

### Post by louieb on 2009-09-01
> **lovelife53 said:**
> I'm havin three OS'es. Ubuntu + XP + Windows 7. Can anyone tell me how to uninstall windows 7, leaving behind ubuntu n xp ??
Hello lovelife53, and welcome to the forum. What you want to do is very different from what the original poster  is trying to archive. That can lead to confusion for you and those trying to help.  

Please start a new thread with a title like **uninstall win7 - leaving Ubuntu and XP.   **It would help if you included in your threads 1st post and much information ans you can - like # of hard drives, location of installs (output of fdisk -l is helpful), order of install. Anything else you might think helpful.

---

### Post by lovelife53 on 2009-09-03
@ above
Ohh..! Ok. My bad..!
And yeah, thanks for the warm welcome..!

---

