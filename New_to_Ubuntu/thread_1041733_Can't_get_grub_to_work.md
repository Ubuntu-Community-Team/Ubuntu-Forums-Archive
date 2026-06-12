---
title: "Can't get grub to work"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by wide-load on 2009-01-16
I have a system with a AMD64 3800.  It is set for dualboot, with Windows XP Home on a Seagate 8.4gb IDE drive.  Ubuntu 8.10 is on a 250 gb SATA drive.  Everything worked like it was supposed to.

I upgraded Windows to a Seagate 120gb IDE drive.  I upgraded Windows to XP Pro.  After I installed Windows I followed the directions in "How to restore Grub from a Live Ubuntu CD".  Everything seemed to go OK when I follwed that procedure, but when I boot I don't get the GRUB menu.  It just boots directly to Win XP.

I can temporarily put the old drive back in and GRUB works.  If I boot from a Live CD Ubuntu can access the Windows drive.  Somehow I must not be changing the MBR of the new drive, but I'm not sure what to do next. Any suggestions?

---

### Post by 2hot6ft2 on 2009-01-16
Boot from the livecd and use this in a terminal

```
sudo grub
find /boot/grub/stage1
```

This will return (hdX,Y), where X and Y are some numbers. Use these numbers below:

```
root (hdX,Y)
setup (hdX)
quit
```
and reboot

---

### Post by wide-load on 2009-01-16
I did that, and it doesn't work.  That was the directions I referenced in "How to restore grub".  I've tried this several times to no avail.

---

### Post by caljohnsmith on 2009-01-16
It sounds like you have an issue with which drive is set to boot first in your BIOS boot order. If you follow 2hot6ft2's instructions, that will install Grub to the MBR of the Ubuntu drive, and then all you should need to do is set your BIOS to boot the Ubuntu drive before any of your other drives. Let us know if that works or if you run into problems. Please note the subtlety of the last "setup" command, because it is "setup (hdX)" and not "setup (hd0)" like most tutorials show. Using (hdX) will ensure Grub is installed to the same drive that Ubuntu is on.

---

### Post by wide-load on 2009-01-16
I tried that & it didn't help.  After I changed the boot order I got the GRUB Menu but when I tried to boot Ubuntu I got a message that said "Error 13: Cannot mount selected partition".  If I tried to boot Windows I got "Error 13: Invalid or unsupported executable format.  I also booted a LiveCD and reran Grub setup again.  No Help.

I would add that everything worked OK with the old drive that had Win XP Home on it and it was the first drive in the boot order.

---

### Post by talsemgeest on 2009-01-16
Can you boot from a live cd and make sure that you can mount your ubuntu and windows drives? Try to open the drives and view a file. And, while you are in your ubuntu partition, post the file "/boot/grub/menu.lst"

---

### Post by wide-load on 2009-01-16
I can mount both the Windows and Unbuntu drives when running on a LiveCD.  I'll try to post the menu.lst file.  If I have trouble finding it what directory will it be in?

---

### Post by talsemgeest on 2009-01-16
> **wide-load said:**
> I can mount both the Windows and Unbuntu drives when running on a LiveCD.  I'll try to post the menu.lst file.  If I have trouble finding it what directory will it be in?
Once you are in the ubuntu partiton, you go to "/boot/grub/menu.lst"

For example, if your ubuntu partition is mounted as "/media/disk" you would type this to open your menu.lst: ```
gedit /media/disk/boot/grub/menu.lst
```

---

### Post by wide-load on 2009-01-17
Here is my menu.lst file.

__________________________________________________________________________
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
default		10

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
# kopt=root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


__________________________________________________________________________________

When everything was working OK, with the XP Home drive in the system, I had to go in and comment out some lines for Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) because there were some many lines in the grub menu that Windows didn't appear.

Before I made that edit I saved a backup of the original file.

---

### Post by talsemgeest on 2009-01-17
Ok, can you also post the output of ```
sudo fdisk -l
``` so that I can compare the two?

---

### Post by wide-load on 2009-01-17
Here it is:

____________________________________________________________
ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda

Disk /dev/sdb: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7660     1956928    e  W95 FAT16 (LBA)
Cannot open /dev/sdc

---

### Post by wide-load on 2009-01-17
Ithink that /dev/sdb1 device is a Flash drive that I have plugged in.

---

### Post by talsemgeest on 2009-01-17
> **wide-load said:**
> Here it is:

____________________________________________________________
ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda

Disk /dev/sdb: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7660     1956928    e  W95 FAT16 (LBA)
Cannot open /dev/sdc
Well, that is a bit of a disturbing fdisk -l. Did you run "fdisk -l" instead of "sudo fdisk -l"?

If you did run, it means that sda and sdc are completely inaccessible, and sdb (your flash drive) is the only thing that can be seen!

---

