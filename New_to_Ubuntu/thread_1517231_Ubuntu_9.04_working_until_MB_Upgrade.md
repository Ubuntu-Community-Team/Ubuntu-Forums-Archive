---
title: "Ubuntu 9.04 working until MB Upgrade"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by bcatanzaro on 2010-06-24
Hi,

  I had Ubuntu 9.04 working great (single O/S PC), but on an old MB.  I  upgraded another PC and scavenged an:  ASUS P5B-E MB w/3 GB RAM.  I  hooked up my IDE drive and booted.  I got the infamous GRUB error:

GRUB Loading stage 1.5.
GRUB loading please wait...
Error 21

  Booting off of the LiveCD, I can see my old drive.  I can identify the  boot partition.  I cannot repair the GRUB.

1.  Is it true that GRUB doesn't work with this MB + IDE drives?
2.  Can I repair GRUB?
3.  Should I replace GRUB with LILO?
4.  Can I recover without trashing my files?

Thanks!

P.S.  Already tried the straightforward:  [http://ubuntuforums.org/showthread.php?t=1146056 .]("http://ubuntuforums.org/showthread.php?t=1146056")
No errors were generated. Didn't help...

[FONT=Courier New]ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/sda: 500.1 GB,  500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units  = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier:  0x0002b64b

   Device Boot      Start         End      Blocks    Id  System
/dev/sda1   *           1       24316   195318238+  83  Linux
/dev/sda2            24317       60801   293065762+   5   Extended
/dev/sda5           60664       60801     1108453+  82   Linux swap / Solaris
/dev/sda6           24317       48631    195310174+  83  Linux
/dev/sda7           48632       60663     96647008+   b  W95 FAT32

Partition table entries are not in disk  order
ubuntu@ubuntu:~$ [/FONT]

---

### Post by oldfred on 2010-06-24
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

I would think the reinstall of grub legacy should have worked. 

Try running boot info script to see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by bcatanzaro on 2010-06-24
Tx oldfred

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002b64b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,636,539   390,636,477  83 Linux
/dev/sda2         390,636,540   976,768,064   586,131,525   5 Extended
/dev/sda5         974,551,158   976,768,064     2,216,907  82 Linux swap / Solaris
/dev/sda6         390,636,666   781,257,014   390,620,349  83 Linux
/dev/sda7         781,257,078   974,551,094   193,294,017   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a5062c99-dc9d-41e5-91c1-cdadc1dab978   ext3                                     
/dev/sda5        d6578777-cbe1-4c8c-97b9-eea05a58f8f6   swap                                     
/dev/sda6        c9ed1eee-c840-4ffe-be7c-98d36e090a21   ext3                                     
/dev/sda7        BC14-7232                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a5062c99-dc9d-41e5-91c1-cdadc1dab978

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a5062c99-dc9d-41e5-91c1-cdadc1dab978
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a5062c99-dc9d-41e5-91c1-cdadc1dab978 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c9ed1eee-c840-4ffe-be7c-98d36e090a21 /home           ext3    relatime        0       2
# /windows was on /dev/sda7 during installation
UUID=BC14-7232  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=d6578777-cbe1-4c8c-97b9-eea05a58f8f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  65.5GB: boot/grub/menu.lst
  65.5GB: boot/grub/stage2
  65.5GB: boot/initrd.img-2.6.28-11-generic
  65.5GB: boot/initrd.img-2.6.28-16-generic
  65.5GB: boot/initrd.img-2.6.28-17-generic
  65.6GB: boot/initrd.img-2.6.28-18-generic
  65.5GB: boot/initrd.img-2.6.28-19-generic
  65.5GB: boot/vmlinuz-2.6.28-11-generic
  65.5GB: boot/vmlinuz-2.6.28-16-generic
  65.5GB: boot/vmlinuz-2.6.28-17-generic
  65.5GB: boot/vmlinuz-2.6.28-18-generic
  65.5GB: boot/vmlinuz-2.6.28-19-generic
  65.5GB: initrd.img
  65.6GB: initrd.img.old
  65.5GB: vmlinuz
  65.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-06-24
I do not see anything wrong with the results.txt. Since you only have Ubuntu you will not see the menu, so perhaps it is something in the install.

Have you pressed escape from the BIOS until a menu appears to see if you get the menu. Then try booting the recovery. In 9.04, it only gets you to a command line it it works.

---

### Post by bcatanzaro on 2010-06-25
Not sure I understand.

1.  Rebooted
2.  Pressed ESC repeatedly after BIOS
3.  Got:

GRUB Loading Stage 1.5.
GRUB Loading please wait...
Error 21

ESC seemed to have no impact.  Are you saying ESC is supposed to bypass GRUB and put me into command line/console Linux or into command line GRUB or ...?

---

### Post by oldfred on 2010-06-25
No escape would get you a menu. But if grub is not loading at all it will not work.

Are you sure you did the full reinstall to the MBR?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You may have to chroot into your system from a liveCD and run updates and the install from there.
chroot to repair
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by bcatanzaro on 2010-06-25
Faithfully executed restoring the bootloader.  Followed 9.10 instructions by accident at first.  Followed up with 9.04 instructions.  All steps from terminal + grub executed without error.

Rebooted...still the same result.

I don't understand the "chroot to repair".  At the terminal prompt, typing "grub" results in:

ubuntu@ubuntu:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
ubuntu@ubuntu:~$ 

So, I dutifully installed using apt-get.  Was that OK?

---

### Post by bcatanzaro on 2010-06-25
[http://ubuntuforums.org/showthread.php?t=341493](http://ubuntuforums.org/showthread.php?t=341493)
Says this MB doesn't support GRUB.  Could this be true?

Can I convert to LILO as suggested?  I don't understand how to do that with a system that won't load the O/S...

---

### Post by oldfred on 2010-06-25
That was back in 2007. Did you update BIOS and I would think by now most other problems would have been fixed, but you are not installing the newest Ubuntu either.

It does not hurt to experiment. You can try lilo, I have only suggested its boot loader in the MBR to boot windows. You have to install part of it to the PBR and set the boot flag (same as windows).

---

### Post by bcatanzaro on 2010-06-25
I saw ([http://ubuntuforums.org/showthread.php?t=341493](http://ubuntuforums.org/showthread.php?t=341493)) was long ago.  This is an old MB (remember I scavenged it) so I can't remember the last time I updated the BIOS.  Now without a Win O/S or a floppy drive, I'm not sure I can flash the BIOS.

The Lilo directions I found implied that I need to install it from a functioning O/S.  I'm not sure I can install it from the Ubuntu boot disk onto an existing O/S.

Using the boot disk, I could access my documents and push them onto a network drive.  At this point, I'm almost happy to just wipe out the O/S and reinstall everything with the lastest Ubuntu.  If I have to re-install, I'll likely put on Ubuntu 10.04-64 bit.  Am I likely to have just as hard a time?

---

### Post by oldfred on 2010-06-25
Often a install of grub2 when really wanting grub legacy confuses legacy and neither work. The you have to chroot into system uninstall both and reinstall one or the other.

If the computer is that old is it compatible with 64bit?

If you can boot from a liveCD or USB key you can chroot into a system and do anything. Chroot uses the operating system from the liveCD but CHange ROOT so all the operations are on the problem system.

IF you are willing to do a new install that would be the cleanest but we like to break things and then try to fix even if it takes days.:smile: My last install from a USB key took 9 minutes (but I had to figure out the nomodeset issue or my monitor went to sleep).

---

