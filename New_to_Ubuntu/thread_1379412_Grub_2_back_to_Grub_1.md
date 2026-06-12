---
title: "Grub 2 back to Grub 1"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by dojida on 2010-01-12
Is it possible to revert to grub1 as I am not getting on with 2? I can't change the boot order using the terminal or the gui. Using the old grub manager there were I think 4 or 5 tabs, one of them being a simple way to change the grub order, but with the new version there are only 3 tabs, without the change the loading sequence. And if I use the terminal (sudo gedit /boot/grub/menu.lst) and then set the default to the number I want, it seems to accept the change but does not work at the reboot. If I look at .lst again the new setting is still there, but does not work. I have used this method with 8.10 successfully in the past with no problems. I have read the grub how to in these forums, but it seems that grub2 is not as functional as grub1 was in this respect.
Sorry, I should have changed my details to 9.10 on the left.

---

### Post by chaanakya_chiraag on 2010-01-12
If you have grub2, then you shouldn't have a menu.lst.  Instead, you should have a grub.cfg **that you do not edit by hand**  Also, try running ```
sudo update-grub2
```

---

### Post by chaanakya_chiraag on 2010-01-12
See this link for more info about Grub2:[URL="http://ubuntuforums.org/showthread.php?p=8191211#post8191211"]
http://ubuntuforums.org/showthread.php?p=8191211#post8191211[/URL]

---

### Post by drs305 on 2010-01-12
You can change which item is the default in Grub 2 by following the instructions in this link:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

Grub 2 is different than Grub legacy. You can learn more about it from the link provided in the previous post, or clicking on the GRUB2 or G-Basics links in my signature line.

When you discuss the 'tabs', etc, you are probably referring to "Startup-Manager". It is a great app that simplified making changes to Grub. Hopefully at some point there will be a similar app that will do the same things for Grub 2, but for now you need to do it manually.

Grub 2 is going to become the default, so at some point you will have to learn it. If you would prefer to wait, you can revert to Grub legacy by following the instructions here:
[https://help.ubuntu.com/community/Grub2#Uninstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

---

### Post by dojida on 2010-01-12
Thanks for the replies, I have been reading the post about reinstalling grub and removing grub2 and it looks a bit scary with my limited knowledge. However there is a lot of useful information in the links which will take me some time to look through, so I will probably be reading through it for the rest of tonight. Your advice is much appreciated.

---

### Post by kansasnoob on 2010-01-12
Is this helpful:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by dojida on 2010-01-13
> **chaanakya_chiraag said:**
> If you have grub2, then you shouldn't have a menu.lst.  Instead, you should have a grub.cfg **that you do not edit by hand**  Also, try running ```
sudo update-grub2
```

Sorry I've been so long, I have been reading all the links (in between the small matter of going to work). Thanks again for all your responses

I tried running sudo update-grub2, but got command not found.

I then checked which version of grub I've got and it is v1.97, which I believe is grub2.

I am now going to try sudo grub-mkconfig and see what happens.

---

### Post by dojida on 2010-01-13
I am now going to try sudo grub-mkconfig and see what happens.[/QUOTE]

The above command caused a lot of action in the terminal, but when I tried a restart, grub still loads Ubuntu first. I'm trying to load Vista first. I checked back in StartUp-Manager and Vista is the default operating system. The tutorials recommend using StartUp-Manager as the best option to change the boot order, yet it doesn't appear to work in this case. The other options appear to be quite complicated and full of warnings about possible loss of grub, so I am reluctant to try another method. I found grub to be much easier to use to change the boot order, which I managed successfully many times.

---

### Post by drs305 on 2010-01-13
In Grub 2, you can set the default via command line rather than editing the /etc/default/grub.

Here is a simple way of doing it from the command line, **but you have to have /etc/default/grub's DEFAULT= set to [COLOR="DarkRed"]saved[/COLOR]** (DEFAULT=saved):
Open a terminal.
```

