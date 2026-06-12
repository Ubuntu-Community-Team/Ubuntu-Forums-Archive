---
title: "Help me!!!"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-28
I lost the proress bar that seems during booting of Ubuntu. The things i am getting during booting is textual. So, can i get that thing back, but how?

---

### Post by Boomhauer on 2009-01-28
go to a terminal and enter in ```
cat /boot/grub/menu.lst
``` and then paste what is returned here.

---

### Post by eshant_engineer on 2009-01-28
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
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/red

#A splash image for the menu
#splashimage=/boot/grub/splashimages/olho.xpm.gz

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
# kopt=root=UUID=8327e800-aadd-44d9-be9a-09cb74098853 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8327e800-aadd-44d9-be9a-09cb74098853

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
# defoptions=splash vga=791 quiet

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
# howmany=5

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
uuid		8327e800-aadd-44d9-be9a-09cb74098853
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8327e800-aadd-44d9-be9a-09cb74098853 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8327e800-aadd-44d9-be9a-09cb74098853
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8327e800-aadd-44d9-be9a-09cb74098853 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8327e800-aadd-44d9-be9a-09cb74098853
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

### Post by eshant_engineer on 2009-01-28
replace smiley by its code

---

### Post by vandorjw on 2009-01-28
I see nothing wrong with grub, its almost identical to my own.
The only time when I see text is when I boot into recovery-mode.

The word splash screen comes to mind. usplash.
Ubuntu still works fine right?

The only problem is that it no longer looks as pretty when it boots?

---

### Post by eshant_engineer on 2009-01-28
Is there any repair option as we have in XP or Vista?

---

### Post by eshant_engineer on 2009-01-28
bump

---

### Post by eshant_engineer on 2009-01-28
no answer?

---

### Post by hyper_ch on 2009-01-28
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Tony Flury on 2009-01-28
Bumping 3 times in 4 hours does not help either.

When Ubuntu does boot do you have the Startup manager applet - Systems -> Preferences -> Startup (or something like that).

I know you can disable the splash screen from there.

---

### Post by eshant_engineer on 2009-01-29
ok......now please give answer

---

### Post by byStanderone on 2009-01-29
...hi,

first try restore, on the grub menu.

---

### Post by eshant_engineer on 2009-01-29
> **byStanderone said:**
> ...hi,

first try restore, on the grub menu.
How to do this?

---

### Post by caljohnsmith on 2009-01-29
How about posting the output of the following commands:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Sometimes losing the Ubuntu splash screen is a symptom of when the UUID of the swap partition changes, and the above commands will tell us if that is your issue.

---

### Post by Eisenwinter on 2009-01-29
> **eshant_engineer said:**
> ok......now please give answer
You don't deserve to be helped with an attitude like this.

---

### Post by eshant_engineer on 2009-01-29
> **caljohnsmith said:**
> How about posting the output of the following commands:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Sometimes losing the Ubuntu splash screen is a symptom of when the UUID of the swap partition changes, and the above commands will tell us if that is your issue.

I think, i have posted fstab in earlier reply.....ok, i am posting for this requirement...



-------(1)-------------
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdba3dba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12675284     6337611   83  Linux
/dev/sda2   *    12677120    43132927    15227904    7  HPFS/NTFS
/dev/sda3        45174780   156296384    55560802+   f  W95 Ext'd (LBA)
/dev/sda4        43134525    45174779     1020127+  82  Linux swap / Solaris
/dev/sda5        86285115    97675199     5695042+   7  HPFS/NTFS
/dev/sda6        97675263   156296384    29310561    7  HPFS/NTFS
/dev/sda7        45174906    86285114    20555104+   7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by eshant_engineer on 2009-01-29
----------(2)--------------
/dev/sda1: UUID="8327e800-aadd-44d9-be9a-09cb74098853" TYPE="ext3" 
/dev/sda2: UUID="16FE4502FE44DC1D" LABEL="MAIN1" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="5ff8c875-f207-4130-bac7-99d56163d95f" 
/dev/sda5: UUID="A8448C38448C0B70" LABEL="DISK_VOL3" TYPE="ntfs" 
/dev/sda6: UUID="92B8C9B9B8C99BDB" LABEL="DISK1_VOL3" TYPE="ntfs" 
/dev/sda7: UUID="74B33B3D5F9F0886" TYPE="ntfs" 




