---
title: "Dualbooting Problem"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by TRouBLe32 on 2009-04-08
I have a 500GB hard disk, divided in 2 250GB partitions. I was dual-booting WinXP and Vista with Windows Vista's default bootloader...  I installed Ubuntu 8.10 x86 (the CD version) over Windows XP and installed GRUB in (at??:-k) /dev/sda (not sda1). So now GRUB can't find Vista, and I have no idea how to add it to the menu.lst...
The Ubuntu installation works great , but I don't really know my way around the OS.

---

### Post by presence1960 on 2009-04-08
> **TRouBLe32 said:**
> I have a 500GB hard disk, divided in 2 250GB partitions. I was dual-booting WinXP and Vista with Windows Vista's default bootloader...  I installed Ubuntu 8.10 x86 (the CD version) over Windows XP and installed GRUB in (at??:-k) /dev/sda (not sda1). So now GRUB can't find Vista, and I have no idea how to add it to the menu.lst...
The Ubuntu installation works great , but I don't really know my way around the OS.

Open a terminal and use this command ```
sudo fdisk -l
``` BTW that is a lowercase L, post the output here and also post the contents of your menu.lst file located at /boot/grub/menu.lst

sudo fdisk -l will show your partitions and file system on each.

---

### Post by TRouBLe32 on 2009-04-08
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

```

I have a second SATA disk on the machine, i can give the rest of the data if it's helpfull...

---

### Post by Jakey_TheSnake on 2009-04-08
```
title		Windows Vista
root		(hd0,0)
makeactive
chainloader	+1
```

should be added to your menu.lst under first Ubuntu entry, the root will either be (hd0,0) or (hd0,1), put in whichever your Ubuntu does not have.

edit: to access the file:

```
sudo gedit /boot/grub/menu.lst
```

edit2: oh, you may have to give your windows partition the "boot" flag, you can do this with System > Administration > Partition Editor, if it's not installed, you can install it with:

```
sudo apt-get install gparted
```

---

### Post by presence1960 on 2009-04-08
> **TRouBLe32 said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

```

I have a second SATA disk on the machine, i can give the rest of the data if it's helpfull...

you are missing info here is my sudo fdisk -l output
```

raz@raz-desktop ~ $ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16840   135267268+  83  Linux
/dev/sda2           16841       18389    12442342+  83  Linux
/dev/sda3           18390       19457     8578710    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612        4569    15727635   83  Linux
/dev/sdb3            4570       29879   203302575   83  Linux
/dev/sdb4           29880       30401     4192965   82  Linux swap / Solaris
```

as you can see I have 2 HDD and they are listed. This is the info I need to put in the exact modification for your windows entry in menu.lst. Don't go blindly trying (hdx,y) combos especially if your windows and Linux are on separate HDDs. Post the full output of sudo fdisk -l so we can be right the first time!

---

### Post by Jakey_TheSnake on 2009-04-08
Ah, didn't see he had separate HDDs, good spot. Listen to the guy above! ^

Edit: if he has Ubuntu just on one HDD, and Vista just on the other then the two should be (hd0,0) or (hd1,0) surely? 

He'd be able to find out the (hdx,y) combo using gparted anyway though, right? You've made me unsure now >_>

---

### Post by TRouBLe32 on 2009-04-08
OK, heres is the full results from the hard disk.
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30595   245754306    7  HPFS/NTFS
/dev/sda2           30596       60801   242629695   83  Linux

```
I selected the wrong text before:p.
Also, i installed gparted but i'm not sure which of the two partitions should have the boot flag on..

From Gparted:
/dev/sda1 is Vista
/dev/sda2 is Ubuntu

---

### Post by presence1960 on 2009-04-08
I have to take my daughter to MCDonald's for lunch- Ipromised her. Will be back later. Please go ahead and post the full output of > sudo disk -l Someone here will surely help you by the time I get back. If not I will check this thread for you and get right on it when I return.

---

### Post by presence1960 on 2009-04-08
> **TRouBLe32 said:**
> OK, heres is the full results from the hard disk.
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30595   245754306    7  HPFS/NTFS
/dev/sda2           30596       60801   242629695   83  Linux

```
I selected the wrong text before:p.
Also, i installed gparted but i'm not sure which of the two partitions should have the boot flag on..

if you look at the output windows already has a boot flag - note the (*).

change your windows entry in menu.lst to:

> title		Microsoft Windows Vista
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by presence1960 on 2009-04-08
> **presence1960 said:**
> if you look at the output windows already has a boot flag - note the (*).

change your windows entry in menu.lst to:

```
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
chainloader	+1
```

that looks better i think

---

### Post by Jakey_TheSnake on 2009-04-08
Windows should have the boot flag, so you're good to go imo, but wait for the other guy to vouch. 

Can you post your entire menu.lst?

---

### Post by Jakey_TheSnake on 2009-04-08
> **presence1960 said:**
> ```
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
chainloader	+1
```

that looks better i think


