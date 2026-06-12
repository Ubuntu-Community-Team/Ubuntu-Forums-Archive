---
title: "ubuntu crashed &lt;sigh&gt;"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by snowman12 on 2009-03-23
last night I downloaded some updates and now this morning when I started my computer up again, whatever option I choose in GRUB always comes up with the same thing......
```
Error 11: unrecognised device string

press any key to continue. . .
```

pressing any key then takes me back to GRUB.

any ideas on what happened and how to fix it? 

(BTW I do not remember exactly which updates I installed, there was LOADS. However I do know that it would be every update from 8.10 was released until now, if that helps).

---

### Post by Xiong Chiamiov on 2009-03-23
Can you boot into a live CD and post the contents of /boot/grub/menu.lst please?

---

### Post by snowman12 on 2009-03-23
Weird. . . .

the boot order only has my hdd, so can't boot off the livecd.
however setup says that the cddrive is first on the list

I'm also dual-booting, can I find it on the windows side, and if so, where?

---

### Post by joewski on 2009-03-24
You need to go into your BIOS and set the boot order correctly for the CD/DVD to work correctly. I have removable hard drives and every time I boot without all the drives installed the Bios changes the boot order causing the grub not to be found.

---

### Post by presence1960 on 2009-03-24
> **snowman12 said:**
> last night I downloaded some updates and now this morning when I started my computer up again, whatever option I choose in GRUB always comes up with the same thing......
```
Error 11: unrecognised device string

press any key to continue. . .
```

pressing any key then takes me back to GRUB.

any ideas on what happened and how to fix it? 

(BTW I do not remember exactly which updates I installed, there was LOADS. However I do know that it would be every update from 8.10 was released until now, if that helps).

I have learned from experience to always check menu.lst after a kernel upgrade, for some reason it changes the > root hd(x,y). I always check it before shutting down or restarting.

---

### Post by snowman12 on 2009-03-25
ok fixed the problem, its one that has popped up now and again with my particular laptop, when the cddrive is not detected, I just pull it out, put in back in and wiggle it a bit until I'm sure its all the way in. So anyway, working from a live session now :P.

here you go:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## #hiddenmenu
# Hides the menu by default (press ESC to see the menu)
##hiddenmenu

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
# kopt=root=UUID=d71583f7-e48f-4113-a590-50749ab0a068 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d71583f7-e48f-4113-a590-50749ab0a068

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
##      altoptions=(single-user) single
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

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		d71583f7-e48f-4113-a590-50749ab0a068
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d71583f7-e48f-4113-a590-50749ab0a068 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		d71583f7-e48f-4113-a590-50749ab0a068
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d71583f7-e48f-4113-a590-50749ab0a068 ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		d71583f7-e48f-4113-a590-50749ab0a068
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d71583f7-e48f-4113-a590-50749ab0a068 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		d71583f7-e48f-4113-a590-50749ab0a068
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d71583f7-e48f-4113-a590-50749ab0a068 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		d71583f7-e48f-4113-a590-50749ab0a068
kernel		/boot/memtest86+.bin

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Recovery Partition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by presence1960 on 2009-03-25
Your info below your avatar says you use Xubuntu 8.10. But that is not in your menu.lst. Debian is in there along with windows and windows recovery partition. Exactly what is installed on your machine? I gotta go to work but you should let us know what OS's you have and also boot a Live CD and post the output of > sudo fdisk -l from terminal. Someone here will surely help you.

---

### Post by snowman12 on 2009-03-25
Details updated.

I'm using xubuntu on our schools old server, and ubuntu on lappy (which is sooo much faster).


Before the update GRUB said Ubutnu, and now its saying Debian. ???

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4354    34973473+   7  HPFS/NTFS
/dev/sda2            8710        9729     8193150    c  W95 FAT32 (LBA)
/dev/sda3            4355        4363       72292+   7  HPFS/NTFS
/dev/sda4            4364        8709    34909245    5  Extended
/dev/sda5            4364        8546    33599916   83  Linux
/dev/sda6            8547        8709     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by presence1960 on 2009-03-26
> **snowman12 said:**
> Details updated.

I'm using xubuntu on our schools old server, and ubuntu on lappy (which is sooo much faster).


Before the update GRUB said Ubutnu, and now its saying Debian. ???

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4354    34973473+   7  HPFS/NTFS
/dev/sda2            8710        9729     8193150    c  W95 FAT32 (LBA)
/dev/sda3            4355        4363       72292+   7  HPFS/NTFS
/dev/sda4            4364        8709    34909245    5  Extended
/dev/sda5            4364        8546    33599916   83  Linux
/dev/sda6            8547        8709     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I missed the part where you said 8.10. My post about hd(x,y) does not apply because GRUB on 8.10 uses UUID. It is weird that your GRUB now says Debian rather than Ubuntu. You can check the UUID # of your partitions by running this command: ```
sudo blkid -c /dev/null
```

Check the output for your Ubuntu partition against your kernel entries in GRUB. I am still a noob myself so hopefully someone with more knowledge will come along.

P.S. Did you have a backup of menu.lst. I always make a backup just in case of stuff like this.

---

### Post by snowman12 on 2009-03-26
just saw in /boot/grub there was a menu.lstbackup.
renamed them and voila! worked like a charm.

thank you all for helping, even if you just pointed me in the right direction.

---

### Post by presence1960 on 2009-03-27
> **snowman12 said:**
> just saw in /boot/grub there was a menu.lstbackup.
renamed them and voila! worked like a charm.

thank you all for helping, even if you just pointed me in the right direction.

Glad to hear you got it working!

---

