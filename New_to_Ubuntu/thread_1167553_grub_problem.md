---
title: "grub problem"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-05-23
i just installed windows on a 1.5g partion and everything went well and ubuntu can boot but i have 2 problems , 

1.ubuntu doesnt have a graphical boot screen anymore , how do i re-enable that

2. how do i add windows xp to the grub menu? (its installed on /dev/sda2 if that helps)

here is my grub menu.lst 

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
# kopt=root=UUID=7fb8c81e-d92f-419b-8da8-35dc0461e5c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7fb8c81e-d92f-419b-8da8-35dc0461e5c7

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7fb8c81e-d92f-419b-8da8-35dc0461e5c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fb8c81e-d92f-419b-8da8-35dc0461e5c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7fb8c81e-d92f-419b-8da8-35dc0461e5c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fb8c81e-d92f-419b-8da8-35dc0461e5c7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7fb8c81e-d92f-419b-8da8-35dc0461e5c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

ok because i had modified my swap partion the uuid had changed and this is what i did to resolve this :

I Ran the command "sudo blkid" which told me the uuids of my partitions.
I then ran "sudo gedit /etc/fstab" and everything was correct in there.
Next I made sure the uuid in /etc/initramfs-tools/conf.d/resume ("sudo gedit /etc/initramfs-tools/conf.d/resume") was the same  as the swap uuid.
After i had corrected those files i updated the initramfs ("sudo update-initramfs -u") and then restarted and presto all was fixed.

---

### Post by QIII on 2009-05-23
Question 2 is fairly easy.  

If you look through the commented lines, you'll find this example:

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

Take off the pound signs and paste this just after

## ## End Default Options ##


and before

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7fb8c81e-d92f-419b-8da8-35dc0461e5c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fb8c81e-d92f-419b-8da8-35dc0461e5c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


You'll want to change the title line to "Windows XP" to avoid confusion.

Also, you may have to fiddle around with the root line to be sure you are trying to access the correct device for Windows.  sudo fdisk -l

As for your first question, I don't know right off the top of my head.  I'll have to do some looking, but someone might chime in before I find it.

---

### Post by QIII on 2009-05-23
After a quick search of the forums, I found this for restoring the graphical login:

sudo update-rc.d -f gdm defaults

But wait a while and see if anyone can confirm this for me.

---

### Post by pspsampsp on 2009-05-23
its usplash that isnt working not gdm

---

### Post by QIII on 2009-05-23
Ouch.  OK.

Hang tight ...

---

### Post by pspsampsp on 2009-05-23
ok thanks for helping , anyone else got some suggestions , i have an fx5500 if it helps i think i had this problem when i used to use fedora with plymouth and i need to add something like vga="975" or something but im not sure.

---

### Post by QIII on 2009-05-23
I don't know if this will last from one boot to the next, but try this:


Hit Esc during Grub boot delay

Find your chosen Ubuntu boot line and press "e".  That should let you edit that line.

Go to the "kernel" line and press "e" again.

At the end of the line, add "splash" and hit enter.

Type "b" to boot the custom boot line.


Like I said, though, I'm not sure if that will help on next boot.

---

### Post by QIII on 2009-05-23
OK.  I just checked my menu.lst

sudo gedit your /boot/grub/menu.lst 

On mine I have the following at the end of the "kernel" line:

ro quiet splash

---

### Post by pspsampsp on 2009-05-23
no it still doesnt work but thanks for stickin with me :) , ill give some more info: the boot splash sort of works , the little bar moves back and foward like it supposed to bu then instead of the loading bar filling up it just goes to a text boot (i can make a video of it if you don't understand that) , maybe you could post your full /boot/grub/menu.lst  so i can compare them?

---

### Post by QIII on 2009-05-23
Here you go:

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
timeout		15

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
# kopt=root=UUID=f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f

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

title		Windows Vista
root 		(hd1,0)
		makeactive
		chainloader +1


title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f7be4770-f5d7-44e8-ab4b-9509c8a7ff9f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by QIII on 2009-05-23
BTW --

I guess this goes without saying, but don't change your uuid . . .

---

### Post by pspsampsp on 2009-05-23
could his be caused by changing my swap partion , i increased its size and made it and it is now sda3 instead of sda2 , also i just reinstalled the ubuntu usplash theme and usplash but still no success. 

edit: i just noticed in gparted the swap isn't on , maybe this is the problem ?

---

### Post by QIII on 2009-05-23
I wouldn't think so.

The swap is just an area of the physical drive Linux uses as "virtual memory" when your RAM gets near to being fully utilized.

---

### Post by pspsampsp on 2009-05-23
ok you were right i fixed my /etc/fstab but that didnt fix anything , im thinking i might have to do a complete reinstall of ubuntu and see if that fixes it.

---

### Post by QIII on 2009-05-23
Míthaitneamhach!

Pretty radical step.

If you're going to do that, find a tutorial about dual booting on one physical drive.

I've always done it on two physical drives.

---

### Post by pspsampsp on 2009-05-23
yay im not going to have to reinstall i fixed it , because the uuid of my swap partion had changed i had to change it in /etc/initramfs-tools/conf.d/resume and then run "sudo update-initramfs -u" i will post more detailed instructions on main post just in case someone else has this issue. Thanks for trying to help me QIII , if they had rep or something on this forum id definitly + you :) .

---

