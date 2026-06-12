---
title: "installed ubuntu 9.04, and now can't boot vista"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Will0w on 2009-08-21
Hello.  Let me start off by stating that I am a complete noob to ubuntu (and while somewhat informed in computing, I'm far from expert level) and this is the first time I have ever attempted to dual boot.  I installed ubuntu mostly to get more experience with linux as well as computers in general.  

I had vista installed first.  Originally when I installed ubuntu, evidently GRUB was not installed with it because when I booted up it just went straight to vista.  I did some searching online and managed to get GRUB to work, however now every time I try to select vista to boot I get GRUB Error 13: Invalid or unsupported executable format.

Looking at my partitions now, it appears that my vista partition, as well as linux and linux-swap are all under an extended partition (with the rest of the disk being unallocated).  When installing ubuntu, I chose to install it to the largest free space (about 85 gb), with my vista partiton being around 167 gb, and I had 342 gb of unformatted partition.  So partitioning definitely got changed somehow while installing ubuntu, and unfortunately I am not as proficient as I would like to be with these things.

I have my Vista installation DVD and tried running Startup Repair (three times now).  Still the same problem.

I've spent the last 2 days searching these forums and Google for solutions but nothing has worked or matched my situation exactly.  I even followed what this page:
[http://members.iinet.net.au/~herman546/p15.html#13]("http://members.iinet.net.au/%7Eherman546/p15.html#13")
said about booting into Windows.  I downloaded TestDisk and followed instructions with Analyse, but in the end the same problem exists.  So yeah, I'm kind of at a loss for what to do, might have to resort to uninstalling Ubuntu entirely (and possibly reinstalling if it doesn't cause problems).  

Thankfully, I built this computer relatively recently and thus I do not really have any data to lose on my vista partition, but by the same token I would prefer not to go through the trouble of reinstalling everything again.  

it seems the output for fdisk and menu.lst are often asked for in these forums, so I'll post them now just in case:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacc09cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53543   430080000    6  FAT16
/dev/sda2           53543      121601   546678784    6  FAT16

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacc09c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33145   266236204+   f  W95 Ext'd (LBA)
/dev/sdb5   *           1       21871   175677783+   7  HPFS/NTFS
/dev/sdb6           21872       32681    86831293+  83  Linux
/dev/sdb7           32682       33145     3727048+  82  Linux swap / Solaris

``````

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ef0548f-4f90-420f-9205-e149e878c279

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader    +1

```
So yeah, I'm wondering if the vista partition itself is corrupt, or something is wrong with the Windows boot loader, or anything like that.  Any help would be MUCH appreciated.

---

### Post by philcamlin on 2009-08-21
ok heres what i would do 
boot into your windows cd and repair the mbr then boot into the live cd and reinstall grub 

you should then be able to boot into vista and ubuntu :popcorn:

---

### Post by sandyd on 2009-08-21
i asure you its not a problem with your patition.
instead it looks like a problem with your menu.lst
i haven't done double hd configs before, so i can't help you. however, perhaps someone more knowledgable can.

perhaps (edit the file with sudo)
```

title        Windows Vista (loader)
rootnoverify    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader    +1

```
needs to be 
```

title        Windows Vista (loader)
rootnoverify    (hd1,5)
makeactive
chainloader    +1

```

or

it needs to be
```

title        Windows Vista (loader)
rootnoverify    (hd1,0)
makeactive
chainloader    +1

```

---

### Post by Will0w on 2009-08-21
I should note that everything is on my 640 gb HDD.  I have yet to put anything on my 1000 gb HDD.


@carlee: Thanks for trying to help, but sadly I tried both of your suggestions.  setting rootnoverify to (hd1,0) still gave me the same problem (Error 13), while (hd1,5) as I thought does not point to any existing partition, though I can understand why one would think to try it.

The reason I think something may be wrong with my vista partition is that in gparted, a yellow triangle with a "!" appears and says that it is unable to read the file contents of the system thus it does not display how much is being used, how much is free, etc.

I never thought trying to dual boot with vista and ubuntu would be this headache inducing :/

---

### Post by cataztrophe on 2009-08-22
hmm...
i think theres somthng wrong about your system, bcoz theres nothing wrong about carlee's sugestion there!

---

### Post by Buuntu on 2009-08-22
+1 philcalmin
Boot off of your windows CD and enter the recovery console.  (Press R or something)
Type ```
fixmbr
``` in the console, exit, and restart.

---

### Post by Will0w on 2009-08-24
Okay for the record Vista doesn't have a "recovery console" as far as I know, however the installation disk has an option to load a command prompt, which I used ```
BootRec.exe /fixMbr
```
to fix the mbr.  I tried reinstalling grub again through methods posted on this forum (finding /boot/grub/stage1, rooting in that hdd and partition, etc.) and that caused the same problem again.  

I think I'm going to load my vista dvd yet again, and use its partition set up to delete the ubuntu partition and linux swap partitions and possibly reinstall ubuntu (already fixed the Mbr)...unless someone has any other suggestions because I've about had it :(

---

### Post by wojmur on 2009-08-24
Perhaps try using Carlee's suggestion, just instead of 
```
rootnoverify (hd1,5)
```use
```
rootnoverify (hd1,4)
```I think GRUB counts partitions from 0. First logical partition, where your Vista lives, would be 4. Good luck!

---

### Post by Codix121 on 2009-08-24
Applications > Accessories > Terminal

Type in:

```
sudo cp /boot/grub/menu.lst /boot/grub/menubackup.lst
```

This will backup your grub menu (Just In case)

Then:

```
sudo gedit /boot/grub/menu.lst
```

This will bring up your grub menu,
Go down to the vista part,
and replace it with this:

```

title        Windows Vista (loader)
rootnoverify    (hd1,4)
makeactive
chainloader    +1 

```

Hit "SAVE" and then "REBOOT"
All should be good on the western front,
if not then change 

```

rootnoverify    (hd1,4)

```

to

```

rootnoverify    (hd1,5)

```

Good luck buddy! and welcome to the world of Linux, where it takes a person with a brain to actual fix an error :)
It pays off in the end, Don't worry! 
Enjoy! and Again Welcome!

---

### Post by Mark Phelps on 2009-08-24
Vista insists on being the "first" disk when it boots, so if your arrangement is the following:
-- Disk 1 xxx
-- Disk 2 Vista

... and ... you boot from Disk 1, you will NOT get Vista to come up unless you add the "map" commands already mentioned:

map (hd0) (hd1)
map (hd1) (hd0)

These commands fool Vista into thinking it's on the first disk (drive 0) when it's really on the second disk (drive 1).

Remember, you only need the map commands if the disk you boot from is NOT the one containing Vista.

---

### Post by Will0w on 2009-09-04
Well, it's been a week and I finally have a little time to work on this problem.  

So I used the Windows boot disk to fix the MBR for the nth time, then reinstalled Grub using the exact instructions from this post: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once again, when I tried to load my vista partition I got Error 13.

I'm looking at the GParted Partition editor, and this is what I see:[ATTACH]127426[/ATTACH]

according to the partition editor, it's not seeing the vista partition at all, and not showing how much memory is being used/etc.

curiously enough, when I'm booting of the Ubuntu LiveCD (and Grub is not installed), the partition editor on the LiveCD sees the vista partition just fine (even shows how much memory is being used, and how much is free).  So this leads me to believe somewhere along the line grub is screwing something up.  The question is how to fix this?

Here's my menu.lst again (just as it is when I reinstalled grub):
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ef0548f-4f90-420f-9205-e149e878c279

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ef0548f-4f90-420f-9205-e149e878c279 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5ef0548f-4f90-420f-9205-e149e878c279
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
makeactive
chainloader    +1
```and here's my fdisk -l output:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacc09cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53543   430080000    6  FAT16
/dev/sda2           53543      121601   546678784    6  FAT16

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacc09c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33145   266236204+   f  W95 Ext'd (LBA)
/dev/sdb5   *           1       21871   175677783+   7  HPFS/NTFS
/dev/sdb6           21872       32681    86831293+  83  Linux
/dev/sdb7           32682       33145     3727048+  82  Linux swap / Solaris

```In response to some suggestions earlier: I tried changing```
rootnoverify    (hd1,0)
``` to ```
rootnoverify    (hd1,4)
``` and then it said the partition does not exist :confused:  So it appears while Linux is on partiton 5, the vista partition is apparently on partition 0 (since that's where the extended partition begins).  Thanks for trying anyway.

As always, any and all help is much appreciated, but I am beginning to wonder if I should just fix the MBR, delete the linux partition altogether and reinstall through windows...

---

### Post by halitech on 2009-09-04
are the drives SATA? (I'm assuming yes but want to verify) If they are, swap them around so the 640gig drive shows up first and then the 1TB second. I think this will help clear some confusion on both windows and Ubuntus part. Otherwise, install Windows on the 1Tb drive and make sure that works, then install ubuntu on the 640gig drive and make sure everything still works. Partition the drives accordingly first before installing.

---

### Post by Windows Nerd on 2009-09-04
I don't know if I read your post wrong, but you said you have your Linux (Ubuntu) partition formatted to an Extended Partition. If it is, this is your problem. You cannot boot from an extended partition, only primary.

Scott

---

### Post by LewRockwell on 2009-09-04
whole thing looks fubar

save everything you need/want

then let Vista do a fresh hard drive check, format, and reinstall

do all the usual windoze updating stuff to get it current

then use the Vista partitioning utility to partition the hard drive for better present and future usage

then install Ubuntu

.

---

### Post by Will0w on 2009-09-04
That's what I was kind of afraid.  Honestly, I have no idea how partitions got moved around so everything ended up being in an extended drive.  Originally, before I installed Ubuntu I had a windows partition set, and I tried to install from the LiveCD by installing into the biggest freespace.  I guess that's where things went haywire.

I'm away from my desktop with vista/ubuntu for the weekend, but thankfully since it was relatively recently built there's nothing to lose as far as important data, so I'll try at least uninstalling ubuntu and fixing partitions when I get back.

oh, and yes my hard drives are SATA (at least one of them, the 640 gig).

---

### Post by mejohnsn on 2009-09-04
> **Will0w said:**
> That's what I was kind of afraid.  Honestly, I have no idea how partitions got moved around so everything ended up being in an extended drive.  Originally, before I installed Ubuntu I had a windows partition set, and I tried to install from the LiveCD by installing into the biggest freespace.  I guess that's where things went haywire.

I'm away from my desktop with vista/ubuntu for the weekend, but thankfully since it was relatively recently built there's nothing to lose as far as important data, so I'll try at least uninstalling ubuntu and fixing partitions when I get back.

oh, and yes my hard drives are SATA (at least one of them, the 640 gig).

The suggestion to reinstall so much, though painful, is a good idea at this point. And your nightmare with partitions and repeated invocations of 'fixmbr' remind me of how long I took studying partitions, MBRs and IPLs before I dared try to install Ubuntu on my laptop (it is now a dual boot w/ Win95 and Ubuntu 8.10).

So this time, may I suggest you back up your MBR and IPL once you have Vista running again, and before you install Ubuntu? Also, you may want to write down the partitioning as reported not just by fdisk -- which uses funny units -- but by Gparted as well. That way you can eliminate the possibility of human error when trying to understand what partitioning you have and what you need.

I can't remember what utilities I used to do all these things -- I just remember that they were available on SystemRescueCD, which also documented how to back up MBR and IPL correctly. This is important, since you may need to restore one without restoring the other.

Then again, the documentation concerning this topic on [http://www.p-dd.com/chapter11-page2.html](http://www.p-dd.com/chapter11-page2.html)  looks impressive, too.

---

### Post by ronparent on 2009-09-04
Not to further confuse things, but before you wipe everything to reinstall, you might try a simple test. Boot to a live cd, open a terminal, and start grub. From the grub prompt write **find /boot/grub/stage1**. The response will locate your ubuntu install in grub terms - ie (hdx,y). The location of vista is y-1. The load command for vista will then be as follows:

r[B]ootnoverify    (hdx,y-1)
map        (hd0) (hdx)
map        (hdx) (hd0)
makeactive
chainloader    +1[/B]

You can edit the menu lne in grub to test before making changes permanent by editing menu.lst. If it works fine. Otherwise plunge into more   drastic  solutions. Good luck.

---

### Post by Will0w on 2009-10-25
Well, it's been a while.  I was quite busy so my new desktop just gathered dust over the last 1.5 months while I used my main computer.  

I used my Vista installation disk to fix the MBR, reformat my hard drives and reinstall Vista.  Then, I loaded my Ubuntu disk, but this time I chose to install within the Vista partition instead of going through the trouble of creating its own partition like I tried last time (in retrospect, I think the best option would have been to have manually edited partitions from within the Live CD instead of choosing one of the predefined options).  So, now both operating systems seem to work perfectly fine.

As a student, I get Windows 7 for free through the MSDNAA, so when I have more free time I plan to download my copy, burn it to a DVD and attempt to install that onto another partition, along with my Vista/Ubuntu one.  Hopefully I won't screw that one up.

Thanks for everyone's help!

---

