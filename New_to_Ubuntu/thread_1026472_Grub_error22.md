---
title: "Grub error22"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by mbzn on 2008-12-31
Hi

I'm busy trying to install Ubuntu 8.10 on my pc
I have an 80GB drive as HSB with a 30GB NTFS for windoze
I then want to us the rest of the disk for Linux
the problem is that after installing Ubuntu, when I reboot i get GRUB error 22, witch i now know means that the partition can't be found
At first i had "/boot" on its own 250MB partition, then i tried to mount the entire (rest of the) disk to "/" exept for swap partition

In both cases i had the same error22 problem.
How can i fix this?

Thanx in advance

---

### Post by toni_uk on 2008-12-31
Have you tried to fix grub by booting into your system using the live cd?

---

### Post by mbzn on 2008-12-31
Hi,

i did read a post that said somthing about
"sudo grub"
"find /boot/grub/stage1"
from the live cd it said that it can not be found
though if i mount my hard drive i can see the file, in the directory as above but canot do anything with it.

how else can i fix it with the live cd?

---

### Post by louieb on 2008-12-31
If you have a separate /boot partition the find command would be
```
 sudo grub
find /grub/stage1
```

See if that works.

---

### Post by mbzn on 2008-12-31
OK, it says hd(0,5)
now what?

I'll look for the other post again an see if it works..

thanx for your help so far!!!

---

### Post by mbzn on 2008-12-31
ok, so.. What are the chances of this being a problem on my cd?
I now deleted the windows partition, reinstalled Ubuntu8.10 on the entire drive,
And I get GRUB error22????

Now i'm confused and am gonna try install 8.04.

---

### Post by caljohnsmith on 2008-12-31
I would recommend sticking with 8.10 rather than go back to 8.04, but I think if we get a little clearer picture of your setup, we can help you solve your Grub problem. How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by mbzn on 2008-12-31
Hi,

Sorry , I got your post a little too late, I'm busy installing 8.04 and plan to upgrade with the 8.10 cd, would that make a big difference?

I've tried most of the other posts "GRUB problems" all with failure.
after installing only Ubuntu and getting the same error i thought this may be an option.

Thank you!

---

### Post by mbzn on 2008-12-31
ok, now it finnished the installation on 8.04, same problem.

I'm asking myself "Harware issues?"
Thats the only logical thing that comes to mind

---

### Post by boof1988 on 2008-12-31
If you can run the code the caljohnsmith mentions in post #7, we can get a better idea of how to help solve your problem.

That script is a very useful tool.  It gives a lot of useful information to help troubleshoot.

---

### Post by mbzn on 2008-12-31
hi

so i unpluged my iomega drive(had no disk in it) and everything is working fine
If anyone knows why, please share

Thanx to all who helped!

---

### Post by wadesmart on 2009-01-25
I was working on my computer tonight when it started getting very slow. I clicked on Home on the toolbar and it said it could not be found and was not associated with ... something. I saved my data and then rebooted. I received the same error as the original poster: Error 22. I performed the following:

Booted to LiveCD, sudo grub, find /grub/stage1 
It is located at hd0,0. 

What do I do now?

Wade

---

### Post by wadesmart on 2009-01-26
I found some other posts about this and followed these instructions:

sudo grub
find /grub/stage1


sudo grub
grub> root (hd0,0)
==
checking if "/boot/grub/stage1" exists ....no
checking if "/grub/stage1" exists... yes
checking if "/grub/stage2" exists... yes
checking if "/grub/e2fs stage1_5 (hd0)"... 16 sectors are embedded
succeeded
running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu.lst" ... secceed
done.

grub> setup (hd0)
grub> quit


=====
rebooted... same message .. .Error 22.

I started live cd again and and did a search and it says hd0,0 for stage1 and stage 2. 

Wade

---

### Post by caljohnsmith on 2009-01-26
**Wadesmart**, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by wadesmart on 2009-01-26
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks 

on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    

Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: 

_________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  

-
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    

Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File 

system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    

Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /etc/fstab

sdb1: 

_________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot 

sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb3: 

_________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  

-
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    

Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: 

_____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 

sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e1fe4bf

