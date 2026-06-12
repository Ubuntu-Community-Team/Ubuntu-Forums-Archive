---
title: "wubi installation not working"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by shubhbansal on 2010-08-26
Hi
I'm the definition of absolute begginarism on ubuntu, please tailor responses accordingly.

A while ago I had someone make me a USB startup disk and installed ubuntu from it, but apparently i messed up some of the settings (didn't allocate enough space) and now i keep getting the "Not enough space on disk" message whenever i try to install, sometimes even run an app (on ubuntu).

I needed it suddenly (also urgently) today so i just finished installing it again (this time through wubi), but whenever i try to boot with the new installed ubuntu, i get a (too quick to read) flashed message followed by a blank screen.

What can i do?

Thanks

---

### Post by M93 on 2010-08-26
open 'wubi' uninstall ubuntu
close 'wubi'
open 'wubi' make the size of the allocated space about 17GB(u can add more if u want of course), install ubuntu

---

### Post by shubhbansal on 2010-08-26
I might not have been clear enough.

My initial installation was the usual desktop version, that's the one for which i didn't allocate enough space. Its still installed, but virtually unusable.

On top of that i installed another version through Wubi, and that's the one which just shows a blank screen whenever i try to boot through it.
Is it because I now have 3 OSs on my system (Windows 7, older Ubuntu, wubi Ubuntu) that the latter doesn't work?

The installation hasn't affected either of the other previously installed OSs.

---

### Post by M93 on 2010-08-26
> **shubhbansal said:**
> I might not have been clear enough.

My initial installation was the usual desktop version, that's the one for which i didn't allocate enough space. Its still installed, but virtually unusable.

On top of that i installed another version through Wubi, and that's the one which just shows a blank screen whenever i try to boot through it.
Is it because I now have 3 OSs on my system (Windows 7, older Ubuntu, wubi Ubuntu) that the latter doesn't work?

The installation hasn't affected either of the other previously installed OSs.

i dont have a better solution in my mind than to back up your win7 and reinstall it giving it all the hdd then use wubi
  maybe someone else have got a better solution

---

### Post by bcbc on 2010-08-26
How big is your Ubuntu partition (not the wubi install)? How much space is on the hard drive.

If you can boot a live CD run and paste the output from: 
```
sudo fdisk -l
```
(lower case L)

EDIT: or better post the results of [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by shubhbansal on 2010-08-26
Here are the results of running bootinfoscript

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5ac6c2b7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,939,711    29,937,664  27 Hidden HPFS/NTFS
/dev/sda2    *     29,939,712    30,144,511       204,800   7 HPFS/NTFS
/dev/sda3          30,144,512   285,726,718   255,582,207   7 HPFS/NTFS
/dev/sda4         285,732,151   488,394,751   202,662,601   f W95 Ext d (LBA)
/dev/sda5         290,965,504   308,170,751    17,205,248   7 HPFS/NTFS
/dev/sda6         308,172,800   488,394,751   180,221,952   7 HPFS/NTFS
/dev/sda7         285,732,153   290,615,849     4,883,697  83 Linux
/dev/sda8         290,615,913   290,953,214       337,302  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       561cdef2-5b8b-420a-9734-22b7073bd022   ext4                                     
/dev/sda1        262C5A892C5A53C1                       ntfs       Recovery                      
/dev/sda2        F6FE4219FE41D313                       ntfs       System Reserved               
/dev/sda3        4E7E437E7E435E39                       ntfs                                     
/dev/sda5        BE867ED2867E8AA3                       ntfs       New Volume                    
/dev/sda6        CE1A95A31A9588DB                       ntfs       New Volume                    
/dev/sda7        ff0b055b-ad51-4845-92d9-7415aeb675fc   ext3                                     
/dev/sda8        6e8ab728-c9cc-42d6-aeab-ee59c320338b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda6        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/New Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ff0b055b-ad51-4845-92d9-7415aeb675fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff0b055b-ad51-4845-92d9-7415aeb675fc

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
uuid        ff0b055b-ad51-4845-92d9-7415aeb675fc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff0b055b-ad51-4845-92d9-7415aeb675fc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ff0b055b-ad51-4845-92d9-7415aeb675fc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff0b055b-ad51-4845-92d9-7415aeb675fc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ff0b055b-ad51-4845-92d9-7415aeb675fc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=ff0b055b-ad51-4845-92d9-7415aeb675fc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6e8ab728-c9cc-42d6-aeab-ee59c320338b none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 148.3GB: boot/grub/menu.lst
 147.9GB: boot/grub/stage2
 148.0GB: boot/initrd.img-2.6.28-11-generic
 148.4GB: boot/vmlinuz-2.6.28-11-generic
 148.0GB: initrd.img
 148.4GB: vmlinuz


```

---

### Post by bcbc on 2010-08-26
> **shubhbansal said:**
> Here are the results of running bootinfoscript


Am I reading that right? 2.5 GB for Ubuntu :)

There is a 90GB partition /dev/sda6 you might be able to shrink and then increase the Ubuntu partition. Try using Win7 disk utility to shrink it. Then you could increase /dev/sda7 to use the newly freed up space - using gparted from a live CD.

Unless you have a need to keep your /dev/sda7 ubuntu you could shrink /dev/sda6, delete /dev/sda7 and the swap, and just reinstall into the freshly created space (this should create a more reasonably sized swap as well). 

It's hard to know without understanding why you have all those partitions and how they're used.

PS your wubi root.disk looks like it has some problems. Either it's corrupted or you never did complete the installation and it's still unformatted. If you have data on it you need, try mounting it manually or fsck'ing it: the [wubi guide]("https://wiki.ubuntu.com/WubiGuide") shows how. If there's no data or you never got it running, just reinstall if you want it.

---

### Post by shubhbansal on 2010-08-26
Yeah, i really did mess up the first installation. 

I'd like to do one of two things here, whichever one's safer and easier.

I could either uninstall the older ubuntu(format its partition), reinstall through wubi and live happily ever after. The problem is that uninstalling ubuntu (i've heard) might delete the grub boot manager that came with it rendering me unable to access *any* OS. 

A second option is the one you pointed out, repartitioning my disks and deleting wubi (i don't have any data on it i need). As far as i know, there's scope for a lot of bad things happening there too..

So which one do you think is better (or is there a third option)? And of course I'd need detailed instructions for whichever one as well (**DETAILED **;))

---

### Post by bcbc on 2010-08-26
> **shubhbansal said:**
> Yeah, i really did mess up the first installation. 

I'd like to do one of two things here, whichever one's safer and easier.

I could either uninstall the older ubuntu(format its partition), reinstall through wubi and live happily ever after. The problem is that uninstalling ubuntu (i've heard) might delete the grub boot manager that came with it rendering me unable to access *any* OS. 

A second option is the one you pointed out, repartitioning my disks and deleting wubi (i don't have any data on it i need). As far as i know, there's scope for a lot of bad things happening there too..

So which one do you think is better (or is there a third option)? And of course I'd need detailed instructions for whichever one as well (**DETAILED **;))
If you are going to repartition you need to backup all your data. (Actually, you should always backup important data since drives can fail.)


Here're your options:
**1. Replace grub bootloader and reinstall wubi**

Insert a windows DVD or repair CD into your computer, boot from it and select Repair. From the command line run: 
```
bootrec.exe /fixmbr
```
Thereafter windows should boot automatically.

If you can't find a windows repair CD you can also do it using an Ubuntu CD using an equivalent bootloader. Boot from the Ubuntu CD, select "Try without installing". Then run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
This will install lilo in a functionally equivalent form to the windows bootloader. (PS you can ignore the lilo warnings as you're not using it to boot linux)

This will leave you with a windows only computer. Reinstall wubi and you're set. You can also remove /dev/sda7 and /dev/sda8 once you've retrieved any data you want from /dev/sda7.

**2. Resize your current install**
Honestly I haven't done this and so can't recommend it although I've seen others say it's straightforward. Maybe someone else can chime in on this.

**3. Delete and reinstall Ubuntu to partition.**
Boot windows and shrink /dev/sda6 giving yourself a space of at least 15GB or as much as you want for Ubuntu.
Then boot an Ubuntu CD in Live mode (try without installing), run GParted, and delete /dev/sda7 and /dev/sda8 after saving any data you need from /dev/sda7.
Then click on Install (on the desktop), and install using the free space you've created.
This is probably what I would do. Make sure when you're installing that you're installing into the free space you've created and not splitting or overwriting a windows partition.

Again, there are inherent risks in doing the above, so make sure you backup any important data, take your time, stop if you're unsure and ask for help.

---

### Post by shubhbansal on 2010-08-28
> **1. Replace grub bootloader and reinstall wubi**

Insert a windows DVD or repair CD into your computer, boot from it and select Repair. From the command line run: 
 	Code:
 	bootrec.exe /fixmbr 
Thereafter windows should boot automatically.

If you can't find a windows repair CD you can also do it using an Ubuntu  CD using an equivalent bootloader. Boot from the Ubuntu CD, select "Try  without installing". Then run:
 	Code:
 	sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
This will install lilo in a functionally equivalent form to the  windows bootloader. (PS you can ignore the lilo warnings as you're not  using it to boot linux)

This will leave you with a windows only computer. Reinstall wubi and  you're set. You can also remove /dev/sda7 and /dev/sda8 once you've  retrieved any data you want from /dev/sda7.

I like this first option. I've actually tried reinstalling from wubi a bunch of times, but each time the same thing happens: After the first step of install, it asks me to reboot which i do. I select the new ubuntu option that appears, after which i select that i want to continue with default installation settings. After this, the screen goes blank. The computer is busy for a while, and automatically restarts. I select the same ubuntu option again, and the screen just goes blank. Nothing happens.Questions:
Will replacing the boot manager solve this problem?
Could I use the repair disks i created when i first got my computer to do this?
And once i format the older ubuntu partitions, how do i expand adjacent partitions to include them?

---

### Post by bcbc on 2010-08-28
> **shubhbansal said:**
> I like this first option. I've actually tried reinstalling from wubi a bunch of times, but each time the same thing happens: After the first step of install, it asks me to reboot which i do. I select the new ubuntu option that appears, after which i select that i want to continue with default installation settings. After this, the screen goes blank. The computer is busy for a while, and automatically restarts. I select the same ubuntu option again, and the screen just goes blank. Nothing happens.Questions:
Will replacing the boot manager solve this problem?
Could I use the repair disks i created when i first got my computer to do this?
And once i format the older ubuntu partitions, how do i expand adjacent partitions to include them?
What graphics card do you have?

---

### Post by shubhbansal on 2010-08-28
> What graphics card do you have? 	

[SIZE=2]NVIDIA GeForce G210M[/SIZE]

---

### Post by bcbc on 2010-08-28
> **shubhbansal said:**
> [SIZE=2]NVIDIA GeForce G210M[/SIZE]

press 'e' when you see the grub menu, use arrow keys to navigate to 'quiet splash'  and add nomodeset i.e. 'quiet splash nomodeset' (without quotes). Hit CTRL+X to boot. See if that works.

---

### Post by shubhbansal on 2010-08-28
IT WORKS!!!! Thanks man (or woman)! Great advice! :D

There's still the minor issue of uninstalling the previous ubuntu installation which is dirtying up my booting (have to go through 3 OS menus) and taking up space.
Is there a simple way of doing that too?

---

### Post by bcbc on 2010-08-28
> **shubhbansal said:**
> IT WORKS!!!! Thanks man (or woman)! Great advice! :D

There's still the minor issue of uninstalling the previous ubuntu installation which is dirtying up my booting (have to go through 3 OS menus) and taking up space.
Is there a simple way of doing that too?

Great!

To get rid of the triple menu, install the windows bootloader - I mentioned how in a previous post.

Also, download the current nvidia driver or you'll have to override the boot each time. Click System, Administration, Hardware Drivers. It should offer the correct one.

---

### Post by shubhbansal on 2010-08-28
> Also, download the current nvidia driver or you'll have to override the boot each time. Click System, Administration, Hardware Drivers. It should offer the correct one.
That's exactly what i did, i downloaded and installed it. But i'm geting the same problem again, with a difference. It now shows the first ubuntu loading screen briefly (until all the loading indicator dots turn red), and then goes blank again.

I tried adding nomodeset again, but no luck.

---

### Post by bcbc on 2010-08-28
> **shubhbansal said:**
> That's exactly what i did, i downloaded and installed it. But i'm geting the same problem again, with a difference. It now shows the first ubuntu loading screen briefly (until all the loading indicator dots turn red), and then goes blank again.

I tried adding nomodeset again, but no luck.

](*,)

that is frustrating. 

Can you boot recovery mode? or text (replace 'quiet splash' with 'text'?)

---

### Post by bcbc on 2010-08-28
Try reading through this [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by shubhbansal on 2010-08-28
I reinstalled it, and didn't install the Nvidia driver this time. Besides having to enter "nomodeset" every time, and minor issues of low graphic quality, this works for the short term.

I'll get back here and post a solution if i ever find one.

Really appreciate the help.

---

### Post by bcbc on 2010-08-28
> **shubhbansal said:**
> I reinstalled it, and didn't install the Nvidia driver this time. Besides having to enter "nomodeset" every time, and minor issues of low graphic quality, this works for the short term.

I'll get back here and post a solution if i ever find one.

Really appreciate the help.

OK... to avoid having to type nomodeset each time you can edit /etc/default/grub
```
gksu gedit /etc/default/grub
```
and change 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Then save, and run 
```
sudo update-grub
```

---

