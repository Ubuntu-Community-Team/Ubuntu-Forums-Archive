---
title: "externall HDD"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by huwaw69 on 2009-01-17
I have 30gb. of hard drive on my hp notebook, but its not enough for me so i will have windows use it, now i have bought an 80gb maxtor onetouch external hard rive, so im wondering if i can install ubuntu using the live CD in the external hard drive? is it possible that i can use it in other notebooks, and does the same settings apply if i have inserted my external hard drive on other notebooks, for example the desktop themes, will it be the same?

---

### Post by albinootje on 2009-01-17
> **huwaw69 said:**
>  im wondering if i can install ubuntu using the live CD in the external hard drive? 

Take a look at these :
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It should certainly be possible, although not every pc can/will boot usb devices properly in my experience.

---

### Post by huwaw69 on 2009-01-17
So it means there is a possibilty that i can't install ubuntu on my hard drive?

---

### Post by akimatsu123 on 2009-01-17
> **albinootje said:**
> Take a look at these :
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It should certainly be possible, although not every pc can/will boot usb devices properly in my experience.

These methods create you a persistent "LiveUSB" which is slightly different from actual installed os. For example, you always have root/sudo privileges which can be a security risk. 

It is perfectly possible to install an actual copy of Ubuntu on an external hard disk. I don't know how experienced you are at installing Ubuntu, but i'll just give you a general overview of what to do. If you need specific commands or instructions, let me know and i'll be more detailed. 

--------------------------

Delete all partitions on ur HDD (of course, copy your files first). 

Double click on the install short cut and follow the instructions. When the partition manager starts, select manual. 

You will get a dialog box with all of the possible partitions you can install Ubuntu on (ur HDD has to be unmounted for this to show up). Create a partition of ext3 filetype (primary) for the linux filesystem (mount point is /). Create a swap partition. (Optional: Create a FAT32 partition. this way, you can still use the HDD for data storage in the extra space in both operating systems).

Press next, and follow the instructions. At the last page (step 7 of 7 if i remember correctly) click "Advanced" and make sure "install bootloader" is ticked and that you are installing it on your HDD (ie. "/dev/sdb" if "sdb" is ur HDD. pick the one without numbers, not "/dev/sdb1" or 2 or 3) 