grep "menuentry" /boot/grub/grub.cfg

```
Count which "menuentry" is Windows, subtract 1. Example: If Windows is the fourth entry, remember "3".
Now run this, with X being the number you came up with (Windows -1):
```

sudo grub-set-default **[COLOR="DarkRed"]X[/COLOR]**
sudo update-grub

```
Done.

---

### Post by tom.swartz07 on 2010-01-13
> **drs305 said:**
> In Grub 2, you can set the default via command line rather than editing the /etc/default/grub.

Here is a simple way of doing it from the command line:
Open a terminal.
```

grep "menuentry" /boot/grub/grub.cfg

```
Count which "menuentry" is Windows, subtract 1. Example: If Windows is the fourth entry, remember "3".
Now run this, with X being the number you came up with (Windows -1):
```

sudo grub-set-default **[COLOR="DarkRed"]X[/COLOR]**
sudo update-grub

```
Done.

+1
Thats the easiest way Ive seen.




Just as a thought- perhaps with the new Ubuntu Guide coming out, we could re-organize the forums here. Everyone seems to have their own 'special guides' and are very knowledgeable about certain aspects. Perhaps we could shuffle things around so that one doesnt have to dig into peoples signatures for helpful guides- we could just make an area of the forums for how-to's, and feature it here on the Beginners board.


Just a thought. Ill cc this to the Community Cafe also.

---

### Post by dojida on 2010-01-13
[QUOTE=drs305;8653803]You can change which item is the default in Grub 2 by following the instructions in this link:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

I tried the instructions in option 2 of your post drs305, but again it seems to accept the change in the terminal, but does not work on reboot.

---

### Post by dojida on 2010-01-13
> **drs305 said:**
> In Grub 2, you can set the default via command line rather than editing the /etc/default/grub.

Here is a simple way of doing it from the command line:
Open a terminal.
```

grep "menuentry" /boot/grub/grub.cfg

```
Count which "menuentry" is Windows, subtract 1. Example: If Windows is the fourth entry, remember "3".
Now run this, with X being the number you came up with (Windows -1):
```

sudo grub-set-default **[COLOR="DarkRed"]X[/COLOR]**
sudo update-grub

```
Done.
I just tried sudo grub-set-default 8 (where Vista sits) 
and get Searching for GRUB installation directory ... found: /boot/grub
..then input sudo update-grub
got a load of action on the terminal ending:
Found GRUB 2 /boot/grub/core.img
Found kernel: boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I am just about to restart and try it out (I thought there was no menu.lst with grub2

---

### Post by dojida on 2010-01-13
Still no joy, Ubuntu loads first. I can't understand it.

---

### Post by drs305 on 2010-01-13
> **dojida said:**
> Still no joy, Ubuntu loads first. I can't understand it.

I take the blame for your latest failure. In the post I omitted that /etc/default/grub must have "GRUB_DEFAULT=saved" for the command to stick. If DEFAULT is set to a number, the command won't work unfortunately.

---

### Post by dojida on 2010-01-13
How do I make "Default=saved

---

### Post by drs305 on 2010-01-13
> **dojida said:**
> How do I make "Default=saved

If your current /etc/default/grub GRUB_DEFAULT is "0", you can simply run this:
```

sudo sed 's/GRUB_DEFAULT="0"/GRUB_DEFAULT="saved"/g' -i /etc/default/grub
sudo grub-set-default [COLOR="DarkRed"]**X**[/COLOR]
sudo update-grub

```

If you aren't sure what it is set to (**I"d recommend this**). Let's keep it simple:
```

gksudo gedit /etc/default/grub &

```
Change the line:
> 
GRUB_DEFAULT="0"
to
GRUB_DEFAULT="X"

With X being the correct number.
Save the file, then run 
```

sudo update-grub

