---
title: "Help setting up grub for multiple OS's"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2009-01-10
I recently installed the windows 7 beta and windows XP, but I'm having trouble setting up my menu.lst file to allow XP to boot. 
[IMG]http://img70.imageshack.us/img70/2953/gpartedxn5.jpg[/IMG]
This is what Gparted looks like currently, with the first NTFS partition the 7 beta which currently boots fine, the 73 gb partition Ubuntu, (also boots fine) and the second NTFS is XP, which I can't figure out how to boot.

---

### Post by Bachstelze on 2009-01-10
> **Tsurugi13 said:**
> and the second NTFS is XP, which I can't figure out how to boot.

How on Earth did that XP make its way to a Logical partition? I don't think GRUB will be able to boot it.

---

### Post by Tsurugi13 on 2009-01-10
I shrunk up Ubuntu's partition to make room for it, and it didn't seem to have any trouble running or booting with the windows bootloader.

---

### Post by Bachstelze on 2009-01-10
> **Tsurugi13 said:**
> I shrunk up Ubuntu's partition to make room for it, and it didn't seem to have any trouble running or booting **with the windows bootloader**.

That's the keypoint. With GRUB, I don't think it will work. You'll have to move it to a Primary partition.

*EDIT: actually, since your other Windows is on a Primary, you should be able to configure its bootloader to boot your XP. But I don't think you'll find how to do that here.*

---

### Post by Tsurugi13 on 2009-01-10
I don't actually know how to do that... is it possible without reinstalling XP?

---

### Post by Bachstelze on 2009-01-10
See the EDIT, there might actually be a way. Shall I move your thread to Windows Discussion, where more people might know how to help you?

---

### Post by unutbu on 2009-01-10
I believe it is possible to boot Windows from a logical partition:
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

You can skip steps 1,2,3 and jump to steps 4 and 5 because at this point there is no evidence that you're are missing ntldr, or any other windows file.

---

### Post by Bachstelze on 2009-01-10
> **unutbu said:**
> I believe it is possible to boot Windows from a logical partition:
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

This looks like a dirty hack, and I wouldn't recommend it.

---

### Post by kansasnoob on 2009-01-10
> **Tsurugi13 said:**
> I recently installed the windows 7 beta and windows XP, but I'm having trouble setting up my menu.lst file to allow XP to boot. 
[IMG]http://img70.imageshack.us/img70/2953/gpartedxn5.jpg[/IMG]
This is what Gparted looks like currently, with the first NTFS partition the 7 beta which currently boots fine, the 73 gb partition Ubuntu, (also boots fine) and the second NTFS is XP, which I can't figure out how to boot.

Well first of all post the full output of:

```
cat /boot/grub/menu.lst
```

And verify what you can and can not boot! I'm assuming that you can boot the new Win and Ubuntu, but not XP????

Do you even get the GRUB menu when you boot and what does it show?

---

### Post by Tsurugi13 on 2009-01-10
Yeah, I'm going to stick with moving it. Can I move it without reinstalling it? That'd be nice.

---

### Post by Bachstelze on 2009-01-10
> **kansasnoob said:**
> Well first of all post the full output of:

```
cat /boot/grub/menu.lst
```

And verify what you can and can not boot! I'm assuming that you can boot the new Win and Ubuntu, but not XP????

Do you even get the GRUB menu when you boot and what does it show?

Please read the messages before you answer to them. Thank you.

---

### Post by kansasnoob on 2009-01-10
> **unutbu said:**
> I believe it is possible to boot Windows from a logical partition:
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

This is absolutely correct!

I've seen caljohnsmith and meierfra do it!

And I was recently scolded for NOT showing enough faith in Unutbu's capabilities by meierfra!

'Nuff said. Listen to Unutbu!

---

### Post by kansasnoob on 2009-01-10
> **HymnToLife said:**
> Please read the messages before you answer to them. Thank you.

I did! What's the problem with asking for more info or verifying info?

---

### Post by Tsurugi13 on 2009-01-10
XP is the only one that doesn't boot, as explained in the first post, all I really want to know now is can I move it out of the logical partition without reinstalling it, and how should menu.lst be changed to accommodate for that.

---

### Post by Tsurugi13 on 2009-01-10
XP is the only one that doesn't boot, as explained in the first post, all I really want to know now is can I move it out of the logical partition without reinstalling it, and how should menu.lst be changed to accommodate for that.

---