Why savedefault, and not makeactive?

---

### Post by presence1960 on 2009-04-08
> **Jakey_TheSnake said:**
> Why savedefault, and not makeactive?

That's what I have been using since going to Ubuntu. The makeactive one never worked for me. That's what I learned on here and have stuck with it. if makeactive works that is fine also.

---

### Post by quasimodo69 on 2009-04-08
> **TRouBLe32 said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f056f0

```

I have a second SATA disk on the machine, i can give the rest of the data if it's helpfull...
I just thought I would add what I had a problem with when I first tried dual booting.When you insert the disc..and it asks you to install...it will go to the partion editor section of the install....I had a problem in that it showed an orange section to format or partion on the right side..the windoze partion was blue and on the left.
 The section of the partition showing on the right had a 3GB partition..which I tried to expand or resize.This was unsuccesful.The install showed all I had was a 3GB partition.But when I allowed the partitioner program to use the whole GRAY AREA on the right and I chose it as an install area..It worked!!Damn guessing is COOL sometimes.It was not intui8tive to a moron likje me!
While a GUI is the best option to get people like me into Ubuntu..it does have it's problems.1st being the loss of security.The 2nd being the people who do write this are such BRAINIACS...and that is a compliment..really!But they fail to realize that to get more people into the system they have to dumb down (and I mean to me also) the retorict or explinations that we noobies (or dummy's like me)documetation with step by step and incriment by incriment and key stroke to follow through.
Sorry for the long reply...I guess I just started and had to say what I had to say.
  Thanks to all who have helped me!!

---

### Post by Jakey_TheSnake on 2009-04-08
> **presence1960 said:**
> That's what I have been using since going to Ubuntu. The makeactive one never worked for me. That's what I learned on here and have stuck with it. if makeactive works that is fine also.

I thought savedefault just makes one partition the default in the actual GRUB menu? Taken from menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.

```

makeactive has always been a necessity for me, how odd :shrugs:

---

### Post by TRouBLe32 on 2009-04-08
I changed the flag to Vista, when i installed gparted and when i saw that only one partition could have the boot flag i asked here.

I added the entry to menu.lst

@Jakey_TheSnake  *stage1* gives *(hd0,1)*.

Going to restart and post results later!

---

### Post by Jakey_TheSnake on 2009-04-08
Then (hd0,0) is right, now to see whether makeactive is necessary >_>

This will be interesting for me.

---

### Post by TRouBLe32 on 2009-04-08
OK, i think GRUB isn't the problem. 
Vista is there as an option but after pressing enter the system doesn't boot. It says Ntldr is missing.
I think that when i installed Vista some files needed for booting where put in the windows xp partition so when i overwrited the partition with ubuntu vista's bootloader was corruped.So naturally GRUB couldn't find it.
I believe that it can be fixed with the restore mode from the installation DVD but that's for a different forum:p

---

### Post by Jakey_TheSnake on 2009-04-08
One more thing...try makeactive in the menu.lst, just for my peace of mind -_-

Put it below (hd0,0).

Why would Vista put Vista files in the XP partition, assuming they were separate? 

[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

### Post by TRouBLe32 on 2009-04-08
tried makeactive, nothing different srry:-?
Anyway, thank you both guys at least i learned some things about linux..

---

### Post by presence1960 on 2009-04-08
> **quasimodo69 said:**
> I just thought I would add what I had a problem with when I first tried dual booting.When you insert the disc..and it asks you to install...it will go to the partion editor section of the install....I had a problem in that it showed an orange section to format or partion on the right side..the windoze partion was blue and on the left.
 The section of the partition showing on the right had a 3GB partition..which I tried to expand or resize.This was unsuccesful.The install showed all I had was a 3GB partition.But when I allowed the partitioner program to use the whole GRAY AREA on the right and I chose it as an install area..It worked!!Damn guessing is COOL sometimes.It was not intui8tive to a moron likje me!
While a GUI is the best option to get people like me into Ubuntu..it does have it's problems.1st being the loss of security.The 2nd being the people who do write this are such BRAINIACS...and that is a compliment..really!But they fail to realize that to get more people into the system they have to dumb down (and I mean to me also) the retorict or explinations that we noobies (or dummy's like me)documetation with step by step and incriment by incriment and key stroke to follow through.
Sorry for the long reply...I guess I just started and had to say what I had to say.
  Thanks to all who have helped me!!
Did you read any of the abundance of documentation on installation and partitioning? Before going to install Ubuntu one should really do some major prep to make sure all ducks are in a row. Although partitioning usually goes well there is always the chance for data loss. Here are a few links :
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

I prefer to plan and lay out my partitions prior to installation and then use manual option for partitioning on the install process to choose which partitions get what I want them to be. One can use the Ubuntu Live CD (gparted) or the gparted Live CD to create partitions first.

---

### Post by presence1960 on 2009-04-08
> **Jakey_TheSnake said:**
> I thought savedefault just makes one partition the default in the actual GRUB menu? Taken from menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.

