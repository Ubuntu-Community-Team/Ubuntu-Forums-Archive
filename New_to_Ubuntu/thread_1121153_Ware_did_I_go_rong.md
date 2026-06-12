---
title: "Ware did I go rong?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by yummydodgerdog on 2009-04-09
Let me begin with my compliments to this forum. It helps to get a basic knowledge, but there are too many variables that i have in my head so i need an easy answer. I have a simple laptop Everex model VA1501V 1.5 gOS v2.20.1 120G SATA HD so on so 4th.
I managed to fix a broken sudo via this forum.(somebody deleted the only admin user.which is the only user)When i did that all these lil neat menu option started working I could mount the DVD and configure everything. Even the little orange square on the desktop panel started blasting messages to me."There are 203 updates for you" "you can upgrade to 8.04LTS" To good to be true. So I found this forum did one week of reading. Now I know better, not to update 203 files all together so i applyd about 15-20 at a time even after filtering thru the correct repos. The machine got wise and somehow "flipped its script". I only had 59 updates togo. They were the language updates. I skipped 'em. Did the update to 8.04LTS from 7.10LTS. It crashed. I made a live install CD on my desktop,cause the Laptop wouldnt go wirless anymore. Restrcted drivers needed Kernal whatever Generic and restricted to use cable router. I Gparted the drive spaced out for the Ubuntu7.10 about 3.9 it is in front  as /dev/sda1 then 49.65gig formatted ext3 and labeled and mounted left the swap part in the middle like it was already. I used the burned LIVE cd and folled instrc from psychocat.net clicked all the right boxes did the man partition on the live disk even though i already did it usuing Gparted the only thing that i feel might have went wrong was i rounded the cylinder headbut I did set the mount using "/ ". I answered the seven ?'s Kept the same user name and p/w didnt transfer over any settins or file cause it was pretty bare It loaded up on the new partition ok. BUT it wont load up when i restart. I can see the files using the file browser but i have to mount it first. Now i have a laptop with the grub loading "ubuntu7.10 using kernal 2.6.22-14 generic", and recovery mode, and another option "ubuntu7.10 using kernal 2.6.22-16 generic, and a 7.10memtest86+ but no ubuntu 8.04. Funny thing is I do remember ticking the create the boot load on the live install. I want to keep the 7.10 14-generic(just in case 8.04 wont work. It is a clean install the Live CD didnt let me use the internet at first I Fixed thst. Went back to psychocat for help  tried to load a Startup from the repo did that but it never showed up on the admin menu. I want to learn but like I said. I have too many variables in my head. Can someone be kind and give this dog a bone?

---

### Post by anjilslaire on 2009-04-09
Wow, I recommend using a couple pragraphs in there, maybe some line breaks to make it easier on the eyes...

Ok, I **strongly** recommend backing up your 7.10 data, and doing a completely clean install of 8.04 from a new 8.04.2 disc. In-place upgrades can get hairy sometimes.

After a clean install of Hardy (8.04.2), install all of the updates (203 or whatever shouldn't be a problem on a clean install . People do it all the time.

After this, then its time to reassess and see what's working and what's not, and post back with details.

---

### Post by yummydodgerdog on 2009-04-11
I am very sorry about the mess.
i will try your advice on the clean install (again)
I may have goofed on the partition. Can I redo the partion?

the current partition goes like this
/dev/sda 117.9 Gib
   dev                      size         used       unused       flag 
/dev/sda1   ext3      /   3.91G    2.98G     952.11M   Boot   7.10   gutsy
/dev/sda3   ext3         49.65G    2.46G     47.2 G           8.04.2 Hardy 
/dev/sda2   extended      2.33G    ---       ---
^/dev/sda5  linux swap    2.33G    ---       ---
/dev/sda4   ext3         55.90     631.71M   55.90G
     
sda1 is up and running 7.10 all updated no personal files only wireless setup. Dont know why,but when Grub boots there are 5 choices
that are listed.
   
1) 7.10 Kernal-2.6.22-14 generic
                   [LEFT]2)  "     "        "     recovery mode
                   3) 7.10 Kernal-2.6.22-16 generic
                   4)   "    "        "     recovery mode
                   5) memtester86[/LEFT]

