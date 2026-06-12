---
title: "Help with a dual boot"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by kyalee on 2009-01-06
So my dad bought a computer from Dell preloaded with Ubuntu. Because he hates Windows. Good for him. Then he decides that he can't live with any of the Linux accounting programs and he has to be able to run Quicken and since you can't run Quicken on a Linux machine, he wants Windows back. Except it has to be XP and not Vista. So he buys himself a copy of Windows XP Home Edition. But then he decides he wants Windows and Ubuntu to be dual booted so that he can use Windows for his accounting and work stuff and Ubuntu for everything else.

That's where I come in. Now, I warned him before doing anything that I'd never successfully dual booted a machine. I tried to dual boot on my computer when I switched to Ubuntu and ended up wiping my hard drive of everything Windows (including not backed up files that I'd actually wanted). So, I'm not the best person in the world for this. But, as his new computer doesn't have anything important on it yet, I agreed to give it a shot.

So, I stick the Windows disc in. Gag my way through the EULA and get things going. Windows shows me a screen and asks me about partitioning the hard drive. There are four partitions. One is huge. The others are relatively small. I stare at them. I try installing to one of the smaller ones. XP tells me I don't have enough space. I go back and try installing to the big one. XP tells me it needs to be reformatted. I let it reformat. I go get lunch. I come back when it's done. I try to install again. Everything seems to go fine from there, but when I restart, things get hairy. I end up back at the partition page. I figure, what the heck, it's not like data loss is an issue here, and I start deleting partitions. Finally, XP decides it's happy and loads. Everything is nicey nice except I have no internet access. I hate Windows.

Before I go loading any additional software onto XP or trying to troubleshoot the internet problem, I decide to go ahead and do the dual boot of Ubuntu. That way, if something goes wrong, I can always just reload Windows.

So, I put in my Ubuntu 8.10 CD that I made back when I did a clean install of Ibex on my computer. The install interface welcomes me with it's clean and easy interface. I tell it I want to install. It asks me about partitioning the hard drive.

Now I get confused. I play with the manual partitioning, but I have no idea what I'm doing. I shrink the size of the partition that contains XP. (I think.) I try to go forward and Ubuntu tells me that I can't because the partition doesn't have root. Or something like that. I don't have a screenshot, and I forget exactly what it said. Sorry.

I go back. I end up choosing Guided--Use Available Free Space. I go ahead with the install. Ubuntu installs fine. I turn the computer back on.

Now, Ubuntu is working fine. The internet is working fine. My problem is, I can't get to XP and I have no idea if it's even still on the hard drive.

So...help? I'm sorry this is so long, but I'm not even sure what information is relevant and which isn't so I figured I'd give you guys the whole story.

How do I find out if XP is still there? How do I access it if it is? How do I convince Quicken to write their program to work with Ubuntu so that I never have to go through this again? These and other exciting questions will be answered by you, the wonderful people of the Ubuntu forums.

I need a drink.

---

### Post by adult swim on 2009-01-06
go to a terminal, applications>accessories>terminal and run ```
sudo fdisk -l
``` then paste the results here.

---

### Post by kyalee on 2009-01-06
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *         399       15596   122077935    7  HPFS/NTFS
/dev/sda3           15597       30394   118864935    5  Extended
/dev/sda5           15597       29787   113989176   83  Linux
/dev/sda6           29788       30394     4875696   82  Linux swap / Solaris

```

---

### Post by adult swim on 2009-01-06
now post the output of ```
cat /boot/grub/menu.lst
```

---

### Post by kyalee on 2009-01-06
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
# kopt=root=UUID=a4269078-e163-4d40-bb2d-bb6c3a4f7c9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4269078-e163-4d40-bb2d-bb6c3a4f7c9f

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a4269078-e163-4d40-bb2d-bb6c3a4f7c9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a4269078-e163-4d40-bb2d-bb6c3a4f7c9f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a4269078-e163-4d40-bb2d-bb6c3a4f7c9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a4269078-e163-4d40-bb2d-bb6c3a4f7c9f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a4269078-e163-4d40-bb2d-bb6c3a4f7c9f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Locke_99GS on 2009-01-06
Looks like sda2 is your windows partition. To see if everything is intact on it (i don't see why it wouldn't be):

```

sudo mkdir /mnt/xp
sudo mount /dev/sda2 /mnt/xp
cd /mnt/xp
ls

```

will moun the drive and list its contents.


When manually partitioning, you have the option to set the mount point of the partition. You want at least one partition to be mounted as /

The installer should have seen windows and added it to grub's menu.lst, if it didn't, you'll want to add it to the end of */boot/grub/menu.lst* Use root (hd0,1) and chainloader.

I'm not at home, so I can't, off the top of my head, tell you how to build a grub section to boot windows.

---

### Post by Locke_99GS on 2009-01-06
double post

---

### Post by adult swim on 2009-01-06
alright now run ```
gksudo gedit /boot/grub/menu.lst
``` a file will pop up and you need to go down to the bottom where is says ### END DEBIAN AUTOMAGIC KERNELS LIST and make a new line beneath that.  then paste in ```
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

``` whiile you have this window open go back toward the top and youll see an where it says hiddenmenu.  place a # in front of that so it looks like #hidddenmenu, close and save the file.  now you should be able to choose which os to boot when you start up.

---

### Post by Locke_99GS on 2009-01-06
add

```

title		Windows
root		(hd0,1)
makeactive
chainloader	+1

```

to the end of your menu.lst

---

### Post by kyalee on 2009-01-06
```
sudo mount /dev/sda2 /mnt/xp
```

yields

```
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

---

### Post by bumanie on 2009-01-06
Quicken file format is compatible with gnucash - just in case you didn't know :) - never used gnucash so can't say how easy or hard it is to get used to.

---

### Post by WRDN on 2009-01-06
You need to edit the menu.lst file to add the entry for Windows. First, open the terminal and type:

```
gksudo gedit /boot/grub/menu.lst
```

Now, under the line, "###END DEBIAN AUTOMATIC KERNELS LIST" add:

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Save the file, and reboot.

---

### Post by dynathi on 2009-01-06
EDIT: Oops, nevermind. It looks like your question has already been answered.

As a side note, why don't you just install XP in VirtualBox? That way, Ubuntu can have the entire hard drive and you don't have to worry about partitioning or getting the internet set up in Windows. You also don't have to reboot the computer everytime you want to use Windows.

---

### Post by kyalee on 2009-01-06
Thanks guys! I can get to XP now. The internet still isn't working with XP, but I'll have to find another board to help me out with that.

bumanie - We tried GNU cash but my dad hated the user interface.

dynathi - Really? How does one go about installing XP to a VirtualBox? EDIT: Actually, I just found the VirtualBox website. I will peruse there for a while to see what it's all about. :)

---

### Post by adult swim on 2009-01-06
you are probably just missing yoyur wireless driver.

---

### Post by kyalee on 2009-01-06
> **adult swim said:**
> you are probably just missing yoyur wireless driver.

It's not wireless. I have the ethernet cable plugged right into the back of the computer.

---

### Post by adult swim on 2009-01-06
it seems like when i used windows i had to even add the ethernet driver manually.

---

### Post by cheeseburgerman1 on 2009-01-06
One question. how do you set which option in the list you want to be highlighted first? so as to say always load vista.

---

### Post by adult swim on 2009-01-06
if you make vista the first entry in the list, it will be the default option

---

### Post by cheeseburgerman1 on 2009-01-06
> **adult swim said:**
> if you make vista the first entry in the list, it will be the default option

soooo i would movie the vista settings up above the line that says its seperating the debian stuff from the others?

---

### Post by adult swim on 2009-01-06
go to a terminal and run ```
cat /boot/grub/menu.lst
``` paste the results here and ill show you how it should go.

---

### Post by cheeseburgerman1 on 2009-01-06
> **adult swim said:**
> go to a terminal and run ```
cat /boot/grub/menu.lst
``` paste the results here and ill show you how it should go.

ah i got it to work out right. seemed pretty risky though so i saved a back up. anyway, i got rid of some redundant ubuntu choices and changed the seperator line so it says ubuntu instead of other op systems. just one question though, it looks all crowded now, is there anyway to add space? and i dont remember if when it was set up to say other operating systems if you could actually select other but once i changed it to say ubuntu you can select it.

---

### Post by adult swim on 2009-01-06
you can add a space by putting a ```
title
root
``` everywhere you want a blank line.  im not sure about it hightlighting ubuntu (previously other operating)

---

### Post by cheeseburgerman1 on 2009-01-06
ah, thanks very much.

---

### Post by cheeseburgerman1 on 2009-01-07
One more question. i just ubdate to 8.10, and i had to go through and manually add the vista stuff back in. kinda sucks, so i dunno how to prevent this through future upgrades. Any help?

---