```

makeactive has always been a necessity for me, how odd :shrugs:

That is referring to the number of entries beginning with the first kernel in the kernel list. "savedefault" in the windows OS entry in other Operating systems is not referring to that. In the section to which you refer my default is set to [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot) (number 0) so the first entry in my kernel list is the default.

---

### Post by presence1960 on 2009-04-08
> **Jakey_TheSnake said:**
> I thought savedefault just makes one partition the default in the actual GRUB menu? Taken from menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.

```

makeactive has always been a necessity for me, how odd :shrugs:

That section of menu.lst above is referring to the number of entries beginning with the first kernel in the kernel list. Numbering starts with 0. That number will be the default OS. "savedefault" in the windows OS entry in other Operating systems is not referring to that because "saved" is not set in the default section. In the section to which you refer my default is set to (number 0) so the first entry in my kernel list is the default.

---

### Post by presence1960 on 2009-04-08
> **Jakey_TheSnake said:**
> I thought savedefault just makes one partition the default in the actual GRUB menu? Taken from menu.lst:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.

```

makeactive has always been a necessity for me, how odd :shrugs:

That section of menu.lst above is referring to the number of entries beginning with the first kernel in the kernel list. Numbering starts with 0. That number will be the default OS. "savedefault" in the windows OS entry in other Operating systems is not referring to that unless "saved" is used in the section you refer to. In the section to which you refer my default is set to (number 0) so the first entry in my kernel list is the default.

check below to see:```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
##      altoptions=(recovery mode) single
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

title		Linux Mint x64, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Linux Mint x64, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Linux Mint x64, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint x64, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a3291e1b-426d-4a99-ac7e-17f615900c1a ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a3291e1b-426d-4a99-ac7e-17f615900c1a ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3291e1b-426d-4a99-ac7e-17f615900c1a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3291e1b-426d-4a99-ac7e-17f615900c1a ro single
initrd		/boot/initrd.img-2.6.24-19-generic


title		Linux Mint x64, kernel memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by presence1960 on 2009-04-08
either way we solved his menu.lst entry for windows, now he has to fix the other issue with his windows CD.

BTW I substituted makeactive for savedefault in my windows entry and it worked. I remember initially it didn't work and someone suggested savedefault in it's place. I have been using that ever since...LOL

---

### Post by meierfra. on 2009-04-08
**What savedefault does:**

Say you boot the fifth item   on menu.lst and that  item contains a "savedefault" line. Then the number "4"  (grubs starts counting at zero) will be written to the file /boot/grub/default".

**How is /boot/grub/default used?**
  
This depends on the "default" line in menu.lst

Case 1)  default 5   (or any other number in place of 5)

In this case "/boot/grub/default" is ignored and the sixth item on menu.lst will be the default boot.


Case 2)  default saved

In this case grub will use the number stored in  /boot/grub/default to determine the default item to boot.


So unless one uses "default saved" the "savedefault" lines in menu.lst are unnecessary.



**What "makeactive" does**

Say you boot an item on menu.lst and that item has the lines "root (hd0,2)"  and "makeactive".  Then grub will set the boot flag to the third partition of the boot drive (and remove all other boot flags from the boot drive)

So if the third partition already has the boot flag, the "makeactive" is unnecessary. Together with the fact that boot flags are (almost) irrelevant if grub is used for booting, there really is no reason to use "makeactive" in menu.lst

Both makeactive and savedefault can cause problems in some situations, so in my opinion the best item to use for Windows is

title Windows
rootnoverify  (hd0,Y)
chainloader +1

or

title Windows
rootnoverify (hdX,Y)
map (hd0) (hdX)
map (hdX) (hd0)
chainloader +1

the first item needs to be used if Windows is on the boot drive, the second item if  Windows is not on the boot drive.

---

### Post by presence1960 on 2009-04-08
as always seems to be the case thank you meirfra. Not only have you directly posted  in response to my posts a few times that really helped me understand something, but also reading your posts to others has helped me. Sometimes it is ok to know something works, but it is way better to know how & why it works. Thanks.

---

### Post by TRouBLe32 on 2009-04-08
Guys, thank you all for your help. Problem is solved!!!

[Here]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")is the guide that i used. It's from the same guys that made tha utility for configuring Vista's bootloader.
Turns out the Vista Install DVD has a boot repair option, and after running it 3-4 times (it does one step at a time like, mbr, boot sector...) i'm up and running again!!:tongue::tongue:

---

### Post by presence1960 on 2009-04-08
> **TRouBLe32 said:**
> Guys, thank you all for your help. Problem is solved!!!

[Here]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")is the guide that i used. It's from the same guys that made tha utility for configuring Vista's bootloader.
Turns out the Vista Install DVD has a boot repair option, and after running it 3-4 times (it does one step at a time like, mbr, boot sector...) i'm up and running again!!:tongue::tongue:

Great!!

---

