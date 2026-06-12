---
title: "Error 21 during GRUB's 1.5 stage"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Arno Sluismans on 2009-05-27
Hello.

First of all, I'd like to state that I have zero Linux experience, and very little knowledge of BIOS, GRUB, and anything related to those things. I know more or less what GRUB is, but I have no idea as to how to configure it.

Here's the story. I have always used Windows XP as OS for my computer. Yesterday I decided to give Ubuntu a try, and installed it without too much trouble. Yet, when I rebooted my PC to give my newly installed Ubuntu a try, my GRUB signalled Error 21 during its "stage 1.5". I know this means that GRUB can't detect my HD, but I have absolutely no clue as to how I could make it work again. I've googled it, and found quite some threads on this matter, but none was really able to help me out.

Can anybody perhaps help me out with this? Any advice, explanation or help would be greatly appreciated.

Thanks in advance & kind regards,
Arno Sluismans.

---

### Post by ajgreeny on 2009-05-27
Can you give us more info about your computer and its disks, please.
Also it would help if you can boot into the live CD, open a terminal from Applications > Accessories > Terminal, and then post the output of this command
```
sudo fdisk -l
``` and then mount your ubuntu hard disk partition, navigate to the */boot/grub/menu.lst* file and post here the menu part from the bottom of that.

It may simply need a reinstall of grub, but it is difficult to say why, or how we can help without more info.

---

### Post by Arno Sluismans on 2009-05-27
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2580    20723818+   7  HPFS/NTFS
/dev/sda2            2581       18013   123965572+   f  W95 Ext'd (LBA)
/dev/sda3           18014       35012   136544467+   7  HPFS/NTFS
/dev/sda4           35013       38913    31334782+   7  HPFS/NTFS
/dev/sda5            2581        3855    10241406   83  Linux
/dev/sda6            3856       10229    51199123+   7  HPFS/NTFS
/dev/sda7           10230       18013    62524948+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

That's what it says after I've done "sudo fdisk -l". Please give me a few minutes to check what kind of HD I have.

Also could you explain how I mount into hard disk partitions? 

Thanks a lot for wanting to help out.
Arno Sluismans

---

### Post by presence1960 on 2009-05-27
to get a better look at your set up boot from the Ubuntu Live CD, choose Try Ubuntu with no changes (or similar). When the Desktop loads open firefox and download to the Desktop the Boot Info Script from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

then open a terminal by Applications > Accessories > Terminal. Paste this command in terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
``` press enter. Post the output here. When you place the text here high light it and click # on the toolbar to place code tags around the text.

This will give us more info to help you.

---

### Post by Arno Sluismans on 2009-05-27
> **presence1960 said:**
> to get a better look at your set up boot from the Ubuntu Live CD, choose Try Ubuntu with no changes (or similar). When the Desktop loads open firefox and download to the Desktop the Boot Info Script from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

then open a terminal by Applications > Accessories > Terminal. Paste this command in terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
``` press enter. Post the output here. When you place the text here high light it and click # on the toolbar to place code tags around the text.

This will give us more info to help you.

Would that show you my hard disk information? I have the thing in my hands at this very moment, trying to figure out what exactly you need to know.

Some things it says:
Seagate is the brand, I guess. It also says "Barracuda 7200.10, 320 Gbytes."

Going to plug in my PC again and do the things you told me.

Thanks.

---

### Post by presence1960 on 2009-05-27
that will give all the info related to your partitions and boot set up. rather than run multiple commands to get the info it is all in this one function.

BTW I swear by Seagate Hard drives, they are all I ever use.

---

### Post by Arno Sluismans on 2009-05-27
> **presence1960 said:**
> that will give all the info related to your partitions and boot set up. rather than run multiple commands to get the info it is all in this one function.

BTW I swear by Seagate Hard drives, they are all I ever use.

Are they that good? Or was that some subtile sarcasm?
I really don't know myself; I really don't know a thing about hard disks and such. I've still got lots to learn, I suppose. :)

---

### Post by presence1960 on 2009-05-27
I think they are the best. I have used many brands over the years and in my experience Seagate internal hard drives are the best.

---

### Post by presence1960 on 2009-05-27
I gotta go food shopping. Post that info so someone will be able to help you.

---

### Post by Arno Sluismans on 2009-05-27
```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
```

That's what it says. The RESULTS.txt document shows pages of text. Is there any specific part you want to see, or all of it?

---

### Post by presence1960 on 2009-05-27
post the entire contents of the RESULTS.txt file which is on your desktop

---

### Post by Arno Sluismans on 2009-05-27
Okay, sorry for the delay. Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,447,699    41,447,637   7 HPFS/NTFS
/dev/sda2          41,447,700   289,378,844   247,931,145   f W95 Ext d (LBA)
/dev/sda5          41,447,763    61,930,574    20,482,812  83 Linux
/dev/sda6          61,930,638   164,328,884   102,398,247   7 HPFS/NTFS
/dev/sda7         164,328,948   289,378,844   125,049,897   7 HPFS/NTFS
/dev/sda3         289,378,845   562,467,779   273,088,935   7 HPFS/NTFS
/dev/sda4         562,467,780   625,137,344    62,669,565   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="184446B244469284" TYPE="ntfs" 
/dev/sda3: UUID="DED24F94D24F7037" LABEL="LWoot" TYPE="ntfs" 
/dev/sda4: UUID="15746CCCEB509BB1" LABEL="Doc" TYPE="ntfs" 
/dev/sda5: UUID="1cdf7b7f-f852-44b8-9d5d-6535f2032979" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="B84464374463F712" LABEL="Stuff" TYPE="ntfs" 
/dev/sda7: UUID="4258B2C558B2B74F" LABEL="Rest" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1cdf7b7f-f852-44b8-9d5d-6535f2032979 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cdf7b7f-f852-44b8-9d5d-6535f2032979

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
uuid        1cdf7b7f-f852-44b8-9d5d-6535f2032979
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cdf7b7f-f852-44b8-9d5d-6535f2032979 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1cdf7b7f-f852-44b8-9d5d-6535f2032979
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cdf7b7f-f852-44b8-9d5d-6535f2032979 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1cdf7b7f-f852-44b8-9d5d-6535f2032979
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
makeactive
chainloader    +1


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
UUID=1cdf7b7f-f852-44b8-9d5d-6535f2032979 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  21.3GB: boot/grub/menu.lst
  21.3GB: boot/grub/stage2
  21.4GB: boot/initrd.img-2.6.28-11-generic
  21.3GB: boot/vmlinuz-2.6.28-11-generic
  21.4GB: initrd.img
  21.3GB: vmlinuz
```

---

