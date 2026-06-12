---
title: "Messed up Grub, need menu.lst for 8.10 64-bit"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-01-04
I installed OpenSolaris and of course it overwrote Ubuntu's Grub. However, I can't figure out how to mount my Ubuntu partition in OS, so I don't know what my entries look like to add to the OS grub menu. 

Could someone that is using Intrepid (I use 64-bit, but I don't know if it matters for menu.lst) that has the current kernel post /boot/grub/menu.lst?

Thanks a lot.

---

### Post by caljohnsmith on 2009-01-04
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Ubuntu.

---

### Post by bodhi.zazen on 2009-01-04
The entries in /boot/grub/menu.lst are all the same :

Title Ubuntu
root (hdx,y)
kernel /boot/vmlinuiz.xyz root=UUID=xxx.yyy.zzz ro quiet splash
initrd /boot/initrd.xyz
boot

See also :

        [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]


[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by jbrown96 on 2009-01-04
The problem is that I don't know the kernel number, and I don't know how OpenSolaris labels devices and whether there is even a package for reiserfs (I couldn't find one). I just need a copy of someone's menu.lst file.

---

### Post by LtPitt on 2009-01-04
Download and burn on cd a tool called SuperGrub.

It made my day =)

---

### Post by MaddMatt on 2009-01-04
How messed up is it? If you just f*d your menu.lst then you should be able to get all of the appropriate data to fill in the blanks from your /boot directory (where you will find your kernel). Then fill this info into the menu.lst using bodhi.zazen's instructions above. 

The thing is that everyone's menu.lst is a little different, so you will need to get the appropriate info for YOUR system. Whether you are using a scsi or ide drive will determine if it is sda,1 or hda,1 (a = first disk), etc. If you are dual booting then it might be sda,3 instead of 1, etc. 

You can get the UUID (all of those cryptic numbers) from this command: I suggest running it from a recovery disk or a live CD:

vol_id -u /dev/YOURPARTITION

Again, the menu.lst should look something like this:

title           Your title
root            GRUB-ROOT
kernel          /boot/vmlinuz-<your kernel version here> root=<your root partition UUID> ro
initrd          /initrd.img-<your kernel version here>
savedefault
boot

then run:
update-grub


Sorry that I can't be more specific but my menu.lst is set up for an encrypted hard disk, so unless you are running dm-crypt over LUKS, it will be useless to you.

---

### Post by boof1988 on 2009-01-04
If you still have a menu.lst but don't know the kernel number the following usually works since it uses the links to the actual (current) kernels.  You can check in / to make sure the links are there before using this.

```
title		Whatever Title
root		(hd0,0) # Use the partition (for (hd0,0)) where vmlinuz and initrd.img resides
kernel		/vmlinuz root=/dev/sda1 ro # Use the partition (for /dev/sda1) where vmlinuz and initrd.img resides
initrd		/initrd.img
```

This just saved my life on my server... It's a pain to disconnect and reconnect a monitor just to get the thing booted.

Hope this helps some.

EDIT:

You can even use (in Ubuntu liveCD)...

```
sudo grub
```

to get a grub prompt.  And then...

```
find /vmlinuz
find /initrd.img
```

to find the links.

Here's my menu.lst, if it helps... I actually copied it from a different os to my server because (for some reason) the menu.lst wasn't created when I installed GrUB (Lilo was the previous bootloader) on the server...

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
timeout		2

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

title		Ubuntu 8.04.1 Server
root		(hd0,0)
kernel		/vmlinuz root=/dev/sda1 ro
initrd		/initrd.img

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
# kopt=root=UUID=c944fa06-e7e4-400c-9654-3ffeb2b7502b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c944fa06-e7e4-400c-9654-3ffeb2b7502b

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
```

---

