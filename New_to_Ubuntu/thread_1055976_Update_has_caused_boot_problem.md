---
title: "Update has caused boot problem"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Jibbering on 2009-01-31
Hi sorry my first post is a question, been using ubuntu for a few years (currently on hardy heron 8.04) and not had any problems (someone else set up the pc) but I updated the system yesterday and thought all was fine, upon booting up today I get the following

Check root= bootarg cat /proc/cmdline
or missing modules, devices cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/11e58cb3-ab2d-47ee-aaae-4c20eb7dab2d does not exist.
Dropping to shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)
any ideas or help great fully received

---

### Post by drs305 on 2009-01-31
Please post the following:
```

sudo blkid -c /dev/null
cat /etc/fstab
cat /boot/grub/menu.lst

```

---

### Post by Jibbering on 2009-01-31
> **drs305 said:**
> Please post the following:
```

sudo blkid -c /dev/null
cat /etc/fstab
cat /boot/grub/menu.lst

```

many thanks for your speedy reply, it brings up

/bin/sh: sudo: not found

any other ideas?

---

### Post by drs305 on 2009-01-31
Boot to the LiveCD desktop and open a terminal:
```
sudo blkid -c /dev/null
```

Determine which partition is your current ubuntu partition and mount it (we will assume */dev/sda1* for this example).
```

sudo mkdir /mnt/*sda1*
sudo mount /dev/sda1 /mnt/*sda1*
cd /mnt/*sda1*
cat /boot/grub/menu.lst
cat /etc/fstab

```
Then post those results plus the blkid results.

---

### Post by Jibbering on 2009-01-31
> **drs305 said:**
> Boot to the LiveCD desktop and open a terminal:
```
sudo blkid -c /dev/null
```

Determine which partition is your current ubuntu partition and mount it (we will assume */dev/sda1* for this example).
```

sudo mkdir /mnt/*sda1*
sudo mount /dev/sda1 /mnt/*sda1*
cd /mnt/*sda1*
cat /boot/grub/menu.lst
cat /etc/fstab

```
Then post those results plus the blkid results.

Hi drs305