Partition  Boot  

      Start          End         Size  Id System

/dev/sda1    *            63      481,949      481,887  83 Linux
/dev/sda2         

40,483,800  398,283,479  357,799,680   5 Extended
/dev/sda5        393,801,408  398,283,479    4,482,072  82 Linux swap / Solaris
/dev/sda6  

       40,483,926  190,482,704  149,998,779  83 Linux
/dev/sda3            481,950   40,483,799   40,001,850  83 Linux


Drive sdb: 

_____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 

sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x157e157d

Partition  Boot    

    Start          End         Size  Id System

/dev/sdb1                 63   61,432,559   61,432,497  83 Linux
/dev/sdb3         

75,714,345   78,156,224    2,441,880   5 Extended
/dev/sdb5         75,714,408   78,156,224    2,441,817  82 Linux swap / Solaris


blkid -c 

/dev/null: ____________________________________________________________

/dev/sda1: UUID="8c858ffd-8d2a-42b5-9501-42bc6a4fc6a7" TYPE="ext3" 
/dev/sda3: UUID="55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3" TYPE="ext3" 
/dev/sda5: UUID="c89caa9d-b64a-436a-87fc-4b348c977f3e" TYPE="swap" 
/dev/sda6: UUID="ca6d646f-329d-4f6a-a3e6-4d8509621a09" TYPE="ext3" 
/dev/sdb1: UUID="f2fdb6a2-f7a0-4cd5-8ef7-cde64885c59f" SEC_TYPE="ext2" 

TYPE="ext3" 
/dev/sdb5: UUID="2d2cf877-894c-4157-8dd2-261e7eed79d4" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs 

(rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs 

(rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs 

(rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts 

(rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon 

(rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type ext3 

(rw,nosuid,nodev,uhelper=hal)
/dev/sda6 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)

============================= 

sda1/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), 

grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the 

default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You 

can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If 

you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout    

    3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and 

command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 

$1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# 

makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# 

Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS 

LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit 

them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you 

want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. 

kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# 

kopt=root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub 

root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. 

alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. 

lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but 

not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic 

boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# 

xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## 

multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# 

altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a 

kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 

boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted 

system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or 

false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd        

/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro single
initrd        

/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,0)
kernel        

/vmlinuz-2.6.24-22-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd        

/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-22-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro single
initrd        

/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        

/vmlinuz-2.6.24-21-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd        

/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-21-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro single
initrd        

/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        

/vmlinuz-2.6.24-19-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd        

/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-19-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro single
initrd        

/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        

/vmlinuz-2.6.24-16-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd        

/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /vmlinuz-2.6.24-16-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro single
initrd        

/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,0)
kernel        /memtest86+.bin
quiet

### 

END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location  of files loaded by Grub: ===================


    .0GB: 

grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.24-16-generic
    .0GB: initrd.img-2.6.24-16-generic.bak
    .0GB: 

initrd.img-2.6.24-19-generic
    .0GB: initrd.img-2.6.24-19-generic.bak
    .0GB: initrd.img-2.6.24-21-generic
    .0GB: 

initrd.img-2.6.24-21-generic.bak
    .0GB: initrd.img-2.6.24-22-generic
    .1GB: initrd.img-2.6.24-22-generic.bak
    .1GB: 

initrd.img-2.6.24-23-generic
    .1GB: initrd.img-2.6.24-23-generic.bak
    .0GB: vmlinuz-2.6.24-16-generic
    .0GB: 

vmlinuz-2.6.24-19-generic
    .0GB: vmlinuz-2.6.24-21-generic
    .0GB: vmlinuz-2.6.24-22-generic
    .1GB: vmlinuz-2.6.24-23-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file 

system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# 

/dev/sda3
UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=8c858ffd-8d2a-42b5-9501-42bc6a4fc6a7 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=ca6d646f-329d-4f6a-a3e6-4d8509621a09 /home           ext3    relatime        0       2
# /dev/sda5
UUID=c89caa9d-b64a-436a-87fc-4b348c977f3e none            swap    sw              0       0
# /dev/sdb5
UUID=2d2cf877-894c-4157-8dd2-261e7eed79d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 

user,noauto,exec,utf8 0       0

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on 

/dev/sdb

00000000  eb 49 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.I....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 

07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 

2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 80 fa 80 ca 80 ea  |... ............|
00000050  54 

7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 40  |T|..1....... ..@|
00000060  7c 3c ff 74 02 88 c2 52  be 8a 7d e8 44 01 f6 c2  

||<.t...R..}.D...|
00000070  80 74 55 b4 41 bb aa 55  cd 13 5a 52 72 4a 81 fb  |.tU.A..U..ZRrJ..|
00000080  55 aa 75 44 a0 41 7c 84  c0 75 

