---
title: "Reboot loop"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by zorblek on 2009-09-16
I dual boot Ubuntu 9.04 and Windows XP on a Dell XPS M1210 laptop. When I tried to boot up today, I got caught in an endless reboot loop. The bios would load normally. Then it would display grub for a split-second (not long enough for the boot menu to appear, just to say that grub was starting). Then the screen would go black for a second and then it would reboot and start the cycle over again.

I tried booting off the LiveCD and fixing grub as described in the Ubuntu wiki, but that had no effect. I also ran fsck, but it didn't turn up any errors.

I'm at a bit of a loss. Any suggestions would be greatly appreciated. Thanks!

---

### Post by TeoBigusGeekus on 2009-09-16
Could it be a hardware problem? Motherboard freaked out?
Have you tried disconnecting it from power, pressing the on/off button 5 or 6 times and then connecting it again?

---

### Post by egalvan on 2009-09-16
Start by posting the contents of /boot/grub/menu.lst.

Also, the output of

```
sudo blkid
```

```
sudo fdisk -l
```

Please surround each with "code" tags, to make them easier to read.

---

### Post by zorblek on 2009-09-16
/boot/grub/menu.lst:

[INDENT]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		5

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
# kopt=root=UUID=2f1c73c2-68b9-40b2-9ad7-0899f0df580b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2f1c73c2-68b9-40b2-9ad7-0899f0df580b

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		2f1c73c2-68b9-40b2-9ad7-0899f0df580b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=2f1c73c2-68b9-40b2-9ad7-0899f0df580b ro 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		2f1c73c2-68b9-40b2-9ad7-0899f0df580b
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=2f1c73c2-68b9-40b2-9ad7-0899f0df580b ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
uuid		2f1c73c2-68b9-40b2-9ad7-0899f0df580b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/INDENT]

sudo blkid:

[INDENT]/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0B01" TYPE="vfat" 
/dev/sda2: UUID="C6A0A35CA0A3522B" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="2f1c73c2-68b9-40b2-9ad7-0899f0df580b" TYPE="ext3" 
/dev/sda6: UUID="85e59819-55a5-47a1-887d-5954ee65321f" TYPE="swap" 
[/INDENT]

sudo fdisk -l:

[INDENT]Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+   6  FAT16
/dev/sda2   *           5        7477    60026872+   7  HPFS/NTFS
/dev/sda3            9049        9545     3992152+  db  CP/M / CTOS / ...
/dev/sda4            7478        9048    12619057+   5  Extended
/dev/sda5            7478        8976    12040686   83  Linux
/dev/sda6            8977        9048      578308+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/INDENT]

I forgot to mention before, I also tried disconnecting the power, but I didn't press the power button, so I'll try that.

---

### Post by Kaymeerah on 2009-09-16
did u set it to runlevel 6 at startup?

---

### Post by zorblek on 2009-09-16
> **Kaymeerah said:**
> did u set it to runlevel 6 at startup?

Not that I know of. I'm not sure what that means.

---

### Post by zorblek on 2009-09-16
Also, I tried disconnecting it from power and pressing the power button several times, but it had no effect.

---

### Post by louieb on 2009-09-16
> **zorblek said:**
> I tried booting off the LiveCD and fixing grub as described in the Ubuntu wiki, but that had no effect. I also ran fsck, but it didn't turn up any errors.

Can you provide a link? and describe exactly what you did to attempt to fix GRUB? 

Menu should show for 5 seconds. Since its not getting the grub menu. did you try something like this
Live CD - terminal window

```
sudo grub
```
from the [COLOR=Red]grub>[/COLOR] prompt 
```

root (hd0,4)
setup (hd0)
quit

```

Should get a message that it was successful.  Reboot and see what happens.

---

### Post by zorblek on 2009-09-17
> **louieb said:**
> Can you provide a link? and describe exactly what you did to attempt to fix GRUB?

The instructions I followed are at [https://help.ubuntu.com/community/GrubHowto#Command%20line]("https://help.ubuntu.com/community/GrubHowto#Command%20line"). I'm pretty sure that they're identical to what you just suggested, unfortunately.

---

### Post by louieb on 2009-09-17
As long as you typed** root (hd0,4)** and** setup (hd0)  **and you got the **success message** that pretty much rules out GRUBS  stage1 code in the MBR being corrupted.  

Just trying to rule out software problems  Kind of weird it will boot the live CD but not the hard drive. Makes me think the problem is either GRUB stage2 program being corrupted or the hard drive going bad. Or maybe both.

Two things to try next.  [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") is probably the most flexible. it should be able to boot your Windows or Ubuntu install. 

or you can try replacing GRUBS stage2 code in the Ubuntu install. 

In /usr/lib/grub/i386-pc there are copies of stage1 stage2 and the stage 1.5 files. Copy these to /boot/grub and run the same setup commands you did earlier.   

And with that I'm out of ideas. Good Luck,

---

### Post by zorblek on 2009-10-12
I thought I had already replied to this thread, but apparently I didn't. I wanted to thank you for all the help. Copying over the files and *then* using grub did the trick.

Unfortunately, I've had the same problem several times since I first posted. It looks like every time I boot into Windows (which is fairly rare lately), it corrupts grub somehow. So I'm just going to blow away both partitions and do clean installs.

But in the meantime, your advice has been invaluable. Thanks again!

---