There is no choice for the 8.o4.2 that is on sda3. I Read on the Official doc install guide.Tofind menu.lst at /boot/grub and add these 3 lines

title  New install
kernal (hd0,0)/boot/newinstall/vmlinuz
initrd (hd0,0)/boot/newinstall/initrd.gz
(replace hd w/sda3,???)
Can i use the gedit program accessed thru file browser for this ? 

sda3 is supposed to be my "clean install" that I did with a Live CD, it   was burned using Windows Vista Premim. the (i386iso) checked for errors with the initial setup install screen that booted when I powered on the laptop. My laptop magically booted up cdrom first. Another mystery.

sda2 and sda5 are connected with that lil triangle and in the middle of the           partition this is the way I got the Laptop.

sda4 WAS unallocated. It now has 6.4M not sure how that happened.

I dont want 7.10gutsy in the front of the partition in fact I really want to start fresh with 50Gigs for 8.4.02 and the rest unallocated for the next release.
I dont need a dual boot.Just the basics gOS and ubuntu. I have read that the alternate install is an easier to use and I do have a burned copy. The live install was tempting due to the GUI approach.But since I have been reading these forums, it seems like there is more options using the terminal. I used the terminal for my first fix. "Fix broken sudo" from 
"psychocats.net"
Thanks a bunch for the tip's. Hopefully i can be just as helpful in the future.

---

### Post by Gen2ly on 2009-04-11
You're doing pretty good, hope you don't mind if i give a couple tips.  First, i'd recommend targeting one problem at a time.  Because it looks like there is a problem in how you'd like your partitions sized and ordered, i'll start there.

Because your partitions are bjorked I'drecommend you restart the install and begin from scratch if possible.  Backup any necessary files you have and try again.  It just may be possible to resize/delete/add new partitions but would probably take longer and be more trouble than it'sworth.

If you want to work with what you got, post your disk partitions with:

```
sudo fdisk -l
```

And label them so that they can be easily read:  For example, here's mine:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1307       11504    81915435    7  HPFS/NTFS # Windows
/dev/sda3           11505       38913   220162792+   5  Extended
/dev/sda5           11505       18032    52436128+  83  Linux     # LinuxRoot
/dev/sda6           18033       38803   166843026   83  Linux     # LinuxHome
/dev/sda7           38804       38913      883543+  83  Linux     # DistroTest
```

Also post your "/boot/grub/menu.lst", mine e.g.:

```
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# (0) Arch Linux
title  Arch Linux
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/3c971fcb-c450-433f-8363-fe816d4773db ro vga=795
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/3c971fcb-c450-433f-8363-fe816d4773db ro
initrd /boot/kernel26-fallback.img

# (2) Windows
title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1
```

---

### Post by k3lt01 on 2009-04-11
When you start the laptop you get Gutsy (7.10) am I correct? You should be able to find your other partitions by using your Places menu. So you should be able to copy your important info.

If you are able to manage that, with the help of the people of this forum, you could do a clean install of 8.04.2 and then copy your previously saved important information to the new system.

---

### Post by yummydodgerdog on 2009-04-12
Here's the -Fdisk


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x04cc7320 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1         510     4096543+  83  Linux 
/dev/sda2            6993        7296     2441880    5  Extended 
/dev/sda3             511        6992    52066665   83  Linux 
/dev/sda4            7297       14593    58613152+  83  Linux 
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris 

Partition table entries are not in disk order 

```

Here's the /boot/grub/menu.lst
I included the default segment just in case there is a prog err. I am using a GUI "Start-up Manager"

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
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro

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
# defoptions=splash vga=792

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro splash vga=792
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks for the help.

---