05 83 e1 01 74 38  |U.uD.A|..u....t8|
00000090  66 8b 4c 10 be 05 7c c6  44 ff 01 66 8b 1e 44 7c  |f.L...|.D..f..D||
000000a0  c7 04 10 00 

c7 44 02 01  00 66 89 5c 08 c7 44 06  |.....D...f.\..D.|
000000b0  00 70 66 31 c0 89 44 04  66 89 44 0c b4 42 cd 13  |.pf1..D.f.D..B..|
000000c0  72 06 bb 00 70 e9 8c 00  b4 08 cd 13 73 19 f6 c2  |r...p.......s...|
000000d0  80 0f 84 ee 00 a0 4a 7c  3c ff 74 08 38 c2 74 04  

|......J|<.t.8.t.|
000000e0  88 c2 eb 83 e9 8d 00 be  05 7c c6 44 ff 00 66 31  |.........|.D..f1|
000000f0  c0 88 f0 40 66 89 44 04  31 d2 

88 ca c1 e2 02 88  |...@f.D.1.......|
00000100  e8 88 f4 40 89 44 08 31  c0 88 d0 c0 e8 02 66 89  |...@.D.1......f.|
00000110  04 66 a1 44 

7c 66 31 d2  66 f7 34 88 54 0a 66 31  |.f.D|f1.f.4.T.f1|
00000120  d2 66 f7 74 04 88 54 0b  89 44 0c 3b 44 08 7d 3c  |.f.t..T..D.;D.}<|
00000130  8a 54 0d c0 e2 06 8a 4c  0a fe c1 08 d1 8a 6c 0c  |.T.....L......l.|
00000140  5a 8a 74 0b bb 00 70 8e  c3 31 db b8 01 02 cd 13  

|Z.t...p..1......|
00000150  72 2a 8c c3 8e 06 48 7c  60 1e b9 00 01 8e db 31  |r*....H|`......1|
00000160  f6 31 ff fc f3 a5 1f 61  ff 26 

42 7c be 90 7d e8  |.1.....a.&B|..}.|
00000170  40 00 eb 0e be 95 7d e8  38 00 eb 06 be 9f 7d e8  |@.....}.8.....}.|
00000180  30 00 be a4 

7d e8 2a 00  eb fe 47 52 55 42 20 00  |0...}.*...GRUB .|
00000190  47 65 6f 6d 00 48 61 72  64 20 44 69 73 6b 00 52  |Geom.Hard Disk.R|
000001a0  65 61 64 00 20 45 72 72  6f 72 00 bb 01 00 b4 0e  |ead. Error......|
000001b0  cd 10 ac 3c 00 75 f4 c3  7d 15 7e 15 00 00 00 01  

|...<.u..}.~.....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 b1 62 a9 03 00 00  |......?....b....|
000001d0  00 00 00 00 00 00 00 00  00 00 

00 00 00 00 00 fe  |................|
000001e0  ff ff 05 fe ff ff 29 4f  83 04 98 42 25 00 00 00  |......)O...B%...|
000001f0  00 00 00 00 

00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: 

===============================

No errors were reported.

```

Wade

---