### Post by kansasnoob on 2009-01-10
> **Tsurugi13 said:**
> Yeah, I'm going to stick with moving it. Can I move it without reinstalling it? That'd be nice.

The only way I'm aware of is using partimage and an external drive.

That doesn't mean there is no other way, just that I don't know another way.

---

### Post by Tsurugi13 on 2009-01-10
I'm fine with reinstalling if necessary, I'd just rather not. In any case, how would I go about this?

---

### Post by Bachstelze on 2009-01-10
As I said in post #4, it might be possible to modify the bootloader of your other Windows so in can boot XP from the logical partition. But since it involves modifying the Windows bootloader, I don't think many people here can help you. Would you want me to move your thread to Windows Discussions?

---

### Post by kansasnoob on 2009-01-10
I'd still like to see the output (from terminal in Ubuntu) of:

```
cat /boot/grub/menu.lst
```

BTW, that's a lower case L, not a "one".

We may or may not be able to do this simple!

---

### Post by Bachstelze on 2009-01-10
> **kansasnoob said:**
> I'd still like to see the output (from terminal in Ubuntu) of:

```
cat /boot/grub/menu.lst
```

BTW, that's a lower case L, not a "one".

We may or may not be able to do this simple!

No, we won't be able to do it "simple".

---

### Post by Tsurugi13 on 2009-01-10
> **HymnToLife said:**
> As I said in post #4, it might be possible to modify the bootloader of your other Windows so in can boot XP from the logical partition. But since it involves modifying the Windows bootloader, I don't think many people here can help you. Would you want me to move your thread to Windows Discussions?

If you think it'd help, sure. I don't actually have anything on XP, it's just that I'd rather not have to fix grub yet again after reinstalling it, so it's not absolutely necessary that I keep the install, It'd just save an hour or so.

---

### Post by bodhi.zazen on 2009-01-10
:lolflag:

I agree we need to see menu.lst

My "Guess" is we may need to either :

1. Mark the windows partition(s) as bootable (not sure on that).

2. When you have more then 1 version of windows installed you often have to "hide" them.

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)

---

### Post by Bachstelze on 2009-01-10
This does not work with Vista, so I don't think it will work with 7 either...

---

### Post by kansasnoob on 2009-01-10
Well, I have no more to add.

I refuse to participate in a screaming match where one party refuses to consider alternatives!

---

### Post by Tsurugi13 on 2009-01-11
So I decided to take the plunge and reinstall XP, outside of the logical partition this time. Here's the Gparted screen:
[IMG]http://img61.imageshack.us/img61/4008/gparted2py5.jpg[/IMG]
And here's my menu.lst:

> # menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=967eefd2-957d-4a77-8969-ce034afe76e7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=967eefd2-957d-4a77-8969-ce034afe76e7

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
uuid		967eefd2-957d-4a77-8969-ce034afe76e7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=967eefd2-957d-4a77-8969-ce034afe76e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		967eefd2-957d-4a77-8969-ce034afe76e7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=967eefd2-957d-4a77-8969-ce034afe76e7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		967eefd2-957d-4a77-8969-ce034afe76e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=967eefd2-957d-4a77-8969-ce034afe76e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		967eefd2-957d-4a77-8969-ce034afe76e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=967eefd2-957d-4a77-8969-ce034afe76e7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		967eefd2-957d-4a77-8969-ce034afe76e7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 Beta
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Sorry for the longnessitude, I wasn't sure what would be ok to leave out, so I left everything in.

EDIT: Had to add spaces in the (8 )'s at the top, the forum thought they were smilies.

---

### Post by Tsurugi13 on 2009-01-11
Just by tinkering I got something to happen by adding:

> title Microsoft Windows XP
root (hd0,2)
savedefault
makeactive
chainloader +1 
To the end of menu.lst, but now when I try to boot it I get a message saying that 


NTLDR is missing
Press Ctrl Alt Del to Restart

And that's it. :confused:

---

### Post by bodhi.zazen on 2009-01-11
> **Tsurugi13 said:**
> EDIT: Had to add spaces in the (8 )'s at the top, the forum thought they were smilies.

Yes [noparse]8)[/noparse] is a 8)

In the future use 

[noparse][noparse]8)[/noparse][/noparse]

use the noparse for a block of code :

[noparse][noparse]block of code[/noparse][/noparse]

to disable smiles in the entire block (rather then one at a time)

Back on topic - What OS are you having problems with ? Looking at your screen shot of gparted both ntfs appear to be primary partitions and both appear to be empty.

---

