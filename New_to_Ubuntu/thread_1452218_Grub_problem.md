---
title: "Grub problem"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by itsvan on 2010-04-11
HI so i had Ubuntu installed,,,i install Windows 7,,and now for some reason,,the grub menu will not boot up,,it loads directly into windows,,how can i change that?? i made sure that the ubuntu partition wasnt touched,,,does this mean i messed up? and now its gone?i need to boot back into ubuntu,,any ideas????:(

---

### Post by perham on 2010-04-11
please do a google search first, before starting a thread.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tom.swartz07 on 2010-04-11
> **itsvan said:**
> HI so i had Ubuntu installed,,,i install Windows 7,,and now for some reason,,the grub menu will not boot up,,it loads directly into windows,,how can i change that?? i made sure that the ubuntu partition wasnt touched,,,does this mean i messed up? and now its gone?i need to boot back into ubuntu,,any ideas????:(

Nope, all it means is that freaking Windows 7 over-wrote your Bootloader. Hit the GRUB2 link in my signature to see how to reinstall your bootloader for GRUB.

---

### Post by oldfred on 2010-04-11
Just be sure to use the correct instructions for your version of grub. Grub legacy is 0.97 and grub2 with Karmic is 1.97 beta4, Lucid will be 1.98.

The above links should be all you need.
Same instructions here:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by itsvan on 2010-04-12
OK so i kinda get what to do,,ut how do i know which grub version i need?:confused:

---

### Post by tom.swartz07 on 2010-04-12
> **itsvan said:**
> OK so i kinda get what to do,,ut how do i know which grub version i need?:confused:

What version of Ubuntu did you install?

Anything before 9.10 is Grub Legacy, the old one.

9.10 or after is Grub 2.

I think the link above me has info on grub legacy. My link covers Grub 2

---

### Post by ranch hand on 2010-04-12
To know the version of grub you have run;
```

grub-install -v

```

---

### Post by philinux on 2010-04-12
If ranch hands command tell you this ,grub-install (GNU GRUB 1.97~beta4),
its grub 2 and you need this.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by wme on 2010-04-12
well i have a  grub propblem  too i got the  black  screen of death on my ubuntu 9.10
i booted up normal and then it  makes the  drum sound  the mouse just  shows up but the screen is  black 
i know i can go t o grub menu on  boot and  change to recovery but it wont work ive tries loading and  pushing esc but nothing it goes straight  load and   dark screen comes back ??? can anyone help me :confused:
i need to   be  able to get to grub menu .....

---

### Post by ranch hand on 2010-04-12
If you are using the newer version of grub try the shift button as it will work better.

---

### Post by philinux on 2010-04-12
> **wme said:**
> well i have a  grub propblem  too i got the  black  screen of death on my ubuntu 9.10
i booted up normal and then it  makes the  drum sound  the mouse just  shows up but the screen is  black 
i know i can go t o grub menu on  boot and  change to recovery but it wont work ive tries loading and  pushing esc but nothing it goes straight  load and   dark screen comes back ??? can anyone help me :confused:
i need to   be  able to get to grub menu .....

Please start your own threads please as it can get very confusing for the Original Poster. Your problem is very different.

---

### Post by UbuNewbie1 on 2010-04-12
I've installed Ubuntu 9.10 and 10.04 about 7 times in the last 24 hours.

I have an AMD 64 PC running Windows 7 Ultimate 64 & decided to try a grown up operating system for a change.

After installing Ubuntu (dual boot) with Win 7, every time I boot into Win 7 grub goes awol & I get endless restarts instead of the OS list to choose from.

I'm running 10.04 from the CD at the moment.

Any help will be greatly appreciated, I've already lost far too much of my life re-installing this OS over and over again instead of learning how to use it.

---

### Post by ranch hand on 2010-04-12
I good place to start would be to learn to start your very own threads and give details on your box (no one is going to look up your box when you could give the info in the first place).

There are 4 stickies at the top of the ABT forum.  Read them, at least the first post.

There is a link in my sig for basic info on grub.  There are several links and the second one is the best in depth info on grub anywhere.

---

### Post by itsvan on 2010-04-12
Ok so do i use TERMINAL in the Live boot disc menu??? OR  do i boot into Ubuntu with the disc and Then use terminal through that???

---

### Post by tom.swartz07 on 2010-04-12
> **itsvan said:**
> Ok so do i use TERMINAL in the Live boot disc menu??? OR  do i boot into Ubuntu with the disc and Then use terminal through that???

You boot into the LiveCD and then use the terminal from there.

---

### Post by itsvan on 2010-04-13
This is my output,if someone whould help me to chose how exactly to mount it,i need Windows and linux to be on the grub menu..ive read the guide but im stil uncertain and i dont want to mess anything up...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x843d9350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12913   103723641    7  HPFS/NTFS
/dev/sda2           19454       19457       32130   ef  EFI (FAT-12/16/32)
/dev/sda3           12914       19453    52532550    5  Extended
/dev/sda5           12914       19180    50339646   83  Linux
/dev/sda6           19181       19453     2192841   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by tom.swartz07 on 2010-04-13
> **itsvan said:**
> This is my output,if someone whould help me to chose how exactly to mount it,i need Windows and linux to be on the grub menu..ive read the guide but im stil uncertain and i dont want to mess anything up...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x843d9350

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12913   103723641    7  HPFS/NTFS
/dev/sda2           19454       19457       32130   ef  EFI (FAT-12/16/32)
/dev/sda3           12914       19453    52532550    5  Extended
/dev/sda5           12914       19180    50339646   83  Linux
/dev/sda6           19181       19453     2192841   82  Linux swap / Solaris

Partition table entries are not in disk order

You need to mount, in your specific case, /dev/sda1 and /dev/sda5
You could do this by running
```
sudo mount /dev/sda1 /mnt
```
```
sudo mount /dev/sda5 /mnt
```

Then you could follow along with the rest of the grub installation process

Specifically, just this one line-r:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```


You should get some output saying that it created grub.cfg, that it found linux-image-blah-blah-blah, etc. If you see the word 'Done.' and a new prompt, its safe to restart.

---

### Post by itsvan on 2010-04-13
Ok so i followed with the instructions,,i reboot and now this weird menu comes up, saying Grub , No bash-line output or something like that,,and all this weird stuff,,,it is not the usual boot menu im used to seeing,,by looks of it it seemed like it didnt work,,,now it doesnt boot into to neither windows or Ubuntu,,what could be the problem??

---

### Post by ranch hand on 2010-04-13
Post results of boot info script.

---

### Post by itsvan on 2010-04-13
This is what i get when i try to boot.........GNU GRUB version 1.97beta 4      {minimal BASH-Like line editing is supported. For the First word. TAB lists possible command completions. Anywhere else TAB lists possible device/file completions }         sh:grub>

---

### Post by ranch hand on 2010-04-13
You can run that script from the live CD.

---

### Post by itsvan on 2010-04-13
okk.soo..um what exactly do i do in order to get to boot ubuntu and windows? im still confused

---

### Post by ranch hand on 2010-04-13
You have these things installed, it should boot, at least to Ubuntu.  To tell you more there is more information needed.

Run the boot info script.  Post the results text here.

It would be nice to know your video card too.

---

### Post by itsvan on 2010-04-13
Sorry again for my ignorance,,but how do i Run the BOOT INFO SCREEN? alot of these terms still slip my mind,,and i think i have an integrated video card on my netbook,,,its an ASUS Eee pc 900HD

---

### Post by ranch hand on 2010-04-13
> **itsvan said:**
> Sorry again for my ignorance,,but how do i Run the BOOT INFO SCREEN? alot of these terms still slip my mind,,and i think i have an integrated video card on my netbook,,,its an ASUS Eee pc 900HD
Every thing you need for the script comes from this page.

Take your time, remember to breath, don't rush.

This can be run and posted from the Live CD.

Edit
While on the live CD run, in terminal;
```

lspci

```
and post the results of that too.

That will tell us what your card or controller is.

---

### Post by oldfred on 2010-04-13
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by itsvan on 2010-04-13
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

---

### Post by itsvan on 2010-04-13
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x843d9350

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,447,344   207,447,282   7 HPFS/NTFS
/dev/sda2         312,512,445   312,576,704        64,260  ef EFI (FAT-12/16/32)
/dev/sda3         207,447,345   312,512,444   105,065,100   5 Extended
/dev/sda5         207,447,408   308,126,699   100,679,292  83 Linux
/dev/sda6         308,126,763   312,512,444     4,385,682  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ACCC24DCCC222DD                       ntfs                                     
/dev/sda5        0c9b39c0-4d74-4508-8c9e-3e74332464dc   ext3                                     
/dev/sda6        1b39a4b8-618b-4dd5-93c6-254e4ad51960   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
# kopt=root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c9b39c0-4d74-4508-8c9e-3e74332464dc

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b39a4b8-618b-4dd5-93c6-254e4ad51960 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/core.img
 150.7GB: boot/grub/menu.lst
 149.9GB: boot/grub/stage2
 149.8GB: boot/initrd.img-2.6.28-11-generic
 149.8GB: boot/initrd.img-2.6.28-15-generic
 149.8GB: boot/initrd.img-2.6.28-16-generic
 149.9GB: boot/initrd.img-2.6.31-15-generic
 149.8GB: boot/initrd.img-2.6.31-16-generic
 149.8GB: boot/initrd.img-2.6.31-17-generic
 149.9GB: boot/initrd.img-2.6.31-19-generic
 141.0GB: boot/initrd.img-2.6.31-20-generic
 149.9GB: boot/vmlinuz-2.6.28-11-generic
 149.8GB: boot/vmlinuz-2.6.28-15-generic
 149.9GB: boot/vmlinuz-2.6.28-16-generic
 149.9GB: boot/vmlinuz-2.6.31-15-generic
 149.8GB: boot/vmlinuz-2.6.31-16-generic
 149.9GB: boot/vmlinuz-2.6.31-17-generic
 149.8GB: boot/vmlinuz-2.6.31-19-generic
 157.6GB: boot/vmlinuz-2.6.31-20-generic
 141.0GB: initrd.img
 149.9GB: initrd.img.old
 157.6GB: vmlinuz
 149.8GB: vmlinuz.old

---

### Post by Don1500 on 2010-04-13
Why doesn't anyone tell him to download the SuperGrub 2 disk? => [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Also I have found that almost any screw-up in "grub.cfg" can be fixed by ```
sudo update-grub
```

P.S. Itsvan, get rid of some of those old kernels, they just take up room and make your grub menu too long. I just keep the current and one previous. Right now I have 19 & 20.

---

### Post by ranch hand on 2010-04-13
> **Don1500 said:**
> Why doesn't anyone tell him to download the SuperGrub 2 disk? => [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Also I have found that almost any screw-up in "grub.cfg" can be fixed by ```
sudo update-grub
```P.S. Itsvan, get rid of some of those old kernels, they just take up room and make your grub menu too long. I just keep the current and one previous. Right now I have 19 & 20.
Well, one problem with that would be, if you look at the boot info script report, is that there is no grub.cfg.  The reason is that this system was upgraded and as happens the 2 grubs are not getting along so that we are supposedly using Grub2 as mentioned in the first entry of the report but using the menu.lst as shown in the grub part of the sda5 section of the report.

Some of us like to know what we are dealing with before making guess'.

---

### Post by ranch hand on 2010-04-13
itsvan
You should make a note that you are using intel graphics.  As happens this does not effect us at this time but you may have another problem that it does.  Intel is well supported and even better in 10.04 when it comes out.

You must have upgraded from 9.04 and chose to stick with grub-legacy or the conversion did not work well.  This was a bad idea when they came up with it and still is.  We need to untangle the mess of 2 competing grub versions.

I will be back very shortly.  I need to go back through your posts for a moment.

---

### Post by itsvan on 2010-04-13
ok thanks,,my pc is a mess right now:(

---

### Post by ranch hand on 2010-04-13
Ok, so you can't boot to Ubuntu at all.

We will have to try this from a live CD.  Do you have a Live CD for 9.04?

---

### Post by itsvan on 2010-04-13
i can boot into the live cd,,im currently on it...Um i think it might be a 9.10 or whatever newer version it is....and the problem is,,i cant burn anything now,because i cant even boot into windows,,where i burned this LIVE cd...im switching posts between my ps3 and the live cd:P

---

### Post by ranch hand on 2010-04-13
Ok.  Actually I think you could do it from the Live session but here is the deal.  Your 9.10 install claims that you are using grub1.97beta4.  The boot script comes up with the menu.lst which is left over from grub0.97.

I was going to have you try and recover grub0.97 to the MBR.  This might work but might not.  When you upgraded to 9.10 you got both mixed together so it is very unstable.  This was a big problem for a lot of people and gave grub1.97 a bad name.

You did upgrade didn't you?  Maybe I better make sure of this before we go on.

---

### Post by itsvan on 2010-04-13
To be honest i do not remember its been a long time,,but if i had to guess i think i did,,because i just threw out a Ubuntu 9.04 install disc that wasnt working, it was scratched,,thats why i downloaded this new live disc,,what whould be the problem if i did or didnt upgrade?

---

### Post by ranch hand on 2010-04-13
If you did a clean install we should not be having this problem at all.  It is the upgrade method going from one grub to the next and giving an option to chain load between them that is the problem.  A clean install just gives you grub1.97beta4.

OK, so we know where we are.  This is a sort of problem because we need to establish a chroot environment from the Live CD into your OS and remove grub, grub-pc and grub-common.  And then install grub-pc and grub-common.

The real problem is that I am not that good at chroot.  I do it all the time with a set of commands that work real well with labeled partitions.  I am sure that yours are not labeled.

We can do that easily, however from the Live CD.

If you are not on the Live CD please boot to it.

When you are on there go to System>Administration>Gparted (also listed in some versions as Partition Editor).

When it is up right click on the partition of your grub install sda5.  If "Unmount" is not grayed out click on that.

When it is grayed out and you right click on your partition the option "Label" will be lit up.  Click on it.

You now have a box to type in.  Use something simple like "Karmic".  I will assume Karmic and you can edit as needed in the stuff below.

Close gparted and go to Applications>Accessories>gedit and open it and paste;
```

#!/bin/sh

## sudo mkdir /mnt/Karmic
sudo mount /dev/sda5 /mnt/Karmic/
sudo mount -o bind /proc /mnt/Karmic/proc
sudo mount -o bind /dev /mnt/Karmic/dev
sudo mount -o bind /dev/pts /mnt/Karmic/dev/pts
sudo mount -o bind /sys /mnt/Karmic/sys
sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolve.conf
sudo chroot /mnt/Karmic /bin/bash

fi

```
into it and save the file to the Live session desktop and to the desktop of your Karmic installation (it may come in handy it the future and there it will be to grab if there is a next time).

On the one on your live session desktop, right click on it and click on "Properties and then the tab for "permissions".  You will see a box, down toward the bottom, that says "Allow executing file as a program".  Close all that and double click on the file on the desktop.  Select "run in terminal".

If we did this right a terminal should open with the user as root so there will be no need for "sudo" in these commands;
```

apt-get update

```
is the first.  If there is a bunch of errors about not connecting to the repo we will deal with that before going on.

---

### Post by itsvan on 2010-04-14
On Labeling the partition,,,,,Before i continue after Gparted,,it tells me 1 operation pending to apply the changes,,but it tells me IF IM SURE,,AND THAT DATA LOSS CAN HAPPEN<, does this mean my data on ubuntu will be gone?? i just want to double check before i proceed with the next steps

---

### Post by ranch hand on 2010-04-14
They throw that up every time you do anything on editing partitions.   There is always a risk.

In this case, however, just go ahead.  I have never heard of anyone loosing data by labeling a partition.

It should take about a second and then a bit to re read the drive.  Let it finish before closing gparted.

---

### Post by itsvan on 2010-04-14
So i clikc on run in terminal,,,and it the screen pops up with a couple of sentences and then it closes real quick,,,,it says something that the mount point doesnt exist or something it doesnt give me much time to read it,

---

### Post by ranch hand on 2010-04-14
Did I put in the correct partition in (sda5)?  That is right isn't it.

Did you use Karmic (upper case K and all)?

If both those answers are yes, then just go to Applications>Accessories>Terminal and open one up.

One at a time copy paste from the script the commands (all the stuff with sudo in front of it).

Run them all in that order.  If some fail ignore it for now.  Let us see what happens and what the problems may be.

That is an edited copy of one I use all the time to update an installation on my test drive.

---

### Post by ranch hand on 2010-04-14
Oh the Devil and all His Helpers, of coarse it  failed.  geeze I can be so stupid at times.

The line
```

## sudo mkdir /mnt/Karmic

```
change to
```

sudo mkdir /mnt/Karmic

```
Save the file and try it again.

If is sure not going to work without a directory to work from.

---

### Post by itsvan on 2010-04-14
Ya both are right,,and i followed through,,i tried it on the terminal and this is what happend,,i did one by one,what the heck :confused:

ubuntu@ubuntu:~$ ## sudo mkdir /mnt/Karmic
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/Karmic/
mount: mount point /mnt/Karmic/ does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/Karmic/proc
mount: mount point /mnt/Karmic/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /dev/pts /mnt/Karmic/dev/pts
mount: mount point /mnt/Karmic/dev/pts does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/Karmic/sys
mount: mount point /mnt/Karmic/sys does not exist
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolve.conf
cp: cannot create regular file `/mnt/Karmic/etc/resolve.conf': No such file or directory
ubuntu@ubuntu:~$ sudo chroot /mnt/Karmic /bin/bash
chroot: cannot change root directory to /mnt/Karmic: No such file or directory
ubuntu@ubuntu:~$

---

### Post by itsvan on 2010-04-14
ahhh there we GO!,,i changed what you said on Gedit,,and now it works,,the terminal is up and ready to go,,now what:guitar:

---

### Post by ranch hand on 2010-04-14
run;
```

apt-get update

```
If it updates instead of giving errors about not being able to connect we can go on.  We can't go on until we know that networking is up and running.

---

### Post by itsvan on 2010-04-14
It seemed liked it updated fine,,heres the output to be sure

root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [88.2kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [197kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [26.7kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [49.7kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [8,486B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [59.0kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [125kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [29.7kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [7,354B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [4,036B]
Fetched 685kB in 3s (178kB/s)                             
Reading package lists... Done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-14
YES.
```

apt-get purge grub grub-pc grub-common

```
If you get told that grub installed don't worry about it.  Just get rid all of them that are present.

---

### Post by ranch hand on 2010-04-14
Then open another terminal and run
```

gksudo nautilus

```

---

### Post by itsvan on 2010-04-14
ok seems fine so far....heres output again to be sure

root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libclxclient3 gtali glchess libgfortran3 gnobots2 g++-4.4 gnome-mahjongg
  ocaml-base-nox same-gnome libstdc++6-4.4-dev g++ gnibbles gnome-games-common
  python-numpy gnotski gnometris libclutter-1.0-0 libclthreads2 iagno glines
  libclutter-gtk-0.10-0 gnome-sudoku libavogadro0 libblas3gf tcl8.5
  libamd2.2.0 liblapack3gf gnotravex gnect tk8.5 ocaml-base python-scipy stops
  libumfpack5.4.0 libclalsadrv1 gnomine
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub* grub-common*
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
After this operation, 3,363kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 265887 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-14
Well, that explains a lot.

grub-pc is grub1.97beta4.

Leaving that terminal open go to the second one (see  the post above your last) and, in nautilus>file system go to the directory "mnt".  There should be one folder there.  Open it and then open the folder "boot" an then "grub".  Delete the menu.lst if present.

---

### Post by itsvan on 2010-04-14
i get an error on the Nautilus one

root@ubuntu:/# gksudo nautilus
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-AJgTOsO6MM: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-DyZX4mWHI7: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-yEWGZjjZq9: Connection refused)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-rE0KufF0Aj: Connection refused)

(gksudo:4556): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:4577): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by itsvan on 2010-04-14
Ah i accidentally put in the code on the same terminal thats why i got that maybe,,but then i opened a second one got this

ubuntu@ubuntu:~$ gksudo nautilus
(nautilus:4715): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:4715): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4715): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4715): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:4715): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
ubuntu@ubuntu:~$

---

### Post by ranch hand on 2010-04-14
To hell with it.  You can go (as root) and delete when you boot into the bugger.

Get back to your chroot an run;
```

apt-get install grub-common grub-pc

```
I think you should get "os-prober" with that but, like grub-pc, it should have been there all ready so you may not.

---

### Post by itsvan on 2010-04-14
So i put the code in the First Terminal Right??? if so this blue screen comes up,,,and it tell me to put in LINUX COMMAND LINE

Package configuration





 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The following Linux command line was extracted from /etc/default/grub or  &#9474; 
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it    &#9474; 
 &#9474; is correct, and modify it if necessary.                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Linux command line:

---

### Post by ranch hand on 2010-04-14
Hit tab and then enter.

---

### Post by itsvan on 2010-04-14
this comes next



The following string will be used as Linux parameters for the default   &#9474; 
  &#9474; menu entry but not for the recovery mode.                               &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; Linux default command line:                                             &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474; quiet splash___________________________________________________________ &#9474; 
  &#9474;                                                                         &#9474; 
  &#9474;                                 <Ok>                                    &#9474; 
  &#9474;

---

### Post by ranch hand on 2010-04-14
That is what you want.

---

### Post by itsvan on 2010-04-14
i got up to this page,,do i change anything or just continue?

                       &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                       &#9474; GRUB install devices:          &#9474; 
                       &#9474;                                &#9474; 
                       &#9474;    [ ] /dev/sda                &#9474; 
                       &#9474;                                &#9474; 
                       &#9474;                                &#9474; 
                       &#9474;             <Ok>               &#9474; 
                       &#9474;

---

### Post by ranch hand on 2010-04-14
YES.

Perfecto.

---

### Post by itsvan on 2010-04-14
ok i hit enter,and it ended...seems like it went through with no prob...what next

---

### Post by ranch hand on 2010-04-14
run
```

update-grub

```
and see if it mentions windows

---

### Post by itsvan on 2010-04-14
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

---

### Post by ranch hand on 2010-04-14
Ok, this is a bummer but it should boot you to Karmic and it is easier to work from there.

So, I am whacked and need to go to bed.

I am going to hang on here untill you are in karmic.

We will get this other straight tommorrow.

---

### Post by itsvan on 2010-04-14
Ok thanks,,ill be on tomorrow then thanks again:KS

---

### Post by ranch hand on 2010-04-14
It did boot to karmic?

---

### Post by ranch hand on 2010-04-14
Let me know when you are up and running and if you can boot to Karmic check and see if you have a /boot/grub directory.  I do not see how it can be otherwise but we better check.

It would be a good idea to open your terminal and run;
```

sudo apt-get autoremove

```
this will get rid of all those extra, old kernels that are just taking up space.

Then run that boot info script again.  You want to keep a copy of that by the way.  It comes in handy just to check up on your system every once in a while.

We will see then what we need to do to get MS to boot.  Hopefully it will be very simple.

---

### Post by itsvan on 2010-04-14
Yes im in KArmic FINALLY!! i have done all so far..heres the output:






                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x843d9350

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,447,344   207,447,282   7 HPFS/NTFS
/dev/sda2         312,512,445   312,576,704        64,260  ef EFI (FAT-12/16/32)
/dev/sda3         207,447,345   312,512,444   105,065,100   5 Extended
/dev/sda5         207,447,408   308,126,699   100,679,292  83 Linux
/dev/sda6         308,126,763   312,512,444     4,385,682  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5ACCC24DCCC222DD                       ntfs                                     
/dev/sda5        0c9b39c0-4d74-4508-8c9e-3e74332464dc   ext3       Karmic                        
/dev/sda6        1b39a4b8-618b-4dd5-93c6-254e4ad51960   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
# kopt=root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c9b39c0-4d74-4508-8c9e-3e74332464dc

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b39a4b8-618b-4dd5-93c6-254e4ad51960 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/core.img
 142.0GB: boot/grub/grub.cfg
 150.7GB: boot/grub/menu.lst
 149.9GB: boot/grub/stage2
 149.8GB: boot/initrd.img-2.6.28-11-generic
 149.8GB: boot/initrd.img-2.6.28-15-generic
 149.8GB: boot/initrd.img-2.6.28-16-generic
 149.9GB: boot/initrd.img-2.6.31-15-generic
 149.8GB: boot/initrd.img-2.6.31-16-generic
 149.8GB: boot/initrd.img-2.6.31-17-generic
 149.9GB: boot/initrd.img-2.6.31-19-generic
 141.0GB: boot/initrd.img-2.6.31-20-generic
 149.9GB: boot/vmlinuz-2.6.28-11-generic
 149.8GB: boot/vmlinuz-2.6.28-15-generic
 149.9GB: boot/vmlinuz-2.6.28-16-generic
 149.9GB: boot/vmlinuz-2.6.31-15-generic
 149.8GB: boot/vmlinuz-2.6.31-16-generic
 149.9GB: boot/vmlinuz-2.6.31-17-generic
 149.8GB: boot/vmlinuz-2.6.31-19-generic
 157.6GB: boot/vmlinuz-2.6.31-20-generic
 141.0GB: initrd.img
 149.9GB: initrd.img.old
 157.6GB: vmlinuz
 149.8GB: vmlinuz.old

---

### Post by Don1500 on 2010-04-14
end

---

### Post by ranch hand on 2010-04-14
Ok.

First, when you post something like that huge amount of text it is good to contain it.  The easiest way is with some typing.  If you [xxxx] where xxxx is the word code at the beginning, and [/xxxx] where xxxx  is again the word code (I can 't show this to you or the stuff in between wood be boxed and you would not see the second set of brackets at all).

This will give you a box as below.

You did not, I believe, run;
```

sudo apt-get auto remove

```
I deleted the entries in the menu.lst and grub.cfg and that got rid of almost 300 line of useless entries of useless kernels on you box.  If I had paid attention to this yesterday though I would have seen that you did indeed upgrade from 9.04 as the kernels are still there.

You don't have to run that command, I just do not like dead kernels cluttering up the drive.

It is interesting from the forensic view though.

I do think that everything looks good to go.  I do not know why there is no entry for MS in grub.cfg as there is one in menu.lst.

The first thing to do is see if the simple answer works first.

Run this;
```

sudo apt-get update
[code]
then
[code]
sudo apt-get upgrade

```
You will be asked for your password.  You will need to approve getting any upgraded packages found.  This should be completely safe to do as 9.10 is stable.

And when that is done;
```

sudo update-grub

```
That should get it.

We will all be waiting with bated breath.  If it does not get it we will do it manually.

---

### Post by itsvan on 2010-04-14
does it look good so far???

itsvan@MAGI:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

---

### Post by ranch hand on 2010-04-14
Not really.  On that list, right after the memtest stuff should be your MS menu entry.

So two things to do.

A get up nautilus>file system>etc>grub.d and check the permissions on 30_os-prober and make sure the box is checked to make the file executable as a program.  This will be under properties on the right click menu and under the permissions tab.

If it is not checked you will have to get into nautilus as root to change it and then run the update-grub thing again and see if that works better.

If it is already checked forget it for now and;
```

gksudo gedit /etc/grub.d/40_custom

```copy paste this into that file below the stuff that in there;
```

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF

```Then save that file as 06_custom.  The change in name will move that entry to the top of your screen menu instead of down below all that other stuff.

Then you will need to run;
[code]
sudo update-grub and see what you get for that.

I think that menu entry is good.  I do/will not have MS in my house so I had to borrow that one but it was a good source and I know it works there and it looks like a match for where your MS installation is.

I do not understand the error at the bottom of your last run of that command at all.

---

### Post by itsvan on 2010-04-14
Sorry the Nautilus part confuses me,,where exactly do i go to open Nautilus??

---

### Post by ranch hand on 2010-04-14
Sorry, nautilus is you file manager.  It is what opens when you go to Places>Home Folder or;
```

nautilus

```
or to be in as root
```

gksudo nautilus

```

---

### Post by itsvan on 2010-04-14
I gotta go for the moment,,but i will be on later,,so do i put those codes in the terminal? sorry my noobish ways are still messing with my head, i might need some patience,,,il be on later

---

### Post by ranch hand on 2010-04-14
Just go to Places>Home Folder in the menu on your top panel.  Then in the left panel of the screnn that comes up select "File System".  If you do not have a left panel go to "View" (upper left of screen) and check the "Side Pane" option.

Then double click on "etc" and then on "grub.d".  That will show you the files that control grub.  They are all scripts that are used to generate your /boot/grub/grub.cfg file that in turn is what generates your screen menu that you see when you boot up.

I just want you to look at the preferences of 30_os-prober.  Right click on the file, select "preferences" and then the "permissions" tab in the box that comes up.  There is a box near the bottom that says "Allow executing file as a program".  This needs to have a check mark in it.

I am actually pretty sure that it does as it  shows up in your grub.cfg file.  The thing is that your computer thought you were running grub1.97beta4 when in fact you did not have grub-pc installed so I have a trust problem and want to see this for myself (in reality I will take your word for it).

If it does just go to the instructions for adding the custom file and do that.

If it does not have a check there then we will do something about that instead of the custom file.

Frankly all I use anymore is a custom menu file as it is just easier to control and there is little or nothing really to maintain.

---

### Post by ed-koala on 2010-04-14
Grub2 doesn't see windows 7 for some reason.  I just solved that problem recently, will link to my thread ...

[http://ubuntuforums.org/showthread.php?t=1453700]("http://ubuntuforums.org/showthread.php?t=1453700")

Hope that helps, it'll fix so you can boot into Windows 7 PROVIDING there isn't anything wrong with windows, just it's missing from Grub2.

---

### Post by itsvan on 2010-04-14
OK yah it was checked of so i did the rest,,,does it look like it changed? or did i do it wrong..i followed through

itsvan@MAGI:~$ gksudo gedit /etc/grub.d/40_custom
itsvan@MAGI:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
itsvan@MAGI:~$

---

### Post by ranch hand on 2010-04-14
The devil and all hes helpers (as my dad used to say).

If you saved that file as 06_custom run
```

sudo nautilus 

```
This will put you in nautilus as root so you can change permissions.  Your new file does not have that box checked.  Check it in the nautilus that opens with the above command.

Then rerun update-grub and it should be there.

---

### Post by itsvan on 2010-04-14
ok i did all of the changes..this is the output

itsvan@MAGI:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory

---

### Post by ranch hand on 2010-04-14
You should be getting something like this;
> 
Adding Lounge on sda7
Adding Lubuntu on sda8
Adding Daily on sda13
Adding ISO-test on sda14

with just your MS menu entry listed at the start on that list.

Pull up the 06_custom file;
```

gksudo gedit /etc/grub.d/06_custom

```
and using the "edit" menu hit "select all" and then "copy" and then paste that bugger back here.

Let us see if I just screwed some thing up or if it looks good.

I am not sure why os-prober is not working to pick this up and that worries me.  Your boot info script results show the MS boot sector as good and I see no reason to doubt that at all.

We may still have a problem with the grub installation on your OS.

Lets look at that file and see what it looks like before getting ahead of our selves with worry about things that may not really be problems.  I need to take my own advice and remember to breath.

---

### Post by oldfred on 2010-04-14
I think this is a minor point but:
Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=DarkRed]/boot/grub/core.img[/COLOR]

This is your windows entry and it has a grub file in it. It may be just enough to confuse the os-prober? I would just delete this from your windows partition.

---

### Post by itsvan on 2010-04-14
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF

---

### Post by ranch hand on 2010-04-15
I could use some help on this one for sure.

I think there is something still wrong with grub.  We purged it and reinstalled it to get it to boot to karmic.

The custom entry that we can't get to come up should no matter what else is going on as it is separate from every thing else.

What you say may well be the trouble with os-prober.

I do not use any MS products (even in wine) so I really do not know how to deal with this?  How would he boot to Win?  Restore the boot sector there and then try to reinstall grub?

This is what I would lean to if we could get grub to work as it should with this file.

I wish kansasnoob would check in here too.  Maybe you guys would have a better plan of attack on this problem.

I am seriously considering  doing grub over again now that we don't have to do it from the Live CD which is how we did it earlier.  I think the problem is actually grub-common but there is no sense trying to do one with out the other and this time take out os-prober too.  Just start over.

---

### Post by ranch hand on 2010-04-15
That looks good to me.  It should work.

Let us see if oldfred has a better idea but I think we really need to wipe grub again and start over.  This works better from in your OS than from the Live session.

It works better now but it is not right.

If you are sure that the permissions are right on the 06_custom file it should show up even if it was wrong on the update-grub output when you run it in terminal.

I am going to hit the hay and let this thing rest again.  We are too close to screw it up now.

---

### Post by itsvan on 2010-04-15
Ya i know where almost there,,but bloody windows like always its a hastle...take your time and thanks again for all the help..ill be here tomorrow to follow further instructions

---

### Post by oldfred on 2010-04-15
Do you have two boot directories like this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

I think this entry is wrong and I have seen it several times. I believe it is copied from somewhere where the instructions were editing from the command line using cat.

remove the red bits.

[COLOR=Red]echo "Adding Win on sda1" >&2 
cat << EOF[/COLOR]
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set [COLOR=Navy]00acffe0acffcde2[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1
}
[COLOR=Red]EOF     

Correct UUID:
[/COLOR]5ACCC24DCCC222DD

---

### Post by itsvan on 2010-04-15
i get something like that at the end,, is it the same??


itsvan@MAGI:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory

---

### Post by oldfred on 2010-04-15
No, the problem is in Linux capitals are different than lower case, but in windows they are the same. so having in Windows /boot and /Boot can be a problem and probably cannot be fixed from windows as it cannot tell them apart.

Did you fix the 40_custom entry to remove the lines and change the UUID to the correct one for your sda1 partition.

You can double check that the UUID is correct for sda1 buy running this from a command line:

```
sudo blkid
```

---

### Post by itsvan on 2010-04-15
this is what i get

itsvan@MAGI:~$ sudo blkid
[sudo] password for itsvan: 
/dev/sda1: UUID="5ACCC24DCCC222DD" TYPE="ntfs" 
/dev/sda5: LABEL="Karmic" UUID="0c9b39c0-4d74-4508-8c9e-3e74332464dc" TYPE="ext3" 
/dev/sda6: UUID="1b39a4b8-618b-4dd5-93c6-254e4ad51960" TYPE="swap"

---

### Post by ranch hand on 2010-04-15
That uuid is wrong.  I am getting senile.

It should be 5ACCC24DCCC222DD

---

### Post by oldfred on 2010-04-15
And you have to delete the second /boot directory in windows per  meierfra's page on sourceforge (the link I gave in 2 posts ago #86) as windows gets confused.

---

### Post by itsvan on 2010-04-15
OK so my PC is going to hell again,,,Ubuntu was running fine this morning,,i come back turn it on and i get this screen saying the following.......Adding Win on SDA1 >82  error: file name required  error: unknown command 'EOF '  error: no such device: 00acffe0acffcde2 Failed to boot default entries. press any key to continue  (I DO SO AND THEN)  error: no such devie: 00acffde2 Failed to boot default entries

---

### Post by oldfred on 2010-04-15
See post #86 you did not delete the red lines and it is trying to execute them.

---

### Post by itsvan on 2010-04-15
ok so how can i go back and do that...il prob need the live disc right???

---

### Post by ranch hand on 2010-04-15
Does your menu come up at all?  If so boot to recovery mode and select return to normal login.  This should give you a text login for your user name and then the password.

When the prompt comes back up type startx.

This is actually good news to me.  It sounds like grub is actually reading the scripts.  This is good.

If you have to go to the Cd to edit files we can do that.

---

### Post by itsvan on 2010-04-15
No no boot menu comes up at all...and even before it didnt anyway,,it just said GRUB and loading i think,and it went direcrtly into Ubuntu...but now just that Menu that i posted before comes up and every time i press a key to continue,,it just keeps on repeating it over and over and over again....so i might need instructions on how to do it from the live disc..:(

---

### Post by ranch hand on 2010-04-15
I think all we need to do is go in and use nautilus (as root) and edit that uuid and the rest of the entry to correct it and then update grub.

This should not take to much doing.

When you get booted to the Live Session open the terminal and;
```

gksudo nautilus

```
this will get you into nautilus as root.

The file system for your installation may not be mounted.  If it is not in the left pane in the root nautilus you will need to open the regular home folder.

It should be listed there as Karmic because you labeled the partition.  Click on that and it should come up there.

Go back to the root nautilus and it should now be in the side pane there.

Why don't you try that and let us know how it goes.

---

### Post by itsvan on 2010-04-15
Its a side tab on the Home folder right that says KARMIC? if so yes its there,,what now?

---

### Post by ranch hand on 2010-04-15
Click on that and it should open.

Then if you have not done so run
```

gksudo nautilus

```
and it should have that in the left pane too.

Click on that and open it there.

Go to "etc".

Go to "grub.d"

Go to "06_custom and open in gedit.  You should be able to double click on it and get an option window.  Click on "display".

This should open it in gedit.

Just get rid of the entry I gave you and put this one in;
```

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}

```
making sure to get that last } in the right place.

Save the file.

Then we will move on to the next step.

---

### Post by itsvan on 2010-04-15
OK do I completely delete everything or just the bottom part.the part that looks like the one you sent me?

---

### Post by ranch hand on 2010-04-15
Get rid of the old entry and replace it with the new one.

---

### Post by itsvan on 2010-04-15
ok done

---

### Post by ranch hand on 2010-04-15
Great.

Now we need to update grub.  We do not have to worry about a network connection so just;
```

sudo mount /dev/sda1 /mnt

sudo mount --bind /dev /mnt/dev

sudo chroot /mnt

update-grub

grub-install /dev/sda

```Do these one at a time in the order given.

The last is probably not needed but the way things have gone we'll just do it anyway.

The reason that there is no sudo on the last two is that you will be in a chroot environment so you are the super user (su = super user) and so you do not need it.

We better see the output of update grub.

---

### Post by itsvan on 2010-04-15
it seems something is going wrong,,i dont know what step isnt right, man these Computers sure are a hastle

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ update-grub

/usr/sbin/grub-mkconfig: You must run this as root
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ grub-install /dev/sda
grub-mkdevicemap: error: cannot open /boot/grub/device.map
ubuntu@ubuntu:~$

---

### Post by ranch hand on 2010-04-15
Well bugger that for a lark.  Did you save that script we used to chroot before to the installed OS?

If so just copy it to the live session desktop and make sure the permissions are right to run as a program and run it and just do;
```

update-grub

grub-install /dev/sda

```
and give us  the results of that.

---

### Post by bcbc on 2010-04-15
You were trying to chroot to /dev/sda1 - that's your windows partition. Try this instead:

```
sudo mount /dev/sda5 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo chroot /mnt
update-grub
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done 
```

---

### Post by itsvan on 2010-04-15
What script?? was it on a post?? ,,if it was one of those other files,,i do have them but there on karmic..:confused:

---

### Post by ranch hand on 2010-04-15
This one;
```

#!/bin/sh

sudo mkdir /mnt/Karmic
sudo mount /dev/sda5 /mnt/Karmic/
sudo mount -o bind /proc /mnt/Karmic/proc
sudo mount -o bind /dev /mnt/Karmic/dev
sudo mount -o bind /dev/pts /mnt/Karmic/dev/pts
sudo mount -o bind /sys /mnt/Karmic/sys
sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolve.conf
sudo chroot /mnt/Karmic /bin/bash

fi

```
Before you run it you need to change the permissions to "execute as a program" AND save it to the desktop of your installed karmic.  That way if you ever need it from the live CD you can copy it right back there.

---

### Post by itsvan on 2010-04-15
ok im the root terminal

---

### Post by ranch hand on 2010-04-15
run;
```

update-grub

```
and give us the results.

If you have not saved the script file to your install do it soon or come back to this thread and grab it from here and save it.  You see how handy it is, keep it.

Thanking phillinux, by the way, who is the perpetrator of that script that he was kind enough to supply me with durring a particularly difficult time in 9.10-testing.

---

### Post by itsvan on 2010-04-15
il save It to a jump drive< Heres the output

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-15
Well I am jiggered.  That should have listed MS instead of those errors.

If you saved that script to your desktop of the install, I think you should try rebooting.  The thing acted like it was trying to read the faulty uuid and failing before.  We have the correct uuid now.  Let us just see if it works that way again.

I wish someone had chimed in here to say if that entry was right or not.  I really do not use MS and this type of problem is a good bit of the reason.  On the other hand I can't try things like this out on my box before inflicting them on others.

Just give it a whack.

---

### Post by itsvan on 2010-04-15
SO now it boots into windows,,but not Ubuntu,,it shows GRUB and then it goes away,,and then it boots into windows,,,seems we cant get both at the same time haha

---

### Post by ranch hand on 2010-04-15
This is fine you must have the default set at "0" in /etc/default/grub and your time out is to short to do anything.

I assume that you have MS set to auto login or what ever those folks call it.

Did you see entries for Ubuntu when the menu flashed by?

---

### Post by ed-koala on 2010-04-15
Just a thought itsvan, how much data do you have in windows and ubuntu?

I don't usually recommend starting over but ....

Can you run the boot script now and post results to see what things look like currently?  I have a dual boot with Win 7 that is working and I'll compare my script to yours and see what is different.

---

### Post by itsvan on 2010-04-15
Trust me ive thought of starting over,,but In Ubuntu i have tons of files and programs it whould be a real hastle to restart it...and in windows i dont have anything but i use some programs on there,,and the whole reason for me installing it is for those programs,,but when i installed it Windows 7 just messed everything up,,i didnt think going back to the GRUB menu whould be this difficult...its a real PICKLE.....

And when the pc boots up i see GRUB on the top left of the screen,,then some words come up that i cant tell,,and then it goes to Windows,,its as if its wanting to go into Ubuntu boot chooses windwos instead...

---

### Post by itsvan on 2010-04-15
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done
root@ubuntu:/#

---

### Post by ed-koala on 2010-04-15
Can you run the Boot Info script, like in post 28 so I can compare to my working system?  I'd like to see how things stand now before mucking with anything.

---

### Post by ranch hand on 2010-04-15
I take it you are on the live session again.

I do not know if it will work without rebooting but try getting back into the files as root and we will change a couple things.

To tell if this will work you need to open the home folder and see if you can get to (in file system) /etc/default/grub.

If you can open the terminal and;
[code]
sudo nautilus and do it again there as root.

If you can't you will have to reboot and try it again then.

---

### Post by ranch hand on 2010-04-15
> **ed-koala said:**
> Can you run the Boot Info script, like in post 28 so I can compare to my working system?  I'd like to see how things stand now before mucking with anything.
This is a good idea too.

---

### Post by itsvan on 2010-04-15
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x843d9350

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,447,344   207,447,282   7 HPFS/NTFS
/dev/sda2         312,512,445   312,576,704        64,260  ef EFI (FAT-12/16/32)
/dev/sda3         207,447,345   312,512,444   105,065,100   5 Extended
/dev/sda5         207,447,408   308,126,699   100,679,292  83 Linux
/dev/sda6         308,126,763   312,512,444     4,385,682  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders, total 3894975 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6093840

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             16     3,894,974     3,894,959   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ACCC24DCCC222DD                       ntfs                                     
/dev/sda5        0c9b39c0-4d74-4508-8c9e-3e74332464dc   ext3       Karmic                        
/dev/sda6        1b39a4b8-618b-4dd5-93c6-254e4ad51960   swap                                     
/dev/sdb1        18AD-128F                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/18AD-128F         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /mnt/Karmic              ext3       (rw)
/dev             /mnt/Karmic/dev          none       (rw,bind)
/dev/pts         /mnt/Karmic/dev/pts      none       (rw,bind)


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
# kopt=root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c9b39c0-4d74-4508-8c9e-3e74332464dc

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b39a4b8-618b-4dd5-93c6-254e4ad51960 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/core.img
 142.2GB: boot/grub/grub.cfg
 150.7GB: boot/grub/menu.lst
 149.9GB: boot/grub/stage2
 149.8GB: boot/initrd.img-2.6.28-11-generic
 149.8GB: boot/initrd.img-2.6.28-15-generic
 149.8GB: boot/initrd.img-2.6.28-16-generic
 149.9GB: boot/initrd.img-2.6.31-15-generic
 149.8GB: boot/initrd.img-2.6.31-16-generic
 149.8GB: boot/initrd.img-2.6.31-17-generic
 149.9GB: boot/initrd.img-2.6.31-19-generic
 141.0GB: boot/initrd.img-2.6.31-20-generic
 149.9GB: boot/vmlinuz-2.6.28-11-generic
 149.8GB: boot/vmlinuz-2.6.28-15-generic
 149.9GB: boot/vmlinuz-2.6.28-16-generic
 149.9GB: boot/vmlinuz-2.6.31-15-generic
 149.8GB: boot/vmlinuz-2.6.31-16-generic
 149.9GB: boot/vmlinuz-2.6.31-17-generic
 149.8GB: boot/vmlinuz-2.6.31-19-generic
 157.6GB: boot/vmlinuz-2.6.31-20-generic
 141.0GB: initrd.img
 149.9GB: initrd.img.old
 157.6GB: vmlinuz
 149.8GB: vmlinuz.old

---

### Post by ed-koala on 2010-04-15
Hmmmm, I noticed this but I doubt it's causing your problems ...

Yours:

```
sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
/boot/grub/core.img

```

Mine: (ignore the difference in sda/sdb)

```
sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

You have some old info left over from grub legacy, shouldn't matter though.  I don't see any other issues right off.

Ok, I'd like Ranch Hand's opinion on this before ya try anything, but I think this might just work, if you have a Windows 7 disk and a LiveCD.

I am thinking ... totally remove Grub2.  Then, boot with the Windows CD and reinstall/fix the MBR to Windows.  Then, boot the LiveCD and reinstall Grub2.  At this point you can edit /etc/default/grub to get the list to show up, which should not show windows and will boot into Ubuntu.  Then we can edit to add Widows and get both booting.

Ranch, think this idea might be the way to go?  My opinion is basicall get ONE boot loader, windows, working, then go on.  I'd like an opinion before trying this though.

---

### Post by ranch hand on 2010-04-15
There is some wierd stuff there that  I do not quite understand but I think I have the cure for.

I will be back directly, I am checking one of my other installations to check to see that the updates will not screw my main 10.04 install.  I need to get back there before I go on.

---

### Post by ed-koala on 2010-04-15
I notice also you still have the grub legacy files hanging around.  Perhaps deleting those also may help?

Here is my boot info script file to compare to ...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=903f98b5-112a-403e-a8f9-75b7893c2aba)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbe8c40

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dbaf8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   937,167,839   937,167,777  83 Linux
/dev/sdb2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sdb5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A2A092A134EA339                       ntfs       Windows                       
/dev/sda                                                nvidia_raid_member                               
/dev/sdb1        903f98b5-112a-403e-a8f9-75b7893c2aba   ext4                                     
/dev/sdb5        89536d05-f423-4796-b1d4-1b63e41757b3   swap                                     
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        610B70B04DE9F32D                       ntfs       My Book                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows_7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=903f98b5-112a-403e-a8f9-75b7893c2aba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=89536d05-f423-4796-b1d4-1b63e41757b3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
   3.2GB: boot/grub/grub.cfg
   3.3GB: boot/initrd.img-2.6.31-14-generic
   3.6GB: boot/initrd.img-2.6.31-20-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   3.4GB: boot/vmlinuz-2.6.31-20-generic
   3.6GB: initrd.img
   3.3GB: initrd.img.old
   3.4GB: vmlinuz
   2.3GB: vmlinuz.old

```

---

### Post by oldfred on 2010-04-15
i have seen ranch hand post slightly different versions of chroot but this should work. You have parts of grub and grub2 adn they often conflict, so we will totally uninstall both and reinstall grub2. anything after the # are comments do not enter them.

Of course you must first know what partition you want to mount, in this example I'm using sda5:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#purge old and reinstall new to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by ranch hand on 2010-04-15
> **ed-koala said:**
> I notice also you still have the grub legacy files hanging around.  Perhaps deleting those also may help?
They are still there after purging grub grub-pc and grub-common and then reinstalling them.  Very strange.

I think that the current problem, though, is caused by;
> 
### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

and a time out that is too short to let you read the menu and having the default set at 0 which is MS;
> 
### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###


So I am going to do another post just for the directions now.

---

### Post by ranch hand on 2010-04-15
Have you tried getting into the /etc/default/grub file yet?

If so and it worked, have you got nautilus up as root?

---

### Post by itsvan on 2010-04-15
I ran the script,,i get all that other stuff,,,but i think im as root though


mkdir: cannot create directory `/mnt/Karmic': File exists
mount: /dev/sda5 already mounted or /mnt/Karmic/ busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt/Karmic
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-16
Can you get into the home folder>file system>etc>default>grub?

If so run;
```

sudo nautilus

```

If not reboot the CD and do not run the script and try getting to that file again.

---

### Post by itsvan on 2010-04-16
Il reboot the cd

---

### Post by itsvan on 2010-04-16
k what now

---

### Post by ranch hand on 2010-04-16
Boy am I glad, you were killing me here.  I can taste victory and was getting antsy.

Pull up the home folder and go to file system and then to "etc" and then "default".

Just leave that up and open the terminal and;
```

gksudo nautilus

```
and go to the same place and open the /etc/default/grub file in gedit.

You will see a line (about line 4) that says
> 
GRUB_DEFAULT=0

Change that to read 1 instead of 0.

About line 7 you will have something like;
> 
GRUB_TIMEOUT="3"

Change that from 3 (or what ever it is) to 30.

Let me know when you are done.  We have a couple other things to do in nautilus as root so don't drop it.

---

### Post by itsvan on 2010-04-16
ok done

---

### Post by ranch hand on 2010-04-16
Great that will put Karmic as the default to boot to if you do not select another in 30 seconds.

Now we need to stay in /etc but go to /grub.d instead of /default.

There I want you to pull up the permissions of 30_os-prober and 40_custom and uncheck the box making them executable.

Let me know.

I may be on an other OS but is will have the browser up on this page.

---

### Post by itsvan on 2010-04-16
OK i unchecked both of the boxes..the ones under the permissions tab right?

---

### Post by ranch hand on 2010-04-16
YES.

If you look at the last results test you posted, scanning down to the grub.cfg file you will see where 30_os-prober starts and then some wierd stuff about timeouts and so on that I think is what is booting your MS so fast and with no real option.  It will not do that now.

You saved the menu entry (the bad one) I gave you to 40_custom.  It will no longer be on your menu.

Well that will be true in a few minutes.

now you can close all the file browsers and the terminal and run the chroot script and, what a surprise;
```

update-grub

```
If we do not do that, what you did to those files will not matter, nothing will change from when you booted to MS last time.

That is because update-grub will re write you grub.cfg file and that is the one that gives you the menu on your screen when you boot.  If we do not run update-grub it will just be the same old crap.

Lets change that now.

I will move on to another OS.  This one seems fine.

---

### Post by itsvan on 2010-04-16
so to be sure i close everything,,Open a NEW terminal,,and then run update grup??? or am i missing something

---

### Post by ranch hand on 2010-04-16
> **itsvan said:**
> so to be sure i close everything,,Open a NEW terminal,,and then run update grup??? or am i missing something
You need to run the chroot script that you (I hope) saved to your installation.

If not;
```

#!/bin/sh

sudo mkdir /mnt/Karmic
sudo mount /dev/sda5 /mnt/Karmic/
sudo mount -o bind /proc /mnt/Karmic/proc
sudo mount -o bind /dev /mnt/Karmic/dev
sudo mount -o bind /dev/pts /mnt/Karmic/dev/pts
sudo mount -o bind /sys /mnt/Karmic/sys
sudo cp /etc/resolv.conf /mnt/Karmic/etc/resolve.conf
sudo chroot /mnt/Karmic /bin/bash

fi

```
Then run;
```

update-grub

```

---

### Post by itsvan on 2010-04-16
im still in the live cd though right???


root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-16
I hope you are.

I think that you ought to try the bugger out.  See if it will boot.

I think it will.

Give it a whack.

---

### Post by itsvan on 2010-04-16
ok wish me luck il be right back

---

### Post by itsvan on 2010-04-16
SIGH... still no luck,,,it still boots up into windows fine,,but no ubuntu....GRUB still shows up at the beginning for a second then couple of sentences like erros come up and boots directly into windows,,,it seems something is still off,or all the changes were doing or not being saved right...well im off for the night..tomorrow is another day:(

---

### Post by ranch hand on 2010-04-16
ok,  i am bummed.

And off to bed.

---

### Post by Silent Warrior on 2010-04-16
It looked to me like the above script missed mounting /boot. I'm not replying from the same page of the topic, so you may have to adapt this a little bit:
```
sudo mount -o bind /boot /mnt/Karmic/boot
```
Try adding that (and adapting as necessary) and give it one more try. Meanwhile, I'll go read through the rest of the topic. :)

Also, consider removing some kernels, if all those are installed. (When you can get back into Ubuntu, that is.) It'll save space, time for Grub-updating, and don't get me started on what it'll do for your mkinitramfs-runs.

---

### Post by ranch hand on 2010-04-16
Thanks.

While I have never had any trouble doing anything I have had to with that script, I am sure not real sure of myself when it comes to the ins and outs of chroot.  I will play with that on my bos in the morning.

I am going to have to have a new boot info script from him tomorrow too.  To see what we changed or failed to change.

This is a bugger.  I do not use MS so I am kind of ignorant there.  I do have 18 linux OS' booting from my internal drive with 12 of them on my external.  I am pretty good with grub usually.  This one is driving me right up the wall.

More eyes may see the simple thing that I am missing.  Could be I am the simple thing.

---

### Post by ed-koala on 2010-04-16
I am going to post my dual boot working files for folks to compare with.  I do have some raid stuff so you'll have to ignore that but hopefully one of the gurus here can do some comparisons and find the problem, assuming the problem is in Grub.  Obviously my sda/sdb stuff and uuid will be different too.

Folder /etc/grub.d files:

00_header:

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

cat << EOF
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  saved_entry=\${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF
```

10_Linux:

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  cat << EOF
menuentry "$1" {
        recordfail=1
        if [ -n \${have_grubenv} ]; then save_env recordfail; fi
EOF
  if [ "x$3" = "xquiet" ]; then
    cat << EOF
	set quiet=1
EOF
  fi
  save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
EOF
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

11_Windows:

```
#! /bin/sh -e
echo “Adding Windows” >&2
cat << EOF
menuentry “Windows_7&#8243; {
set root=(hd0,1)
chainloader +1
}
EOF
```

20_memtest86+:

```
#!/bin/sh
set -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

# older versions of grub2 do not have this yet (LP: #459080)
if [ ! -e ${libdir}/grub/grub-mkconfig_lib ]; then
    echo "no grub-mkconfig_lib, exiting"
    exit 0
fi

. ${libdir}/grub/grub-mkconfig_lib

# We can't cope with loop-mounted devices here.
case ${GRUB_DEVICE_BOOT} in
  /dev/loop/*|/dev/loop[0-9])
    exit 0
  ;;
esac

if test -e /boot/memtest86+.bin ; then
  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+.bin" )
  echo "Found memtest86+ image: $MEMTESTPATH" >&2
  cat << EOF
menuentry "Memory test (memtest86+)" {
	linux16	$MEMTESTPATH
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	$MEMTESTPATH console=ttyS0,115200n8
}
EOF
fi
```

30_os-prober:

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

         if [ "${LROOT}" != "${LBOOT}" ]; then
           LKERNEL="${LKERNEL#/boot}"
           LINITRD="${LINITRD#/boot}"
         fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
        cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
    ;;
    hurd|*)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```

40_custom:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

And finally /boot/grub.cfg:

```
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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows_7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Hope these help somehow.  :)

---

### Post by ed-koala on 2010-04-16
I also have another idea for a scorched earth approach if you are getting tired of fooling with this. Opinions on whether this is a good idea are welcome.

If you have enough free disk space, make a partition (ext3 or ext4), copy all the files you don't want to lose over to it.

Then, use gparted from the live CD and delete ALL your other partitions making them free space.

Next, make 1 partition as an NFTS partition for Windows. Leave the rest free space for your Ubuntu to be installed soon. 

Reinstall Windows 7 ... since Windows doesn't "see" ext partitions, your data is safe.

Reinstall Ubuntu. I'd suggest manual partitioning and then let the installer partition that free space for Ubuntu.

At this point you'll probably only need to edit /etc/default/grub to make grub list show up and add the windows entry.

Everything should then be working. You can then move the partitions around, if you want, using the LiveCD or copy your data back and get rid of that partition, adding the space to Ubuntu.

---

### Post by ranch hand on 2010-04-16
Well, I certainly like the looks of your Win menu entry.  Nice short and to the point.

The one we are using here is edited from another guys os-prober inspired entry generated in his grub.cfg file.

Just where in West by God Virginia are you?  I had a farm near Salem for 20 years.

---

### Post by ed-koala on 2010-04-16
South-central WV, in the mountains, nowhere close to anything. What's really hysterical is when you get on the interstate near me you see a sign saying I-64 High Tech Corridor ... and nothing for 20 miles either way but trees.

Hopefully once itsvan comes online one of my posts will help get him running smoothly. From my experience problems like this that give many hours of headaches seem to be the result of something that takes 2 lines of code and 60 seconds to fix, once you finally find the problem.  Just the way it is I guess.

---

### Post by itsvan on 2010-04-16
Hello everyone..i am ready to follow instructions...:popcorn:

---

### Post by ed-koala on 2010-04-16
How do you feel about reinstalls?  Got free room on your drives?  I posted a rather drastic solution I think should work, but I don't want you trying it without a little info first, assuming you even want to do something as drastic as reinstalls.

---

### Post by bcbc on 2010-04-16
What about oldFred's suggestion from post 125?

[http://ubuntuforums.org/showpost.php?p=9129160&postcount=125](http://ubuntuforums.org/showpost.php?p=9129160&postcount=125)

---

### Post by itsvan on 2010-04-16
Id rather avoid the reinstalls to be honest,,,i dont even have the windows 7 cd,,my friend had let me borrow it..is there no other way???

---

### Post by ed-koala on 2010-04-16
Right now I'm thinking a modified scorched earth approach getting rid of Ubuntu and fixing Windows might be best, but without a way to fix the MBR with a windows disk it won't work.

I'm thinking its probably best at this point to get one OS installed and working, fresh. Then do the other.  Since it is best to install Windows first, eliminating Ubuntu altogether and then repairing Windows might be your best bet.  Once it's booting up fine, then we get Ubuntu going.

Any thoughts folks?

---

### Post by oldfred on 2010-04-16
The chroot should not change any windows boot or files. It uses the liveCD to CHange ROOT to allow working inside a non-working system.

If you do not have a windows repair disk you must download this from neosmart for future use. It is just for repairs but when you need it you should already have it. Yesterday it was not working but I just checked and it is working again.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

Link to drs305 recommending chroot to uninstall & reinstall grub. He used sda7 but otherwise I think it is the same.
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

---

### Post by itsvan on 2010-04-16
The one OS that id rather not touch is Ubuntu,, cus thats where i have EVERYTHINGGGG..id be a real hastle to start all over..im downloading the Windows 7 repair disc

---

### Post by itsvan on 2010-04-16
ok its done

---

### Post by ed-koala on 2010-04-16
itsvan, I found this page on how to fix Windows 7 MBR.

[http://www.ehow.com/how_4836283_repair-mbr-windows.html]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")

Does your repair disk follow the same procedure?  I especially think the bootsect /nt60 ALL command listed there would be especially good to get rid of any excess boot stuff and get a clean Windows 7 MBR.

---

### Post by ranch hand on 2010-04-16
I just got home from the big city.  Need to unload the Dreaded Mother in Laws van.

I would really like to see another boot info script result.

If you are not that fond of Win7, dumping it would probably fix things quickly.  I just hate to give up on this but it is not my box.

---

### Post by ed-koala on 2010-04-16
itsvan, are you worried about reinstalling the Ubuntu software on a reinstall, or things like pictures, music, etc?

If all you are worried about is the latter, I think my prior suggestion is a good one ... make a new partition as things are now using free space, if you have enough, copy your precious files to it, and just nuke everything else.

At worst, you'll borrow the Windows DVD again for one last time, and this will *certainly* fix everything.

I'm not sure there's another way, I sure don't know of one but I'm not as expert as Ranch and oldfred on Grub.

---

### Post by itsvan on 2010-04-16
so the problem here is windows 7 not letting me go back into ubuntu or what??

---

### Post by ranch hand on 2010-04-16
No, you have a number of problems that all combine to give you the perfect storm of problems.

A>No MS install is real easy to install second.
B>The upgrade from grub-legacy in 9.04 to grub in 9.10 is badly flawed and caused many problems for many people.  You got that too.
C>grub1.97beta4 is not the best grub version but they are not backporting grub1.97 or grub1.98 to 9.10 (beats me why not).

I will admit right off that if you wiped your drive, leaving a backup partition for your data, installed MS and then installed Ubuntu it would probably work without a hitch.

You could also install Ubuntu on 2 partitions which is a lot safer to recover than doing it on one partition.

I would like to be able to get you into Ubuntu before doing that though as you could install "debfoster" and save the list of all packages installed to you back up partition.  This may well be possible through chroot and nautilus from the Live CD but I have never tried it.

I would really like a new boot info script to see exactly what is going on now.

---

### Post by ed-koala on 2010-04-16
I don't think so.  Windows is booting, so it seems to be ok.  I think Grub is the problem, somehow.

The only idea I can think of besides doing reinstalls is this ... Open Synaptic, search for Grub and Grub2, COMPLETELY remove all the grub packages, then do a file search and make sure files and folders like /etc/default/grub, /etc/grub.d and /boot/grub are gone .... basically nuke Grub as completely as you can.

This may cause you not to boot at all.  Two options here - repair Windows from the repair disk (recommended), or install Grub2 from a CD.

A fresh install should help, but it needs to really be fresh without any residual files still hanging around. Personally, I'd like to get one OS working first which is why I recommend doing windows repair even tho you'll be nuking it immediately after by installing grub.

After installing Grub2 I'm sure you'll lose Windows 7 booting, temporarily. This is easily fixed. We can fix it after Grub2 is installed and Ubuntu boots.

This is all I can think of.  I'll have to let greater minds go at it if this doesn't work.

---

### Post by ranch hand on 2010-04-16
We did purge and install grub.

We did not delete or rename the files (good practice as you may need them or information in them - they can be removed completely later).

That is why I want to get the boot info script output again.  To see why our last changes did not work.  I think they should have.

---

### Post by ed-koala on 2010-04-16
I saw you did the purge.  If I read it right though there were files still hanging around after doing the purge commands.

I'm not sure how that matters, but as I said, it's all I can think of to do ... as complete a scrub of Grub as possible, including all files and folders, then fix windows MBR, boot windows, then *** *because fixing the MBR from the windows repair disk will really kill grub in the MBR* ***, reinstall Grub2.

---

### Post by ranch hand on 2010-04-16
That is actually what  I am leaning toward too.

I do want to see what the boot info script has to say first.  The reason is that we killed the operation of major scripts and got the same result.  That means that we either did not kill those operations or something else is the problem.   I would like to see what is what.

That script was written and is maintained by 2 of the best grub guys around and it really does give you the info you need if you are smart enough to see it.

Some times I wonder.

---

### Post by ed-koala on 2010-04-16
I know I'm not smart enough to see it.  One thing you can count on though is Windows will surely screw any other operating system, so fixing windows will surely kill grub dead lol

Want me to repost my results.txt also to compare with?

---

### Post by itsvan on 2010-04-16
is there a way to delete everything but once i reinstall ubuntu have all the programs i installed back to normal?

---

### Post by itsvan on 2010-04-16
if you need any other data or info tell me..just give me some steps il send it

---

### Post by ranch hand on 2010-04-16
That is what debfoster does.  It gives you a list of all installed packages so that you can re install the ones you may have forgotten.

One advantage of going that route is that you will also loose a bunch of packages that are left on your system that are doing nothing at all as the are obsolete, have been superseded but not removed.

---

### Post by ranch hand on 2010-04-16
> **itsvan said:**
> if you need any other data or info tell me..just give me some steps il send it
Run that boot info script again please.

I am on a different install now and do not have the website at my finger tips but it is in this thread.

Got to go to another one right now to see if I can get it to work with the new updates from today (almost 200MB today in testing).

---

### Post by itsvan on 2010-04-16
```

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x843d9350

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,447,344   207,447,282   7 HPFS/NTFS
/dev/sda2         312,512,445   312,576,704        64,260  ef EFI (FAT-12/16/32)
/dev/sda3         207,447,345   312,512,444   105,065,100   5 Extended
/dev/sda5         207,447,408   308,126,699   100,679,292  83 Linux
/dev/sda6         308,126,763   312,512,444     4,385,682  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders, total 3894975 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6093840

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             16     3,894,974     3,894,959   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ACCC24DCCC222DD                       ntfs                                     
/dev/sda5        0c9b39c0-4d74-4508-8c9e-3e74332464dc   ext3       Karmic                        
/dev/sda6        1b39a4b8-618b-4dd5-93c6-254e4ad51960   swap                                     
/dev/sdb1        18AD-128F                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/18AD-128F         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
# kopt=root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c9b39c0-4d74-4508-8c9e-3e74332464dc

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b39a4b8-618b-4dd5-93c6-254e4ad51960 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/core.img
 142.8GB: boot/grub/grub.cfg
 150.7GB: boot/grub/menu.lst
 149.9GB: boot/grub/stage2
 149.8GB: boot/initrd.img-2.6.28-11-generic
 149.8GB: boot/initrd.img-2.6.28-15-generic
 149.8GB: boot/initrd.img-2.6.28-16-generic
 149.9GB: boot/initrd.img-2.6.31-15-generic
 149.8GB: boot/initrd.img-2.6.31-16-generic
 149.8GB: boot/initrd.img-2.6.31-17-generic
 149.9GB: boot/initrd.img-2.6.31-19-generic
 141.0GB: boot/initrd.img-2.6.31-20-generic
 149.9GB: boot/vmlinuz-2.6.28-11-generic
 149.8GB: boot/vmlinuz-2.6.28-15-generic
 149.9GB: boot/vmlinuz-2.6.28-16-generic
 149.9GB: boot/vmlinuz-2.6.31-15-generic
 149.8GB: boot/vmlinuz-2.6.31-16-generic
 149.9GB: boot/vmlinuz-2.6.31-17-generic
 149.8GB: boot/vmlinuz-2.6.31-19-generic
 157.6GB: boot/vmlinuz-2.6.31-20-generic
 141.0GB: initrd.img
 149.9GB: initrd.img.old
 157.6GB: vmlinuz
 149.8GB: vmlinuz.old

---

### Post by ranch hand on 2010-04-16
Thanks.

Copied to gedit so i can  read it and extract from it.

I will be back.

---

### Post by ranch hand on 2010-04-16
Ok all you MS users what if anything is wrong with this;
> 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

I am not sure why we need to "repair" MS.  It boots.  The above looks good to me but that is not saying much.

Elucidate me.

---

### Post by itsvan on 2010-04-16
Ya Windows is booting up fine,,the only thing that now is blocked is ubuntu...

---

### Post by ed-koala on 2010-04-16
Well, I suggested it for this reason - I'm assuming Grub is the bootloader right now, as windows won't even see ubuntu.  By fixing the MBR with windows repair, we kill any grub in the MBR.  If grub is the problem, it'll be gone totally that way.

---

### Post by ranch hand on 2010-04-16
Things that REALLY concern me.
> 
sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
/boot/grub/core.img

do not like the continued mention of menu.lst
> 
set default="0"

set timeout=10


All of the above, from the /etc/default/grub file was changed in nautilus and gedit as root.  Was not picked up by update-grub.
> 
### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
if keystatus; then
if keystatus --shift; then
set timeout=-1
else
set timeout=0
fi
else
if sleep --interruptible 3 ; then
set timeout=0
fi
fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 00acffe0acffcde2
drivemap -s (hd0) ${root}
chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###

These 2 scripts were changed in nautilus as root to not have permission to be executed as programs.  This was not picked up by update-grub.

This seems to me to mean that yes, a completely new and more complete assault on grub must be run including the displacement, renaming and/or deleting of files and directories is called for.  The bugger just doesn't work.

The good thing about this is that, hopefully, itsvan is learning a lot in a hurry.

I hold a grudge and MS has pissed me off for the last time.  I won't have it around.  Please keep this in mind in reading the following.

I would redo grub one more time.  At the rate we were going it could take 2 days.

Installing is easy.

You have a whole wasted partition to work with.  Just reformat sda1 to ext4.  Back up all files in home folder there and all .whatever (hidden) config files from home to there.

Attempt to chroot and install an run debfoster, generate list, save to sda1 with other backup files.

Reinstall where you have it now but on 2 partitions (one for root {/} and one for home {/home}).

Shift backup files back from sda1 and continue to use sda1 as a storage partition.

---

### Post by ranch hand on 2010-04-16
MS users I for got this one.  What in flinderation is it and why is it sdb?
> 
Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders, total 3894975 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6093840

Partition Boot Start End Size Id System

/dev/sdb1 * 16 3,894,974 3,894,959 b W95 FAT32


---

### Post by ed-koala on 2010-04-16
I might know that one ... supposedly Windows 7 makes a hidden/secret partition as a recovery area, that may be what it is as its FAT32, definitely something windows.

The more I see from Ranch, the more certain I'm getting that Grub is seriously screwed up somehow, and scorching it, and preferably Ubuntu itself (after saving files), thoroughly should fix things.

---

### Post by mal1958 on 2010-04-16
> **ed-koala said:**
> I might know that one ... supposedly Windows 7 makes a hidden/secret partition as a recovery area, that may be what it is as its FAT32, definitely something windows.

The more I see from Ranch, the more certain I'm getting that Grub is seriously screwed up somehow, and scorching it, and preferably Ubuntu itself (after saving files), thoroughly should fix things.

The Fat32 is a legacy from the older Windows 98 (OSR2) days.  The original Win98 shipped with the old Fat16 file system at first, but their rival IBM who had OS2 WarP out, could read that easily and move files between the two OS's with out much problem. That prompted Microscroft to put out a patch that updated the whole OS.  They didn't want any other OS to beable to read their file table so they made it impossible.  They did it for the money and to remove any possible competition, but managed to spin themselves clean on it anyway by claiming that fat32 was the most efficient file system around.  Despite the fact that OS2 Warp used a varible cluster size, not the fixed cluster size that FAT 16 or 32 used.  The newer Window releases use either Fat32 or NTSF file system now.

Mike

---

### Post by ranch hand on 2010-04-16
> **ed-koala said:**
> I might know that one ... supposedly Windows 7 makes a hidden/secret partition as a recovery area, that may be what it is as its FAT32, definitely something windows.

The more I see from Ranch, the more certain I'm getting that Grub is seriously screwed up somehow, and scorching it, and preferably Ubuntu itself (after saving files), thoroughly should fix things.
You know, this is the kind of crap that got me to switch to Linux.  It makes the veins stick out on my neck.

I figure I owe the good folks at MS thanks.  If vista had not been a downgrade from 98 I would still be using their OS and probably had a stroke by now.

---

### Post by itsvan on 2010-04-17
ya i sure am learning alot of things little by little haha...:)

---

### Post by mal1958 on 2010-04-17
> **itsvan said:**
> ya i sure am learning alot of things little by little haha...:)

That is how we all got our start in things, itsvan.  Soon, you will be giving advice, and help to somebody else, and they will probably say the same thing to you. :lolflag:

---

### Post by itsvan on 2010-04-17
So what steps should i follow???

---

### Post by ed-koala on 2010-04-17
Basically my post 163 and Ranch's post 177 are doing the same thing. Copying files you want to save, purging grub thoroughly, fix the MBR and reinstall Grub.

As Ranch is a more experienced and knowledgable user than I, I'd follow his instructions.

---

### Post by ranch hand on 2010-04-17
What are we going to do here.  There are many suggestions on how to proceed, all pretty good.

The thing is, it is your box.  What do you want to do?

---

### Post by itsvan on 2010-04-17
Ideally id like to some how fix whatever it is without reinstalling everything,,,i mean both are running fine,,its just the boot that is really messing things up,,obviously we have tried couple of things with no succes...if there is any other thing maybe we can try again..

IF All else fails,,and if we do go with cleaning out everything id still like a change to save all the files and programs i have from Ubuntu...

---

### Post by ranch hand on 2010-04-17
First, you are on a 160Gb HDD.  You have nowhere near that much data.   If it comes to redoing your drive we can pretty easily save all that to a new partition (or your sda1 partition now taken up by up by some weird off brand OS).

As for the programs that is easier if we can actually boot into the system but not that tough even from the live CD.
> 
debfoster is a wrapper program for apt and dpkg.  When first run, it
will ask you which of the installed packages you want to keep
installed.

After that, it maintains a list of packages that you want to have
installed on your system.  It uses this list to detect packages that
have been installed only because other packages depended on them.  If
one of these dependencies changes, debfoster will take notice, and
ask if you want to remove the old package.

This helps you to maintain a clean Debian install, without old
(mainly library) packages lying around that aren't used any more.

Canonical does not provide updates for debfoster. Some updates may be provided by the Ubuntu community.

That is the package needed to get a list of what is installed.   You save that list and there is a way to have dpkg (the thing that really does your package management, apt, aptitude, etc are built on top of it) use that list to reinstall the stuff or just use the list your self and install from it using apt or synaptic or aptitude.

You could also, if installing 9.10 as you have now, copy your /var/cache/apt/archives directory to your backup.  It contains the .deb from every thing you installed.  You could get it all from there.  This is not as easy as it sound but it is possible.

Basically, yes, barring major problems that are a slim possibility, your system can be restored to what you have now and probably work somewhat better with some of the unused crap cleared out.

Second I think that we can get you to booting to Ubuntu, which, to me, seems like the important thing here.

You need to boot to the live CD and run gparted (System>Administration>GParted (in some versions it is Partition Editor in that menu) and send us a screen shot so we know exactly what we are dealing with here.

Then we can deal with grub harshly and see what we can do.

---

### Post by itsvan on 2010-04-17
Ok how can i take a picture of gparted and how do i post it on here?

---

### Post by ranch hand on 2010-04-17
When you have grub up, go to Applications>Accessories>Take Screen Shot.  Open that and click "Take Screen Shot".  It should ask if you want it saved to the desktop.  Click "OK".

On the forum page you will see an option for "New Reply" on the left side opposite the page numbers.  Click on that.

Below the message box there or "Additional Options".  One of them is "Manage Attachments" Click on that and follow the directions.

---

### Post by itsvan on 2010-04-17
hers the pic

---

### Post by ranch hand on 2010-04-17
I have no objection to redoing grub again, we  had it booting to Ubuntu earlier we should be able to doe that again.

However, as new as I am to Linux myself, I really like to see the partitions in a graphic manner.  Now that I see it there are some things about it that have been nagging me from reading the info on the boot info script.

Sda2 is what it boils down to.  This is not a healthy partition and it is not used.  You really should consider, at some point.   Redoing your drive.

If Ubuntu is your main OS then the ntfs partition is way too big.  Even if I would let it on my box it sure would not be bigger than 50GB.

Your Ubuntu should be installed on 2 partitions so that your data is much safer if you have to reinstall.

So, sda1 should be resized down to 50GB, sda2 deleted, sda3 resized both directions to take up the unused space left from the sda1 resize and the sda2 deletion.

Right now you are pushing sda5 pretty hard for space.  You have it 80% used.  This is not a real emergency but it is not a real good thing either.  If it had a little room to breath it would work faster for one thing.

Think about those points, but let us move on.

Open nautilus as root and go to /boot/grub and delete /menu.lst.

Then open the chroot script and run it and then when it is up run;
```

apt-get update

```
so that we know we have a connection.

---

### Post by itsvan on 2010-04-17
i completely agree on all those points,and i am willing to do all of that....


- i do not see that menu list under boot/grub

---

### Post by ranch hand on 2010-04-17
We are getting is on the boot info script results.  It has to be there.  It is listed as "menu.lst" not "menu.list".

If it is not there, we have a problem.

---

### Post by itsvan on 2010-04-17
if i had to guess it is possible im looking in the wrong place i get mixed up all the time...but all i see is a file called  GRUBENV

---

### Post by ranch hand on 2010-04-17
I am assuming that the upper case letters are yours not the actual file name.  That is a correct file to be in there but there should be a lot more.

If you are worried about being lost here are the directions just to be sure.

In nautilus go to left pane
Bring up "file system"
In main window bring up "boot"
In boot bring up "grub"
In grub hit "m" on the keyboard, then "e" and then "n"

If menu.lst is in there it should be close to where that brought you.

---

### Post by itsvan on 2010-04-17
ya grubenv is the ONLY file in that folder..nothing else...

---

### Post by ranch hand on 2010-04-17
Go to /boot and right click on the grub file.  Send it to Trash.

Go to /etc and click on "File" (upper right of screen) sellect and click on "create new folder".

Name folder "A"

Go to /etc/grub.d and right click on /06_custom and select "copy"

Go to /etc/A and right click on it and select "paste"

Open /A and make sure /06_custom is there.

Go to /etc and right click on /grub.d.  Send it to trash.

I had the above written ahead on gedit.

We need a to decide if you want to try to repair grub again or start over with a new install.  I think repairing is a good idea first and then do the reinstall after saving things from inside the OS but we can do it from the live CD too without much difficulty.

---

### Post by itsvan on 2010-04-17
so everything was going fine, untl i find out there is no 06_custom file in the folder.....its weird because ive seen it there before,,but its gone now...what the heck!!! maybe all of these things are not letting ubuntu boot up???

---

### Post by ranch hand on 2010-04-17
Ok, that is fine, all we had in there was the MS menu entry and I have that anyway.  I only have five files on this thread so far.

Just delete the grub.d folder.

Then get the chroot script running and run;
```

apt-get update

```
this will make sure we have a connection.

You will not be able to boot to anything but the Live CD for a while now so don't reboot and try anything else

Do you use more than one workspace (applet on bottom panel left end with boxes in it).  I use six of the buggers most use four.

You could leave nautilus as root on one and go to another space for the chroot terminal.

---

### Post by ed-koala on 2010-04-17
I'm back online and following progress,ready to help if necessary (but ranch hand looks well in control)  :)

---

### Post by ranch hand on 2010-04-17
I like your sig.  I don't game at all so I see no reason for MS at all, not even the poor one that you need it for games.

My son plays games on his box.  He has been using Ubuntu for at least 2 years longer than I have.  He doesn't seem to be suffering.

---

### Post by ed-koala on 2010-04-17
I ran without MS for a couple of years, just recently I broke down and put a copy on for a few games I might want to play occasionally.

I got by fine with Wine and WoW mostly. Eh, I won't use it much, but I have the room so wtf huh?

---

### Post by itsvan on 2010-04-17
heres my output,,,,dont know if i did it wrong or not


mkdir: cannot create directory `/mnt/Karmic': File exists
mount: /dev/sda5 already mounted or /mnt/Karmic/ busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt/Karmic
root@ubuntu:/# apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# 
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-17
Ok go back to the nautilus screen and go to /etc and look at the resolv.conf file (that is spelled right).

I bet it doesn't have an like "nameserver 10.0.0.2" in it.  If not, put that in, save the file and try the chroot again.  I do notthink it is going to work because that is the one for my box, connection and ISP but that is all I can think of.

No it is not, you could check the same file in the file system of the Live session and see if it has an entry like that.  If so that would work.  You will have to paste that in as root in nautilus and save the file.

If you can't get it to work let us know.

---

### Post by ranch hand on 2010-04-17
I have got to run out for a few and pick up the wife.

Be back soon.

---

### Post by itsvan on 2010-04-17
OK ya it wasnt there,,so i pasted it and its saved now:P

---

### Post by ranch hand on 2010-04-17
It was there before.  I think you have some very serious basic problems with your system.  That is the file that alows us to connect in a chroot environment.

Does the box connect now?

---

### Post by itsvan on 2010-04-17
by connect do you mean run the update???? speaking of,,do i run the code in the same terminal as root,,or a brand new one

---

### Post by ranch hand on 2010-04-17
Sorry for the delay. I was on the phone to a potential boss.  Been living in town for a year unemployed.

Don't make a good town dog.  My cattle dog doesn't make a good town dog.  My horse is earning her keep at a ranch south of town.  We need to be together, the hell out of town.

Times are not real good in agriculture these days.  I hope I can land this job.

If you  still have the chroot terminal open you should be able to hit the up arrow key and have the same command come right back up.  Just hit enter and see if it goes.

---

### Post by ranch hand on 2010-04-18
I have to get off here.

If that didn't work, I have one thing that I am going to try on an install of 9.10 of mine in chroot to install grub-pc and grub-common.

I would like you to let me know when you will be on tomorrow.  And we will try to get this to some kind of resolution, one way or the other.

---

### Post by ranch hand on 2010-04-18
I dropped you a PM.  You will have to go to your "User CP" to pick it up (top right of this page).

---

### Post by ranch hand on 2010-04-18
Yes I think that we can get grub back on there fine.  And use a newer version as well.  Without a network connection to your chroot environment.

---

### Post by itsvan on 2010-04-18
SO i have a bit of a problem right now,,i need to do a big report for tomorrow for school..and im on windows,,and i dont have the disc to reinstall it at all,,and i know reformatting everything is part of getting my pc back on its feet..but is there any way to maybe prolong deleting windows for the day..or what can we do?

---

### Post by ranch hand on 2010-04-18
I am not into deleting windows at all if you want to keep it.

If you are working on home work I would leave things alone until you have some breathing room.

It is never a good idea to rush when doing these things.  Almost always causes more problems that could have been avoided by going slowly and achieving success.

I would like to know if you are on a 32bit (386) box or 64bit.  I can drop you the files for either version of grub from here as I have both versions install.

I am on a 64 bit box so I have no trouble with either.

The next time you are on the Live CD, if you do not know the answer, run;
```

uname -a

```and post the results.

Mine looks like this;
```

sam@sam-desktop:~$ uname -a
Linux sam-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
sam@sam-desktop:~$ 

```this indicates that I am running the 64bit kernel right now (x86_64).

I have a folder for this thread and in it, right now, are;
> 
sam@sam-desktop:~$ ls /home/sam/Desktop/Grub-Prob
grub-common_1.98-1ubuntu5_amd64.deb  Grub-Problem0
grub-common_1.98-1ubuntu5_i386.deb   Grub-Problem1
grub-pc_1.98-1ubuntu5_amd64.deb      Grub-Problem1a
grub-pc_1.98-1ubuntu5_i386.deb       Grub-Problem.png
Grub-Problem
sam@sam-desktop:~$
As you can see, there are the grub-pc and grub-common .deb packages for both 32 and 64 bit systems.

Just let me know when you are ready.

Did you see the PMs I sent you?

---

### Post by itsvan on 2010-04-18
im running 32 bit architecture....if you want we can take the day off,,and maybe start working on everything tomorrow or later today when i have most of my work done,,i dont want to risk not being able to boot into any of them,,,so ideally what should be done? reinstall both right?? or is it one of them causing the problem?

---

### Post by ranch hand on 2010-04-18
I am trying to leave them both installed and get a grub that will work with both OS'.  If we can achieve that then we can worry about cleaning up your partition table, and maybe shrinking XP to a reasonable size but we need input from MS users on the advisablity of doing that with gparted.

Let us see if we can get grub straight first.

On that note - How are you booting to MS?  Did you restore its boot loader to the MBR?

---

### Post by itsvan on 2010-04-18
oh ok that sounds good,,,well to be honest ive put in so many codes i dont even know what i did,,,but i just turn on the computer, the word GRUB shows up on the top left,,some error senteces come up afer,,and it boots straight into windows 7 with no problem....but no sign of ubuntu now,,and last time,,when ubuntu was working,,it whouldnt boot into windows.

---

### Post by ed-koala on 2010-04-18
Wouldn't boot? Or there just wasn't a windows entry in the grub list?  The latter is normal until fixed.

---

### Post by ranch hand on 2010-04-18
> **ed-koala said:**
> Wouldn't boot? Or there just wasn't a windows entry in the grub list?  The latter is normal until fixed.
The problem is that Ubuntu is not showing at all on the screen menu.

The having grub screwed on upgrades from 9.04 to 9.10 is all too common.

Add to that the fact that we started 10.04 testing with grub1.97 not 1.97beta4 and are now on the 5th version of 1.98 means that the grub in 9.10 is badly out dated even if done on a clean install.

I think that transplanting grub1.98 to his Ubuntu will fix that problem.

---

### Post by itsvan on 2010-04-18
There is no GRUB Menu AT ALL!...only the word GRUB shows up on the screem and nothing else,,,,there is no list or anyting else..it just boots up into windows,,and last time it was the same only that it booted into ubuntu instead

---

### Post by ranch hand on 2010-04-18
I wouldn't worry about that.  You just have a very badly corrupted grub.  We will replace the whole deal with a newer, better version.

Pretty much a root nautilus operation until the end when we will chroot in and run update-grub and grub-install to get the new version on the MBR.

Before we do the chroot work we will take a close look at several of the grub files to make sure we have the right stuff and usable configuration.

---

### Post by itsvan on 2010-04-18
ok sounds good,,ya i think all of GRUB is so messed up right now,,we need to do a fresh install of it

---

### Post by ranch hand on 2010-04-18
When we tried that before it still came up bad.  That is why I wanted to try the new version and a "transplant" out here first.

It could be that your Ubuntu install has just been too corrupted too but that is another matter and we are trying to avoid reinstalling any OS here.

You have data on Ubuntu you don't want to loose and MS that you do not have an install disk for.

Giving another shot at salvaging things is a good idea.

We can try to fix things better later when you have a little more confidence.  A success at this would help in that direction too.

---

### Post by itsvan on 2010-04-18
Ya i agree,,,il be on later on in a bit,,and we can start working on it,,but for now im gonna try to get some work done,,il let you to your duities, see ya in a few

---

### Post by ed-koala on 2010-04-18
I'm curious about something itsvan.  Could you post the contents of your /etc/default/grub file for me?

---

### Post by itsvan on 2010-04-18
Heres what i got Ed-Koala'


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by ed-koala on 2010-04-18
I have an errand for you...

Open the file /etc/default/grub and edit the line GRUB_HIDDEN_TIMEOUT=0 to read # GRUB_HIDDEN_TIMEOUT=0

then open a terminal and run update-grub ... getting late, not sure its needed but it can't hurt.

This will make the grub menu show up when you boot.  Reboot and make a note of what you see ... I want to know if there is a windows entry as well as ubuntu entries.

---

### Post by ranch hand on 2010-04-18
That default "0" was supposed to be changed as was the time out default.

Non of that was done when update-grub was run.  It should have changed to "1" and "30".

Oh well, to late now.

We will wait either for a response from him or until tomorrow to do this, up to you.

---

### Post by ed-koala on 2010-04-18
I'm just directly commenting out the line so grub will show, then when he boots he'll see what it says, and maybe it'll tell us something.  Won't take him long to do this.

---

### Post by ranch hand on 2010-04-18
I was going to have him delete the bugger along with /etc/grub.d and /boot/grub and /var/cache/apt/archives/<all grub, grub-pc and grub-common .debs>.

I have the i386 .deb packages to send to him for grub-pc and grub-common version 1.98 to copy/paste to /var/cache/apt/archives.  Then run "apt-get install --reinstall grub-pc grub-common.  This should install grub1.98, a much improved grub, and all associated files.  Tried  it out on one of my installs earlier and it worked with no network connection.

Do you, ed-koala, know if we can re rise the partition with MS on it with gparted?  Well I know we can but is this likely to ruin MS when we do it?

---

### Post by itsvan on 2010-04-18
so wait what do i change the default time to be???

---

### Post by ed-koala on 2010-04-18
ranch, with windows 7 I'm not sure but I suspect it'll probably ruin windows using gparted.

itsvan, don't change the time at all, just put a # in front of the line like I showed, with a space between the # and the words, that will just make it show up.  Make sure you do the correct line.

ranch, this should only take a minute, then I think your ideas are good.  I really want to see what his list looks like before we kill it all.

---

### Post by RetchingRabbit on 2010-04-18
This is freaking amazing. 23 (TWENTY-THREE) pages (PAGES!!!) of to and fro about how to reinstall grub?!
Use Mepis. It has the gui tools to do this from a live cd without (WITHOUT!!!) the terminal....

Another fine example of the futility of "cutting edge" for the average user. GRUB2 is not ready for production. GRUB (one) has no problems.

---

### Post by ranch hand on 2010-04-18
Grub legacy is no longer supported, if we like it or not, grub has moved on.

This particular user has little experience and a fairly well corrupted system.  This type of comment is not what is needed.

Try reading the 23 pages before jumping to conclusions.

---

### Post by itsvan on 2010-04-18
this is the output..now i will reboot

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/5ACCC24DCCC222DD: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done
root@ubuntu:/#

---

### Post by ed-koala on 2010-04-18
Besides, this way is a learning experience.  It's easy to nuke everything and start over, but what do you learn?  This way, if another problem pops up down the road, he, and I for that matter, will be better equipped to fix it.

---

### Post by ed-koala on 2010-04-18
If you boot right up into Ubuntu now, after the time runs out, or you select an entry, you are almost done!!

I know exactly how to make Windows show up in your list so you can choose it to boot to.

If you want to fiddle with it further though ...

---

### Post by itsvan on 2010-04-18
ya i have learned a bit i must say haha....anyway,,so i reboot,,but still the same,,the GRUB menu still doesnt pop up,,i dont know why the heck it doesnt,,it only boots straight to windows,,unless im doing it completely wrong...but i dont think so

it only shows

GRUB


and then some windows errors like split second speed,,then it boots directly into windows 7 with no problem

---

### Post by ed-koala on 2010-04-18
Time to go with ranch's instructions, we gotta thoroughly nuke grub. (I really recommend fixing the MBR with the windows disk afterward, just to wipe any trace of grub.) Then do a reinstall as ranch suggests.

---

### Post by ranch hand on 2010-04-18
@ed
I really would like to know, for when we get this fixed, if we can safely resize MS using gparted.  I am sure we can do Ubuntu.  I just finished one (shrink) and checked it and have finished the other (expand) but have not checked it (I know it is good any way).

@itsvan
It is getting pretty late.  Are you sure you want to do this now?

---

### Post by ed-koala on 2010-04-18
Do not use gparted to shrink the windows 7 partition.  I did a search and found this [URL="http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html"] which is what I already figured, it'll probably screw up your windows stuff.

[http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html]("http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html")

---

### Post by ranch hand on 2010-04-18
This is XP we are working with here though, is it more robust?  I have only fooled with the recovery partition of Vista and it was no trouble, worked just as poorly when I finished as when I started.

---

### Post by ed-koala on 2010-04-19
Oh, XP shouldn't be any problem.  It's the newer Windows stuff that's gotten picky, as usual. MS just hates anything else mucking with it. And it doesn't play nice with anything either, as we know.

---

### Post by ranch hand on 2010-04-19
So when we get grub straight, we could resize XP down to 50GB, delete that little ugly bugger way at the end of the drive, expand the extend partition both ways, move swap to the end and create move the entire ubuntu install down into the unused space below it and then create a small partition at the other end for back up and reinstall Ubuntu, clean, on 2 partitions and ext4.

This would, I think, make the bugger very solid and reliable for the next year of life for support of 9.10 and make XP boot fine also.

We do need to check when done installing the new grub, but I have a lot of faith in it booting to Ubuntu on reboot, even if MS doesn't show on the menu, and booting to both if update grub is run from Ubuntu once booted into.  That version of grub is a lot better if you haven't tried 10.04 yet.

Does that sound safe for XP to you?

---

### Post by ed-koala on 2010-04-19
Yes.  Grub should also spot XP just fine too.  I'd say it's time to roll with this and finally fix itsvan's system once and for all :)

---

### Post by ranch hand on 2010-04-19
I don't know about you and him but I am ready to take a break from thinking.  Both my resizings worked and the one I made bigger boots again (testing is a lot of FUN) for the first time in several days.

I don't think it really need the extra room but I had to purge grub-power-manager (which removed ubuntu-desktop) and reinstall gnome-power-manager.  Ubuntu-desktop is a meta package that you don't really need but there may be some things (not real important) that may not get updated and some things (I doubt it at  this stage of development) that may not get installed so I will put it on before updating tomorrow.

Hopefully the ISO for 10.04RC will be out for testing tomorrow so I will have to down load it and test if it works or not.  I do the 64 bit Live Session and Manual Install tests.  One of these days I want to do the OEM test.

That is the type of install for people selling computers preinstalled with Ubuntu.  So the first time you boot you get to set your user and password and all that jazz.

This testing is important.  It is how we can be confident on release day (Thursday) that the RC ISO will boot to peoples boxes  and install correctly.  Besides that it is FUN.

---

### Post by itsvan on 2010-04-19
I dont even know what half of that stuff is,,but im down lol

---

### Post by ranch hand on 2010-04-19
I'll see you folks on here tomorrow and we will whip this thing into shape.

I am done in for the night.

---

### Post by ranch hand on 2010-04-19
> **itsvan said:**
> I dont even know what half of that stuff is,,but im down lol
Pre release testing is a lot of fun if you do not mind the fact that it WILL crash, fail to boot, boot but fail to have a desktop, all sorts of things.

The devs only have a limited amount of hard ware to test on.  There is a lot of different hardware out there.  So this stuff is thrown out to the nuts to try it out.  Our job is not to get it to run but to have it break, file bug reports and let the devs fix it.

Now we do come up with some work arounds which make things work sometimes but the real idea is to just have it on as much different hardware as possible and then the devs can make it work.

The ISO is what you down load and burn to your CD or DVD.  There is the same problems there with booting and so forth but also the installer has to work.  I just finished burning the RC (release cndidate) ISO to a CD and will be installing it shortly to see if the Live Session works, the installer will work with manual partitioning (I always use 2 partitions) and if I have time I will install it again (I have pair of partitions that are just for ISO testing) to see what the OEM (original equipment manufacturer) install is all about and if it works.

As for the trouble I was having with one of my installs, it was just part of the FUN  of testing.  These things happen.  They happen so that, hopefully, when you, for instance, download the ISO of the final release it will boot to your computer, install on your computer, run on your computer.

Just my little contribution and one dandy way to learn a lot about the system and how to deal with problems.

---

### Post by ed-koala on 2010-04-19
I believe I learned something about the latest version of Grub2 today.

Seems like, for me, update-grub wasn't working.  I think you may now have to use the sudo grub-mkcfg -o /boot/grub/grub.cfg command to get it to update properly.

Strange, but it finally worked for me after upgrading to Lucid.

---

### Post by ranch hand on 2010-04-19
grub-mkconfig is not really enabled in the version (1.97beta4) used in 9.10.  It came in with 1.97 real early in 10.04 testing.  update-grub still works in 1.98 which is what we are using now.

It was the failure of update-grub that convinced me that just wiping the thing in an aggressive manner was the only solution.  If that is not working you just do not have grub in a usable condition at all.

Grub1.98 that you are using now is just a lot better version.  I just got done installing from the LiveCD checking it and then installing over that with the OEM install and playing with that (RC ISO testing).  Looking good on my hardware anyway.

I think we may get another image to test there were fails on both the i386 and amd64 desktops.  Bugs filed and all that.

I saw a new post here when I got back from new install land and thought the fun had started.

---

### Post by ed-koala on 2010-04-19
It did start, for me. I took the plunge and installed Lucid, and then Grub went wonky.  Couldn't get my changes to take effect, but then using that new command they did show up, finally.

---

### Post by ranch hand on 2010-04-19
Yes, update-grub is an old grub-legacy command that has been kept around for comfort sake.  It usually still works by itself but yes it is better with grub-mkconfig.  I always use that anyway as it is the easiest way to take a look at the results.

---

### Post by itsvan on 2010-04-19
sorry guys just got home,,its probably to late to start this whole thing..maybe tomorrow? its up to you guys

---

### Post by ranch hand on 2010-04-19
Tomorrow sounds better to me.  If we can start earlier we will be in less of a hurry and less groggy when getting to the end when we do not want to make any mistakes.

---

### Post by itsvan on 2010-04-19
i should be home from school around 2,,il sign on asap

---

### Post by ranch hand on 2010-04-20
What time aone are you in anyway?

---

### Post by itsvan on 2010-04-20
im in California

---

### Post by ranch hand on 2010-04-20
OK, so around about 3 here.  I should be here.

---

### Post by QLee on 2010-04-20
> **ranch hand said:**
> Yes, update-grub is an old grub-legacy command that has been kept around for comfort sake.  It usually still works by itself but yes it is better with grub-mkconfig.  I always use that anyway as it is the easiest way to take a look at the results.

I don't want to get in the way here and I am aware that "too many cooks spoil the broth" but you're not explaining this correctly Ranch Hand. The command update-grub is an alias for "grub-mkconfig -o /boot/grub/grub.cfg" it's what generates the grub2 config file. You should get the same results from using either, and I wouldn't expect different results if you run them in succession.

I'll let you guys go back to having fun now, wow lots of pages.

---

### Post by ranch hand on 2010-04-20
You are correct.  I have a tendency to simplify things for clarity for folks that have not read the grub wiki.  This does cause problems for folks that have a better understanding.

I much prefer grub-mkconfig as it throws you the grub.cfg file at the same time.  Much better than the output from update-grub which just doesn't give a whole lot of data.

Os-prober, for instance, in my setup, actually lists every OS on my drive in every partition.  Only the first entry generated for each partition is correct.  This is not reflected in the out put from update-grub.  I believe this is caused by my use of custom entries for all OS' and it screws with os-prober in some way.  It also gives me a very long grub.cfg file with 12 OS' on the drive as you can imagine (a little math will show this to be gross with all 12 listed 12 times).  I disable 30_os-prober as soon as I have the custom menu setup so I do not have to deal with this.

---

### Post by QLee on 2010-04-20
> **ranch hand said:**
> You are correct.  I have a tendency to simplify things for clarity for folks that have not read the grub wiki.  This does cause problems for folks that have a better understanding.

It's not going to cause big problems for those who have read the wiki or who have a "better" understanding. The danger is one of misleading "lurkers" who won't ask for clarification and thus end up with an incorrect impression. Sometimes in the forum we even see people link to incorrect information and thus perpetuate it. One of the strengths of a help forum like this is that there is peer review which helps to keep our information factual. That's one way we work together so that we all become more proficient.

---

### Post by itsvan on 2010-04-20
ok jsut got home,,,what do i need for the installation

---

### Post by ranch hand on 2010-04-20
Hold on a minute and I will drop you the files.

Meanwhile you can get into root nautilus from the Live CD (gksudo nautilus) and go to /var/cache/apt/archives and delete all files (.deb) having to do with grub, grub-pc and grub-common.

Then move to /etc/default and delete the grub file.

Then move to /etc and delete the grub.d directory (folder).

---

### Post by ranch hand on 2010-04-20
When you have finished that go, still in nautilus as root to file system /home/<your user name>/Desktop

After you are there right click on these files from this post and save them (save as) to the Desktop where you can then grab them fro nautilus root.

Copy paste them (as root) to /var/cache/apt/archives (just right click on that directory (folder) and hit paste.  Next open that directory and make sure they are there.

What ever the out come let us know.

---

### Post by ranch hand on 2010-04-20
You will have to hold on I am having trouble with the attachment.  Just work up to that point and I will have them.  I think I have a problem with making a gz file here on this install.  Or I could just be making a mistake.

---

### Post by ranch hand on 2010-04-20
here

[ Download grub-pc_1.98-1ubuntu5_i386.deb for free on uploading.com]("http://uploading.com/files/c1mmfmd9/grub-pc_1.98-1ubuntu5_i386.deb/")

[ Download grub-common_1.98-1ubuntu5_i386.deb for free on uploading.com]("http://uploading.com/files/62m75e1f/grub-common_1.98-1ubuntu5_i386.deb/")

try this

---

### Post by itsvan on 2010-04-20
the only thing in ARCHIVES is a folder called PARTIAL which is empt and a file called LOCK

---

### Post by ranch hand on 2010-04-20
You come up with the most interesting stuff.

This is mine;
```

sam@sam-desktop:~$ ls /var/cache/apt/archives
app-install-data_0.10.04.7_all.deb
apport_1.13.3-0ubuntu2_all.deb
apport-gtk_1.13.3-0ubuntu1_all.deb
apport-gtk_1.13.3-0ubuntu2_all.deb
apt_0.7.25.3ubuntu7_amd64.deb
aptdaemon_0.11+bzr345-0ubuntu4_all.deb
apt-transport-https_0.7.25.3ubuntu7_amd64.deb
apt-utils_0.7.25.3ubuntu7_amd64.deb
at-spi_1.30.0-0ubuntu2_amd64.deb
base-files_5.0.0ubuntu18_amd64.deb
bash_4.1-2ubuntu3_amd64.deb
bash-completion_1%3a1.1-3ubuntu2_all.deb
binutils_2.20.1-3ubuntu5_amd64.deb
bogofilter_1.2.1-0ubuntu1_amd64.deb
bogofilter-bdb_1.2.1-0ubuntu1_amd64.deb
bogofilter-common_1.2.1-0ubuntu1_all.deb
busybox-initramfs_1%3a1.13.3-1ubuntu10_amd64.deb
busybox-static_1%3a1.13.3-1ubuntu10_amd64.deb
byobu_2.68-0ubuntu1_all.deb
casper_1.235_amd64.deb
clamav_0.96+dfsg-1ubuntu2_amd64.deb
clamav-base_0.96+dfsg-1ubuntu2_all.deb
clamav-freshclam_0.96+dfsg-1ubuntu2_amd64.deb
command-not-found_0.2.40ubuntu5_all.deb
command-not-found-data_0.2.40ubuntu5_amd64.deb
console-setup_1.34ubuntu14_all.deb
cron_3.0pl1-106ubuntu5_amd64.deb
defoma_0.11.10-4ubuntu1_all.deb
desktopcouch_0.6.4-0ubuntu2_all.deb
devscripts_2.10.61ubuntu5_amd64.deb
dmraid_1.0.0.rc16-3ubuntu2_amd64.deb
dpkg_1.15.5.6ubuntu4_amd64.deb
dpkg-dev_1.15.5.6ubuntu4_all.deb
e2fslibs_1.41.11-1ubuntu2_amd64.deb
e2fsprogs_1.41.11-1ubuntu2_amd64.deb
empathy_2.30.0.1-0ubuntu3_amd64.deb
empathy-common_2.30.0.1-0ubuntu3_all.deb
evolution_2.28.3-0ubuntu9_amd64.deb
evolution-common_2.28.3-0ubuntu9_all.deb
evolution-data-server_2.28.3.1-0ubuntu2_amd64.deb
evolution-data-server-common_2.28.3.1-0ubuntu2_all.deb
evolution-plugins_2.28.3-0ubuntu9_amd64.deb
fglrx-modaliases_2%3a8.723.1-0ubuntu2_amd64.deb
firefox-3.5-gnome-support_3.6.3+nobinonly-0ubuntu3_all.deb
firefox_3.6.3+nobinonly-0ubuntu3_amd64.deb
firefox-branding_3.6.3+nobinonly-0ubuntu3_amd64.deb
firefox-gnome-support_3.6.3+nobinonly-0ubuntu3_amd64.deb
gdm_2.30.0-0ubuntu5_amd64.deb
gdm-guest-session_0.15_all.deb
gedit_2.30.0git20100413-0ubuntu1_amd64.deb
gedit-common_2.30.0git20100413-0ubuntu1_all.deb
gnome-app-install_2.0.1_all.deb
gnome-app-install_2.0.2_all.deb
gnome-app-install_2.0_all.deb
gnome-applets_2.30.0-0ubuntu2_amd64.deb
gnome-applets-data_2.30.0-0ubuntu2_all.deb
gnome-doc-utils_0.20.0-0ubuntu2_all.deb
gnome-orca_2.30.0-0ubuntu3_all.deb
gnome-settings-daemon_2.30.0-0ubuntu4_amd64.deb
gnome-settings-daemon_2.30.0-0ubuntu5_amd64.deb
gnome-system-tools_2.30.0-0ubuntu2_amd64.deb
gnome-user-guide_2.30.0+git20100403ubuntu2_all.deb
gnome-user-guide-en_2.30.0+git20100403ubuntu2_all.deb
gthumb_3%3a2.11.2.1.is.2.10.11-0ubuntu1_amd64.deb
gthumb-data_3%3a2.11.2.1.is.2.10.11-0ubuntu1_all.deb
gvfs_1.6.0+git20100414-0ubuntu1_amd64.deb
gvfs-backends_1.6.0+git20100414-0ubuntu1_amd64.deb
gvfs-bin_1.6.0+git20100414-0ubuntu1_amd64.deb
gvfs-fuse_1.6.0+git20100414-0ubuntu1_amd64.deb
hdparm_9.15-1ubuntu8_amd64.deb
ia32-libs_2.7ubuntu25_amd64.deb
indicator-application_0.0.19-0ubuntu3_amd64.deb
indicator-messages_0.3.6-0ubuntu2_amd64.deb
initramfs-tools_0.92bubuntu72_all.deb
initramfs-tools_0.92bubuntu73_all.deb
initramfs-tools_0.92bubuntu74_all.deb
initramfs-tools-bin_0.92bubuntu72_amd64.deb
initramfs-tools-bin_0.92bubuntu73_amd64.deb
initramfs-tools-bin_0.92bubuntu74_amd64.deb
jockey-common_0.5.8-0ubuntu8_all.deb
jockey-gtk_0.5.8-0ubuntu8_all.deb
kdebase-runtime_4%3a4.4.2-0ubuntu4_amd64.deb
kdebase-runtime-data_4%3a4.4.2-0ubuntu4_all.deb
kdelibs5_4%3a4.4.2-0ubuntu4_amd64.deb
kdelibs5-data_4%3a4.4.2-0ubuntu4_all.deb
kdelibs-bin_4%3a4.4.2-0ubuntu4_amd64.deb
kde-window-manager_4%3a4.4.2-0ubuntu13_amd64.deb
kerneloops-daemon_0.12+git20090217-1ubuntu7_amd64.deb
language-pack-en_1%3a10.04+20100413.1_all.deb
language-pack-en-base_1%3a10.04+20100413.1_all.deb
language-pack-gnome-en_1%3a10.04+20100413.1_all.deb
language-pack-gnome-en-base_1%3a10.04+20100413.1_all.deb
language-selector_0.5.5_all.deb
language-selector_0.5.6_all.deb
language-selector-common_0.5.5_all.deb
language-selector-common_0.5.6_all.deb
libappindicator0_0.0.19-0ubuntu3_amd64.deb
libappindicator-dev_0.0.19-0ubuntu3_amd64.deb
libatspi1.0-0_1.30.0-0ubuntu2_amd64.deb
libc6_2.11.1-0ubuntu6_amd64.deb
libc6-dev_2.11.1-0ubuntu6_amd64.deb
libc6-i386_2.11.1-0ubuntu6_amd64.deb
libcamel1.2-14_2.28.3.1-0ubuntu2_amd64.deb
libc-bin_2.11.1-0ubuntu6_amd64.deb
libc-dev-bin_2.11.1-0ubuntu6_amd64.deb
libclamav6_0.96+dfsg-1ubuntu2_amd64.deb
libcomerr2_1.41.11-1ubuntu2_amd64.deb
libdbusmenu-glib1_0.2.9-0ubuntu2_amd64.deb
libdbusmenu-glib1_0.2.9-0ubuntu3_amd64.deb
libdbusmenu-glib-dev_0.2.9-0ubuntu2_amd64.deb
libdbusmenu-glib-dev_0.2.9-0ubuntu3_amd64.deb
libdbusmenu-gtk1_0.2.9-0ubuntu2_amd64.deb
libdbusmenu-gtk1_0.2.9-0ubuntu3_amd64.deb
libdmraid1.0.0.rc16_1.0.0.rc16-3ubuntu2_amd64.deb
libebackend1.2-0_2.28.3.1-0ubuntu2_amd64.deb
libebook1.2-9_2.28.3.1-0ubuntu2_amd64.deb
libecal1.2-7_2.28.3.1-0ubuntu2_amd64.deb
libedata-book1.2-2_2.28.3.1-0ubuntu2_amd64.deb
libedata-cal1.2-6_2.28.3.1-0ubuntu2_amd64.deb
libedataserver1.2-11_2.28.3.1-0ubuntu2_amd64.deb
libedataserverui1.2-8_2.28.3.1-0ubuntu2_amd64.deb
libegroupwise1.2-13_2.28.3.1-0ubuntu2_amd64.deb
libexchange-storage1.2-3_2.28.3.1-0ubuntu2_amd64.deb
libgdata1.2-1_2.28.3.1-0ubuntu2_amd64.deb
libgdata-google1.2-1_2.28.3.1-0ubuntu2_amd64.deb
libgl1-mesa-dri_7.7.1-1ubuntu2_amd64.deb
libgl1-mesa-glx_7.7.1-1ubuntu2_amd64.deb
libglib2.0-0_2.24.0-0ubuntu2_amd64.deb
libglib2.0-data_2.24.0-0ubuntu2_all.deb
libglib2.0-dev_2.24.0-0ubuntu2_amd64.deb
libglib2.0-doc_2.24.0-0ubuntu2_all.deb
libglibmm-2.4-1c2a_2.24.1-1_amd64.deb
libglu1-mesa_7.7.1-1ubuntu2_amd64.deb
libgnomekbd4_2.30.0-0ubuntu2_amd64.deb
libgnomekbd-common_2.30.0-0ubuntu2_all.deb
libgnome-keyring0_2.30.0-0ubuntu4_amd64.deb
libgssapi-krb5-2_1.8.1+dfsg-2_amd64.deb
libgtkhtml3.14-19_1%3a3.29.6.is.3.28.3-0ubuntu2_amd64.deb
libgtkhtml-editor0_1%3a3.29.6.is.3.28.3-0ubuntu2_amd64.deb
libgtkhtml-editor-common_1%3a3.29.6.is.3.28.3-0ubuntu2_all.deb
libgtkmm-2.4-1c2a_1%3a2.20.2-1_amd64.deb
libgudev-1.0-0_1%3a151-11_amd64.deb
libgudev-1.0-0_1%3a151-12_amd64.deb
libgvfscommon0_1.6.0+git20100414-0ubuntu1_amd64.deb
libk5crypto3_1.8.1+dfsg-2_amd64.deb
libkdecorations4_4%3a4.4.2-0ubuntu13_amd64.deb
libkephal4_4%3a4.4.2-0ubuntu13_amd64.deb
libkrb5-3_1.8.1+dfsg-2_amd64.deb
libkrb5support0_1.8.1+dfsg-2_amd64.deb
libkwineffects1_4%3a4.4.2-0ubuntu13_amd64.deb
libkworkspace4_4%3a4.4.2-0ubuntu13_amd64.deb
libldap-2.4-2_2.4.21-0ubuntu4_amd64.deb
libpangomm-1.4-1_2.26.1-1_amd64.deb
libphonon4_4%3a4.6.2-0ubuntu5_amd64.deb
libplasma3_4%3a4.4.2-0ubuntu4_amd64.deb
libplymouth2_0.8.2-1_amd64.deb
libplymouth2_0.8.2-2_amd64.deb
libpython2.6_2.6.5-1ubuntu6_amd64.deb
libqt4-assistant_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-dbus_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-designer_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-help_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-network_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-opengl_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-qt3support_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-script_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-scripttools_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-sql_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-svg_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-test_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-webkit_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-xml_4%3a4.6.2-0ubuntu5_amd64.deb
libqt4-xmlpatterns_4%3a4.6.2-0ubuntu5_amd64.deb
libqtcore4_4%3a4.6.2-0ubuntu5_amd64.deb
libqtgui4_4%3a4.6.2-0ubuntu5_amd64.deb
libsane_1.0.20-13ubuntu2_amd64.deb
libschroedinger-1.0-0_1.0.9.is.1.0.8-0ubuntu1_amd64.deb
libsoprano4_2.4.2+dfsg.1-0ubuntu1_amd64.deb
libspeechd2_0.6.8~unofficial~rc2-0ubuntu3_amd64.deb
libss2_1.41.11-1ubuntu2_amd64.deb
libthai0_0.1.13-1build1_amd64.deb
libthai-data_0.1.13-1build1_all.deb
libtotem-plparser17_2.30.0git201000413-0ubuntu1_amd64.deb
libudev0_151-11_amd64.deb
libudev0_151-12_amd64.deb
libvlc2_1.0.5-2ubuntu3_amd64.deb
libvlccore2_1.0.5-2ubuntu3_amd64.deb
light-themes_0.1.6.4_all.deb
light-themes_0.1.6.5_all.deb
lintian_2.3.4ubuntu2_all.deb
linux-firmware_1.34_all.deb
linux-generic_2.6.32.21.22_amd64.deb
linux-headers-2.6.32-21_2.6.32-21.31_all.deb
linux-headers-2.6.32-21_2.6.32-21.32_all.deb
linux-headers-2.6.32-21-generic_2.6.32-21.31_amd64.deb
linux-headers-2.6.32-21-generic_2.6.32-21.32_amd64.deb
linux-headers-generic_2.6.32.21.22_amd64.deb
linux-image-2.6.32-21-generic_2.6.32-21.31_amd64.deb
linux-image-2.6.32-21-generic_2.6.32-21.32_amd64.deb
linux-image-generic_2.6.32.21.22_amd64.deb
linux-libc-dev_2.6.32-21.31_amd64.deb
linux-libc-dev_2.6.32-21.32_amd64.deb
locales_2.11+git20100304-3_all.deb
lock
mesa-utils_7.7.1-1ubuntu2_amd64.deb
module-init-tools_3.11.1-2ubuntu1_amd64.deb
mountall_2.12_amd64.deb
nautilus-actions_2.30.2-0ubuntu1_amd64.deb
nautilus-sendto-empathy_2.30.0.1-0ubuntu3_amd64.deb
notify-osd_0.9.29-0ubuntu2_amd64.deb
openoffice.org_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-base_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-base_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-base-core_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-base-core_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-calc_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-calc_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-common_1%3a3.2.0-7ubuntu1_all.deb
openoffice.org-common_1%3a3.2.0-7ubuntu3_all.deb
openoffice.org-core_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-core_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-draw_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-draw_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-emailmerge_1%3a3.2.0-7ubuntu1_all.deb
openoffice.org-emailmerge_1%3a3.2.0-7ubuntu3_all.deb
openoffice.org-filter-binfilter_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-filter-binfilter_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-filter-mobiledev_1%3a3.2.0-7ubuntu1_all.deb
openoffice.org-filter-mobiledev_1%3a3.2.0-7ubuntu3_all.deb
openoffice.org-impress_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-impress_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-java-common_1%3a3.2.0-7ubuntu1_all.deb
openoffice.org-java-common_1%3a3.2.0-7ubuntu3_all.deb
openoffice.org-math_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-math_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-officebean_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-officebean_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-report-builder-bin_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-report-builder-bin_1%3a3.2.0-7ubuntu3_amd64.deb
openoffice.org-style-galaxy_1%3a3.2.0-7ubuntu1_all.deb
openoffice.org-style-galaxy_1%3a3.2.0-7ubuntu3_all.deb
openoffice.org-writer_1%3a3.2.0-7ubuntu1_amd64.deb
openoffice.org-writer_1%3a3.2.0-7ubuntu3_amd64.deb
os-prober_1.38_amd64.deb
partial
phonon-backend-xine_4%3a4.4.0-0ubuntu2_amd64.deb
plasma-scriptengine-javascript_4%3a4.4.2-0ubuntu4_amd64.deb
plymouth_0.8.2-1_amd64.deb
plymouth_0.8.2-2_amd64.deb
plymouth-theme-ubuntu-text_0.8.2-1_amd64.deb
plymouth-theme-ubuntu-text_0.8.2-2_amd64.deb
pm-utils_1.3.0-1ubuntu1_all.deb
psfontmgr_0.11.10-4ubuntu1_all.deb
python2.6_2.6.5-1ubuntu6_amd64.deb
python2.6-minimal_2.6.5-1ubuntu6_amd64.deb
python-apport_1.13.3-0ubuntu1_all.deb
python-apport_1.13.3-0ubuntu2_all.deb
python-apt_0.7.94.2ubuntu6_amd64.deb
python-aptdaemon_0.11+bzr345-0ubuntu4_all.deb
python-aptdaemon-gtk_0.11+bzr345-0ubuntu4_all.deb
python-desktopcouch_0.6.4-0ubuntu1_all.deb
python-desktopcouch_0.6.4-0ubuntu2_all.deb
python-desktopcouch-records_0.6.4-0ubuntu1_all.deb
python-desktopcouch-records_0.6.4-0ubuntu2_all.deb
python-eggtrayicon_2.25.3-4.1ubuntu4_amd64.deb
python-gda_2.25.3-4.1ubuntu4_amd64.deb
python-gdl_2.25.3-4.1ubuntu4_amd64.deb
python-gksu2_2.25.3-4.1ubuntu4_amd64.deb
python-gtkmozembed_2.25.3-4.1ubuntu4_amd64.deb
python-gtkspell_2.25.3-4.1ubuntu4_amd64.deb
python-papyon_0.4.6-0ubuntu2_all.deb
python-problem-report_1.13.3-0ubuntu1_all.deb
python-problem-report_1.13.3-0ubuntu2_all.deb
python-pyatspi_1.30.0-0ubuntu2_all.deb
python-software-properties_0.75.10_all.deb
python-speechd_0.6.8~unofficial~rc2-0ubuntu3_all.deb
python-twisted-bin_10.0.0-2ubuntu2_amd64.deb
python-twisted-core_10.0.0-2ubuntu2_all.deb
python-ubuntuone-client_1.2.0-0ubuntu1_all.deb
python-ubuntuone-storageprotocol_1.2.0-0ubuntu1_all.deb
python-uno_1%3a3.2.0-7ubuntu1_amd64.deb
python-uno_1%3a3.2.0-7ubuntu3_amd64.deb
python-zope.interface_3.5.3-1ubuntu2_amd64.deb
rhythmbox_0.12.8-0ubuntu2_amd64.deb
rhythmbox_0.12.8-0ubuntu3_amd64.deb
rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu2_amd64.deb
rhythmbox-plugin-cdrecorder_0.12.8-0ubuntu3_amd64.deb
rhythmbox-plugins_0.12.8-0ubuntu2_amd64.deb
rhythmbox-plugins_0.12.8-0ubuntu3_amd64.deb
sane-utils_1.0.20-13ubuntu2_amd64.deb
screen-profiles_2.68-0ubuntu1_all.deb
shared-mime-info_0.71-1ubuntu2_amd64.deb
software-center_2.0.1_all.deb
software-center_2.0.2_all.deb
software-center_2.0_all.deb
software-properties-gtk_0.75.10_all.deb
soprano-daemon_2.4.2+dfsg.1-0ubuntu1_amd64.deb
speech-dispatcher_0.6.8~unofficial~rc2-0ubuntu3_amd64.deb
sun-java6-bin_6.20dlj-1ubuntu2_amd64.deb
sun-java6-jre_6.20dlj-1ubuntu2_all.deb
sun-java6-plugin_6.20dlj-1ubuntu2_amd64.deb
synaptic_0.63.1ubuntu4_amd64.deb
synaptic_0.63.1ubuntu5_amd64.deb
synaptic_0.63.1ubuntu6_amd64.deb
totem_2.30.0git20100413-0ubuntu1_amd64.deb
totem-common_2.30.0git20100413-0ubuntu1_all.deb
totem-gstreamer_2.30.0git20100413-0ubuntu1_all.deb
totem-mozilla_2.30.0git20100413-0ubuntu1_amd64.deb
totem-plugins_2.30.0git20100413-0ubuntu1_amd64.deb
ttf-indic-fonts-core_1%3a0.5.8ubuntu1_all.deb
ttf-kacst_2.0+mry-2ubuntu1_all.deb
ttf-opensymbol_1%3a3.2.0-7ubuntu1_all.deb
ttf-opensymbol_1%3a3.2.0-7ubuntu3_all.deb
ubiquity-casper_1.234_all.deb
ubiquity-casper_1.235_all.deb
ubiquity-ubuntu-artwork_2.2.17_all.deb
ubiquity-ubuntu-artwork_2.2.18_all.deb
ubiquity-ubuntu-artwork_2.2.20_all.deb
ubufox_0.9~rc2-0ubuntu2_all.deb
ubuntu-docs_10.04.3_all.deb
ubuntu-mono_0.0.17_all.deb
ubuntuone-client_1.2.0-0ubuntu1_all.deb
ubuntuone-client-gnome_1.2.0-0ubuntu1_amd64.deb
ubuntu-standard_1.196_amd64.deb
ubuntu-standard_1.197_amd64.deb
ubuntu-wallpapers_0.31.3_all.deb
udev_151-11_amd64.deb
udev_151-12_amd64.deb
uno-libs3_1.6.0+OOo3.2.0-7ubuntu1_amd64.deb
uno-libs3_1.6.0+OOo3.2.0-7ubuntu3_amd64.deb
update-manager_1%3a0.134.6_all.deb
update-manager-core_1%3a0.134.6_amd64.deb
ure_1.6.0+OOo3.2.0-7ubuntu1_amd64.deb
ure_1.6.0+OOo3.2.0-7ubuntu3_amd64.deb
user-setup_1.28ubuntu6_all.deb
vim-common_2%3a7.2.330-1ubuntu3_amd64.deb
vim-tiny_2%3a7.2.330-1ubuntu3_amd64.deb
vinagre_2.30.0-0ubuntu2_amd64.deb
vlc_1.0.5-2ubuntu3_amd64.deb
vlc-data_1.0.5-2ubuntu3_all.deb
vlc-nox_1.0.5-2ubuntu3_amd64.deb
vlc-plugin-pulse_1.0.5-2ubuntu3_amd64.deb
xdg-user-dirs_0.12-0ubuntu2_amd64.deb
xinput_1.5.0-2ubuntu1_amd64.deb
xkb-data_1.8-1ubuntu8_all.deb
xscreensaver-data_5.10-3ubuntu4_amd64.deb
xscreensaver-gl_5.10-3ubuntu4_amd64.deb
xserver-common_2%3a1.7.6-2ubuntu5_all.deb
xserver-xorg-core_2%3a1.7.6-2ubuntu5_amd64.deb
xserver-xorg-input-synaptics_1.2.2-1ubuntu4_amd64.deb
xserver-xorg-video-ati_1%3a6.13.0-1ubuntu3_amd64.deb
xserver-xorg-video-ati_1%3a6.13.0-1ubuntu5_amd64.deb
xserver-xorg-video-intel_2%3a2.9.1-3ubuntu4_amd64.deb
xserver-xorg-video-radeon_1%3a6.13.0-1ubuntu3_amd64.deb
xserver-xorg-video-radeon_1%3a6.13.0-1ubuntu5_amd64.deb
yelp_2.30.0-0ubuntu2_amd64.deb
sam@sam-desktop:~$ 

```That is from this 10.04 install but my 9.10 (i386) looks just like it (contents do vary).  This is where all the .debs go, unless you have it marked not to save them, so that you can reinstall with out downloading the bugger again.

Just paste the .debs from the link I sent and paste them into the /archives and we will see what happens.

---

### Post by itsvan on 2010-04-20
so i copied the code from your post,,is it supposed to be like this? i copied the command and got all of that,,so now what?

root@ubuntu:/# ls /var/cache/apt/archives
aeolus_0.8.1-1_i386.deb
akonadi-server_1.2.1-0ubuntu4_i386.deb
app-install-data-partner_12.9.10.3_all.deb
avogadro_0.9.7-1ubuntu2_i386.deb
brutalchess_0.5.2+dfsg-3_i386.deb
cdrdao_1%3a1.2.2-18ubuntu3_i386.deb
celestia-common_1.5.1+dfsg1-2ubuntu1_all.deb
celestia-glut_1.5.1+dfsg1-2ubuntu1_i386.deb
devicekit-disks_007-2ubuntu5_i386.deb
devicekit-disks_007-2ubuntu6_i386.deb
dmraid_1.0.0.rc15-11ubuntu3_i386.deb
dssi-host-jack_0.9.1-2ubuntu1_i386.deb
dssi-utils_0.9.1-2ubuntu1_i386.deb
earth3d_1.0.5-1.1ubuntu1_i386.deb
erlang-base_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-crypto_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-inets_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-mnesia_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-public-key_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-runtime-tools_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-ssl_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-syntax-tools_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
erlang-xmerl_1%3a13.b.1-dfsg-2ubuntu1.1_i386.deb
firefox-3.0_3.5.9+nobinonly-0ubuntu0.9.10.1_all.deb

---

### Post by ranch hand on 2010-04-20
No, that is not what you need to put in there.  That is to show the names of what should be in there if it were run in the normal manner.

Go back a few posts and you will find links to download the 2 packages I want you to put in there.

Take the other stuff out while you are at it.  Leave the Lock directory, it is supposed to be there.

---

### Post by itsvan on 2010-04-20
im kinda confused on the part on how to put the files on that directory

---

### Post by ranch hand on 2010-04-20
Just download them to your desktop.

Then in nautilus as root (gksudo nautilus) that I think you have open, go to file system>home>"your user name">desktop and copy the files.  Then go to /var/cache/apt, right click on the archives directory (folder) and select paste.

Open the directory and check to make sure then are there.

---

### Post by itsvan on 2010-04-20
ok its done

---

### Post by ranch hand on 2010-04-20
Sorry for the delay, we ate late but it was very good.

Did you delete the grub.d directory and the grub file from the /etc/default directory?  I am just makeing sure before we move on.

---

### Post by ranch hand on 2010-04-21
And I did forget one that needs to go.

Go to /boot and delete the grub directory (folder).  Good thing I checked my notes.

---

### Post by itsvan on 2010-04-21
yah its all deleted so far

---

### Post by ranch hand on 2010-04-21
Including the /boot/grub directory?  We need to get them all.

---

### Post by itsvan on 2010-04-21
yepp

---

### Post by ranch hand on 2010-04-21
Great.

Now you can dig up the chroot script again and run it to get the terminal for it up.

Run;
```

apt-get install --reinstall grub-pc grub-common

```
Post  the output of that command.

Do not close the chroot terminal, we still need it.

---

### Post by itsvan on 2010-04-21
root@ubuntu:/# apt-get install --reinstall grub-pc grub-common
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1,428kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...n]? 
(Reading database ... 261086 files and directories currently installed.)
Preparing to replace grub-common 1.97~beta4-1ubuntu4.1 (using .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace grub-pc 1.97~beta4-1ubuntu4.1 (using .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done

root@ubuntu:/#

---

### Post by itsvan on 2010-04-21
im gunna go for the night, gotta wake up early,,but il leave everything on,,if you wnat to leave some last steps for the night il do some in the morning before school, i get out earlier tomorrow so il be one faster,,goodnight

---

### Post by ranch hand on 2010-04-21
What the devil is going on here?  What is this grub1.97beta4 crap?  Where is this coming from?

I, personally, think your box is possessed.

Oh well.  Let us go with it one more time.

The error  about /var/lib/os-prober/mount/boot I find real interesting because my i386 9.10 does have a /var/lib/os-prober/mount directory  but it is empty.  My x86-64 9.10 has a /var/lib/os-prober directory but all it has in it is a "labels" file that only has "Ubuntu 4" in it.

That 64bit 9.10 boots 6 OS' on the drive it is on and 12 on my external if they are both on at the same time.

OK we are gong to assume that this dog will boot Ubuntu.  So;

Run;
```

grub-mkconfig

```
and post those results.

Do not close the chroot terminal. we still need it.

---

### Post by ranch hand on 2010-04-21
Good idea.

Good night to you too.

---

### Post by itsvan on 2010-04-21
root@ubuntu:/# apt-get install --reinstall grub-pc grub-common
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1,428kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...n]? 
(Reading database ... 261086 files and directories currently installed.)
Preparing to replace grub-common 1.97~beta4-1ubuntu4.1 (using .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace grub-pc 1.97~beta4-1ubuntu4.1 (using .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done

root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
OK, that explains a lot.

You did not remove the /etc/grub.d directory.  That is the old one.

I do not know what the problem there is.  Could be my directions.  Could be your following those directions.  Could be a problem with nautilus.

We are also using the old /etc/default/grub file.  This is the reason you are booting to MS.

I hope you still have the root nautilus window still open.  If so go to /etc then /default and pull up the grub file there on gedit.

I want you to change it so that it looks like this;
```

GRUB_DEFAULT=1
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="30"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
instead of your current setup;
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
You can just copy paste mine in place of yours or edit yours.  If you edit make sure that the "default is set at 1, the # is put in the right line (that is why you see no menu), and that you change the Grub Timeout to 30 from 10 so that you have longer to see the menu when it comes up.

Save the file and rerun the grub-update and grub-mkconfig.  They will tell us if we are making progress.

---

### Post by itsvan on 2010-04-21
ok i changed the grub file,,then i ran those codes this is what i get


root@ubuntu:/# grub-update
grub-update: command not found
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
You better try the codes again.

You ran "grub-update".

It is "update-grub".

The grub-mkconfig you ran just right.

We need them both to run though.  Grub-mkconfig was not fully implemented in 1.97beta4.  All it did there was give you the file read out.  It did not re write the bugger.  So we have to have both.

---

### Post by itsvan on 2010-04-21
ok i ran the codes again,,il be back in an hour or so,,have a couple of things to do...

menuentry: command not found
root@ubuntu:/#         recordfail=1
root@ubuntu:/#         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
save_env: command not found
root@ubuntu:/# set quiet=1
root@ubuntu:/# insmod ext2
insmod: can't read 'ext2': No such file or directory
root@ubuntu:/# set root=(hd0,5)
bash: syntax error near unexpected token `('
root@ubuntu:/# search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
No command 'search' found, did you mean:
 Command 'setarch' from package 'util-linux' (main)
search: command not found
root@ubuntu:/# linux/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
bash: linux/boot/vmlinuz-2.6.28-15-generic: No such file or directory
root@ubuntu:/# initrd/boot/initrd.img-2.6.28-15-generic
bash: initrd/boot/initrd.img-2.6.28-15-generic: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
menuentry: command not found
root@ubuntu:/#         recordfail=1
root@ubuntu:/#         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
save_env: command not found
root@ubuntu:/# insmod ext2
insmod: can't read 'ext2': No such file or directory
root@ubuntu:/# set root=(hd0,5)
bash: syntax error near unexpected token `('
root@ubuntu:/# search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
No command 'search' found, did you mean:
 Command 'setarch' from package 'util-linux' (main)
search: command not found
root@ubuntu:/# linux/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
bash: linux/boot/vmlinuz-2.6.28-15-generic: No such file or directory
root@ubuntu:/# initrd/boot/initrd.img-2.6.28-15-generic
bash: initrd/boot/initrd.img-2.6.28-15-generic: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# Found linux image: /boot/vmlinuz-2.6.28-11-generic
No command 'Found' found, did you mean:
 Command 'pound' from package 'pound' (universe)
Found: command not found
root@ubuntu:/# Found initrd image: /boot/initrd.img-2.6.28-11-generic
No command 'Found' found, did you mean:
 Command 'pound' from package 'pound' (universe)
Found: command not found
root@ubuntu:/# menuentry "Ubuntu, Linux 2.6.28-11-generic" {
menuentry: command not found
root@ubuntu:/#         recordfail=1
root@ubuntu:/#         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
save_env: command not found
root@ubuntu:/# set quiet=1
root@ubuntu:/# insmod ext2
insmod: can't read 'ext2': No such file or directory
root@ubuntu:/# set root=(hd0,5)
bash: syntax error near unexpected token `('
root@ubuntu:/# search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
No command 'search' found, did you mean:
 Command 'setarch' from package 'util-linux' (main)
search: command not found
root@ubuntu:/# linux/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
bash: linux/boot/vmlinuz-2.6.28-11-generic: No such file or directory
root@ubuntu:/# initrd/boot/initrd.img-2.6.28-11-generic
bash: initrd/boot/initrd.img-2.6.28-11-generic: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
menuentry: command not found
root@ubuntu:/#         recordfail=1
root@ubuntu:/#         if [ -n ${have_grubenv} ]
> insmod ext2
> set root=(hd0,5)
bash: syntax error near unexpected token `('
root@ubuntu:/# search --no-floppy -
No command 'search' found, did you mean:
 Command 'setarch' from package 'util-linux' (main)
search: command not found
root@ubuntu:/# linux/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
bash: linux/boot/vmlinuz-2.6.28-11-generic: No such file or directory
root@ubuntu:/# initrd/boot/initrd.img-2
bash: initrd/boot/initrd.img-2: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# ### END /etc/grub.d/10_linux ###
root@ubuntu:/# 
root@ubuntu:/# ### BEGIN /etc/gru
root@ubuntu:/# Found memtest86+ image: /boot/memtest86+.bin
No command 'Found' found, did you mean:
 Command 'pound' from package 'pound' (universe)
Found: command not found
root@ubuntu:/# menuentry "Memory test (memtest86+)" {
menuentry: command not found
root@ubuntu:/# linux16/boot/memtest86+.bin
bash: linux16/boot/memtest86+.bin: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry: command not found
root@ubuntu:/# linux16/boot/memtest86+.bin console=ttyS0,115200n8
bash: linux16/boot/memtest86+.bin: No such file or directory
root@ubuntu:/# }
bash: syntax error near unexpected token `}'
root@ubuntu:/# ### END /etc/grub.d/20_memtest86+ ###
root@ubuntu:/# 
root@ubuntu:/# ### BEGIN /etc/grub.d/30_os-prober ###
root@ubuntu:/# ls: cannot access /var/lib/os-prober/mount/boot
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# Boot: No such file or directory
Boot:: command not found
root@ubuntu:/# ls: cannot access /media/18AD-128F: No such file or directory
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# ls: cannot access /media/18AD-128F: No such file or directory
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# ls: cannot access /media/18AD-128F: No such file or directory
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# ls: cannot access /m
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# ls: cannot access /media/18AD-128F: No such file or directory
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# ls: cannot
No command 'ls:' found, did you mean:
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lsw' from package 'dwm-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'ls' from package 'coreutils' (main)
ls:: command not found
root@ubuntu:/# if [ ${timeout} != -1 ]; then
>   if keystatus; then
>  
>       set timeout=-1
>     else
>       set timeout=0
>     
>   else
bash: syntax error near unexpected token `else'
root@ubuntu:/#     if sleep --interruptible 3 ; then
>       set timeout=0
>     fi
sleep: invalid option -- '-'
Try `sleep --help' for more information.
root@ubuntu:/#   fi
bash: syntax error near unexpected token `fi'
root@ubuntu:/# fi
bash: syntax error near unexpected token `fi'
root@ubuntu:/# ### END /etc/grub.d/30_os-prober ###
root@ubuntu:/# 
root@ubuntu:/# ### BEGIN /e
root@ubuntu:/# # This file pro
root@ubuntu:/# # menu entries you want to add after this comment.  Be careful not to change
root@ubuntu:/# # the 'exec t
root@ubuntu:/# 
root@ubuntu:/# echo "Adding Win on sda1" >&2 
Adding Win on sda1
root@ubuntu:/# cat << EOF
> menuentry "Microsoft Windows XP Professional (on /dev/sda1)"
>     insmod ntfs
>     set root='(hd0,1)'
>     search --no-floppy --fs-uuid --set 00acffe0acffcde2
>     drivema
>     chainloader +1
> }
> EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)"
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivema
    chainloader +1
}
root@ubuntu:/# ### END /etc/grub.d/40_custom ###
root@ubuntu:/# done
bash: syntax error near unexpected token `done'
root@ubuntu:/# root@ub
root@ub: command not found
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
We need to get this right.

Run;
```

update-grub

```
Then;
```

grub=mkconfig

```
I need to work on the truck for a bit anyway.  Hurry back.

---

### Post by itsvan on 2010-04-21
ok im back

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
done
root@ubuntu:/# grub=mkconfig
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
Try;
```

grub-mkconfig

```
sorry about that, can't type very well.

---

### Post by itsvan on 2010-04-21
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
ls: cannot access /media/18AD-128F: No such file or directory
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
Are you sure that you edited the /etc/default/grub file from nautilus as root and properly saved it (save as) in gedit?

I have to ask because we are, again, getting no response from our commands at all if you did.

---

### Post by itsvan on 2010-04-21
ya i did,,u just double checked this is what i have

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="30"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by ranch hand on 2010-04-21
OK, while you are there with the chroot terminal open try;
```

apt-get update

```
one more time.

---

### Post by itsvan on 2010-04-21
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                          
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US               
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US           
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                  
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US       
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US   
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US        
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done                                                
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/#

---

### Post by ranch hand on 2010-04-21
Well, what a surprise.

OK, we will have to just straighten out your partitions  and re install.

I need to know a couple of things because of things you have said.

You are worried about programs.  What programs and where did you get them?

Most programs are from the repos and a lot of them are installed with the OS.  The installed with the default installation you can check by seeing what is on your Live CD.

If you are talking about programs run in wine there are a couple of concerns.  I do not use wine and know nothing about it.  You have a MS install so why bother?

How much data do you have that we need to back up?  You should be able to tell roughly by right clicking on the directory /home/<your user name> under "file system" and checking properties which should have the size right there.  You may have to wait a while for that to finish calculating if it is a large directory.

---

### Post by ed-koala on 2010-04-21
Tis a shame he has to reinstall but at this point it'll be the best option I think.  Once you fresh install you may need to make a couple of edits to have Windows 7 in Grub but that is easy.

Good luck itsvan!!  Back up those pics and whatever and fry that non-working SOB!  lol

---

### Post by ranch hand on 2010-04-21
I figure on shrinking MS and expanding the extended partition, making a backup ext4 partition in that reclaimed space and transferring the files there.  We appear to be able to copy paste but not deliver commands that work or delete files from the OS.

Then install on ext4 and 2 partitions.  Transfer the files back to the /home.  Move the / partition down where the back up was (delete it when done transferring) and then enlarge the /home to fill the space on the extended.

---

### Post by cuberts on 2010-04-21
> **itsvan said:**
> HI so i had Ubuntu installed,,,i install Windows 7,,and now for some reason,,the grub menu will not boot up,,it loads directly into windows,,how can i change that?? i made sure that the ubuntu partition wasnt touched,,,does this mean i messed up? and now its gone?i need to boot back into ubuntu,,any ideas????:(I dont recognize your problem, but mabye this link will help you: [here]("http://www.dedoimedo.com/computers/grub.html")

---

### Post by itsvan on 2010-04-21
its not so much about how much data i have per se,,but its the data itself its important,,,and i have some programs that kinda took me a while to get working...like some Keyboard synthesisers and other crap, and other data,,so there is no way of at least booting back to save all of that?

---

### Post by ranch hand on 2010-04-21
> **cuberts said:**
> I dont recognize your problem, but mabye this link will help you: [here]("http://www.dedoimedo.com/computers/grub.html")
The biggest problem we have is that the entire system is unresponsive to commands.  We can edit files, but not delete them.  Commands like update-grub and grub-mkconfig will run, give you output, and have no effect what so ever other than the output which, at least lets you know that nothing has changed.

---

### Post by ranch hand on 2010-04-21
> **itsvan said:**
> its not so much about how much data i have per se,,but its the data itself its important,,,and i have some programs that kinda took me a while to get working...like some Keyboard synthesisers and other crap, and other data,,so there is no way of at least booting back to save all of that?
We are not going to boot that system.

I believe that we may well be able to save your config files if they are in the home directory anyway (most of them are).

I you go to your home directory and then click on "view at the top of the page and check the box "Show Hidden Files" you will see a bunch of file that start with a . and most of them are config files and your bookmarks and things like that.

Why don't you take a look in there and see if what you are needing is in there.  It should be file like ".mozilla" (where mozilla is the name of your package or app).

I need to run to the store and back, won't take long.  I am also trying to find out where the devil the install history is located.

---

### Post by ranch hand on 2010-04-21
So are you finding things you need to save?

We need to be doing some partitioning here and you should be able to look at things in your Ubuntu while we are doing that.

---

### Post by itsvan on 2010-04-21
Ill check in a bit, my sis is using the comp 4 a paper she needs to do , sucks because that pc is the only one in the house, she should be done soon

---

### Post by itsvan on 2010-04-21
Ok Finally backkk

---

### Post by ranch hand on 2010-04-22
All right.

If you are up to it let us see if we can resize that huge amount of wasted space on sda1.

You need to be on the LiveCD and go to gparted.

Right click on that partition and choose the option to Resize/Move

This will give you a graphic box to resize the partition.  Use your mouse to grab the right hand  end of the thing and slide it to the left.

You may have to move the mouse around a little to fine the right place (the little pointed black thingy at the end.

Watch the numbers in the size box below the slider and run that down to 50000 (This is in MB so that is 50GB).

Click on ok in in that box and then up on the tool bar the check mark icon to apply.  Yes you will get a warning about possible data loss as you did with the labeling.  ed-koala thinks it is safe for XP.  I think it is safe.

I also use gparted to copy partitions to other drives.  I move partitions.  I resize partitions.  I trust gparted.

There is a box that comes up when it goes to work.  If you click on "details" you will be able to see what it is doing if you expand it sideways a bit.  You will see it testing the best way to do the job and then doing it.

You could be looking for your config files on another workspace while this is going on and it will take a while.

If it is getting late just let it run and turn in.

We will check it out tomorrow.  If you stay with it drop me a line here when it is done.  I will sleep better.

Tomorrow we will expand the extended partition to the left, delete that dead space and extend the extended partition to the right.

I think we had best also boot to XP and make sure it is all right.  And we will try (once) to boot to Ubuntu if we can too.

---

### Post by itsvan on 2010-04-23
hey i just got home from work,,coudnt log on all day,,tomorrow i aint got anything to do,,so i think we should try to fry this damn computer once and for all, il sign in in the morning, latest the afternoon...

---

### Post by ranch hand on 2010-04-23
Sounds fine.

---

### Post by ed-koala on 2010-04-23
Resizing an XP partition is pretty safe. XP doesn't do any funky "hide-the-data-from-everyone" stuff. like Win 7 seems to do.

---

### Post by itsvan on 2010-04-23
people keep mentioning XP partition do i have windows xp still on my comp? it doesnt work thats why i installed 7

---

### Post by ranch hand on 2010-04-23
Oh the devil and all his helpers.  So it is.  I really need to learn to read one of these days.

That truly sucks.

Oh well.  Is it possible to get hold of the install disc for that bugger again?

While we ponder that problem, how about trying this.

You have the little box pop up that indicates grub is loading.  Try to boot, having your finger cocked and ready over the Shift button (left).  When that pox pops up, hit shift and hold it down.

The menu should come up.  IF it does hit the down arrow key.  This SHOULD stop the timer.  What I would like you to select is the option to boot recovery mode for the newest kernel.  This should be the second menu entry but check to make sure.

When it runs its course it will give you a menu.  Select Dpkg fix broken packages and hit enter.  Then just follow the directions as they come up.

When that is finished and sends you back to the menu, select Return to normal boot.  You will probably get a terminal login for user and then password.  Then another prompt.

At that prompt type     startx   

That should take you to the desktop.

I would print these instructions out to make following them easier if you can.

IF you get in, do not reboot or shut down as I do not trust things as they stand at all.

Let us know what happens as soon as you can.

---

### Post by itsvan on 2010-04-23
so th shift key thing worked,,and the whole list came out,,and i selected the first ubuntu,,ther were tons of other ones,,and i think two windwos xp,,should i still restart and follow the last isntructions? what are we still trying to do?

---

### Post by ranch hand on 2010-04-23
Well if you didn't do the dpkg thing it would be good to do because I am pretty sure that something is broken.

However, we are booted in now so lets try to fix grub from there.  May well work better.

Open your terminal and;
```

gksudo gedit /etc/default/grub

```
and make sure that the default is set to 1.

The Grub Timeout set to 30.

The "#GRUB_HIDDEN_TIMEOUT=0" line has the # at the start of it.

If it is that way already, great.  Do a "save as" on it anyway.  If it is not that way make it so and run the save as on it.

Then run;
```

sudo update-grub

```
and then
```

sudo grub-mkconfig

```
and give us the output one more time.

---

### Post by itsvan on 2010-04-23
to make sure,,check what still needs to be fixed

GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="30"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by ranch hand on 2010-04-23
> **itsvan said:**
> to make sure,,check what still needs to be fixed

GRUB_DEFAULT=1
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="30"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
Should read;
[code]
GRUB_DEFAULT=1
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="30"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[/code

---

### Post by itsvan on 2010-04-23
itsvan@MAGI:~$ gksudo gedit /etc/default/grub
itsvan@MAGI:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/5ACCC24DCCC222DD/boot
Boot: No such file or directory
done
itsvan@MAGI:~$ sudo grub-mkconfig
Generating grub.cfg ...
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
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /media/5ACCC24DCCC222DD/boot
Boot: No such file or directory
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
itsvan@MAGI:~$

---

### Post by ranch hand on 2010-04-23
If you got the # into the default/grub file I would now try rebooting.

Just look at the menu, don't touch the keyboard at all.  MS should be on top, then the current kernel, then the recovery mode for the current kernel.

We have the timeout set for 30 seconds.  Let is run out and do what ever it is going to do.  It should boot to Ubuntu on its own.

When we are satisfied that things are working right you can change that time out to anything you like.  If you hit enter at anytime it will boot then.

This time just let it run on its own.

---

### Post by itsvan on 2010-04-23
Yes!!! the bloody Menu finally came out!!! HALLELUJAH!!!!  now what

---

### Post by ranch hand on 2010-04-23
ALL RIGHT.

Now, we have the option of trying to change your grub version.  This would save you from having this problem again if you install something else.

On the other hand the bugger is working.

If you want to stick with the one that is installed and working I would just suggest improving the looks of the thing and the speed of it by adding this;
```

echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}

```
To your 06_custom file by
```

gksudo gedit /etc/grub.d/06_custom

```
and just copy/pasting that under your MS entry.

This will leave the Ubuntu entry in the right place for your default boot option and give you a recovery entry in that file.

If you put this in you will have to, of coarse, run;
```

sudo update-grub

```
and 
```

sudo grub-mkconfig

```
If the new entries are in the grub.cfg output of grub-mkconfig you should try rebooting again.  If that entry comes up as the default, just hit enter and you should boot right in.

Then we will shorten your menu (easy) so that you do not have to wait for all that other stuff to load.

---

### Post by ranch hand on 2010-04-23
I have got to run to the store.  Be gone minutes as am expecting a call.

---

### Post by itsvan on 2010-04-23
does this look right??

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}

---

### Post by ranch hand on 2010-04-23
Sorry for the delay.  got a wind storm going on and the power flashed off.  My UPS caught it so the box kept on running but it must have put my ISP down as I couldn't send for a few minutes.

That looks great.  Stick it in, save as, run the commands and see if it works.

---

### Post by itsvan on 2010-04-23
itsvan@MAGI:~$ gksudo gedit /etc/grub.d/06_custom
itsvan@MAGI:~$ sudo update-grub
[sudo] password for itsvan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
itsvan@MAGI:~$ sudo grub-mkconfig
Generating grub.cfg ...
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
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
itsvan@MAGI:~$

---

### Post by itsvan on 2010-04-23
il brb shortly for more instructions

---

### Post by ranch hand on 2010-04-23
Looking good so far.

---

### Post by ed-koala on 2010-04-23
Yeah, it is looking promising :)

I'm still following this thread. :)

---

### Post by ranch hand on 2010-04-23
To use my fathers version of an expletive - Dad blamed Win7.

What a thing to do to an innocent computer.

---

### Post by mal1958 on 2010-04-23
> **ranch hand said:**
> To use my fathers version of an expletive - Dad blamed Win7.

What a thing to do to an innocent computer.

I agree 100% on that. leave it to MS and billy boys Brain-dead child Winblows to pull something like this.

> 
Quote from Ed-koala ---
Yeah, it is looking promising :smile:

I'm still following this thread. :smile:

I'm following this one too, even though I can't contribute Jack on this subject. In fact it was ranch hand who helped me be able to upgrade my copy of grub "Before" I went and upgraded from 9.04 to 9.10.  I am just hoping that this all works out.

Mike

---

### Post by ranch hand on 2010-04-23
It has already pretty much worked out.  Just trying to get it to be a little cleaner.  I think that for someone of this experience level the guy has shone a lot of stamina and grit.

I wish we had a disk for Vista or 7 to resize with.  Not sure even how you go about it with those tools though.

It would be nice to have Ubuntu have the space it deserves on the HDD.  2 partitions would be awfully nice too, but we really need to resize to have the space to back up and do that on.  Oh well.  It looks like the bugger is going to work anyway.

---

### Post by oldfred on 2010-04-23
Herman says we can use gparted to resize Vista and 7.  But use of the checkbox is vital so gparted does not round to cylinders and move 7 back to 63 from 2048. Even if it does it can be repaired but after all this I do not think more repairs are wanted.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by ranch hand on 2010-04-23
> **oldfred said:**
> Herman says we can use gparted to resize Vista and 7.  But use of the checkbox is vital so gparted does not round to cylinders and move 7 back to 63 from 2048. Even if it does it can be repaired but after all this I do not think more repairs are wanted.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Oh man, thank you a BIG bunch.  I only ran vista for about a month and the MS before that was 98 (I was real good at 98).

Basically I know nothing at all about MS in the 21st century.

We are not going to ve messing with the start end of the MS partition at all, just the end.

It is the first one on the drive and it is just too big is all.

So we will just uncheck the round to to cylinders box and be happy.

That is assuming itsvan wants to do this after all this ordeal.  I hope so because it will make a better system.

I wasn't going to risk the MS stuff though with my knowledge of that stuff.  You have a hard time finding a better source than herman though.  I fell better.

My Dreaded Mother in Law has vista on her box and now I know I can work on it too.  This is just great.

Thanks again.

---

### Post by itsvan on 2010-04-24
hello everyone i have returned whats new

---

### Post by ranch hand on 2010-04-24
Well I am not sure what is new.  did you reboot with the new menu addition?

You need to read the post by oldfred above, and the link to hermans post on resizing Vista and 7.  I am game if you are.

Herman is a very solid source of good information.

We really need to now if the new menu addidtion is working though.  Tell us that first, read later.

---

### Post by ed-koala on 2010-04-24
I'm happy to see Herman's post.  I know just resizing a Win 7 partition without doing *something* was risky, now I know the answer.

---

### Post by itsvan on 2010-04-24
Well the menu keeps on coming up so thats good,,i get two KARMIC on Sda5 options one being hte recovery,,there are still a bunch of other ubuntus, and there is one windwos xp one,,which doesnt work,,no 7

---

### Post by ed-koala on 2010-04-24
Try this - change the entry in 06_custom to this:

menuentry "Microsoft Windows 7 Ultimate" {
    insmod chain
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    chainloader +1
}

Then see if Win 7 boots from the menu entry. This is a copy of my menu entry with your disk id. Be sure to run sudo update-grub and the sudo grub-mkconfig commands after editing the file.

---

### Post by ranch hand on 2010-04-24
Wow there, the very first entry should be your MS and it should work.  It is what we have been booting into 7 with.

The very last entry is also for it but it has the wrong uuid because the guy that sent it to you is an idiot (I should know).

The other Ubuntu entries are all your dead kernels going back to Jaunty and every kernel since.

Please try the first entry for MS and make sure it works.  I assume you are booting into Ubuntu with the second entry on your menu.

We can safely assume that if it works so does the recovery entry.

So, try the MS entry at the top of the menu, reboot into Ubuntu and let us know how that went.

---

### Post by ed-koala on 2010-04-24
Try to boot like ranch said first before doing any editing!

If you actually boot into Win 7 despite it saying XP all ya gotta do then is change the text.

---

### Post by ranch hand on 2010-04-24
> **ed-koala said:**
> Try this - change the entry in 06_custom to this:

menuentry "Microsoft Windows 7 Ultimate" {
    insmod chain
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    chainloader +1
}

Then see if Win 7 boots from the menu entry. This is a copy of my menu entry with your disk id. Be sure to run sudo update-grub and the sudo grub-mkconfig commands after editing the file.
I believe he is tolking about the MS entry at the very end of the menu from 40_custom which is wrong.  He has been booting to windows with an entry identical to yours from 06_custom.  Even has the right uuid in it.

You do have a different tittle as I put XP in but that does not effect the boot, you could call it "Grannies Duck" and it would boot to MS.

---

### Post by ed-koala on 2010-04-24
Yeah, I saw what you said right after my post.  I mistakenly thought he was saying he couldn't boot windows at all.

Seems like now if the entries work its just minor editing of text and removing some stuff, easy easy easy!

---

### Post by ranch hand on 2010-04-24
> **ed-koala said:**
> Yeah, I saw what you said right after my post.  I mistakenly thought he was saying he couldn't boot windows at all.

Seems like now if the entries work its just minor editing of text and removing some stuff, easy easy easy!
Yup, just want to make sure first.  Then we will turn it into a 3 entry menu.

---

### Post by itsvan on 2010-04-24
ok so im a bit confused,,so i reboot the pc and what am i looking for again?

---

### Post by ranch hand on 2010-04-24
Use the top menu entry.  I may say XP but it should boot you right into 7.

Then just reboot and come back to Ubuntu.  Then we will finish this up.

---

### Post by itsvan on 2010-04-24
yah it doesnt work, a error comes up and boots back to the GRUB menu...

---

### Post by ranch hand on 2010-04-24
What error, this is the entry that was booting you to MS automatically when the menu wouldn't come up where you could see it.

Well how about this.  Run;
```

sudo grub-mkconfig 

```
and post it.

Go to bed after that.  We will take a look at this and see what we think is up now.

---

### Post by ed-koala on 2010-04-24
Hmmmm, what do you think Ranch?  I posted my (working) entry for Win 7 and edited it to use his disk ID.  It's not the same as his (currently not working) menu entry.

I'm thinking edit his entry to what I posted in post 339 and see if Win 7 boots.  Your thoughts?

---

### Post by itsvan on 2010-04-24
The error is like like some numbers and letters,,and it says somehing abot device non existant or something like that



itsvan@MAGI:~$ sudo grub-mkconfig
[sudo] password for itsvan: 
Generating grub.cfg ...
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
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
    drivemap -s (hd0) ${root}
    chainloader +1

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
itsvan@MAGI:~$

---

### Post by ranch hand on 2010-04-24
Sounds like a plan to me I looked at it and the one he is using and thought they looked alike.  They were not side by side and I think I am too whipped to remember things long enough to change workstations.

We will worry about it tomorrow unless you and he want to fight with it tonight.  I think I can make it until he posts the grub.cfg output.

---

### Post by ranch hand on 2010-04-24
Thanks, I will look at that in the morning when I have a brain.

You need to check eds post above your last.  He has an idea that may well be right.

I do not know if you want to fool with it now or not.

I'm off to bed.

---

### Post by itsvan on 2010-04-24
il sign in tomorrow im tired,,goodnight to everyone..

---

### Post by ed-koala on 2010-04-24
I don't know for sure, but I'm wondering ...

Your windows menu entry :

```
echo "Microsoft Windows XP Professional (on /dev/sda1)" >&2
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
drivemap -s (hd0) ${root}
chainloader +1

```

My entry:

```
menuentry "Microsoft Windows 7 Ultimate" {
    insmod chain
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0A2A092A134EA339
    chainloader +1
}
```

Notice especially the absence of the drivemap line in my entry. I doubt it is necessary as my entry works fine.  Since you are getting a device error, I'm wondering if that line is what's messing it up? Obviously you have to keep your ID in the search line and not use my ID.

---

### Post by itsvan on 2010-04-24
ok whats for today guys?

---

### Post by itsvan on 2010-04-24
O _o

---

### Post by ranch hand on 2010-04-24
Well I am over on 9.04 and so do not have my notes but you may want to try the suggestion in the post right above yours.

Sure can't hurt.

I would like a new screen shot of your gparted.  I would not recommend using it from the drive you are on but it is handy for checking on your partitions, graphically so if you do not have it;
```

sudo apt-get install gparted

```
will put it in your System>Administration menu.

If you ever get another drive on that box it will be handy and is not a big download as the back end is on there anyway.

---

### Post by ranch hand on 2010-04-24
I am moving and deleting partitions in prep for the next testing cycle.  I will be over there in a bit.

---

### Post by itsvan on 2010-04-24
heres the pic

---

### Post by ranch hand on 2010-04-24
Hey thats great.

Did you try ed-koalas menu entry?

I am on my way over there right now but I may be held up if I did not edit my fstab right.  Got some changed uuid and may have some problem with the partition numbers in my menu too.

I know I have one that will boot.

---

### Post by ranch hand on 2010-04-24
Well I am back and have even done all my updates on all of these 10.04 installs that are left.

How goes the war?

---

### Post by ranch hand on 2010-04-24
I do not know if you have run any updates since you have been back on Ubuntu.  I suppose you use Update Mangler.

You really should try;
```

sudo apt-get update

```
and then;
```

sudo apt-get upgrade

```
once in a while.

The reason I mention this is all your dead kernels.  If you run the abouve command you are going to, in addition to the list of upgrades and removals and installs, get a list of things on board that you are not using and no longer need for anything.

All  those kernels will be on the list.

You will also get a message saying you should run;
```

sudo apt-get autoremove
[
```
to get rid of them.  I think this would save you a bit of room on your drive.

That savings will be listed too.

Anytime you want to shorten your menu down to 3 entries let me know.

I have no idea what is wrong with Win Whatever.  Someone else will have to help you with that.

I will be leaving Monday afternoon and not returning until sometime Thursday evening.

---

### Post by itsvan on 2010-04-24
i ran those commands,,i need some help on Ed Koalas message...


itsvan@MAGI:~$ sudo apt-get update
[sudo] password for itsvan: 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
itsvan@MAGI:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
itsvan@MAGI:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
itsvan@MAGI:~$ [

---

### Post by ranch hand on 2010-04-24
That is truly weird.  There really is something not right about your system right down in the core of it.

What is the problem with eds missive, pray tell?

---

### Post by ed-koala on 2010-04-25
You simply need to edit your 06_custom file and replace what you have with the text below. The file has to be edited as root. After editing, run the sudo update-grub and sudo grub-mkconfig (or whatever that command is).


menuentry "Microsoft Windows 7 Ultimate" {
insmod chain
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set **5ACCC24DCCC222DD**
chainloader +1
}

The bold number is the ID for YOUR disk. After that, you can try rebooting and selecting that entry and see if windows boots.

I'm heading to bed, will check tomorrow how it went, hopefully success!

---

### Post by ranch hand on 2010-04-25
I am going to let you boys play with that, I'll watch from back on my other drive so I can continue my depredations on the partition table of this one.

---

### Post by itsvan on 2010-04-25
does this looks right???

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows 7 Ultimate" {
insmod chain
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
chainloader +1
}

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}

---

### Post by ranch hand on 2010-04-25
That looks good to me as far as that file goes it should read and so forth.

As far as an entry for MS, beats me.  It is lacking the line that concerned ed-koala and that was the point so I would give it a whack.

Remember you must update grub to get that generated in your menu so you can try it.

Back to hacking and cursing my way through the test drive in view of  10.10-testing starting on the 6th.  All most have all my root partitions where I want them.

---

### Post by itsvan on 2010-04-25
ok i changed the 06 custom file and ran the codes,,heres the output,,il try to reboot see what happens

itsvan@MAGI:~$ sudo update-grub 
[sudo] password for itsvan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/5ACCC24DCCC222DD/boot
Boot: No such file or directory
ls: cannot access /media/HP: No such file or directory
done
itsvan@MAGI:~$ sudo grub-mkconfig
Generating grub.cfg ...
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
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows 7 Ultimate" {
insmod chain
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
chainloader +1
}

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=0c9b39c0-4d74-4508-8c9e-3e74332464dc ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /media/5ACCC24DCCC222DD/boot
Boot: No such file or directory
ls: cannot access /media/HP: No such file or directory
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win on sda1" >&2 
cat << EOF
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 00acffe0acffcde2
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
### END /etc/grub.d/40_custom ###
done
itsvan@MAGI:~$

---

### Post by ranch hand on 2010-04-25
Looks good to me.  It should boot to Ubuntu fine anyway.

I only know one way to find out if it will boot MS.  Give it a whack.

---

### Post by itsvan on 2010-04-25
SUCCESSS!!!!!!!!!!! Windows 7 is on the list and it boots perfectly!!!
 what a miracle hahaha thanks guys...

There is still a bunch of those old kernels lying around there,,and there is still that windwos xp one there,,they personally dont bother me since i can get the others ones to boot,,but it deffenatly would be better to get rid of them and make it look neater.

and i guess also giving ubuntu more disk space..since windows 7 is not my preferred os to use, and its hogging up all the hard-drive space.:popcorn:

well il be on tomorrow,,i can rest so much better now that Ubuntu and Windows are working as a team.

---

### Post by ranch hand on 2010-04-25
Yes, this is all good.

All you need to do now to have a really clean menu is open nautilus as root, go to /etc/grub.d and take away the permission to "execute file as a program" from 10_linux, 20_memtest86, 30_os-prober and 40_custom.

While there I would open 40_custom and delete that bad MS entry.

Run the usual commands and you will have 3 lines of menu, all that you now know to work.

To change the partitions around you may want to do some research and see if you can get an install disk again to resize that with.

With the info from herman I am willing to risk using gparted, on your box.  You should probably study this pretty well first.

I know a real easy way to do it and have no more trouble with MS at all.  You may have some reluctance to just deleting that partition though so we probably better get all our ducks in a row so that we can leave that pig on board.

You also need to find those configuration files.  Nautilus has a very good search feature that you could use for that (magnifying glass icon at top of the window) just choose "file system" for the location to search and use the name of the package (get that from synaptic).  That "home folder" file browser is just nautilus with out root permissions.  It is about as powerful a tool as you can ask for.

---

### Post by ed-koala on 2010-04-25
**[COLOR="Red"]Congratulations!!![/COLOR]**

Ranch's post (362?), the one with the update and autoremove commands, should take care of those extra kernels and entries (you'll probably need to run the update-grub/grub-mkconfig commands afterward also to update the grub list).

He's also correct about the file permissions, and removing that useless entry from 40_custom. All that will save you space and clean up your grub list.

It's all downhill from here!!!  Enjoy!

---

### Post by ranch hand on 2010-04-25
It sure was nice that someone who actually uses a 21st century MS product was around.  I know little about them and what I do know is more than I really want to know.

Just thinking about it makes my blood pressure go up.  I can't really express my feelings about MS on these forums due to the family orientation of the language restrictions.  Some things require the full use of idiomatic expletives.

---

### Post by itsvan on 2010-04-25
i ran all those codes,and changed the permission,,,heres my output


itsvan@MAGI:~$ sudo update-grub 
Generating grub.cfg ...
done
itsvan@MAGI:~$ sudo grub-mkconfig
Generating grub.cfg ...
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
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0c9b39c0-4d74-4508-8c9e-3e74332464dc
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
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows 7 Ultimate" {
insmod chain
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5ACCC24DCCC222DD
chainloader +1
}

}echo "Adding Karmic on sda5" >&2 
menuentry "Karmic on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

echo "Adding Karmic on sda5 (recovery)" >&2 
menuentry "Karmic on sda5 (recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###
done
itsvan@MAGI:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
itsvan@MAGI:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
itsvan@MAGI:~$ [

---

### Post by ranch hand on 2010-04-25
The menu looks great.

The apt output indicates to me that there is a problem there somewhere.

You could just go to synaptic and remove the buggers there.

Have you found the config files you want to save?  If you can find them the dead kernels mean little as we can reinstall your system and it will be clean and everything should work right.

These strange behaviors are probably due to actions on your part and/or anyone that may have helped install in the first place.

I know that I really screwed things on my first install.  I had nothing else on the drive and started dual booting with the same OS (8.04) so that I could try things out there rather than on the  one that we really needed to work.

Only took me a week to come up with that plan.  Had to reinstall 8.04 5 times in 7 days.  It was too much fun to play with.  The wife was not amused.

---

### Post by mal1958 on 2010-04-25
[FONT=Verdana][SIZE=1]I am glad to see this has turned out on a good note.  I have seen too many horror stories about Win7 and any form of Linux trying to co-habit the same system.  Now I just need to solve my own problem and I will be a very happy camper.  Though this problem is one that nobody here can help me with.. Story goes as so:

Local church/school was dumping about 25 P4's three days ago and I happened on them while they were doing it. Seems that they got a donation of 30 Core-Duos and didn't need the older systems. I simply grabbed them all, vacumed out the inside and the fan ports, checked them all to see that they were clean and proptly took them to a *School for the Special*.  :) Heard back from them this morning and found out that those P4's were 3 gigahertz systems with 4 gig of ram, and twin terrabite HDs in them. Plus each was sporting a brand new Invidia 9600 vid card too. :shock: Now my system is starting to give me the same headaches that my older system did when it was ready to die. I could have kept one or two of those and been fine,  :oops:  Now I have to nurse this one along until I get a job and get a new (or refurbished system).    ](*,) Bummer...[/SIZE][/FONT][FONT=Verdana][SIZE=1]   I eventually will get another system, till then I have to nurse this one along...[/SIZE][/FONT]

Mike

---

### Post by itsvan on 2010-04-26
ya so far its been looking good,,thanks to you guys....im still trying to remove those kernels,,il look at Ranch Hands idea and give it a try

---

### Post by itsvan on 2010-04-30
Ok so all of the Kernels are in Order,The Grub menu is clean and the booting of ubuntu and windwos is flawless....now,,,I got a message in my update manager that there is a new 10.04 LTS release, and if i want to upgrade....Should i? what does it mean? and will it mess up all that we have done?

---

### Post by ranch hand on 2010-04-30
The new release is out as of yesterday (10.04) and it is very nice.

I would not recommend upgrading your system to it at this time.  This is a LTS (long term service) release and so it will have support for 3 years instead of 1.5 years as with your current Ubuntu.

It was, however, released on pretty much the same schedule as a regular release.  This means that there are unresolved bugs.  At the end of July there will be another ISO released for 10.04.1.  Most issues will have been taken care of by then (hopefully) and that is when I would upgrade if I were you.  9.10 has support through April 2011.

In your case a clean install would be best.   You have some problems with your system that may or may not be resolved with an upgrade.  You are running on ext3.  You really should think about a 2 partition install.

You are not really going to see any benifit from an upgrade at this time and ext4 is what the bugger is meant to run on.

If you want to reinstall 9.10 or upgrade to 10.04 we should really work on your partition setup, Back some things up and do that.

This would best be done in another thread.  Just start one and post a link here so we can find it.

EDIT

Get the live CD for 10.04 and see if it works for you.

---