### Post by caljohnsmith on 2009-01-26
How about doing:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/grub/menu.lst
```
First thing is put a pound sign or hash # in front of the hiddenmenu line near the beginning:
```
#hiddenmenu
```
Next change your first Ubuntu entry as follows:
```
title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        (hd0,0)
kernel      /vmlinuz-2.6.24-23-generic root=UUID=55feb78d-5aa5-45fe-90a5-6d0a9b9eb3e3 ro quiet splash
initrd      /initrd.img-2.6.24-23-generic
quiet
```
Then reboot, see if you get the Grub menu, and if you do, choose the first "2.6.24-23-generic" kernel, and let me know if it boots. We can work from there.

---

### Post by wadesmart on 2009-01-26
The only thing I found to change was the #hidden menu part. What you put down was already there exactly as you have written it.

When it rebooted it was Error 22 again.

Wade

---

### Post by caljohnsmith on 2009-01-26
Are you getting the Grub error before seeing the Grub menu? If so, have you checked to make sure your Ubuntu drive is first in the BIOS boot order? Also, what HDD-related settings do you have in your BIOS? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc, and please let me know what you have.

---

### Post by wadesmart on 2009-01-26
When I turn on the computer I get the error pretty much straight away. Nothing happens before or after this error. 

On the boot menu:
SS-WDC Wd400EB-11CPF0 - hard drive
SM-HL-DT-ST RW/DVD GCC-4480B

BIOS
Boot Device Priority->
1st - cd 
2nd hd
3nd disabled


Under BIOS > Advanced > IDE Configuration
IDE Controller = both
PCI IDE Bus Master = enabled
Primary IDE Master = Maxtor
Primary Slave = 
Secondary IDE Master = HL-DT-ST RW/DVD
Secondary IDE Slave = WDC WD400EB

Primary IDE Master
Type = Auto
LBA Mode = supported
Block Mode = 16 sectors
PIO Mode = Mode 4
Ultra DMA = Mode 6

Secondary IDE Master
Type = audo
LBA Mode = supported
PIO Mode= Mode 4
Ultra DMA = Mode 2

Secondary IDE Slave
Type = auto
Block Mode = 16 sectors
LBA Mode = supported
PIO Mode= Mode 4
Ultra DMA = Mode 2

---

### Post by caljohnsmith on 2009-01-26
The script showed results for both a 200 GB drive and a 40 GB drive. Is the 40 GB HDD your "Maxtor" drive, and is the 200 GB drive your Western Digital (WDC) drive? How about trying this:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
And please post the output before doing "quit". Then reboot, and let me know if you still get the Grub error 22, or if it is a different error.

---

### Post by wadesmart on 2009-01-26
Maxtor = 200gb drive 
/dev/sda

Western Ditigal = 40gb drive
/dev/sdb

grub > setup (hd0)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists.... yes
Checking if "/grub/stage2" exists.... yes
Checking if "/grub/e2fs_stage1_5" exists .... yes
Running "embed /grub/e2fs_stage1_5 (hd0)".... 16 sectors are embedded.
succeeded
Running "install /grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/grub/stage2 /grub/menu.lst" ... succeeded
Done.

grub>
grub> quit

After quit it shows: Proving devices to guess BIOS drives. This may take a long time.
and there is a ubuntu@ubuntu:~$ prompt immediately following.

A menu came up with a list.. but immediately went away and presented:
Error 15: File not found
Select any key...

A menu list came up and I am selected the first one

Error 15: file not found

same error on every on of the options listed

---

### Post by caljohnsmith on 2009-01-26
OK, that means you are actually booting the 40 GB sdb drive on start up instead of your Ubuntu drive. If you don't mind that, then you can do the following to correct your menu.lst:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/grub/menu.lst
```
And change all your Ubuntu entries to use (hd1,0) instead of (hd0,0). Reboot, and let me know how far you get.

---

### Post by wadesmart on 2009-01-26
Dont I want to start on the drive that has ubuntu on it?
I dont care either way as long as it works.
One drive has my backups and the other is my os and programs.

Wade

---

### Post by caljohnsmith on 2009-01-26
> **wadesmart said:**
> Dont I want to start on the drive that has ubuntu on it?
I dont care either way as long as it works.
One drive has my backups and the other is my os and programs.

Wade
Yes, it would be a lot more ideal if you could just boot the Ubuntu drive on start up instead of your 40 GB drive, but I assumed you haven't figured out a way to change your BIOS to boot the Ubuntu drive. If you wanted, you could open up your computer and swap the Ubuntu drive and 40 GB drive so that the Ubuntu drive is primary master. Then I would think you could boot it on start up. It's up to you, but if you keep your present setup, you'll need to modify your menu.lst as per post #22 so you can boot Ubuntu.

