---
title: "grub error 21"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-03
I just installed hardy on a friends blank drive.  After I shut down and removed the drive my computer no longer worked.  I'm running on a live CD right now.  I can see in the drive that everything is still there and normal.  It just won't boot.  

I entered bios and looked to change the settings on the primary master and primary slave drives but I don't think I have those options in my BIOS.

How do I get this box working again?
Thanks

---

### Post by hortstu on 2010-02-03
Is there a better forum for this question?

---

### Post by ubunterooster on 2010-02-03
1: reinstall or 
2: use a rescue CD to reconfigure grub

Reinstall is usually not done but seeing there is no data to lose this way give it a try as this was likely due to a flaw in the install process. BTW, did you check the CD for defects before installing?

---

### Post by presence1960 on 2010-02-03
Let's see exactly what you have on that rig. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

Should be a simple fix. GRUB error 21 (see [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")) means that the selected disk or partition does not exist. You probably put GRUB on your disk when installing ubuntu to your friends disk. Now GRUB can't find that disk because you put it back in your friends computer. Run the script and post the results, we should get this sorted out easily.

---

### Post by hortstu on 2010-02-05
> **ubunterooster said:**
> 1: reinstall or 
2: use a rescue CD to reconfigure grub

Reinstall is usually not done but seeing there is no data to lose this way give it a try as this was likely due to a flaw in the install process. BTW, did you check the CD for defects before installing? 

The problem isn't with the new installation.  The problem is with the old one.  When I remove the drive that I just installed hardy on, it was connected by USB, the one that is in the internal drive becomes the problem.  Seems like everything is still on the drive when I access it from the live CD so I don't want to reinstall.

Is it possible to just reinstall the grub loader?

---

### Post by hortstu on 2010-02-05
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bfd06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,415,499   300,415,437  83 Linux
/dev/sda2         300,415,500   312,576,704    12,161,205   5 Extended
/dev/sda5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74e3c250-12d0-4313-ae9c-1d6e7b2f63bb   ext3                                     
/dev/sda5        300acce5-0b6b-409a-a1f8-a463045a0e2d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=300acce5-0b6b-409a-a1f8-a463045a0e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  34.0GB: boot/grub/menu.lst
  34.1GB: boot/grub/stage2
  34.1GB: boot/initrd.img-2.6.24-23-generic
  34.1GB: boot/initrd.img-2.6.24-23-generic.bak
  34.1GB: boot/initrd.img-2.6.24-26-generic
  34.1GB: boot/initrd.img-2.6.24-26-generic.bak
  34.1GB: boot/vmlinuz-2.6.24-23-generic
  34.1GB: boot/vmlinuz-2.6.24-26-generic
  34.1GB: initrd.img
  34.1GB: initrd.img.old
  34.1GB: vmlinuz
  34.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory 
```



Thanks for the help.

---

### Post by presence1960 on 2010-02-05
> **hortstu said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bfd06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,415,499   300,415,437  83 Linux
/dev/sda2         300,415,500   312,576,704    12,161,205   5 Extended
/dev/sda5         300,415,563   312,576,704    12,161,142  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74e3c250-12d0-4313-ae9c-1d6e7b2f63bb   ext3                                     
/dev/sda5        300acce5-0b6b-409a-a1f8-a463045a0e2d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74e3c250-12d0-4313-ae9c-1d6e7b2f63bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=300acce5-0b6b-409a-a1f8-a463045a0e2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  34.0GB: boot/grub/menu.lst
  34.1GB: boot/grub/stage2
  34.1GB: boot/initrd.img-2.6.24-23-generic
  34.1GB: boot/initrd.img-2.6.24-23-generic.bak
  34.1GB: boot/initrd.img-2.6.24-26-generic
  34.1GB: boot/initrd.img-2.6.24-26-generic.bak
  34.1GB: boot/vmlinuz-2.6.24-23-generic
  34.1GB: boot/vmlinuz-2.6.24-26-generic
  34.1GB: initrd.img
  34.1GB: initrd.img.old
  34.1GB: vmlinuz
  34.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory 
```



Thanks for the help.

Boot the 8.04 Live CD/USB, choose "try ubuntu without any changes." When the desktop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,0)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

This will fix your GRUB so that it points to your Ubuntu partition on sda1. Currently GRUB is looking for the disk you removed for menu.lst- that is your problem and this will fix it. See from the script results:

=> Grub 0.97 is installed in the MBR of /dev/sda and [COLOR="Red"]looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]

Next time you install ubuntu when you get to the Ready to install window click the Advanced button and choose where to install GRUB. When you installed Ubuntu to your friends disk you let GRUB be installed to your disk- that is why it is looking on boot drive #2 (your friend's disk) for menu.lst! See pic below for the window with Advanced button to click.

---

### Post by hortstu on 2010-02-05
Thanks presence. 