I'm unsure how to boot to the liveCD desktop and open the terminal, it will only let me use F2, F12 or Esc on startup, sorry for the basic questions, I'm baffled :(

---

### Post by Jibbering on 2009-01-31
just downloading ubuntu 8.04 to put onto a cd to boot from as the guy who installed it didn't leave us one but it's taking a while

thanks

---

### Post by prabhuft on 2009-02-01
Jibbering,

You do not need to burn a CD:

in ubuntu (go to old version to boot up - for that hit esc when you select ubuntu on boot up, then down arrow to previous kernel version), once ubunut is up on any version, on top left, select "Applications-->Accessories-->terminal, and then copy and paste each line individually, hit enter, wait, then next line, in drs305's message, 

drs305,

I have the exact same problem and error message, so i did what you asked jibbering to do and have posted my results below:

I also saw another post and followed marcobra's instructions on that:
[https://answers.launchpad.net/ubuntu/+question/59032](https://answers.launchpad.net/ubuntu/+question/59032)
I will post the results of that in next message:

Here are the results of the instructions you provided jibbering:

I noticed that while version 11 says alert! /dev/disk/by uuid/D88C56888C566154 does not exist", the same file is also requested in version 9, and that is working fine. I am now booting on kernel 9 generic.

prabhu@ubuntu:~$ sudo blkid -c /dev/null
[sudo] password for prabhu: 
/dev/sda1: LABEL="HP_RECOVERY" UUID="77BA-7EAF" TYPE="vfat" 
/dev/sda2: UUID="D88C56888C566154" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/loop0: UUID="da1561a5-aa00-4119-8a5c-0aef081b62a7" TYPE="ext3" 
prabhu@ubuntu:~$ sudo mkdir /mnt/sda2
prabhu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2
prabhu@ubuntu:~$ cd /mnt/sda2
prabhu@ubuntu:/mnt/sda2$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=D88C56888C566154 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional Edition
root		(hd0,1)
savedefault
chainloader	+1

prabhu@ubuntu:/mnt/sda2$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
prabhu@ubuntu:/mnt/sda2$

---

### Post by Jibbering on 2009-02-02
@ prabhuft it won't boot from a previous version only the cd

[QUOTE=drs305;6651287]Boot to the LiveCD desktop and open a terminal:
```
sudo blkid -c /dev/null
```

Brings up

/dev/sda1: UUID="2ff7b309-54ff-46ea-8d57-357e4f6a31fb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="23282ee3-b7fc-475f-9ec6-9556aba02239" TYPE="swap" 
/dev/loop0: TYPE="squashfs"

```
cat /etc.fstab
```

Brings up

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

---

### Post by drs305 on 2009-02-02
Jibbering,

The fstab results appear to be from your LiveCD and not from your actual installation. To get your ubuntu install's CD, you must first make a mount point and mount your ubuntu partition, *then* run the commands (see post #4).

Having said that, here is my experience in *Intrepid*: I updated my desktop to kernel -11 several days ago without a problem. Yesterday I tried updating my lenovo laptop and when I rebooted I got a similar "*alert! /dev/disk/by uuid/D88C56888C566154 does not exist*" message.  I checked all the UUIDs and they were correct and had not been changed.

In my case, I was *unable* to boot into any previous kernel in my menu.lst and had to restore the system to the -9 kernel using a backup partimage image. Then, with a leap of faith, I attempted to install the -11 kernel again and it was successful.

@ **Jibbering** and **prabhuft** - Based on my results, I don't think the error message is actually generated because of UUIDs being changed (which is the whole purpose of switching to UUIDs to identify devices in the first place). I don't know what causes the failure but reinstalling the new kernel (not the whole system) appeared to fix it in my case.

*prabhuft* provided a link to a thread [https://answers.launchpad.net/ubuntu/+question/59032]("https://answers.launchpad.net/ubuntu/+question/59032") in which *marcobra* recommended the steps for attempting a reinstall, which at this point is what I would recommend if you can get back to a working system and feel the need to upgrade to l -11. Note that marcobra's first set of instructions was amended to: ```
sudo apt-get --reinstall install linux-image-2.6.27-11-generic
``` if you are using the *generic* kernel.

**@ Jibbering** - I believe you are still using Hardy (8.04) unless the update you did was also an upgrade to Intrepid - so the issue of the -11 kernel is not exactly the same for you. There might be a similar issue in a newer Hardy kernel but I don't know. If possible, try to boot to the previous kernel. If you don't see any menu (that allows you to select the kernel), hit the ESC key repeatedly as the computer is first booting (immediately after the system *beep* if you get that audio input) and see if you get to the grub menu where you can select the previous working kernel.

---

### Post by Jibbering on 2009-02-02
@DRS still using Hardy 8.04 and none of the kernels I've tried boot up and presume I dont have a backup partimage

Is there a way to easily reinstall or fix the missing file using the boot cd or should I try the reinstall as mentioned above?

---

### Post by drs305 on 2009-02-02
> **Jibbering said:**
> Is there a way to easily reinstall or fix the missing file using the boot cd?

Jibbering,

Did you try to get back to a working system by selecting the previous kernel during boot? (Hitting the ESC key). That would be by far the easiest solution if it works. 

If you can't get back to the previous kernel, perhaps someone else will be able to provide an "easier" fix to the upgrade problem. In my search of similar problems either the user went back to the older kernel (if able) or had to reinstall the system. 

I know you have had this problem for several days so perhaps you can wait a bit longer to see if someone offers a solution. I am not a big fan of recommending reinstalling the complete system unless it is really necessary (even though sometimes it is faster).

---

### Post by Jibbering on 2009-02-02
> **drs305 said:**
> Jibbering,

Did you try to get back to a working system by selecting the previous kernel during boot? (Hitting the ESC key). That would be by far the easiest solution if it works. 

If you can't get back to the previous kernel, perhaps someone else will be able to provide an "easier" fix to the upgrade problem. In my search of similar problems either the user went back to the older kernel (if able) or had to reinstall the system. 

I know you have had this problem for several days so perhaps you can wait a bit longer to see if someone offers a solution. I am not a big fan of recommending reinstalling the complete system unless it is really necessary (even though sometimes it is faster).

None of the previous kernels boot up (think I've tried them all now)

I tried the code from the forum link that was posted but must have done something wrong as I said it couldn't update as I was running from CD (not sure how to get it to try and update the actual File system. I don't think the person who set the computer up partitioned it by the looks of things

thanks again for your help

---