--------------(3)-------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8327e800-aadd-44d9-be9a-09cb74098853 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
/dev/sda6/media/DISK1_VOL3 ntfs-3g force 0 0
/dev/sda5/media/DISK_VOL3 ntfs-3g force 0 0
/dev/sda7/media/DISK_VOL2 ntfs-3g force 0 0
/dev/sda2/media/MAIN1 ntfs-3g force 0 0



UUID=f429b75b-0611-4fc4-9186-aeffe7638c21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0





---------------(4)--------------------
RESUME=UUID=f429b75b-0611-4fc4-9186-aeffe7638c21

---

### Post by caljohnsmith on 2009-01-29
> **eshant_engineer said:**
> ```
/dev/sda1: UUID="8327e800-aadd-44d9-be9a-09cb74098853" TYPE="ext3" 
/dev/sda2: UUID="16FE4502FE44DC1D" LABEL="MAIN1" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="[COLOR="Red"]5ff8c875-f207-4130-bac7-99d56163d95f[/COLOR]" 
/dev/sda5: UUID="A8448C38448C0B70" LABEL="DISK_VOL3" TYPE="ntfs" 
/dev/sda6: UUID="92B8C9B9B8C99BDB" LABEL="DISK1_VOL3" TYPE="ntfs" 
/dev/sda7: UUID="74B33B3D5F9F0886" TYPE="ntfs" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8327e800-aadd-44d9-be9a-09cb74098853 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
/dev/sda6/media/DISK1_VOL3 ntfs-3g force 0 0
/dev/sda5/media/DISK_VOL3 ntfs-3g force 0 0
/dev/sda7/media/DISK_VOL2 ntfs-3g force 0 0
/dev/sda2/media/MAIN1 ntfs-3g force 0 0
UUID=[COLOR="Red"]f429b75b-0611-4fc4-9186-aeffe7638c21[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

RESUME=UUID=[COLOR="Red"]f429b75b-0611-4fc4-9186-aeffe7638c21[/COLOR]
```
As shown highlighted in red, it looks like the problem is that your swap partition UUID changed; did you resize/move or do anything with your swap partition recently? To fix the problem, how about trying:
```
sudo mkswap -U "f429b75b-0611-4fc4-9186-aeffe7638c21" /dev/sda4
```
Then reboot, see if you get the Ubuntu splash screen again, and once you get back into Ubuntu please post:
```
free
sudo blkid -c /dev/null

```

---

### Post by eshant_engineer on 2009-01-29
I had made some changes to swap.......ya sure.......my pleasure.....i will definitely post here

---

### Post by eshant_engineer on 2009-01-29
eshant@eshant-desktop:~$ sudo mkswap -U "f429b75b-0611-4fc4-9186-aeffe7638c21" /dev/sda4
Setting up swapspace version 1, size = 1020120 KiB
no label, UUID=f429b75b-0611-4fc4-9186-aeffe7638c21


eshant@eshant-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2582208    1213528    1368680          0     355556     302104
-/+ buffers/cache:     555868    2026340
Swap:            0          0          0


eshant@eshant-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="8327e800-aadd-44d9-be9a-09cb74098853" TYPE="ext3" 
/dev/sda2: UUID="16FE4502FE44DC1D" LABEL="MAIN1" TYPE="ntfs" 
/dev/sda4: UUID="f429b75b-0611-4fc4-9186-aeffe7638c21" TYPE="swap" 
/dev/sda5: UUID="A8448C38448C0B70" LABEL="DISK_VOL3" TYPE="ntfs" 
/dev/sda6: UUID="92B8C9B9B8C99BDB" LABEL="DISK1_VOL3" TYPE="ntfs" 
/dev/sda7: UUID="74B33B3D5F9F0886" TYPE="ntfs"

