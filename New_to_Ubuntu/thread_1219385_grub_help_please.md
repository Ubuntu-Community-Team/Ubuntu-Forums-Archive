---
title: "grub help please?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by tjc.501 on 2009-07-21
Hey guy,
I recently installed suse 11.1 to play around with the moblin ui. Needless to say, their grub didnt detect my ubuntu installation. I got the ubuntu grub back from the live cd but it doesnt detect the suse installation. I searched hours for a solution and nothing worked!
Can someone please help? Heres is some outputs - sudo os prober - dev/sda6:openSUSE 11.1 (i586):SuSE:linux
fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25812580

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2079    16699536    5  Extended
/dev/sda2            2080        8327    50187060   83  Linux
/dev/sda3            8328        9474     9213277+  83  Linux
/dev/sda4            9475        9729     2048287+  82  Linux swap / Solaris
/dev/sda5            1021        2079     8506417+  83  Linux
/dev/sda6               1        1020     8193055+  83  Linux

Partition table entries are not in disk order
menu.lst - I added the suse as a chainloader
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
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=4b6c7787-de99-4fa5-84a3-bfc3745866f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4b6c7787-de99-4fa5-84a3-bfc3745866f9

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        4b6c7787-de99-4fa5-84a3-bfc3745866f9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4b6c7787-de99-4fa5-84a3-bfc3745866f9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        4b6c7787-de99-4fa5-84a3-bfc3745866f9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4b6c7787-de99-4fa5-84a3-bfc3745866f9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
title         SUSE11.1
root            (hd0,2)
chainloader    +1



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

Thanks for any help guys.

---

### Post by LewRockwell on 2009-07-21
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by swerdna on 2009-07-21
Edit these lines into the Ubuntu menu.lst in place of the chainloader entry:
```
# Swerdna's entry to boot the openSUSE installation on /dev/sda3 by symlinks
title openSUSE 11.1 (on /dev/sda3) by symlinks
root (hd0,2)
kernel /boot/vmlinuz root=/dev/sda3
initrd /boot/initrd
savedefault
boot
```
That assumes Suse on sda3. Reference is here:
[HowTo Boot / Multiboot openSUSE from the Grub Bootloader in Ubuntu]("http://ubuntu.devel.org/ububootsuse.html")

---

### Post by tjc.501 on 2009-07-21
I'm at work now, I will try that as soon as I get home. I forgot to mention, I'm not even sure if this matters but the suse install is on my extended partition. Sda1 is my extended, I created two drives on the extended. sda5 & sda6. Sda6 is where suse is installed. But thank you so much, I'll post the results.

---

### Post by swerdna on 2009-07-21
Then change sda3 in my example to sda6 and (hd0,2) to (hd0,5).

Luck

---

### Post by tjc.501 on 2009-07-21
I will. Thank you so much. I'll be home in 45 minutes. I'll post the results within the hour. Thanks again.

---

### Post by tjc.501 on 2009-07-21
Solved! Thank you swerdna, your code worked perfectly. I greatly appreciate it.

---

### Post by swerdna on 2009-07-21
> **tjc.501 said:**
> Didn't work. Any suggestions?

Mount sda6 in Ubuntu and make sure it's the root partition. You can recognise that by the folders in the mount, a standard Linux tree of directories like these on mine:>  bin   dev  home  lib64  media  opt   root  srv  tmp  var boot  etc  lib   lost+found  mnt    proc  sbin  sys  usrand also the file /mount_path/etc/SuSE-release should exist with contents similar to these:> openSUSE 11.1 (x86_64)
VERSION = 11.1

And key thing is that this command : ```
ls -l /mount_path/boot/ | egrep "initrd|vmlinuz"
```should show (amongst other things) the links vmlinuz and initrd similar to this from mine:
```
john@ubuntu904:~$ ls -l /mount_point/boot/ | egrep "initrd|vmlinuz"
lrwxrwxrwx 1 root root      28 2009-07-17 23:51 initrd -> initrd-2.6.27.23-0.1-default
lrwxrwxrwx 1 root root      29 2009-07-17 23:50 vmlinuz -> vmlinuz-2.6.27.23-0.1-default
john@ubuntu904:~$ 
```

---

### Post by tjc.501 on 2009-07-21
To anyone who plans to try suse 11.1, suses' grub will not detect the ext4 file system. The dvd image may, I'm not sure but the install from the live cd will not.

---

### Post by tjc.501 on 2009-07-21
Swerdna, my mistake when I said it didnt work. I double check the code after it failed and I hit the 6 instead of the 5. I corrected my error and it worked perfectly. Thank you again, I had hoped I edited my post before you replied. I greatly appreciate the time you took to help me. One more question for you, have you messed around with grub2 yet? If so, how is it?

---

### Post by swerdna on 2009-07-21
> **tjc.501 said:**
> Swerdna, my mistake when I said it didnt work. I double check the code after it failed and I hit the 6 instead of the 5. I corrected my error and it worked perfectly. Thank you again, I had hoped I edited my post before you replied. I greatly appreciate the time you took to help me. One more question for you, have you messed around with grub2 yet? If so, how is it?
Glad it's working.

No I haven't tried grub2. Looking forward to it.

---

