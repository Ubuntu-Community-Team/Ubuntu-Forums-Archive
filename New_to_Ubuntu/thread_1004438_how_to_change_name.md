---
title: "how to change name"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by huwaw69 on 2008-12-07
i have 2 OSes in my laptop, one xp and one ubuntu...
when i boot my laptop i have the option of choosing 1 OS
and of course its ubuntu... My question is, how do i change the name
of microsoft XP and Ubuntu when i boot up my laptop?

Any ideas?
:guitar:

---

### Post by scragar on 2008-12-07
it's all stored in GRUB

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by vanadium on 2008-12-07
You might prefer a tool to do this graphically

[http://ubuntuforums.org/showthread.php?t=1004429](http://ubuntuforums.org/showthread.php?t=1004429)

(I do not know it myself, so I am not sure if it allows you to change the name of the item).

---

### Post by lovelyvik293 on 2008-12-07
Go to the end of the file /boot/grub/menu.lst 
It look likes this
```

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And to change the name of ubuntu or the Xp if exist then change the name in title.Do not change other things.:popcorn:

---

### Post by huwaw69 on 2008-12-07
Thats not what i meant...
when i boot there is 2 OS selection Xp And Ubuntu
not the hidden menu...
any ideas?

---

### Post by lovelyvik293 on 2008-12-07
There is a option of hidden menu at the /boot/grub/menu.lst

```

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

```

Use '#' at the starting of the hiddenmenu.

---

### Post by huwaw69 on 2008-12-07
What will i edit there? there is no title, and no xp nor ubuntu?
Sorry for being such an idiot about this...

---

### Post by drs305 on 2008-12-07
Are you saying you have 2 identical entries for each OS?

It probably would be easiest to post your menu.lst:

```
cat /boot/grub/menu.lst
```

---

### Post by huwaw69 on 2008-12-07
Nope what i mean is when i first hit the power button right? There will be 2 choices, WindowsXP or Ubuntu just those two.
no other names appear, no Generic or recovery mode or memtest. thats what i mean, not the hidden menu selection. i hope someone understands me...

---

### Post by huwaw69 on 2008-12-07
**here is my menu.lst**





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
# kopt=root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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

title		The Ultimate Operating System Of Them All
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
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
title		Secret Operating System
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by lovelyvik293 on 2008-12-07
Remove the lines which you don't wanaa see like the line of recovery modes and memo test.

Like:-
```


## ## End Default Options ##

title The Ultimate Operating System Of Them All
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=38B4FABFB4FA7F26 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash
initrd /boot/initrd.img-2.6.27-9-generic



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Secret Operating System
root (hd0,0)
savedefault
chainloader +1

```

---

### Post by huwaw69 on 2008-12-07
Nah Never Mind, just close this thread, i think im just gonna have to figure it out myself... :::sigh:::

---

### Post by crwmike on 2008-12-07
Did you do a Wubi install of Ubuntu? If so, the boot menu would be on the windows partition. In windows, edit C:\boot.ini.

---

### Post by handydan918 on 2008-12-07
From the menu.lst that was posted, it does't look like there is a windows partition. Perhaps if the OP could include the output of ```
sudo fdisk -l
```

---

### Post by lovelyvik293 on 2008-12-07
There is a windows partation on the sda1 which is posted by huwaw69.
He changed the name to the Secret Operating System.

---

