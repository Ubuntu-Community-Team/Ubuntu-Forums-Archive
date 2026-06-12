---
title: "Edit grub file so it starts WinXP again"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by longtom on 2009-02-22
Hi, 

I just reinstalled WinXP and need to edit the grub/menu.lst file in order for it to be able to start XP again.

There are some guides on the net, but either I'm to thick or I do something wrong or I don't understand correctly or all three....

Please help

longtom

---

### Post by Kevbert on 2009-02-22
Please post your grub file. Go to Applications-Accessories-Terminal and enter
```
gedit /boot/grub/menu.lst
```
Press Ctrl-A to select all text, then Ctrl-C to copy and open a new post and enter Ctrl-V to paste to the post.

---

### Post by longtom on 2009-02-22
> **Kevbert said:**
> Please post your grub file. Go to Applications-Accessories-Terminal and enter
```
gedit /boot/grub/menu.lst
```
Press Ctrl-A to select all text, then Ctrl-C to copy and open a new post and enter Ctrl-V to paste to the post.

Here you are:

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
default		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf6621f7-dc75-4926-926d-59e47aac66c4

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

longtom

---

### Post by Kevbert on 2009-02-22
You need to change the line that says
```
default 3
```
to 
```
default 6
```
You need to count from zero every time that 'title' occurs. Where you've commented out title (and kernel etc) with '#' you need to remove the # as you want to be able to get to the old kernels and memtest in case you have problems with the new kernel (that is updated operating system). 
Your new menu.lst should read as follows:
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
default		6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf6621f7-dc75-4926-926d-59e47aac66c4

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf6621f7-dc75-4926-926d-59e47aac66c4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf6621f7-dc75-4926-926d-59e47aac66c4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
When you edit the menu.lst file don't forget to use 'sudo'.

---

### Post by longtom on 2009-02-22
Thamks.

My problem was actually, that I can not start WinXP again.  So the fault must be at the end of the file.

The other entries I crossed out in order to make my list smaller - I doesn't have anything to do with the ability to strat WinXP.

I stand to be corrected

longtom

---

### Post by LastWho on 2009-02-22
i m going to dual boot windows - intrepid in few minutes, and i read about changing this list as u did, the only difference i can see is this 2 lines: 
```
map		(hd0) (hd1)
map		(hd1) (hd0)

```

may the root values (hd1,0) is wrong also, as it was said [in this thread]("http://ubuntuforums.org/showpost.php?p=6527371&postcount=1"):

> if that does not work on re-boot try &#8220;hd0,0 or hd0,2&#8221; and so on until it works.

---

### Post by Kevbert on 2009-02-22
It may be worth booting into Ubuntu 8.10 and running the following in terminal
```
sudo update-grub
```
That may fix the windows problem on the second (IDE ?) drive. If you are running windows on the first drive you may not need the map commands.

---

### Post by longtom on 2009-02-22
> **LastWho said:**
> 
may the root values (hd1,0) is wrong also, as it was said [in this thread]("http://ubuntuforums.org/showpost.php?p=6527371&postcount=1"):

Into my arms....root values should have been (hd1,1).  Thank you!

That had me in sixes and sevens...I certainly wasn't looking forward to reinstall Windows again, get all the drivers on, anti virus software....etc etc.

Thanks for everybody putting in an effort to help!

longtom

---