```

---

### Post by dojida on 2010-01-13
Still no joy, it's almost as if there are 2 grubs and one takes the commands while the other just does the loading. Is that possible?

---

### Post by drs305 on 2010-01-13
> **dojida said:**
> Still no joy, it's almost as if there are 2 grubs and one takes the commands while the other just does the loading. Is that possible?

Yes, it is possible you aren't making the changes in the correct place. And you always must run "sudo update-grub" for the changes to take effect. thought that we had asked for you to post the results of the boot info script, but that must have been another thread I was on. Please go to this post, follow the instructions and post the results here:
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by dojida on 2010-01-13
I have been running "sudo update-grub" after every change. I tried downloading boot info script, but it didn't work first time. Unfortunately my daughter has been hassling me for the laptop so she can "talk" to her friends on facebook or whatever, so I'll have to call it a day today. I'll try again tomorrow. Thanks again for your time.

---

### Post by kansasnoob on 2010-01-13
Look at post #6 again!

Click on the link!

---

### Post by dojida on 2010-01-13
Sorry kansasnoob, I did look at post #6, and will try it out if I can't get grub2 working. Will try again tomorrow.

---

### Post by dojida on 2010-01-14
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ed962e5

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   254,451,711   233,969,664   7 HPFS/NTFS
/dev/sda3         254,451,712   376,105,083   121,653,372   7 HPFS/NTFS
/dev/sda4         376,113,780   488,392,064   112,278,285   5 Extended
/dev/sda5         376,113,843   483,717,149   107,603,307  83 Linux
/dev/sda6         483,717,213   488,392,064     4,674,852  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="EAEE-EB49" TYPE="vfat" 
/dev/sda2: UUID="1E5A005C5A003357" LABEL="Acer" TYPE="ntfs" 
/dev/sda3: UUID="248EA4118EA3D996" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="608787b6-43be-4974-986e-5ea380beae15" TYPE="ext4" 
/dev/sda6: UUID="fb6fa0f9-3c9d-4c0e-bdc8-39880e0ddfc2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/helen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=helen)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default		7

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
# kopt=root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=608787b6-43be-4974-986e-5ea380beae15

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		608787b6-43be-4974-986e-5ea380beae15
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 608787b6-43be-4974-986e-5ea380beae15
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 608787b6-43be-4974-986e-5ea380beae15
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 608787b6-43be-4974-986e-5ea380beae15
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 608787b6-43be-4974-986e-5ea380beae15
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 608787b6-43be-4974-986e-5ea380beae15
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=608787b6-43be-4974-986e-5ea380beae15 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set eaee-eb49
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 1e5a005c5a003357
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=608787b6-43be-4974-986e-5ea380beae15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fb6fa0f9-3c9d-4c0e-bdc8-39880e0ddfc2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 192.5GB: boot/grub/core.img
 192.5GB: boot/grub/grub.cfg
 192.5GB: boot/grub/menu.lst
 192.5GB: boot/initrd.img-2.6.31-14-generic
 192.5GB: boot/initrd.img-2.6.31-15-generic
 192.5GB: boot/initrd.img-2.6.31-16-generic
 192.5GB: boot/initrd.img-2.6.31-17-generic
 192.5GB: boot/vmlinuz-2.6.31-14-generic
 192.5GB: boot/vmlinuz-2.6.31-15-generic
 192.5GB: boot/vmlinuz-2.6.31-16-generic
 192.5GB: boot/vmlinuz-2.6.31-17-generic
 192.5GB: initrd.img
 192.5GB: initrd.img.old
 192.5GB: vmlinuz
 192.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
Hi, just a quick update before I have to go back to work. The above is the results from Boot Info Script. I made an error earlier and counted Vista as 8th in line rather than 7, but have updated grub with the correct info since, with no success.
Will log in again in a few hours. Sorry for posting such a long message, but I didn't think I should delete any of it in case it may be of help.

---

### Post by dojida on 2010-01-14
Problem solved! I suspected that grub legacy was causing it and so with drs305's help I was able to back up the grub- related folders, uninstalled grub, grub-pc and grub-common, and then reinstalled grub-pc and grub-common. I still don't know how grub legacy came to be on the system or why all the changes were being written to it and not to grub2, but that's for another time. Thanks to everyone who responded to my thread, it's good to know theres such good support out there.

---

### Post by dbrowdy on 2010-01-16
Wait, I'm having the SAME EXACT problem!  Can you please go into more detail on how you fixed this?

- What directories did you back up?
- Were there any configurations that had to be done after reinstalling those packages?

Honestly, this is an almost completely stock install of Ubuntu.  I have no idea how it could have gotten borked already.

---

### Post by drs305 on 2010-01-16
> **dbrowdy said:**
> Wait, I'm having the SAME EXACT problem!  Can you please go into more detail on how you fixed this?

- What directories did you back up?
- Were there any configurations that had to be done after reinstalling those packages?

Honestly, this is an almost completely stock install of Ubuntu.  I have no idea how it could have gotten borked already.

dbrowdy,

We had tried numerous other things in another venue that aren't documented above. Completely removing and reinstalling Grub 2 should not be necessary in most cases. However, nothing we had tried had worked, so we decided to completely remove and reinstall Grub 2. This should not be considered a standard way to fix Grub 2 problems.

I had him back up the  /boot/grub and /etc/grub.d folders to his Desktop, just as a precaution and to be able to refer to them later if we needed to retrieve some settings from them. It wouldn't normally be necessary to do this.

He then removed all traces of grub and grub-pc (Grub 2) with the following commands:
```

