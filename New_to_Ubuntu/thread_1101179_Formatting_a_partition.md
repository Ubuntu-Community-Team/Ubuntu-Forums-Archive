---
title: "Formatting a partition"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Francis3366 on 2009-03-20
I have been running Ubuntu, 7.1 (updated from disk version 7.04) on my desktop for quite some time.  It functions almost perfectly and does everything I want it to do.  However, I recently loaded Ubuntu version 8.04 into my laptop (Acer, Extensa 5420).  The laptop came with Vista so when I loaded Ubuntu I partitioned (or rather the installation disk partitioned) the hard disk.  Windows functions OK (although I found that I hardly ever use it) and at first, Ubuntu worked well also.  Then I began having problems (a blue Kubuntu screen appearing on boot . . . and staying, crashes requiring rebooting, all open-programs tabs disappearing . . . permanently, non-functioning programs, etc.) all of which I sought the solution for in von Hagen's, _Linux Bible_;  O'Reilly's, _Linux Pocket Guide_;  Grant's, _Ubuntu for Non-Geeks_: and in the Ubuntu Help Forum, without success.  

My problem is that I want to remove Ubuntu version 8.04 from my laptop and install version 7.04.  When I insert the Ubuntu version 7.04 disk into my disk drive and boot, it appears that the disk wants to create another partition (partition #3). I see no method on the disk's installation instructions for removing the existing Ubuntu program from my hard drive. My question is: can I format only the existing partition containing Ubuntu version 8.04 without wiping out the partition containing Windows, Vista?  If so, how do I do it?

Thank you,

F. Walker

---

### Post by lisati on 2009-03-20
From the 7.04 CD you can use the partition editor (gparted) to delete your Ubuntu partition - it will probably show up as formatted to ext3. Be careful not to delete your windows partition if you wish to keep it on your system. Then you can close gparted and reinstall. Tell the installer to use the "Guided - use largest free space" option for partitioning.

---

### Post by jelle_ on 2009-03-20
yes, you can
when the installer asks you how to partition your disk, select manual. select your old ubuntu partition, partition it and mount it to /

---

### Post by Francis3366 on 2009-03-20
Many thanks. I appreciate the information.  I will try it tomorrow and let you know how it goes.  

F. Walker

---

### Post by bapoumba on 2009-03-20
Moved to ABT.

---

### Post by ivanvajar on 2009-03-20
You can format partition from LiveCD mode or during installation. It's on you. Windows partition will remain the same.

If you format from LiveCD, open gparted and select partition you want to format. In format dialog give it ext3 filesystem. Then run installation. When you get to preparing partitions for installation, go to manual, then select your ext3 partition, give it mountpoint '/' and that's it.

---

### Post by Francis3366 on 2009-03-21
I received the following list when I went to "Manual" format while installing Ubuntu ver 7.04.   The disk asked what partitions I wanted to delete but I couldn't figure which partition is which on the following list:

                   used           size               
/dev/sda1 fat32    10485MB      7300MB
/dev/sda2 ntfs     54775MB     41500MB
/dev/sda3 ntfs     27774MB      3200MB
/dev/sda5 ntfs     25827MB      7100MB
/dev/sda6 swap     1159MB          0MB 

In addition, the disk ask me to set up "root /"  I know what root means in the directory system but I do not know what they are referring to here. 

I used the "sudo fdisk" command as an additional search, but the listing on the screen did not give me any relevant information as is shown in my manuals.  (The examples in the Manual [von Hagen's "...Bible"] showed much more information using this command.)

One additional question: I now have a choice of two disks to install, both of which are Ubuntu ver 7.04.  One is a 32 bit and the other a 64 bit.  Will it make any difference which one I install?  I do nothing with graphics nor play any games.  I write, do spread sheets and duplicate some disks.  My laptop is an Acer Extensa, 6420: Athlon Dual-Core Processor: 2 GB RAM: 120 GB HD.

I use Ubuntu ver 7.04 32 bit on my desktop and it has never given me any problems.


F. Walker

---

### Post by ivanvajar on 2009-03-21
Open Terminal and run:
> sudo gedit /boot/grub/menu.lst
and post output, please :-)

---

### Post by Francis3366 on 2009-03-21
About three screens of information came up.  Is there any particular part I should be looking at?

---

### Post by InfectedWithDrew on 2009-03-21
> **Francis3366 said:**
> About three screens of information came up.  Is there any particular part I should be looking at?
Just post the output, please.

----------------
Now playing: [Switchfoot - Underwater](http://www.foxytunes.com/artist/switchfoot/track/underwater)

---

### Post by Francis3366 on 2009-03-21
I think I found the location I want.  It's under "Other Operating Systems" and lists Windows on:

/dev/sda1
Windows (hd0,0)

/dev/sda2
Windows (hd0,1)

I'll give this a try.

Does it make any difference if I use the 64 bit disk instead of the 32 bit disk?


Thank you for the help.

---

### Post by Francis3366 on 2009-03-21
I copied the data from my laptop and will post it here for your information.

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
# kopt=root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic 
quiet 

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic 

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic 
quiet 

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic 

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic 
quiet 

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic 

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=025726ea-d174-4168-b818-9d3203ab25d9 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Ubuntu 8.04.2, memtest86+ 
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
title		Windows Vista/Longhorn (loader) 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title		Windows Vista/Longhorn (loader) 
root		(hd0,1) 
savedefault 
makeactive 
chainloader	+1

---

### Post by Francis3366 on 2009-03-22
Problem solved.  I made a few mistakes but eventually solved the problem with your suggestions.  Many thanks for the help you all provided.

F Walker

---

