---
title: "faron45's  menu.lst file"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by faron45 on 2009-05-13
When I enter this into a terminal...   gksudo mousepad /boot/grub/menu.lst

I get this opening up in mousepad...

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
# kopt=root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by spcwingo on 2009-05-13
Boy, that's a lot of kernels.  :)  Other than that, it simply did what you told it to do.

---

### Post by MontelEdwards on 2009-05-13
Damn. Uh, that is a lot. 
Have you looked at upgrading from 8.04?

---

### Post by Didius Falco on 2009-05-13
Faron,

You forgot to put the code tags around it, so I'll just post the entry that  needs to be changed. copy/paste this over the same part of the menu.lst file:

```
## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0751556e-f70f-4820-a20a-129bb5725deb ro 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet
```

Regards,

Didius

---

### Post by faron45 on 2009-05-13
Okay,I'm sorry.I'm just as confused as hell now.I just don't understand where I'm actually supposed to copy/paste this.Somewhere inside the mousepad that's open with all that info in it somewhere ? Argh !

---

### Post by Didius Falco on 2009-05-13
Just scroll down until you see the line that says ```
## ## End Default Options ##
```

then copy/paste the part I posted from there to where is says "quiet" in that first little block. Either that or just delete the two words "quiet" and "'splash" from the end of the line that starts with "kernel" - just that first block.

Regards,

Didius

---

### Post by faron45 on 2009-05-13
Thank you,thank you,thank you.Girlfriend helped me to figure it out also.So,what you're saying is [there are #'s in each block.Up to # 24.And,each of these blocks say generic or generic recovery mode] to delete block # 24 [or just copy & paste over the top of it.OR,to just delete the words quiet & splash from block #24] & then "save" what I've just done ?

---

### Post by Didius Falco on 2009-05-13
I'm not sure what you mean by block 24. Look for the part that says "## ## End Default Options ##"

Right under that is a little block of lines that start with "title" "root" "kernel" "initd" and "quiet".

The line you want to edit is the line that starts with "kernel" - just the one in that first block. At the end of that line, you'll see the words "quiet" and "splash".

Just edit those two words out and then save the file.

That will give you no graphics logo and a lot more text output and give you a much better chance to see any errors so you can write them the down to check on.

Since it's just an annoyance and not something that is keeping your PC from running, you can take your time and catch the errors over a series of shutdowns.

Regards,

Didius

---

### Post by faron45 on 2009-05-13
Okay,going for a shutdown to try it out now.Thanks again for all your help.

---

### Post by Didius Falco on 2009-05-13
My pleasure!

Didius

---

### Post by faron45 on 2009-05-13
Okay,well,that didn't work at all.Darn ! Now,I get extra text.But,it still just flys by so fast there's just no possible way of ever making heads or tails out of it & instead of doing it upon shut down,it's doing it on start up ! Hmph !! I give up !

 I am now going to throw this cmputer through the window.Thank you very much ! Hmph ! Just kiddingh.

---

### Post by Didius Falco on 2009-05-14
> **faron45 said:**
> Okay,well,that didn't work at all.Darn ! Now,I get extra text.But,it still just flys by so fast there's just no possible way of ever making heads or tails out of it & instead of doing it upon shut down,it's doing it on start up ! Hmph !! I give up !

 I am now going to throw this cmputer through the window.Thank you very much ! Hmph ! Just kiddingh.

Let's get your pretty graphics back for you: Just open menu.lst again and add the words "quiet" and "splash" back to the end of the first kernel line.

That'll get you back where you started.

Regards,

Didius

---