### Post by caljohnsmith on 2009-01-17
OK, it looks like the only problem is with how your menu.lst is configured, so how about doing:
```

sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) instead of (hd1,0), similar to:
```
title Ubuntu 8.04.1, kernel 2.6.24-23-generic
root [COLOR="Blue"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet
```
Also change the "# groot=(hd1,0)" to use (hd0,0):
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
And lastly, change your Windows entry at the end of the file to be:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, reboot, and let us know what happens when you boot Ubuntu and Windows from your Grub menu. We can work from there if you want.

---

### Post by wide-load on 2009-01-17
You were correct I forgot to run it as sudo.  Here is what I got when I ran it correctly:
__________________________________________________
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7660     1956928    e  W95 FAT16 (LBA)

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb542b542

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14592   117210208+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by bailbath on 2009-01-17
title Ubuntu 8.04.1, kernel 2.6.24-23-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

**try doing this**

title Ubuntu 8.04.1, kernel 2.6.24-23-generic
uuid  2212e269-9d5d-41e0-83c6-e6259ef5e505
kernel  /boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd  /boot/initrd.img-2.6.24-23-generic
quiet

**Here is mine**

# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda1)
uuid		ff98c5ab-099d-419e-aedf-9afaa7bee7f6
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ff98c5ab-099d-419e-aedf-9afaa7bee7f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		fa9a250f-e10d-450c-8fc4-fe340c4d5add
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=fa9a250f-e10d-450c-8fc4-fe340c4d5add ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		fa9a250f-e10d-450c-8fc4-fe340c4d5add
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=fa9a250f-e10d-450c-8fc4-fe340c4d5add ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

Ian

---

### Post by wide-load on 2009-01-17
Well I edited menu.lst as you suggested to change the references from (hd1,0) to(hd0,0) and changed the code associated with Windows XP and saved it.  I rebooted and it didn't help.  I ran the Grub setup again, just to see if that helped and it didn't. Thnking it might shed some light on the matter, here is a post of that activity.
___________________________________________________________
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
________________________________________________
Any thoughts on what to do next?

---

### Post by wide-load on 2009-01-17
We are getting better.  After my last post I went into BIOS and changed my boot order toboot the disk with Ubuntu on first.  Now when I do, I get the Grub Menu and can boot Ubuntu.  However I can't boot Windows XP.  When I try I get an error message that says "Error 11: Unrecoginized Device String".  Here is the current contents of menu.lst.
__________________________________________________________________
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
default		10

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
# kopt=root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
#initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2212e269-9d5d-41e0-83c6-e6259ef5e505 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP
rootnoverify		(hd1,0)
map		(hd0( (hd1)
map		(hd1) (hd0)
chainloader	+1
____________________________________________________________
Something must be messed with the code for Windows.  I note that the code I put in there was changed in several ways from the original code.
Here is the original code
_________________________________________________________________
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
________________________________________________

Note it didn'thave the 2 map lines in it and instead had the savedefault and makeactive commands.  Wheter or not this has anything to do with Windows not booting fromthe Grub menu I'm not sure.  Your Thoughts?

---

### Post by caljohnsmith on 2009-01-17
It looks like you have a typo:
```
title Microsoft Windows XP
rootnoverify (hd1,0)
map (hd0[COLOR="Red"]([/COLOR] (hd1)
map (hd1) (hd0)
chainloader +1
```
Try instead:
```
title Microsoft Windows XP
rootnoverify (hd1,0)
map (hd0[COLOR="Red"])[/COLOR] (hd1)
map (hd1) (hd0)
chainloader +1
```
And let me know if that works.

---

### Post by wide-load on 2009-01-17
You Rock!!!!!  It works great.  I kept looking at that file and knew I must have made some dumb mistake.  But you know how that goes, you see what you meant to type, not what you really typed.

2 final questions. Somewhere I saw that there is supposed be something under Thread Tools that let you mark it as solved.  I don't seem to have that option.  Is there another place to look?  Also, I saw something that said we should click on the "Metal" Icons to thank the people that help us.  I can't find that either.

So, if I can't find that Icon let me think you for your help.

---

### Post by caljohnsmith on 2009-01-17
I'm glad to hear that did the trick. About your questions, it turns out both the "marked as solved" and "thanks" features have been temporarily disabled because of the Ubuntuforums.org server problems, so there's not much you can do at the moment about that I think. Anyway, cheers and have fun with Windows and Ubuntu. :)

---

### Post by talsemgeest on 2009-01-17
> **wide-load said:**
> You Rock!!!!!  It works great.  I kept looking at that file and knew I must have made some dumb mistake.  But you know how that goes, you see what you meant to type, not what you really typed.

2 final questions. Somewhere I saw that there is supposed be something under Thread Tools that let you mark it as solved.  I don't seem to have that option.  Is there another place to look?  Also, I saw something that said we should click on the "Metal" Icons to thank the people that help us.  I can't find that either.

So, if I can't find that Icon let me think you for your help.
Yes, both the "Mark thread as solved" and the thanks plugins have been temporarily disabled, because they are "unessential." As soon as the forums are back and running at full speed, they will be re-enabled.

I am very happy that you solved your problem. :)

---