Can you give me a link that explains what we did in a little more depth so that it makes more sense to me and I can do it again?

Thanks again for the help.
Mike

---

### Post by presence1960 on 2010-02-05
> **hortstu said:**
> Thanks presence. 

Can you give me a link that explains what we did in a little more depth so that it makes more sense to me and I can do it again?

Thanks again for the help.
Mike

Unfortunately I have no links for you. Maybe I can help.

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)".
Use whatever your computer spits out for the following lines.
3. Type "root (hd0,0)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

In #1 you are invoking the grub command

In #2 you are asking to find your stage1 file which is used by GRUB 0.97. It is located in /boot/grub. The response is telling you what location stage1 is at. (hdx,y) where x = device & y = partition. Note in GRUB Legacy numbering for devices & partitions start at 0. The first hard disk is (hd0), the first partition on the first hard disk is (hd0,0), the second partition on the first hard disk is (hd0,1), etc. The second hard disk is (hd1), the first partition on the second hard disk is (hd1,0), the second partition on the second hard disk is (hd1,1), etc.

In #3 you are setting your root partition that contains the stage1 & other files needed to boot. GRUB will look here for those files.

In #4 you are choosing which hard disk MBR to put GRUB onto.

---

### Post by hortstu on 2010-02-05
Thank you again.  Maybe you can help me with one more issue related to this scenario.

The drive I installed hardy on via USB is apparently missing something.  It won't boot.  I have no problem reinstalling hardy if that's the best way but how do I do it so that I don't end up with these same issues?thing 

I already did a bunch of updates and installed some things that I'd rather not redo if I don't have to.  Is there a way to solve the boot problem without reinstalling?

---

### Post by presence1960 on 2010-02-05
> **hortstu said:**
> Thank you again.  Maybe you can help me with one more issue related to this scenario.

The drive I installed hardy on via USB is apparently missing something.  It won't boot.  I have no problem reinstalling hardy if that's the best way but how do I do it so that I don't end up with these same issues?thing 

I already did a bunch of updates and installed some things that I'd rather not redo if I don't have to.  Is there a way to solve the boot problem without reinstalling?

It won't boot because when you installed Ubuntu on it you put GRUB on your disk which is why you had the problem that you had. What you need to do is put GRUB on that disk's MBR. if you don't know what commands to run to do so run in terminal ```
sudo fdisk -l
``` That is a lowercase L in -l

Post the output from that command & I'll tell you what commands to run from terminal on Live CD. Oh yeah I am assuming this disk is in your friends machine. If not we can put GRUB on it from your machine. Either way will work, just let me know which machine the disk is in.

---

### Post by hortstu on 2010-02-05
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfd06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa8ffa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris
```


Another thing I should have asked before is what information are you getting from these things that is helping you determine how to solve the problem?

Just in case you can't tell from the output, the 160Gig is my internal drive, and the 120 Gig is my friends which is hooked up via USB.

Thanks again for all your help.  It is really appreciated...

I see you're in philly... you getting as much snow as were getting here on the coast?

---

### Post by presence1960 on 2010-02-05
> **hortstu said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfd06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa8ffa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris
```


Another thing I should have asked before is what information are you getting from these things that is helping you determine how to solve the problem?

Just in case you can't tell from the output, the 160Gig is my internal drive, and the 120 Gig is my friends which is hooked up via USB.

Thanks again for all your help.  It is really appreciated...

I see you're in philly... you getting as much snow as were getting here on the coast?

OK you want to put GRUB on MBR of that external disk. The disk is sdb (hd1) and the root partition is (hd1,0). So boot the Live CD with that external disk plugged in. Choose "try Ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo grub
```
At the grub. prompt we can skip the find /boot/grub/stage1 command because we know that info already. But if you want you can run that command. you will get both the (hd0,0) and (hd1,0) replies. We want to use the (hd1,0) because that is the external disk.

Next run ```
root (hd1,0)
```

Then run ```
setup (hd1)
```

Then run ```
quit
```

GRUB will now be on MBR of the external disk. When you put that back in your friends machine he/she should be good to go.

As far as GRUB Legacy 0.97 goes the instructions I gave you are all I have. The knowledge comes with doing it. But for GRUB2 and partitioning I have links if you want them.

Also the boot info script is a great tool to learn about your setup & boot process. Do this:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Open the file and review all the info about your machine & boot process. This is a great troubleshooting tool. If you need help interpreting the info PM me.

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by presence1960 on 2010-02-05
Oh yeah BTW we are expecting 14" - 18"

---

### Post by hortstu on 2010-02-06
Thanks everything is working perfectly.  I'll pm some questions about the text file.

How do I mark this solved?

---

### Post by presence1960 on 2010-02-06
> **hortstu said:**
> Thanks everything is working perfectly.  I'll pm some questions about the text file.

How do I mark this solved?

On the forum page under Thread Tools (top right) choose "Mark as Solved"

---