Press next, and wait for it to install. After install, shut down the computer, and interrupt start up when you turn it on. Boot off ur HDD, and you should see GRUB come up. Select ubuntu, and it should work! (If it doesn't you may need to tweak GRUB to boot off a different HDD number, it should be hdd0,0 or at least thats what mine says)

those are the steps I followed to install Ubuntu on my HDD. I am using the OS as I speak. The system is actually faster than my Vista even off an external USB, and it's exactly like booting from my inbult hard disk. :D

Good luck!

---

### Post by adult swim on 2009-01-17
if your computer can boot from a usb device then you most likely wont have any problems. here is a guide i did a while ago

you can install ubuntu on an external hard drive that you can take from computer to computer.  note, however, this is only possible if the computers you are planning to use are able to boot from a usb device.  also note that this is going to wipe everything on the external drive so back up the stuff you want to keep!

step 1
boot the ubuntu live cd and choose try ubuntu without installing

step 2 
when the desktop comes up, plug in your usb drive.  an icon for the drive will appear on the desktop.  IT IS VERY IMPORTANT to right click the drive icon and select UNMOUNT

step 3
double click on the install icon on the desktop.  set it up however you want until you get to the install step 4

step 4
on the prepare disk space screen, select manual.  
[IMG]http://farm4.static.flickr.com/3240/3126122859_4ca0da5957_o.png[/IMG]

step 5
this next part is very important.  your disk layout will be different than mine so be careful.  you want to select your external hard drive.  in this picture my computers hard drive is labeled /dev/sda and you can see the different partitions it is split up into ie /dev/sda1.  below all of that you can see /dev/sdb.  that is my external hard drive and where we want to install ubuntu.  double click the first partition, in my case it is /dev/sdb1 and see the next step below.
[IMG]http://farm4.static.flickr.com/3256/3126931894_bbc0fdbab5_o.png[/IMG]

step 6
a new dialog box will pop up.  select a ext3 as a filesystem (you can choose a different one if you want but in most cases ext3 is the best bet.
now for the mount point put in /   then click ok and click next on the screen that pops up
[IMG]http://farm4.static.flickr.com/3078/3126101691_7755d0e918_o.png[/IMG]

step 7
this step is important as well as it installs grub onto your external drive and not your hard drive.  click on the advanced button that you can see in the picture
[IMG]http://farm4.static.flickr.com/3088/3126983758_d75253cc74_b.jpg[/IMG]

step 8
this is where you choose to install grub to the external drive.  you want to select your external drive.  earlier when you chose where to install ubuntu to you installed it to the first partition of the drive which in my case was /dev/sdb1.  now when we install grub we want to choose the drive itself not a partition.  make sure that the install bootloader box is checked and on the dropdown menu choose the drive itself, in my case this will be /dev/sdb.  
[IMG]http://farm4.static.flickr.com/3201/3126101607_80d46b99b1_b.jpg[/IMG]

now click on ok and then install.  ubuntu will install to the external drive.  once this is done, to launch ubuntu off of the drive you will need to reboot the computer.  whenever the bios is coming up there will be a key you have to hit (its different on different computers) in order to change the boot order.  hit the key and then select to boot from usb.  make sure that your external drive is plugged in and boot it.  you should now be able to launch ubuntu.

---

### Post by huwaw69 on 2009-01-17
@akimatsu123
So i should delete all the partition in my HDD? but how? i mean what HDD should i delete the partitions? the external or the built in HDD of my notebook, by the way my external HDD is formated as ntfs so i don't know if that means something, it just finished formatting right now, im still using my windows black...

@adult swim
Wow thats on hell of an explanation, well thanks my friend. ill try your guide first before i put [SOLVED] in this case.. thanks a lot anyways

---

### Post by albinootje on 2009-01-17
> **akimatsu123 said:**
> These methods create you a persistent "LiveUSB" which is slightly different from actual installed os. 

You're right about this.
> 
For example, you always have root/sudo privileges which can be a security risk. 

After a normal installation you also have sudo/root privileges, perhaps you meant that the live CD doesn't ask for a password, because the default live CD user doesn't have a password, which is indeed not so handy for permanent usage. You're right about the latter.
> 
It is perfectly possible to install an actual copy of Ubuntu on an external hard disk. 

Indeed.
It is very important to make sure that things go well with the Grub bootloader.
I prefer to detach any device that is not needed during installation, and then let Grub write to the usb-device.

---

### Post by adult swim on 2009-01-17
i dont think you want to delete the partitions on your internal hd, you should leave it alone.  whenever you install ubuntu to your external drive, you can format it to ext3 in one of the steps.

---

### Post by albinootje on 2009-01-17
> **huwaw69 said:**
> So i should delete all the partition in my HDD? but how? i mean what HDD should i delete the partitions? the external or the built in HDD of my notebook, by the way my external HDD is formated as ntfs so i don't know if that means something, it just finished formatting right now, im still using my windows black...

Do you have your data backed up to some other device or media ?

If so, then don't worry about formatting or deleting partitions, you will get the chance to do that during the Ubuntu installation.

You can make more than just one partition on your external disk.
For the installation of Ubuntu a 10 Gb / partition is more than enough to start with imho, use the rest for data storage.

---

### Post by huwaw69 on 2009-01-17
> **albinootje said:**
> Do you have your data backed up to some other device or media ?

If so, then don't worry about formatting or deleting partitions, you will get the chance to do that during the Ubuntu installation.

You can make more than just one partition on your external disk.
For the installation of Ubuntu a 10 Gb / partition is more than enough to start with imho, use the rest for data storage.

hahaha ill allocate 50gb on ubuntu then the 20gb is for data storage...
i have only one partition in the HDD of my laptop so i hope i won't have any problems deciding what HDD to use...

---

### Post by akimatsu123 on 2009-01-17
sorry, i should have been more clear. I meant delete all partitions off the external HDD that you want to install ubuntu on. don't touch your internal HDD or you may mess ur windows operating system  up. 

and it IS possible to simply resize the partition to create some unallocated space but it's just faster and clearner to make new partitions. 

but enough said, adult swim has screen shots of the entire process I was trying to describe :D

---

### Post by ubuntark on 2009-05-19
Hi AdultSwim and actually all the posters in here..... thanks for all your most helpful posts with pictures...  Im followed them and have Ubuntu 9.04 installed on an external westerndigital 258 usb drive.

So far this is my first experience with ubuntu and the OS seems great. 
However -- when i boot up my system and it gives me the choice to either go into 
- ubunto OS ( which works fine when I click that ) or at the bottom of the list i can choose XP   

when i choose xp i get an error that says :
"Error 13: Invalid or unsupported executable format....

Press any key to continue.... "

hit any key and it  loops me back to the OS choice menu.

- their is an option which gives me a prompt with grub>_    however i have no idea what to do with it.

Any help on how i can gain access to my xp system when i need to would be great.

Thanks in advance for anyone that can help point me in the correct direction .

---

### Post by albinootje on 2009-05-20
> **ubuntark said:**
> 
"Error 13: Invalid or unsupported executable format....

Can you post the output of the following :
```

sudo fdisk -l

```

---

### Post by ubuntark on 2009-05-22
> **albinootje said:**
> Can you post the output of the following :
```

sudo fdisk -l

```


I'm sorry but I have no idea what to do with what you gave me :(

---

### Post by tacantara on 2009-05-22
What albinootje has given you is a terminal command to run.  Open up the terminal and type the command just as it appears on the thread.  Once you run that command, post the output from that on this forum so he can look at it and figure out a solution to the problem.

---

### Post by ubuntark on 2009-05-22
> **tacantara said:**
> What albinootje has given you is a terminal command to run.  Open up the terminal and type the command just as it appears on the thread.  Once you run that command, post the output from that on this forum so he can look at it and figure out a solution to the problem.


Thanks here's what I see:

Disk /dev/sda: 640.1 GB, 640135028736 bytes    [COLOR=Green]<-----this is where my xp system is located [/COLOR]
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x048be184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38245   307202931    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x555d555d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       63741   511999551    7  HPFS/NTFS
/dev/sdb2           63742      121601   464760450    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes    
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd97aea6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30037   241272171   83  Linux
/dev/sdc2           30038       30401     2923830    5  Extended
/dev/sdc5           30038       30401     2923798+  82  Linux swap / Solaris

---

### Post by albinootje on 2009-05-22
To the OP, are you trying to boot from the external disk or from the hard disk ?

I assume you want the grub boot loader on the external disk, and not on your hard disk.

There's a few boot loader experts on this forum (I'm not one of them), and they recommend using this script to help you further :
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

See e.g. here :
[http://ubuntuforums.org/showthread.php?t=1081677](http://ubuntuforums.org/showthread.php?t=1081677)

---

### Post by ubuntark on 2009-06-02
Yes I want to be able to boot from my external to Ubuntu OS and then either have a choice at boot up to go with my original XP system or go with Ubuntu--- or just be able to disconnect the external drive and then boot to xp with no problem. 

I used a sourceforge script to get the following info:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x048be184

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   614,405,924   614,405,862   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x555d555d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,023,999,164 1,023,999,102   7 HPFS/NTFS
/dev/sdb2       1,023,999,165 1,953,520,064   929,520,900   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd97aea6c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   482,544,404   482,544,342  83 Linux
/dev/sdc2         482,544,405   488,392,064     5,847,660   5 Extended
/dev/sdc5         482,544,468   488,392,064     5,847,597  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B2A0A147A0A112C1" LABEL="DRIVE_Ct" TYPE="ntfs" 
/dev/sdb1: UUID="3C50D74150D70096" LABEL="DRIVE_Z" TYPE="ntfs" 
/dev/sdb2: UUID="FCF88269F88221CE" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="e08a7179-948d-4fe5-a69f-f41cfac58508" TYPE="ext3" 
/dev/sdc5: UUID="1ad80022-446a-4ea3-9394-e6feba9dc6b3" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/treztark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=treztark)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb2 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e08a7179-948d-4fe5-a69f-f41cfac58508 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e08a7179-948d-4fe5-a69f-f41cfac58508

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
uuid        e08a7179-948d-4fe5-a69f-f41cfac58508
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e08a7179-948d-4fe5-a69f-f41cfac58508 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e08a7179-948d-4fe5-a69f-f41cfac58508
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e08a7179-948d-4fe5-a69f-f41cfac58508 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e08a7179-948d-4fe5-a69f-f41cfac58508
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=e08a7179-948d-4fe5-a69f-f41cfac58508 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=1ad80022-446a-4ea3-9394-e6feba9dc6b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  31.4GB: boot/grub/menu.lst
  31.4GB: boot/grub/stage2
  31.4GB: boot/initrd.img-2.6.28-11-generic
  31.4GB: boot/vmlinuz-2.6.28-11-generic
  31.4GB: initrd.img
  31.4GB: vmlinuz

---

