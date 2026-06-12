---
title: "Boot Info Script: How to"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by louieb on 2009-10-14
One useful tool for finding and fixing boot problems is the Boot Info Script. I often ask for the output when helping find and fix boot problems. So I put this little how to together to keep from typing the same thing over and over. (lazy). 

Special thanks to meiefra for authoring the script and making it available.  

[COLOR=Navy]**How to get it **[/COLOR]- Download it from here. [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

How to run it:  
[COLOR=Navy]**From your Ubuntu hard drive install:**[/COLOR]

Open a terminal window - Applications>Accessories>Terminal 

Type or cut n paste the following. 
```
sudo bash ~/Desktop/boot_info_script*.sh
```[COLOR=Purple]Update Karmic users [/COLOR]- the default download directory is now ~/Downloads 
```
sudo bash ~/Downloads/boot_info_script*.sh
```If you have changed the Firefox default download location. Then change the **~/Downloads/** part of the command to your download directory. 

You will be asked for a password - your user password. You will not see the cursor move or see any stars as you type - thats the way of the Linux terminal. Type it in and press enter.

**[COLOR=Navy]Where to find its output: [/COLOR]**
The script creates file RESULTS.TXT in same directory it is stored in. ( default ~/Downloads)
[COLOR=Navy]**Add it to your post:**[/COLOR]
Open RESULTS.TXT in your favorite text editor - cut and paste - it can be long **please use code tags** (the # on the tool bar) or add the file as an attachment.
[B][COLOR=Navy]
If you can't boot into the Ubuntu install:[/COLOR][/B]
From a live Ubuntu CD:
Same as above - except you will not be asked for a password.
 
Comments and suggestions are welcome.

---

### Post by louieb on 2009-10-20
Here is the RESULTS.TXT file for a Desktop that Boots XP, Win 7 and Ubuntu Jaunty. It has a 200GB and a 320GB HDD. Both are SATA hard drives.   

Whats in the MBR? This PC boot straight to XP if sda is 1st in the boot order.
If sdb is 1st it boots to Grub legacy. The menu has 3 entries for Jaunty, XP and Win7.  
```

============================= Boot Info Summary: 

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

```sda1 -  A boot able XP is installed. note the boot files
```

sda1: ___________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   [COLOR=Red]/boot.ini /ntldr /NTDETECT.COM[/COLOR]

```sda2 -  A partition for data formated with the NTFS file system. Not bootable note no boot files. 
```

sda2: ____________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```Note sda6 - Linux swap - Ubuntu installed on sdb - though it would be a good idea to put swap on sda. 
```

sda3: _____________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: ____________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: ____________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```Small (25MB) dedicated Grub partition. When sdb is the boot drive the Grub menu in this partition is displayed.
```

sdb1: _________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

```sdb2 - Win7 installed and bootable by grub - note boot files
```

sdb2: __________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   [COLOR=Red]/bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

```Extended partiton - Holds Ubuntu Jaunty /home and / (root) + a couple of data partitions. 
```

sdb3: ____________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: ____________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _____________________________________________________________
    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 94839384 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   [COLOR=Red]/boot/grub/menu.lst /etc/fstab[/COLOR]

sdb7: ____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: ____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

```output of fdisk -lu (start and end block listed in sectors). 
```

=========================== Drive/Partition Info: 

Drive: sda ___________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0af20af2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    65,529,134    65,529,072   7 HPFS/NTFS
/dev/sda2          65,529,135   325,701,809   260,172,675   7 HPFS/NTFS
/dev/sda3         388,612,350   390,716,864     2,104,515   5 Extended
/dev/sda5         388,612,413   390,716,864     2,104,452  82 Linux swap / Solaris
/dev/sda4         325,701,810   388,612,349    62,910,540   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf106f8b9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        64,259        64,197  83 Linux
/dev/sdb2    *         64,260    60,854,219    60,789,960   7 HPFS/NTFS
/dev/sdb3          60,854,220   625,137,344   564,283,125   5 Extended
/dev/sdb5          60,854,283    71,344,664    10,490,382  83 Linux
/dev/sdb6          71,344,728   134,255,204    62,910,477  83 Linux
/dev/sdb7         134,255,268   618,839,864   484,584,597   7 HPFS/NTFS
/dev/sdb8         618,839,928   625,137,344     6,297,417   7 HPFS/NTFS


``````

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="48FC850AFC84F40A" LABEL="XPOS" TYPE="ntfs" 
/dev/sda2: UUID="C4842336842329FE" LABEL="XPData" TYPE="ntfs" 
/dev/sda4: UUID="2A4F1B1F6E9AF820" LABEL="XPextra" TYPE="ntfs" 
/dev/sda5: UUID="a9fdf3fc-0dc5-4c4d-82dd-04eb21e59d38" TYPE="swap" 
/dev/sdb1: LABEL="grub" UUID="aeb5f918-5e5f-11de-b06b-00112fd54e0a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="63A1491B45782151" LABEL="win7" TYPE="ntfs" 
/dev/sdb5: LABEL="Jauntyh" UUID="f5633bca-4f6e-4e75-9f4d-a6b19effa94f" TYPE="ext3" 
/dev/sdb6: LABEL="Jauntyr" UUID="c9cbf367-eb07-45d1-802f-0e3708630de4" TYPE="ext3" 
/dev/sdb7: UUID="0A1BC8AB538A1664" LABEL="blackstuff" TYPE="ntfs" 
/dev/sdb8: UUID="1C798EDE5631E28B" LABEL="xpswap" TYPE="ntfs" 

=============================== "mount" output: 
[COLOR=Red]/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)[/COLOR]
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
[COLOR=Red]/dev/sdb5 on /home type ext3 (rw,relatime)[/COLOR]
/dev/sdb7 on /media/blackstuff type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lou/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lou)


```if found the content of will be listed. 
    /boot/grub/menu.lst
   /grub/menu.lst  /NST/menu.lst  
   /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
 

```

================================ sda1/boot.ini: 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

``````

============================= sdb1/grub/menu.lst: =============================

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
default   saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout   7

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage=/splash/debsplash.xpm.gz


## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

title Microsoft Windows XP Professional (hd1,0)
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      savedefault
      chainloader +1
title Microsoft Windows 7 (hd0,1)
      rootnoverify (hd0,1)
      makeactive
      savedefault
      chainloader +1
title Linux2 chain load (hd0,5)
     root   (hd0,5)
     savedefault
     chainloader  +1

title Linux2 configfile (hd0,5)
     savedefault
     configfile (hd0,5)/boot/grub/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2

``````

=========================== sdb6/boot/grub/menu.lst: ===========================

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
default   0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout   10

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
# title   Windows 95/98/NT/2000
# root    (hd0,0)
# makeactive
# chainloader +1
#
# title   Linux
# root    (hd0,1)
# kernel  /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c9cbf367-eb07-45d1-802f-0e3708630de4

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
# defoptions=quiet splash quiet

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

title   Ubuntu 9.04, kernel 2.6.28-15-generic
uuid    c9cbf367-eb07-45d1-802f-0e3708630de4
kernel    /boot/vmlinuz-2.6.28-15-generic root=UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 ro quiet splash quiet 
initrd    /boot/initrd.img-2.6.28-15-generic
quiet

title   Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid    c9cbf367-eb07-45d1-802f-0e3708630de4
kernel    /boot/vmlinuz-2.6.28-15-generic root=UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 ro  single
initrd    /boot/initrd.img-2.6.28-15-generic

title   Ubuntu 9.04, kernel 2.6.28-14-generic
uuid    c9cbf367-eb07-45d1-802f-0e3708630de4
kernel    /boot/vmlinuz-2.6.28-14-generic root=UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 ro quiet splash quiet 
initrd    /boot/initrd.img-2.6.28-14-generic
quiet

title   Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid    c9cbf367-eb07-45d1-802f-0e3708630de4
kernel    /boot/vmlinuz-2.6.28-14-generic root=UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 ro  single
initrd    /boot/initrd.img-2.6.28-14-generic

title   Ubuntu 9.04, memtest86+
uuid    c9cbf367-eb07-45d1-802f-0e3708630de4
kernel    /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title   Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title   Microsoft Windows XP Professional
rootnoverify  (hd0,0)
savedefault
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title   Windows Vista (loader)
rootnoverify  (hd1,1)
savedefault
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader +1


=============================== sdb6/etc/fstab: 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=c9cbf367-eb07-45d1-802f-0e3708630de4 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=f5633bca-4f6e-4e75-9f4d-a6b19effa94f /home           ext3    relatime        0       2
# /media/blackstuff was on /dev/sdb7 during installation
UUID=0A1BC8AB538A1664 /media/blackstuff ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=a9fdf3fc-0dc5-4c4d-82dd-04eb21e59d38 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```Good to know if dealing with Grub error 18.
```

=================== sdb6: Location of files loaded by Grub: ===================


  48.5GB: boot/grub/menu.lst
  48.5GB: boot/grub/stage2
  48.5GB: boot/initrd.img-2.6.28-14-generic
  48.5GB: boot/initrd.img-2.6.28-15-generic
  48.5GB: boot/vmlinuz-2.6.28-14-generic
  48.4GB: boot/vmlinuz-2.6.28-15-generic
  48.5GB: initrd.img
  48.5GB: initrd.img.old
  48.4GB: vmlinuz
  48.5GB: vmlinuz.old

```This is a card reader built in to an HP printer. 
```

=======Devices which don't seem to have a corresponding hard drive==============

sdc

```

---

### Post by audiomick on 2010-01-28
Hi Louie,
thanks for a great "how to". I have posted links to it heaps of times. :popcorn:

One thing though, there is a typo that jumps out at me every time I look at it
> If you can't boot into the Ubuntu install:
From a live Ubuntu CD:
Same as above - except you will [COLOR="Red"]no[/COLOR] be asked for a password.

"no" should be "not"

---

### Post by louieb on 2010-01-28
> **audiomick said:**
> "no" should be "not"

brain fart or fat finger. maybe both.  Thanks for the heads up - changed
:guitar:

---

### Post by nuwave on 2010-02-03
great info 

thanks

---

### Post by codemaniac on 2010-02-26
cannot download the  boot info script from source forge!!!!!!

---

### Post by meierfra. on 2010-02-26
> cannot download the boot info script from source forge!!!!!! 
 What exactly is the problem?  What happens if  you click on big green "Download Now" button?  
I suggest to try again. Might just have been a bad Internet connection.

---

### Post by louieb on 2010-02-26
FYI: Just downloaded **boot_info_script055.sh** - no problem.

---

### Post by BrokeMahPC on 2010-04-13
Great script - lots of use-full info! I get an unknown MBR at the end of my result.txt
Anyone know what that is?
My info is here:
[http://ubuntuforums.org/showthread.php?t=1453422](http://ubuntuforums.org/showthread.php?t=1453422)
linsay7 has multiple instances of this here:
[http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader](http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader)

---

### Post by idealistic on 2010-11-29
hi,

i tried to run the bootinfoscript 

```
ubuntu@ubuntu:/$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
```

from the live cd

and it would not create the result file

how long did it take you guys to have a result ?
after several minutes i decided it was just not wrking...

---

### Post by jvanc on 2011-03-13
I'm having trouble with GRUB not booting WinXP. I ran the bootinfo script and have posted my results.txt file. I was wondering if anyone could help me interpret it. Sorry if I'm not posting to the right place. This is my first time using a forum. Thank you.

---

### Post by wilee-nilee on 2011-03-13
> **jvanc said:**
> I'm having trouble with GRUB not booting WinXP. I ran the bootinfo script and have posted my results.txt file. I was wondering if anyone could help me interpret it. Sorry if I'm not posting to the right place. This is my first time using a forum. Thank you.

This thread is a info thread, so start a thread all your own and put the script there. Copy all the text from the script generated file, click on the (#) in the reply and paste the text between. You need the text on the thread, your own, if you can.:)

Try in the Ubuntu terminal.
sudo update-grub
before you start a new thread.

---

### Post by geazzy on 2011-05-08
> **louieb said:**
> One useful tool for finding and fixing boot problems is the Boot Info Script. I often ask for the output when helping find and fix boot problems. So I put this little how to together to keep from typing the same thing over and over. (lazy). 

Special thanks to meiefra for authoring the script and making it available.  

[COLOR=Navy]**How to get it **[/COLOR]- Download it from here. [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

How to run it:  
[COLOR=Navy]**From your Ubuntu hard drive install:**[/COLOR]

Open a terminal window - Applications>Accessories>Terminal 

Type or cut n paste the following. 
```
sudo bash ~/Desktop/boot_info_script*.sh
```[COLOR=Purple]Update Karmic users [/COLOR]- the default download directory is now ~/Downloads 
```
sudo bash ~/Downloads/boot_info_script*.sh
```If you have changed the Firefox default download location. Then change the **~/Downloads/** part of the command to your download directory. 

You will be asked for a password - your user password. You will not see the cursor move or see any stars as you type - thats the way of the Linux terminal. Type it in and press enter.

**[COLOR=Navy]Where to find its output: [/COLOR]**
The script creates file RESULTS.TXT in same directory it is stored in. ( default ~/Downloads)
[COLOR=Navy]**Add it to your post:**[/COLOR]
Open RESULTS.TXT in your favorite text editor - cut and paste - it can be long **please use code tags** (the # on the tool bar) or add the file as an attachment.
[B][COLOR=Navy]
If you can't boot into the Ubuntu install:[/COLOR][/B]
From a live Ubuntu CD:
Same as above - except you will not be asked for a password.
 
Comments and suggestions are welcome.

thaks for this tips :)

---

### Post by lister171254 on 2011-06-21
I'm getting and eeror when I run the script, but have no problems booting into either ubuntu or Windows 7.
 I have attached part (size restirction on upload) of the RESULT.txt

Do I need to run grub-install again to fix this?

---

### Post by Quackers on 2011-06-21
I would suggest that you make a new thread stating what exactly has happened. You should also mention RAID in the title perhaps.

---

### Post by conkermaniac on 2011-08-29
I have installed Ubuntu but I cannot log in (although I can get into the shell). Could someone please post detailed instructions on how to download and install the file from the shell?

(Note: I installed from the Ubuntu alternate CD, the live CD does not work for me.)

---

### Post by monkeyBug on 2011-10-05
Here's the link of my results.txt :D

[http://pastebin.ubuntu.com/703005/](http://pastebin.ubuntu.com/703005/)



MonkeyBug ;D

---

### Post by roopeshmicasa on 2012-02-18
Hi, 
I have some problem with my boot drive. Here is the output of the boot_info_script.sh attached as text file with this reply. I have already started a thread on my booting problem 
Here is link to the thread 
[http://ubuntuforums.org/showthread.php?t=1914197](http://ubuntuforums.org/showthread.php?t=1914197)
Any help will be much appreciated. Thanks in advance.

---

### Post by YannBuntu on 2012-04-24
**@louieb:** thanks for your howto. To complete your 1st post, here is also a little GUI that runs BootInfo script in 1 click (it also checks that all necessary packages are installed, creates a convenient Pastebin URL when internet is detected, and adds useful information to the log): [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)
(I'm also working with Gert to improve the script.)


[IMG]http://pix.toile-libre.org/upload/original/1335260967.png[/IMG]

---