sudo apt-get purge grub grub-pc grub-common

```
During the running of this command, Ubuntu will warn you that if you don't install a bootloader you won't be able to boot.
Next, reinstall Grub 2. X is the drive designation - a for the first drive, b for the second, etc. The third command shouldn't be necessary but I do it anyway:
```

sudo apt-get install grub-common grub-pc
sudo grub-install /dev/sdX
sudo update-grub

```

Before rebooting, check to make sure the default menuentry in  /boot/grub/grub.cfg looks correct: correct UUIDs, kernel, etc. Then reboot.

---

### Post by dbrowdy on 2010-01-16
Thanks a lot for the quick response.  I'll give this a shot.  

> **drs305 said:**
> 
Next, reinstall Grub 2. X is the drive designation - a for the first drive, b for the second, etc.

Is there somewhere I can quickly check which drive my current installation is on?  My current grub.cfg maybe...

EDIT - Oh wait, I only have one HDD.  I have multiple partitions though.  My bootable is sda1, my /boot is sda3.  Do I use just sda?

---

### Post by drs305 on 2010-01-16
EDIT:  Use "sda".

You can use this command to see your partitions:
```

mount

```

Your Linux partition should look something like this:
> 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)

The type could be "ext3".  In the above, you would look for "**/**" and then use the correct **sdX**, in this case "sd**a**".

---

### Post by dbrowdy on 2010-01-16
Okay cool everything reinstalled fine.  And it works great when I set the default to 8 (my Windows selection).  For some reason setting it to "saved" (tried with and without quotes) doesn't remember my last selection.  I'll look for help on that issue separately so as not to derail this thread.  

Thanks for all your help!

---

### Post by drs305 on 2010-01-16
> **dbrowdy said:**
> Okay cool everything reinstalled fine.  And it works great when I set the default to 8 (my Windows selection).  For some reason setting it to "saved" (tried with and without quotes) doesn't remember my last selection.  I'll look for help on that issue separately so as not to derail this thread.  

Thanks for all your help!

Glad you got it working again.

You don't have to respond, but did you update grub after changing it to "saved" and then reboot? It will only start saving after the next boot I believe - i.e. it wouldn't save the boot you are currently in.

---

