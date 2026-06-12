---
title: "grub boot help"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Makosz on 2010-08-23
I have installed Backtrack 4 on my computer it boots first, but i would like Ubuntu to be on top of the list. What is at /boot/grub.menu.lst is

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
timeout        5

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
# kopt=root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05808ecb-307c-4534-b7bf-235e45400dd2

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1






also could you tell me how to put codes in here the way other people do?

---

### Post by uRock on 2010-08-23
In backtrack install startupmanager and it will give you a GUI for selecting and altering the boot menu.list

---

### Post by drs305 on 2010-08-23
I was about to turn off my computer so I don't have the time to research your grub problem; but to put everything in a code box you highlight the text then press the # icon in the post's top menu or manually type [noparse]```
 at the start and 
``` at the end of what you want in the code box.

If you see smilies, which are generated by certain combinations of characters, you can prevent them by using [noparse] [/noparse] in the applicable section. [/noparse]

If I have time tomorrow morning I'll try to help you with your problem. I'm on vacation and am not spending as much time on the forums for a couple of weeks as normal.

---

### Post by oldfred on 2010-08-23
this looks like Ubuntu's menu.lst from upgrades prior to 9.10. Or is Backrack also based on 10.04 but using grub legacy?

Run this so we can see your entire configuration and give better instructions:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

If you are still using old grub you can limit the number of kernals:

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=[COLOR=Red]all[/COLOR]

Change [COLOR=Red]all[/COLOR] to [COLOR=Red]2[/COLOR].

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

Even easier is to use SUM - drs305 has a link in his signature. It works better with old grub. Startup manager is in the repositories.

---

### Post by uRock on 2010-08-23
> **oldfred said:**
> this looks like Ubuntu's menu.lst from upgrades prior to 9.10. Or is Backrack also based on 10.04 but using grub legacy?
I think Back|Track 4 was based on Karmic. When It first came out I installed it and remember it having legacy grub.

---

### Post by drs305 on 2010-08-24
You are getting good advice from *oldfred* and *urock*. 

Install StartUp-Manager via Backtrack. 

In the "Bootup Options", set the default OS/kernel.

In the "Advanced" tab you can change the value of the "Limit number of kernels to keep" to reduced the number of choices you see. It doesn't actually remove any kernels from your system.

[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Makosz on 2010-08-24
I did what oldfret told me and here it is. Oh why do I so many partitions? and why is there Ubuntu 9.04 and 10.04 with Backtrack 4? I have windows 7 Ubuntu 10.04 and Backtrack 4 that i need.

Thank you for help

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   326,356,076   295,554,157   7 HPFS/NTFS
/dev/sda4         326,360,475   625,137,344   298,776,870   5 Extended
/dev/sda5         619,916,283   624,783,914     4,867,632  83 Linux
/dev/sda6         624,783,978   625,137,344       353,367  82 Linux swap / Solaris
/dev/sda7         326,360,601   580,235,669   253,875,069  83 Linux
/dev/sda8         607,915,728   619,916,219    12,000,492  82 Linux swap / Solaris
/dev/sda9         580,235,733   606,662,594    26,426,862  83 Linux
/dev/sda10        606,662,658   607,915,664     1,253,007  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       4a5d5f61-6ac4-44cf-a607-181dfea71135   swap                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        38C0B22EC0B1F26C                       ntfs       RECOVERY                      
/dev/sda3        3AE4B445E4B40563                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e1388bc7-6a83-4d68-8c07-9825334bcd99   ext3                                     
/dev/sda6        97603b18-5265-4a97-85e5-dd82472adc98   swap                                     
/dev/sda7        05808ecb-307c-4534-b7bf-235e45400dd2   ext3                                     
/dev/sda8        8a750e05-9b77-41d6-9477-ff4e2b90e61b   swap                                     
/dev/sda9        72a7d62d-351b-4604-a5ea-63b0c296eac8   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e1388bc7-6a83-4d68-8c07-9825334bcd99 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=97603b18-5265-4a97-85e5-dd82472adc98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

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
timeout        5

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
# kopt=root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05808ecb-307c-4534-b7bf-235e45400dd2

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        05808ecb-307c-4534-b7bf-235e45400dd2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
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
UUID=05808ecb-307c-4534-b7bf-235e45400dd2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8a750e05-9b77-41d6-9477-ff4e2b90e61b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 206.8GB: boot/grub/menu.lst
 206.9GB: boot/grub/stage2
 206.8GB: boot/initrd.img-2.6.28-19-generic
 206.9GB: boot/initrd.img-2.6.31-22-generic
 206.8GB: boot/initrd.img-2.6.32-23-generic
 206.8GB: boot/initrd.img-2.6.32-24-generic
 206.9GB: boot/vmlinuz-2.6.28-19-generic
 206.8GB: boot/vmlinuz-2.6.31-22-generic
 206.8GB: boot/vmlinuz-2.6.32-23-generic
 206.9GB: boot/vmlinuz-2.6.32-24-generic
 206.8GB: initrd.img
 206.8GB: initrd.img.old
 206.9GB: vmlinuz
 206.8GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=72a7d62d-351b-4604-a5ea-63b0c296eac8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=72a7d62d-351b-4604-a5ea-63b0c296eac8

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=72a7d62d-351b-4604-a5ea-63b0c296eac8/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        72a7d62d-351b-4604-a5ea-63b0c296eac8
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=72a7d62d-351b-4604-a5ea-63b0c296eac8 ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        72a7d62d-351b-4604-a5ea-63b0c296eac8
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=72a7d62d-351b-4604-a5ea-63b0c296eac8 ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        72a7d62d-351b-4604-a5ea-63b0c296eac8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro single 
initrd        /boot/initrd.img-2.6.32-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro single 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro single 
initrd        /boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode) (on /dev/sda7)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=05808ecb-307c-4534-b7bf-235e45400dd2 ro single 
initrd        /boot/initrd.img-2.6.28-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title        Ubuntu 10.04.1 LTS, memtest86+ (on /dev/sda7)
root        (hd0,6)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=72a7d62d-351b-4604-a5ea-63b0c296eac8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=4a5d5f61-6ac4-44cf-a607-181dfea71135 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 297.4GB: boot/grub/menu.lst
 297.4GB: boot/grub/stage2
 297.4GB: boot/initrd.img-2.6.30.9
 297.4GB: boot/vmlinuz-2.6.30.9
 297.4GB: initrd.img
 297.4GB: vmlinuz
```

---

### Post by spiky001 on 2010-08-24
I have just unstalled BT4 it shows up as 8,10 if this helps

---

### Post by oldfred on 2010-08-24
The grub in the MBR is from Backtrack. Do you want to boot it and have Ubuntu first in its menu.lst or do you want to boot Ubuntu first and have backtrack in its menu?

I would boot Ubuntu. With old grub this is how to reinstall grub to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

#reset grub boot
[COLOR=DarkRed]sudo grub[/COLOR]
find /boot/grub/stage1 #you will get a response such as  (hd0,6) & you may get several drive, partition listings Ubuntu is in 0,6 or  partition sda7
[COLOR=DarkRed]root (hd0,6)[/COLOR] #use the numbers from the previous command x is drive, y is partition  or root (hd0,6)
[COLOR=DarkRed]setup (hd0)[/COLOR]

---