---

### Post by wadesmart on 2009-01-26
Ok. I changed the hd cables. 
Rebooted.
It gave me a Error file not found, and then gave me the menu list. Same problem clicking on each one.

I booted again to cmd and did 
grub> find grub/stage1
Error 15: file not found
did it again and it said
grub> (hd1,0)
grub> setup (hd1,0)
Checking if "/boot/grub/stage1? exists... no
checking if "/grub/stage1" exists .... yes
checking if "/grub/stage2" exists .... yes
checking if "/grub/e2fs_stage1_5" exists .... yes
Running "embed /grub/e2fs_stage1_5 (hd1,0)" ... failed (this is not fatal)
Running "embed /grub/e2fs_stage1_5 (hd1,0)" ... failed (this is not fatal)
Running "install /grub/stage1 (hd1,0) /grub/stage2 p /grub/menu.lst " ... succeeded
Done.

Then I typed quit and it said Error 27: Unrecognized command

I screwed up ... didnt I ?

---

### Post by wadesmart on 2009-01-26
I hit submit too quick.

I just rebooted and I have the list but I still get Error File not Found

---

### Post by caljohnsmith on 2009-01-26
If you are still getting a file not found error when you select Ubuntu from the Grub menu, it sounds like you are still booting the 40 GB drive unless you all ready modified your menu.lst per the instructions in post #22. How about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd0,0)" (assuming you haven't changed your menu.lst yet), press "e" to edit it, change it to "root (hd1,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works. Let me know how that goes.

---

### Post by wadesmart on 2009-01-26
Opps... forgot that. 

Ok. 
sudo mount /dev/sbd1 /mnt
gksudo gedit /mnt/grub/menu.lst

Hidden has # in front of it. 

found root (hd0,0) and changed to (hd1,0)

My WesternDigital 40gb hd is sda
My Maxtor 200gb hd is sdb

rebooted.....

waiting..... waiting with fingers crossed....

AH!!! Opps....  A few things popped up on the screen super fast... then the menu list... and then..... then.... AH!!! got it!!

Hey, thanks for your help. I  *really* appreciate it. 

One question. How does this happen?
What causes something like this?

Wade

---

### Post by caljohnsmith on 2009-01-26
> **wadesmart said:**
> 

One question. How does this happen?
What causes something like this?

Wade
Unfortunately it happens because probably 90% of the time, the user is booting the sda drive on start up, so that's what the Ubuntu installer assumes for its defaults. But in your case it became clear you were actually booting your 40 GB sdb drive instead. Since (hd1,0) worked to boot Ubuntu, there's one last thing you will want to take care of in your menu.lst so your menu.lst doesn't break the next time you get a kernel upgrade; how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "# groot=(hd0,0)" line to use (hd1,0):
```
# groot=(hd1,0)
```
Then I think you should be all set. Cheers and enjoy your new Ubuntu install. :)

---

### Post by wadesmart on 2009-01-26
I have a hp laserjet 4050 that uses a parallel to usb cable to attach to my computer. Last week I finally got a kit to fix a problem with it. When I turned it on I started getting these errors:

kernel: [   50.037312] usb 2-1: new full speed USB device using uhci_hcd and address 6
kernel: [   50.157087] use 2-1 device descriptor read/64, error -71
kernel: [   50.384611] use 2-1 device descriptor read/64, error -71

kernel: [ 499.318187] usb 2-1: new full speed USB device using uhci_hcd and address 66

and it goes on from there counting up and up. 

This all worked before but now there is a problem. And its on any of the 6 usb ports I have.

The reason I bring this up is - this just happened like thrusday and friday and then saturday my computer was very slow and then sunday I was down. Could this be related?

Wade

---

### Post by mbzn on 2009-01-26
hi Wade

I doubt that this is related in any way. This is not a grub error.
Please start a new thread for your last question if it is not a problem, as i'm going to mark this thread as solved. So it could help other people with the same problem. Thanx for helping as i know the  answer now aswell.

Hope you find your way

---

