---
title: "Upsplash gone, need help!"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Alfx on 2009-01-18
Its been gone for a long time.

But now I want it back.

My upsplash screen is only text.
In the started manager, text IS disabled.

I have no idea how to fix this.

Help!

---

### Post by mjheagle8 on 2009-01-19
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
you need to add quiet splash to the grub menu.lst

---

### Post by Alfx on 2009-01-19
[QUOTE=mjheagle8;6576052][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

That's what I got.
So what's causing the problem here exactly?

---

### Post by Alfx on 2009-01-19
Anyone?

---

### Post by mjheagle8 on 2009-01-19
did you read the article that i posted?

---

### Post by aun on 2009-01-19
I'm guessing this has something to do with the "vga=791".  A quick google for "grub vga=791" led to this:

[http://ubuntuforums.org/showthread.php?t=158969]("http://ubuntuforums.org/showthread.php?t=158969")


Good luck.

---

### Post by cariboo on 2009-01-19
Usually when usplash stops working, it is because of some sot of problem during boot up. When the text is scrolling by do you notice a [COLOR="Sienna"]Fail[/COLOR] during the boot process. If you see it press the Pause/Break key to stop the process and check to see what it is that is failing.

You could also check the log files located in /var/log for errors. I usually look for errors by entering the following in a terminal:

```
cat /var/log/messages | grep error
```

This will find any of the occurences of the word error in /var/log/messages.

Jim

---

### Post by Alfx on 2009-01-19
> **cariboo907 said:**
> Usually when usplash stops working, it is because of some sot of problem during boot up. When the text is scrolling by do you notice a [COLOR="Sienna"]Fail[/COLOR] during the boot process. If you see it press the Pause/Break key to stop the process and check to see what it is that is failing.

You could also check the log files located in /var/log for errors. I usually look for errors by entering the following in a terminal:

```
cat /var/log/messages | grep error
```

This will find any of the occurences of the word error in /var/log/messages.

Jim
Yes, there is one fail.

Firestarter seems to fail everytime.

EDIT:
I removed firestarter, it doesnt change anything.

I found this error using your command:

Jan 19 11:07:42 DarkEmpire kernel: [   55.129543] canberra-gtk-pl[5935]: segfault at 1019ed230 ip 00007f6cbc59d6ec sp 000000004200fbd0 error 6 in libc-2.8.90.so[7f6cbc521000+169000]

---

### Post by kansasnoob on 2009-01-19
I suspect a uuid problem which generally occurs if SWAP has been resized or moved.

Post the output of:

```
sudo blkid -c /dev/null
```

And also:

```
cat /etc/fstab
```

And finally:

```
cat /etc/initramfs-tools/conf.d/resume
```

What we want to do there is compare the uuid's for SWAP in all three of those locations.

---

### Post by Alfx on 2009-01-19
> **kansasnoob said:**
> I suspect a uuid problem which generally occurs if SWAP has been resized or moved.

Post the output of:

```
sudo blkid -c /dev/null
```

And also:

```
cat /etc/fstab
```

And finally:

```
cat /etc/initramfs-tools/conf.d/resume
```

What we want to do there is compare the uuid's for SWAP in all three of those locations.

```
/dev/sda1: UUID="C0D0824DD0824A1C" LABEL="DarkEmpire" TYPE="ntfs" 
/dev/sda5: UUID="f654c563-5451-448e-b747-7cd839b2a8d9" TYPE="ext3" 
/dev/sda6: UUID="bd2e006f-7e47-48c7-b70a-a4b301834266" TYPE="swap" 

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f654c563-5451-448e-b747-7cd839b2a8d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=bd2e006f-7e47-48c7-b70a-a4b301834266 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
RESUME=UUID=bd2e006f-7e47-48c7-b70a-a4b301834266

```

Unless Im wrong....those look fine right?

---

### Post by kansasnoob on 2009-01-19
Hmmmm, that looks fine! So that's not the problem:confused:

---

### Post by Alfx on 2009-01-19
> **kansasnoob said:**
> Hmmmm, that looks fine! So that's not the problem:confused:

This is so confusing.

---

### Post by kansasnoob on 2009-01-19
I know you already posted a portion of it but would you please copy and paste the entire output of:

```
cat /boot/grub/menu.lst
```

I'm puzzled too.

---

### Post by Alfx on 2009-01-19
> **kansasnoob said:**
> I know you already posted a portion of it but would you please copy and paste the entire output of:

```
cat /boot/grub/menu.lst
```

I'm puzzled too.

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

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,4)/boot/grub/splashimages/appleblack.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 SECRET
# password SECRET
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
# kopt=root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet vga=795 splash

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f654c563-5451-448e-b747-7cd839b2a8d9 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
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

```

---

### Post by kansasnoob on 2009-01-19
OK! Now we're getting somewhere, but be patient, we want to check some other things!

You've added a "custom" usplash theme:

> #A splash image for the menu
splashimage=(hd0,4)/boot/grub/splashimages/appleblack.xpm.gz


But before we change anything in the menu list I want you to go to synaptic and type in Search: usplash.

Make sure you have the following packages installed:
libusplash0
usplash
usplash-theme-ubuntu

Also tell me what other packages (in the usplash category), besides startupmanager (which is OK), that you have installed!

---

### Post by stchman on 2009-01-19
You can install a splash screen manager through the repositories.

```
sudo apt-get -y install gnome-splashscreen-manager
```

This will allow you to install a login splash through an easy GUI.

If you are referring to the boot splash use StartUpManager

```
sudo apt-get -y install startupmanager
```

This will give you a GUI to control boot splash and other GRUB features.

---

### Post by Alfx on 2009-01-19
> **kansasnoob said:**
> OK! Now we're getting somewhere, but be patient, we want to check some other things!

You've added a "custom" usplash theme:



But before we change anything in the menu list I want you to go to synaptic and type in Search: usplash.

Make sure you have the following packages installed:
libusplash0
usplash
usplash-theme-ubuntu

Also tell me what other packages (in the usplash category), besides startupmanager (which is OK), that you have installed!

This is what I got

[[IMG]http://img176.imageshack.us/img176/1043/screenshothk2.png[/IMG]](http://imageshack.us)

---

### Post by kansasnoob on 2009-01-19
OK, do you see the two lines I'm talking about:

> # Pretty colours
#color cyan/blue white/blue

[B]#A splash image for the menu
splashimage=(hd0,4)/boot/grub/splashimages/appleblack.xpm.gz[/B]

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 SECRET
# password SECRET


I highlighted them in BOLD!

I want to be sure we're on the same page so to speak:)

Those are the only lines I see different from a default Ubuntu 8.10 menu list.

Proceed only if you're sure what I'm talking about!

Open the menu list with a text editor by:

```
sudo gedit /boot/grub/menu.lst
```

Then using your mouse highlight only those two lines of text and click on Cut, then click on Save, then go to File > Quit.

If when you restart you still don't have the default Ubuntu usplash go to synaptic and tick each of those three packages for re-installation and try restarting again.

---

### Post by Alfx on 2009-01-19
> **kansasnoob said:**
> OK, do you see the two lines I'm talking about:



I highlighted them in BOLD!

I want to be sure we're on the same page so to speak:)

Those are the only lines I see different from a default Ubuntu 8.10 menu list.

Proceed only if you're sure what I'm talking about!

Open the menu list with a text editor by:

```
sudo gedit /boot/grub/menu.lst
```

Then using your mouse highlight only those two lines of text and click on Cut, then click on Save, then go to File > Quit.

If when you restart you still don't have the default Ubuntu usplash go to synaptic and tick each of those three packages for re-installation and try restarting again.

I did all that and I made sure that the default usplash was selected in start-up manager.

Now I got the default one back, thanks alot!

---

