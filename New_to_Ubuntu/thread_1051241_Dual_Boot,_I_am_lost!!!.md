---
title: "Dual Boot, I am lost!!!"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Synt4xError on 2009-01-26
Hello, I hope you are all well.

So I am having a problem right now, I know for a fact I didn't loose any data but I just need some guidance.

I have 2 250GB HDs in my computer. I have windows 64bit on one and I have ubuntu 64bit on the other. I had windows installed first and then had ubuntu installed.

How the heck do I get the dual boot opitions on start-up ? Ubuntu took over the boot sequence and now I can't even get into windows.


Does anyone have a fix to this? 

Please! Hehe thanks for your time in advanced!

---

### Post by ugm6hr on 2009-01-26
> **Synt4xError said:**
> So I am having a problem right now, I know for a fact I didn't loose any data but I just need some guidance.

How do you know this?

Boot into Ubuntu, and post the result of the following command:

```
sudo fdisk -l
```

---

### Post by Synt4xError on 2009-01-26
I can still browse my Windows Folders.

Here is the output:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e835

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29157   234203571   83  Linux
/dev/sda2           29158       30394     9936202+   5  Extended
/dev/sda5           29158       30394     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13271326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+   7  HPFS/NTFS

---

### Post by ugm6hr on 2009-01-26
It looks like sdb is your Windows HD, and sda Ubuntu.

Post:

```
cat /boot/grub/menu.lst
```

---

### Post by Synt4xError on 2009-01-26
synt4x@synt4x-desktop:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory

---

### Post by Synt4xError on 2009-01-26
> **Synt4xError said:**
> synt4x@synt4x-desktop:~$ cat /boot/grub/menu.list
cat: /boot/grub/menu.list: No such file or directory

Whoops, haha. You want all of the output?

---

### Post by ugm6hr on 2009-01-26
> **Synt4xError said:**
> Whoops, haha. You want all of the output?

menu.lst (not list)

And yes - post using the [CODE] # symbol as I posted the commands above.

---

### Post by Synt4xError on 2009-01-26
```
synt4x@synt4x-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=67392fa3-9006-4572-9b1c-49a6a3e7caae

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by ugm6hr on 2009-01-26
Backup your current menu.lst first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
```

Then edit it:
```
gksudo gedit /boot/grub/menu.lst
```

This will open the same file you just posted above.

At the very bottom of this, paste the following:
```
# on /dev/sdb1
title        Windows 
root        (hd1,0)
savedefault
makeactive
chainloader    +1

```

You should also put a # symbol in front of the line (near the top) that says "hiddenmenu" to make it "# hiddenmenu"

Then try rebooting.

---

### Post by Synt4xError on 2009-01-26
I appreciate your help. Let me re-boot, I will let you know what happens,

---

### Post by Synt4xError on 2009-01-26
Ok so I see an option now with like 5 linux options and a windows options at the bottum.

But it will not let me select which to boot from, I can't choose anything, it only loads the selected linux format.

Any ideas?

---

### Post by Muffinabus on 2009-01-26
> **Synt4xError said:**
> Ok so I see an option now with like 5 linux options and a windows options at the bottum.

But it will not let me select which to boot from, I can't choose anything, it only loads the selected linux format.

Any ideas?

Your keyboard doesn't work in GRUB?  Hitting the up or down arrows doesn't do anything?  Do you have a USB keyboard or PS/2?

---

### Post by Synt4xError on 2009-01-26
haha, what's funny is that it does give me a keyboard failure, but it works once OS is loaded. I guess I didn't think of that.


It is a USB keyboard. Should I change ports while starting? That has helped before? So is that my only problem?

---

### Post by Muffinabus on 2009-01-26
> **Synt4xError said:**
> haha, what's funny is that it does give me a keyboard failure, but it works once OS is loaded. I guess I didn't think of that.


It is a USB keyboard. Should I change ports while starting? That has helped before? So is that my only problem?

Yeah, I'd try changing USB ports or doing whatever you do to get it working, heh.  That should be your only problem, for now at least.

---

### Post by Synt4xError on 2009-01-26
Muffianbus and ugm6hr, I want to thank you both very much for your assistance. If I have any further problems i will post them here.

Have a great rest of the week!

---

### Post by kansasnoob on 2009-01-26
I think this:

> # on /dev/sdb1
title        Windows 
root        (hd1,0)
savedefault
makeactive
chainloader    +1

Should be this:

> # on /dev/sdb1
title        Windows
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

But it sounds like you also have a problem with BIOS recognizing your USB keyboard and/or mouse.

---

### Post by Synt4xError on 2009-01-26
Yeah I have had problems with keyboard failure for a while, I even flashed the BIOS, used a different keyboard. It happens randomly, I don't know why. It now always says it ever since I installed Ubuntu. 

So are you sure I should change the above text? reason why I ask is because you said "I think", just making sure :)

---

### Post by Muffinabus on 2009-01-26
> **Synt4xError said:**
> Yeah I have had problems with keyboard failure for a while, I even flashed the BIOS, used a different keyboard. It happens randomly, I don't know why. It now always says it ever since I installed Ubuntu. 

So are you sure I should change the above text? reason why I ask is because you said "I think", just making sure :)

That's what my menu.lst looks like, actually.  My Ubuntu drive is Primary Master with Windows set to it's slave, and it works perfectly.

---

### Post by ugm6hr on 2009-01-26
> **Muffinabus said:**
> That's what my menu.lst looks like, actually.  My Ubuntu drive is Primary Master with Windows set to it's slave, and it works perfectly.

Have to admit - I have never installed with 2 HDs - so they are probably correct.

---

### Post by Synt4xError on 2009-01-26
> **Muffinabus said:**
> That's what my menu.lst looks like, actually.  My Ubuntu drive is Primary Master with Windows set to it's slave, and it works perfectly.

Now is there a way I can make it only show 2 options in the boot section. I want just 1 Ubuntu option and the windows option.

I have this:

```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=67392fa3-9006-4572-9b1c-49a6a3e7caae ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		67392fa3-9006-4572-9b1c-49a6a3e7caae
kernel		/boot/memtest86+.bin
quiet

# on /dev/sdb1
title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

```

---

### Post by Jack Shankle on 2009-01-26
try the neosmart forum.

---

### Post by Muffinabus on 2009-01-26
> **Synt4xError said:**
> Now is there a way I can make it only show 2 options in the boot section. I want just 1 Ubuntu option and the windows option.

I have this:


The other options are there for recovery purposes and are actually best left alone in case something does go wrong and you do need to use the others to boot.

---

### Post by Synt4xError on 2009-01-26
ok cool, thanks all!

---

### Post by Synt4xError on 2009-01-26
ACTUALLY I have one more thing, how can I fix this USB keyboard problem? I stated what i have done before with this. 

Any other ideas?

---