---

### Post by caljohnsmith on 2009-01-29
Have you tried rebooting yet? After rebooting, then post the output of the free and blkid commands.

---

### Post by Dirjel on 2009-01-29
Sorry for jumping in like this, but I *want* my computer to boot up all text-y.  If I had to guess, I'd probably say I would have to change this bit in the /boot/grub/menu.lst
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
I don't want to play with this, though, because I'm not entirely certain what I'm doing.  I just read through this thread, and it looks like people keep talking about the splash screen and referring to this file here.

Thanks.

---

### Post by eshant_engineer on 2009-01-29
> **caljohnsmith said:**
> Have you tried rebooting yet? After rebooting, then post the output of the free and blkid commands.

I donot get any changes....after rebooting

-----------free------------
             total       used       free     shared    buffers     cached
Mem:       2582208     701348    1880860          0      20840     200480
-/+ buffers/cache:     480028    2102180
Swap:      1020116          0    1020116

-------blkid----------

/dev/sda1: UUID="8327e800-aadd-44d9-be9a-09cb74098853" TYPE="ext3" 
/dev/sda2: UUID="16FE4502FE44DC1D" LABEL="MAIN1" TYPE="ntfs" 
/dev/sda4: UUID="f429b75b-0611-4fc4-9186-aeffe7638c21" TYPE="swap" 
/dev/sda5: UUID="A8448C38448C0B70" LABEL="DISK_VOL3" TYPE="ntfs" 
/dev/sda6: UUID="92B8C9B9B8C99BDB" LABEL="DISK1_VOL3" TYPE="ntfs" 
/dev/sda7: UUID="74B33B3D5F9F0886" TYPE="ntfs"

---

### Post by BatsotO on 2009-01-29
Generally it's about swap uuid mismatch. Try replace the swap uuid in /etc/fstab and /etc/initramfs-tools/conf.d/resume with the one stated on the blkid output, your swap uuid is f429b75b-0611-4fc4-9186-aeffe7638c21 and do update-initramfs -u then reboot.

---

### Post by eshant_engineer on 2009-01-30
I cheked at both address. But now UUID is same, but still i don't have usplash.

---

### Post by eshant_engineer on 2009-01-30
please...

---

### Post by BatsotO on 2009-01-30
have you done sudo update-initramfs -u ?
if you have done it would you mind re post the swap line in fstab and resume, just curious, so far it always works for me, i clone partitions alot so the swap uuid in both file was from my master partition and that method always put the progress bar back.

---

### Post by blazemore on 2009-01-30
has nobody thought of running
```
sudo apt-get install usplash
```

---

### Post by hyper_ch on 2009-01-30
you keep bumping threads continuously without waiting 24h as you were kindly told before. You just made it onto my ignore list.

---

### Post by eshant_engineer on 2009-01-30
> **BatsotO said:**
> have you done sudo update-initramfs -u ?
if you have done it would you mind re post the swap line in fstab and resume, just curious, so far it always works for me, i clone partitions alot so the swap uuid in both file was from my master partition and that method always put the progress bar back.

ya, ofcourse i did it, that's why i update UUID at all places mentioned.
> **hyper_ch said:**
> you keep bumping threads continuously without waiting 24h as you were kindly told before. You just made it onto my ignore list.

Dear, with the passing of time threads become invisible, to keep it under ur consideration and make u aware of problem i pop it up in 2-3 hrs...is any thing wrong?:(

---

### Post by blazemore on 2009-01-30
We do check pages other than 1... And we tend to check threads in which we have posted.

You're not *entitled* to support, remember.

---

### Post by boof1988 on 2009-01-30
> **eshant_engineer said:**
> Dear, with the passing of time threads become invisible, to keep it under ur consideration and make u aware of problem i pop it up in 2-3 hrs...is any thing wrong?:(

When you continually bump your thread (before 24hr), there are many people who will not help you.  Please do not bump your thread in less than 24hr.  You will get much better help that way.

And as someone has mentioned... people do look for threads that are not on the first page and then try to help them.

---

