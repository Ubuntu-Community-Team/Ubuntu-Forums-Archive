---
title: "Quad-boot: Grub can find only 2/4 OS's"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by webwiller on 2009-05-09
Hi all 'n thx in advance for your kind help! Well, I repartitioned my drive and wanted to have **Win7, WinXP, Jaunty & Intrepid** (4-OS's) on it. I tried out Jaunty but it's giving me some trouble here and there so I'd like to keep the possibility to boot into Intrepid just in case.

Therefore I created 1 partition for Win7, one for XP, a "/boot" partition, 1 for Jaunty, 1 for Intrepid, 1 swap, 1 "/home" & a shared ntfs partition "/mnt/data".

**In order I installed** Win7 first, WinXp second, Jaunty and Intrepid.

Everything went through fine 'n easy, very smoothly. The "only" trouble is that, after all, **grub can only load 2-OS's: Intrepid & Win7**. Jaunty & XP **are missing from grub boot menu**.

I tried this ([http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")) to recover grub. From a live-cd in a terminal window I put:

> webwiller@webwiller-laptop$ sudo grub

As a result I got a  shell where then I put:

> >root (hd0,2)

>setup (hd0)

>quit

Maybe I made a mistake cause having **a separate /boot partition** I had to give grub the command: ">setup (hd0,2)" --which is my actual /boot partition-- instead of the command: ">setup (hd0)" that rewrites grub to the MBR.

But I believe this is not the real problem...any clue P-L-E-A-S-E-?? 

TxTxTx!!!;)

---

### Post by Black_Wolf_92 on 2009-05-09
please post what your fstab file looks like, from this output.

> 
sudo gedit /etc/fstab


---

### Post by Elfy on 2009-05-09
I wouldn't use sudo gedit to open a file to look, rather you can use cat in a terminal (or just gedit if you prefer :) ) - in fact it's best to use gksudo with gui apps - link below

```
cat /etc/fstab
```

It might also be helpful to have a list of your partitions

```
sudo fdisk -l
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by webwiller on 2009-05-09
NB: I MADE A MISTAKE, GRUB CAN LOAD ONLY XP AND INTREPID. Therefore I guess that XP loader overwrited Win7 boot-loader, and Intrepid's grub overwrited Jaunty's one! I still havnt a clue 'bout how to sort this out! lol;)


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=108ef78e-3c80-4c1c-bbac-bf4ac062bb55 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=1a2e04f1-1561-46a0-a629-b26db1b92bf1 /home           ext3    relatime        0       2
# /dev/sda9
UUID=5292FCB0425C232B /mnt/data       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1A2B268F2DDE0810 /winseven       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=716CEAA91E12525A /winxp          ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=877c5f08-c81b-4530-9b9d-25cb0e1a6054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by webwiller on 2009-05-09
> webwiller@webwiller-laptop:~$ sudo fdisk -l

Disco /dev/sda: 250.0 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x80d2f3ee

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        5221    10482412+   7  HPFS/NTFS
/dev/sda3            5222        5237      128520   83  Linux
/dev/sda4            5238       30401   202129830    5  Esteso
/dev/sda5            5238        6804    12586896   83  Linux
/dev/sda6            6805        8109    10482381   83  Linux
/dev/sda7            8110        8240     1052226   82  Linux swap / Solaris
/dev/sda8            8241        9415     9438156   83  Linux
/dev/sda9            9416       30401   168570013+   7  HPFS/NTFS

Disco /dev/sdb: 640.1 GB, 640135028224 byte
255 testine, 63 settori/tracce, 77825 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x1a146509

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    7  HPFS/NTFS

(the last one is my picture cd which is usb connected, sry)

---

### Post by webwiller on 2009-05-09
> webwiller@webwiller-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=108ef78e-3c80-4c1c-bbac-bf4ac062bb55 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=1a2e04f1-1561-46a0-a629-b26db1b92bf1 /home           ext3    relatime        0       2
# /dev/sda9
UUID=5292FCB0425C232B /mnt/data       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1A2B268F2DDE0810 /winseven       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=716CEAA91E12525A /winxp          ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=877c5f08-c81b-4530-9b9d-25cb0e1a6054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Here is it!

---

### Post by webwiller on 2009-05-09
I'm missing the 5th partition there! But...if I open GParte from inside Intrepid, not from live cd, I can see it right there!
????

---

### Post by webwiller on 2009-05-09
Anyway... /dev/sda5 file system is ext4 and mount point is root (/) and it's Jaunty's. Dont know why it isn't there.

---

### Post by webwiller on 2009-05-09
I tried to move grub to its own /boot partition as follows:

> grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,2) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.

It looks like it didnt work...

But my boot menu still gives me same options, XP or 8.10. Well, really tooooo late now, I go to sleep, back in 6hrs time to sort things out! ;)

---

### Post by Operan on 2009-05-09
I can only help you boot into Win 7.

sudo vim /boot/grub/menu.lst (sudo gedit /boot/grub/menu.lst )

then add the following line to the end of file:

title Windows 7 
root (hdx,y)          
makeactive
chainloader +1

Replace x,y with your partition which Win 7 is installed.

Save it. Next time power on your computer U will see the opntion Windows 7 to boot.

---

### Post by b0b138 on 2009-05-09
As a side note the reason sda5 (jaunty) isn't in your fstab from intrepid is because intrepid can't read ext4. Shoud've installed jaunty last. ;)

I'm under the assumption that reinstalling grub will be necessary and will also need to be done from a jaunty disk (again so ext4 can be seen)

---

### Post by Jungle_King on 2009-05-09
This might not work as I've made it from chopping up from various sources.

You might also need to play with the root. E.g change it to (hd0,3) or (hd0,5) until you find the right partition.

From terminal:

```
# sudo gedit /boot/grub/menu.lst[code]


add this right to the end

[CODE]
# Jaunty 

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=258c88ed-3e3c-4b7b-85ff-df042eb99f38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
boot

```

My bad if its wrong. It's not tested

---

### Post by caljohnsmith on 2009-05-09
I think it would help to first get a clearer picture of your setup related to your Grub/booting problems, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by webwiller on 2009-05-09
There we are again. **I edited /boot/grub/menu.lst and at first reboot I got my Win7 on the grub menu, _BUT, loaded me into XP again!_** So I rebooted and tried the other option, "XP", and it loaded into XP as well.

Looking better at the grub menu.lst file I found an option, "*usedefault*" which was in the XP menu but not in your suggestions. I tried to insert it too. **Now I get an error trying load into Win7: BOOMGR is missing** (or "not found"...cant remember exactly). Tried again I still can boot into XP. I erased the option but the problem remained there.

I checked my Win7 and WinXP partition from inside Ubuntu, as I mounted them during installation and I found out that **file boot.ini inside Win7 partition actually points to WinXP!!!** **_This reinforce my believe tha Win XP, being installed AFTER WinSeven, HAS OVERWRITTEN Win7 bootloader._** (Maybe I can copy some files from Win7 DVD into its folder...but dont know which ones.."boot.ini" is windows's grub?)

In the grub menu.lst file I also saw how grub "tells" ubuntu to boot up, but to insert a new line for it as well I would need to know the UUUUID__bla---bla---bla code of its partition (/dev/sda5), which is missing from /etc/fstab.

:confused: I wouldnt mind reinstalling Win7 and/or Jaunty, BUT I would like to know how to make it right this time.

If I try installing LILO in the boot partition...would it be any better? Never even seen it so...if yes you shoud be so kind to guide me through.

Please GURU'S, help me out! Thx in advance!

This is how my menu.lst file looks like now (I paste ONLY the non-commented lines):

> title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Seven (loader)
root		(hd0,0)
makeactive
chainloader	+1

#Following lines addes by webwiller in order to make grub load two windows os's and another linux distro:
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

---

### Post by webwiller on 2009-05-09
```
===================== Boot Info Summary: ==========================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 84111911 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: tipo di filesystem 'ext4' sconosciuto

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

======================== Drive/Partition Info: ===========================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.0 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    62,910,539    62,910,477   7 HPFS/NTFS
/dev/sda2    *     62,910,540    83,875,364    20,964,825   7 HPFS/NTFS
/dev/sda3          83,875,365    84,132,404       257,040  83 Linux
/dev/sda4          84,132,405   488,392,064   404,259,660   5 Extended
/dev/sda5          84,132,468   109,306,259    25,173,792  83 Linux
/dev/sda6         109,306,323   130,271,084    20,964,762  83 Linux
/dev/sda7         130,271,148   132,375,599     2,104,452  82 Linux swap / Solaris
/dev/sda8         132,375,663   151,251,974    18,876,312  83 Linux
/dev/sda9         151,252,038   488,392,064   337,140,027   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 640.1 GB, 640135028224 byte
255 testine, 63 settori/tracce, 77825 cilindri, totale 1250263727 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x1a146509

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1A2B268F2DDE0810" TYPE="ntfs" 
/dev/sda2: UUID="716CEAA91E12525A" TYPE="ntfs" 
/dev/sda3: UUID="108ef78e-3c80-4c1c-bbac-bf4ac062bb55" TYPE="ext3" 
/dev/sda5: UUID="5a78e1d5-043a-40cc-bd6e-fb491c9ca0c2" TYPE="ext4" 
/dev/sda6: UUID="40e9c885-3779-4634-9d93-a54cbe0b3970" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="877c5f08-c81b-4530-9b9d-25cb0e1a6054" 
/dev/sda8: UUID="1a2e04f1-1561-46a0-a629-b26db1b92bf1" TYPE="ext3" 
/dev/sda9: UUID="5292FCB0425C232B" TYPE="ntfs" 
/dev/sdb1: UUID="9A4825294825059B" TYPE="ntfs" 

============================ "mount" output: =============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /boot type ext3 (rw,relatime)
/dev/sda8 on /home type ext3 (rw,relatime)
/dev/sda9 on /mnt/data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /winseven type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /winxp type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/webwiller/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=webwiller)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


============================= sda1/boot.ini: ==============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


========================== sda3/grub/menu.lst: ============================

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
timeout		10

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
# kopt=root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=108ef78e-3c80-4c1c-bbac-bf4ac062bb55

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

[B]# Jaunty 

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=258c88ed-3e3c-4b7b-85ff-df042eb99f38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
boot[/B]






title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Seven (loader)
root		(hd0,0)
makeactive
chainloader	+1

[B]#Following lines addes by webwiller in order to make grub load two windows os's and anothe linux distro:
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1[/B]

================ sda3: Location of files loaded by Grub: =================


  43.0GB: grub/menu.lst
  43.0GB: grub/stage2
  42.9GB: initrd.img-2.6.27-11-generic
  42.9GB: initrd.img-2.6.27-9-generic
  42.9GB: vmlinuz-2.6.27-11-generic
  42.9GB: vmlinuz-2.6.27-9-generic

======================== sda6/boot/grub/menu.lst: =========================

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
timeout		10

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
# kopt=root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=108ef78e-3c80-4c1c-bbac-bf4ac062bb55

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

[B]# Jaunty 

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=258c88ed-3e3c-4b7b-85ff-df042eb99f38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
boot[/B]






title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Seven (loader)
root		(hd0,0)
makeactive
chainloader	+1

[B]#Following lines addes by webwiller in order to make grub load two #windows os's and anothe linux distro:
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1
[/B]
============================ sda6/etc/fstab: ============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=108ef78e-3c80-4c1c-bbac-bf4ac062bb55 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=1a2e04f1-1561-46a0-a629-b26db1b92bf1 /home           ext3    relatime        0       2
# /dev/sda9
UUID=5292FCB0425C232B /mnt/data       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1A2B268F2DDE0810 /winseven       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=716CEAA91E12525A /winxp          ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=877c5f08-c81b-4530-9b9d-25cb0e1a6054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================ sda6: Location of files loaded by Grub: =================


  56.0GB: boot/grub/menu.lst
  56.0GB: boot/grub/stage2
  55.9GB: boot/initrd.img-2.6.27-11-generic
  55.9GB: boot/initrd.img-2.6.27-9-generic
  55.9GB: boot/vmlinuz-2.6.27-11-generic
  55.9GB: boot/vmlinuz-2.6.27-9-generic
  55.9GB: initrd.img
  55.9GB: initrd.img.old
  55.9GB: vmlinuz
  55.9GB: vmlinuz.old
```


BOLD is what I ADDED as sugested to try sort things out. Eraseble in any time! ;)

---

### Post by caljohnsmith on 2009-05-09
Yes, your Windows XP in sda2 put its boot files in your Windows 7 install in sda1, and also XP modified the boot sector of sda1 to boot "ntldr" (XP's boot file) instead "bootmgr" (Win 7's boot file). You could have avoided that problem by first installing Win XP, and then installing Win 7; if you do that, Win 7 will put its boot files in the Win XP partition, but you will get the option to boot either OS. Or even better, if you pull a linux trick and set the file system ID of the XP partition to "0" before you install Win 7, Win 7 will not "see" the XP partition and thus leave it untouched. That's ideal because then you would be able to boot XP and Win 7 separately from Grub without any hassle.

Or if you don't want to reinstall any OSes, you can still sort out the problem by moving Win XP's boot files back to its partition, and fixing the boot sector of both the XP and Win 7 partitions. If you have both your Win 7 and Win XP Install CD's, that would actually be pretty easy I think. If you want specific help doing that, let me know.

John

---

### Post by webwiller on 2009-05-09
YES PLEASE CARRIE ME THROUW THIS! Either one or the other method!

Yes, what I'd like is to get my grub menu letting me choose any of the OS's without any hassle.

If you think it could be made pretty easily by copyinf files around yes, I have all the installation cd's/dvd's. If you believe a clean install of everything is really needed (it really takes long to install them all, update bloody XP SP3 and everything!), please guide me throw with doing that thing about tellin Win7 to leave XP alone. I did catch the point but havn't got a clue about how to do it practically.

TyTyTy!;)

---

### Post by caljohnsmith on 2009-05-09
OK, how about starting by doing the following while you are booted into Ubuntu 8.10 on your sda6 partition:
```
sudo mv /winseven/boot.ini /winseven/ntldr /winseven/NTDETECT.COM /winxp
```
Then boot your Windows 7 Install CD, go to the command line and run:
```
bootrec /fixboot
```
Next boot your Windows XP Install CD, go to the "recovery console", and do:
```
map
```
That will show all your partitions with their corresponding drive letters; find the one that is Windows XP on sda2 (most likely it will be "C") and do:
```
fixboot C:
```
But replace "C" if the drive letter for XP on sda2 is different. Then reboot, and try booting Windows 7 and Windows XP from your Grub menu using the Grub entries that are in your menu.lst from post #15. Let me know exactly what happens, and if you run into any problems, please post the following:
```
sudo xxd -s128 -l2 -p /dev/sda1
sudo xxd -s128 -l2 -p /dev/sda2
```
And we can work from there.

John

---

### Post by webwiller on 2009-05-09
Firs code I did it, I got no response from terminal, but I guess it's fine. (dont understand the code really, I trust you! ;))

But...in order to boot in my Win7 cd...well, I have to install it first...it is not a live cd as ubuntu is...or is there a way to get a cmd line without installing it?

---

### Post by caljohnsmith on 2009-05-09
> **webwiller said:**
> Firs code I did it, I got no response from terminal, but I guess it's fine. (dont understand the code really, I trust you! ;))

That's good the command didn't return any error, it means the XP boot files should be back in the XP partition now. :)
> **webwiller said:**
> 
But...in order to boot in my Win7 cd...well, I have to install it first...it is not a live cd as ubuntu is...or is there a way to get a cmd line without installing it?
You shouldn't have to go through the Win 7 installation again when booting the Win 7 CD; I don't know exactly how to get to the command line after booting the Win 7 CD, but I know from a friend's experience there is definitely some way of doing it. See if you can do it, and if not, let me know what all the options are when you boot the Win 7 CD.

John

---

### Post by webwiller on 2009-05-09
I booted my Win7 cd, choosed "repair your PC" and got this:

```
System recovery options:
Windows found problems with your computer start up options.
Do you want to apply repairs and restart your computer?

```
If I click on "view details" I get:
```
The following start up options will be aded:
Name: Windows 7 Ultimate (recovered)
Path: Windows
Windows Device: Partition=E (30718MB)

Name: Windows Recovery Environment (recovered)
Path: Recovery\003e6205-3b74-11de-afb1-d64ae66f8b48\Winre.wim
Windows Device: Partition=E (30718MB)


```Or, if I choose "no", under that I have a window where I can choose between:

```
Use recovery tools that can fix problems starting windos, select an operating system to repair 
```  ----or:----

```
Restore your computer using a system image that you created earlier
```

---

### Post by webwiller on 2009-05-09
Leave it, I got the cmd line, I go on with your instruction;)

---

### Post by caljohnsmith on 2009-05-09
You could go ahead and choose the "repair your PC" option, and that will probably work just fine to fix your Win 7 boot sector. Or you could choose the other option about "Use recovery tools that can fix problems starting windows, select an operating system to repair", because that will give you the command line I think where you can run the bootrec command I gave. Either option would probably work, so it's up to you.

---

### Post by webwiller on 2009-05-09
Operation succeded in Win7, XP will take some time to load files

---

### Post by webwiller on 2009-05-09
the bloody prompr asked me to choose the installation I wanted to repair:
C:\windows
F:\WINDOWS

I choosed F:\, assuming is XP and it prompt me for an admin pwd!!!! But I'm quite sure I DID NOT put in a pwd! I left it blank! And also in case I did, I would SURELY have put the same I use in ubuntu, and I'm sure about which one it is but I got error 3times and pc restarted so it's now reloading files.

I a problem now...cause I dont have any other pwd to try! The only thing is....in my pwd I have a @ symbol, but I dont know if keyboard settings are for italian keyboard (QWERTY) or not in the console. Where is the symbol @ located in us keyboard?

---

### Post by caljohnsmith on 2009-05-09
> **webwiller said:**
> the bloody prompr asked me to choose the installation I wanted to repair:
C:\windows
F:\WINDOWS

I choosed F:\, assuming is XP and it prompt me for an admin pwd!!!! But I'm quite sure I DID NOT put in a pwd! I left it blank! And also in case I did, I would SURELY have put the same I use in ubuntu, and I'm sure about which one it is but I got error 3times and pc restarted so it's now reloading files.

I a problem now...cause I dont have any other pwd to try! The only thing is....in my pwd I have a @ symbol, but I dont know if keyboard settings are for italian keyboard (QWERTY) or not in the console. Where is the symbol @ located in us keyboard?
When it asks you for the password, have you tried simply not typing anything and pressing "enter"? That might work. If you do manage to login to the C: or F: Windows installs, be sure to first do:
```
dir \
```
And make sure the directory looks like the Win XP root directory (it should not have a "boot" directory for instance like Win 7 does).

BTW, the @ symbol is SHIFT+2 on a US keyboard (it's above the 2 key).

---

### Post by webwiller on 2009-05-09
I booted normally into XP to check about the pwd. Admin account did not have any, as I believed. I created one to see if it helps. I tried "fixboot F:" from the cmd line inside XP but it returnded that fixboot is not a valid cmd. Let's see...

---

### Post by sandyeggoboy on 2009-05-09
This sounds like you are in the same boat as I .. i ma tracking down how to re-install the bootloader (GRUB) back onto the hard drive. something like "sudo grub-install ....... " i am trying to figgure out the ...... part.

---

### Post by caljohnsmith on 2009-05-09
> **sandyeggoboy said:**
> This sounds like you are in the same boat as I .. i ma tracking down how to re-install the bootloader (GRUB) back onto the hard drive. something like "sudo grub-install ....... " i am trying to figgure out the ...... part.
Actually, webwiller is not trying to do anything with the "grub-install" command, and he is not trying to reinstall Grub. If you have a question about that command, please be considerate and don't hijack this thread--instead start your own thread.

Thanks,
John

---

### Post by webwiller on 2009-05-09
noway! 
It continue saying password is wrong. I tried with the one I just programmed, tried admin or passord, none of them worked.

I find it very weird...and I find also weird that win7 call C:\ its own partition (fine) but XP has called F:\ its one! And it is on the second partition...maybe cause Win7 already numerated existing partitions? I'm sure XP is on F:\, but could it be he believes to be in C:\ cause he's ovrewrittn boot files there, over win7 ones? Do I maybe have to choose C:\ to fixboot XP???? that's why it hassles me with pwd which belongs to win7 (that obliged me to put in one?)

HELP! aNY WORKAROUND?

---

### Post by caljohnsmith on 2009-05-09
Try logging into the C:\ partition instead and run the "dir \" command to check if it is Win XP or Win 7.

---

### Post by webwiller on 2009-05-09
I'm actually SURE XP is on F, I can see it from inside xp (whare I can boot) and cause of partition dimensions. Do I have to make: \dir to check this? IfI'm in the right partition?

---

### Post by webwiller on 2009-05-09
Enter is the command to restart the computer and that's what it does. Can I not do fixboot F: from INSIDE win xp? A cmd prompt inside the OS? Or in any other way?

---

### Post by caljohnsmith on 2009-05-09
OK, let's instead do this the linux way. How about downloading the attached "XP_PBR_9sectors.txt" file to your Ubuntu desktop, and then do:
```
sudo dd if=~/Desktop/XP_PBR_9sectors.txt of=/dev/sda2 bs=80 skip=1 seek=1 conv=notrunc
```
Also, please post the output of the following:
```
sudo xxd -s128 -l2 -p /dev/sda1
```
Next reboot, and try XP and Win 7 from your Grub menu. Let me know exactly what happens and we can work from there.

John

---

### Post by webwiller on 2009-05-09
Sry for the delay...but first I found out how STUPID am zi, cause F:\ was just my mediabox remained connected to the pc all time long!!!
Lately I found out I had C:\ and E:\ drives, tried log into E:\ but looks like it is WIN7 partition, which is weird but....so I am now trying to log into C:\ to have a look in there too.
Inbetween I had to solve the pwd issue....ty for spending your time with me, really much appreciated!

---

### Post by webwiller on 2009-05-09
ok, i go for download and other way round

---

### Post by webwiller on 2009-05-09
```
webwiller@webwiller-laptop:~$ sudo dd if=~/Scrivania/XP_PBR_9sectors.txt of=/dev/sda2 bs=80 skip=1 seek=1 conv=notrunc
[sudo] password for webwiller: 
56+1 registrazioni dentro
56+1 registrazioni fuori
4528 byte (4,5 kB) copiati, 0,000426524 s, 10,6 MB/s
webwiller@webwiller-laptop:~$ sudo xxd -s128 -l2 -p /dev/sda1
08cd

```

This is it, I go for reboot now n let oyu know!;)

Translated is:
56+1 registrations out
56+1 registrations in

---

### Post by webwiller on 2009-05-09
Rebooting and trying to get into WIN7 I get this error: NTLDR missing, press ctrl+alt+del to reboot.

Trying to log into Jaunty reports: Error15, press a key to continue, and takes me bak to grub's menu...

---

### Post by webwiller on 2009-05-09
But...if you explain me in donkey way, how do I tell Win7 to leave XP untouched, I will reinstall everything in another moment, cause now I will have to go to work I'm afraid. And I will do a clean install in this order:
1-XP
2-WIN7
3-INTREPID
4-JAUNTY.
Is that fine?
Is it true that Intrepid can NOT read/write to ext4? Is it better I make it all ext3 then?

Thank you very, very much for your kind help! I ought you a steak as soon as I'm over to california...or if you like to visit venice, your welcome at my place anytime!

---

### Post by caljohnsmith on 2009-05-09
According to the results of the xxd command you ran, it looks like the "bootrec /fixboot" did not succeed, because your Windows 7 boot sector is still an XP type boot sector. Did you try booting Windows XP, and if so, what exactly happened?

---

### Post by webwiller on 2009-05-09
I can boot into XP with NO PROBS at all, same as for INTREPID. It's WIN7&JAUNTY I'm missing.

When I did bootfix in WIN7 I'm sure I got the prompr operation succeeded...but you know...

---

### Post by caljohnsmith on 2009-05-09
That's great you can boot Win XP now--I think we can get your Win 7 booting too with just a little more work, so I would not suggest reinstalling. If you don't have time to do the following before heading off to work, no problem, we can pick up later. But when you get the chance, how about downloading the attached "Vista_PBR_9sectors.txt" to your Ubuntu desktop, and then do:
```
sudo dd if=~/Desktop/Vista_PBR_9sectors.txt of=/dev/sda1 bs=80 skip=1 seek=1 conv=notrunc
```
Then reboot, try Windows 7 from your Grub menu, and let me know how far you get.

---

### Post by webwiller on 2009-05-09
Please describe how do I have to reinstall everything the way you suggested, telling W7 not to violate XP at all...I go that way when I'm backk from work...4hrs time...

---

### Post by webwiller on 2009-05-09
```
webwiller@webwiller-laptop:~$ sudo dd if=~/Scrivania/Vista_PBR_9sectors.txt of=/dev/sda1 bs=80 skip=1 seek=1 conv=notrunc
[sudo] password for webwiller: 
56+1 registrazioni dentro
56+1 registrazioni fuori
4528 byte (4,5 kB) copiati, 0,000417791 s, 10,8 MB/s
webwiller@webwiller-laptop:~$ 

webwiller@webwiller-laptop:~$ sudo xxd -s128 -l2 -p /dev/sda1
55aa 
```

---

### Post by webwiller on 2009-05-09
G-R-E-A-T-!!!!!! I can boot into WIN7 & XP now from grub with no prob at all!!!!
I'm missing only Jaunty...which says: error15....and takes me back to grub....



Ps: I REALLY MUST GO NOW. Terribly late. If you already have an idea bout how to recover Jaunt I check this 3d as soon as I'm back. 4hrs time. Ty!!!!!! v-v-v-v-much!!!!!!:D:D:D:D

---

### Post by caljohnsmith on 2009-05-09
That's great news Windows 7 and Windows XP are now booting separately from Grub. :) About getting your Jaunty install booting, how about first booting your Jaunty Live CD, and then re-run the Boot Info Script from the Jaunty CD. If you post the output from that, I will have a better idea about what might be the best course of action to get your Jaunty install booting. We can pick up whenever you get back from work if I'm around.

John

---

### Post by webwiller on 2009-05-09
```
========================== Boot Info Summary: ============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 84111911 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

========================= Drive/Partition Info: ==========================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    62,910,539    62,910,477   7 HPFS/NTFS
/dev/sda2    *     62,910,540    83,875,364    20,964,825   7 HPFS/NTFS
/dev/sda3          83,875,365    84,132,404       257,040  83 Linux
/dev/sda4          84,132,405   488,392,064   404,259,660   5 Extended
/dev/sda5          84,132,468   109,306,259    25,173,792  83 Linux
/dev/sda6         109,306,323   130,271,084    20,964,762  83 Linux
/dev/sda7         130,271,148   132,375,599     2,104,452  82 Linux swap / Solaris
/dev/sda8         132,375,663   151,251,974    18,876,312  83 Linux
/dev/sda9         151,252,038   488,392,064   337,140,027   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1A2B268F2DDE0810" TYPE="ntfs" 
/dev/sda2: UUID="716CEAA91E12525A" TYPE="ntfs" 
/dev/sda3: UUID="108ef78e-3c80-4c1c-bbac-bf4ac062bb55" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="5a78e1d5-043a-40cc-bd6e-fb491c9ca0c2" TYPE="ext4" 
/dev/sda6: UUID="40e9c885-3779-4634-9d93-a54cbe0b3970" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="877c5f08-c81b-4530-9b9d-25cb0e1a6054" 
/dev/sda8: UUID="1a2e04f1-1561-46a0-a629-b26db1b92bf1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="5292FCB0425C232B" TYPE="ntfs" 

============================ "mount" output: =============================

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


============================= sda2/boot.ini: =============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


========================= sda3/grub/menu.lst: ============================

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
timeout		10

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
# kopt=root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=108ef78e-3c80-4c1c-bbac-bf4ac062bb55

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

#Followin first entry added by webwiller in order to boot Jaunty: 

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5a78e1d5-043a-40cc-bd6e-fb491c9ca0c2
root		(hd0,4)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=5a78e1d5-043a-40cc-bd6e-fb491c9ca0c2 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-9-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Seven (loader)
root		(hd0,0)
makeactive
chainloader	+1

#Following lines addes by webwiller in order to make grub load two windows #os's and anothe linux distro:
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

================ sda3: Location of files loaded by Grub: =================


  43.0GB: grub/menu.lst
  43.0GB: grub/stage2
  42.9GB: initrd.img-2.6.27-11-generic
  42.9GB: initrd.img-2.6.27-9-generic
  42.9GB: vmlinuz-2.6.27-11-generic
  42.9GB: vmlinuz-2.6.27-9-generic

============================ sda5/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5a78e1d5-043a-40cc-bd6e-fb491c9ca0c2 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=73321688-a846-4374-9750-dba45e20484f /boot           ext3    relatime        0       2
# /home was on /dev/sda8 during installation
UUID=1a2e04f1-1561-46a0-a629-b26db1b92bf1 /home           ext3    relatime        0       2
# /mnt/data was on /dev/sda9 during installation
UUID=5292FCB0425C232B /mnt/data       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /winseven was on /dev/sda1 during installation
UUID=1A2B268F2DDE0810 /winseven       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /winxp was on /dev/sda2 during installation
UUID=716CEAA91E12525A /winxp          ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=877c5f08-c81b-4530-9b9d-25cb0e1a6054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

============================ sda6/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=108ef78e-3c80-4c1c-bbac-bf4ac062bb55 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=1a2e04f1-1561-46a0-a629-b26db1b92bf1 /home           ext3    relatime        0       2
# /dev/sda9
UUID=5292FCB0425C232B /mnt/data       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1A2B268F2DDE0810 /winseven       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=716CEAA91E12525A /winxp          ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=877c5f08-c81b-4530-9b9d-25cb0e1a6054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Is this one the script you meant to run FROM INSIDE JAUNTY'S LIVE CD?
Well, if yes, this is it;)

---

### Post by caljohnsmith on 2009-05-09
It looks like part of the problem is that when you installed Ubuntu 8.10, you set it to use the same boot partition (sda3) as your installed Ubuntu 9.04; unfortunately 8.10 erased all your 9.04 boot files during the installation process. I would suggest reinstalling 9.04 to your sda5 partition, but this time don't set the sda3 partition as the boot partition, or I think you will erase all of 8.10's boot files in that partition. Just let the /boot directory stay in your main 9.04 file system on sda5. When you reinstall 9.04, if you accept the defaults for Grub, then 9.04 will then take over your booting process; that will be ideal since 9.04 can boot 8.10, but 8.10 can't boot 9.04 if 9.04 is on an ext4 partition (unless you update 8.10's Grub boot files). Let me know how reinstalling 9.04 goes or if you run into problems.

John

---

### Post by webwiller on 2009-05-09
Would reinstalling Jaunty ERASE all the work we did ( you did actualyy;)) about booting win7/xp?

Well...when I decided to setup a /boot partition was primarily 'cause I wanted it to be the one for all linux distro's I'd like to try from now on. Is it not possible like that? I read it somewhere...

I catch your point anyway, just asking if....you know what I mean...

You're right, I gave same mount point to /boot on hd0,2 for both 8.10/9.04 for the reason above...am I so so wrong about it?

Now terminal from live cd jaunty's says he cannot find grub stage1, he can find but cannot move satge1_5, and he successfully moved stage2 to hd0,2 ( I tried "setup (hd0,2)" to move all grub files to their partition).

---

### Post by webwiller on 2009-05-09
Well...done. I reinstalled Jaunty leaving it to set /boot by itself. Everythig went smoothly BUT...

Now I'm missing Intepid & XP.

Back to the very beginning actually, the only difference is that b4 I could boot Intrepid/XP, now Jaunty/Win7. The old ones vs the new ones.

Would our hero's win the battle against the "electro-stuff"???

We'll see it in the next episode, now I gotta go to sleep, it's 6in the morning already!!!! Uf;););)

:(:(:(

We lost a battle, not the war!

---

### Post by caljohnsmith on 2009-05-10
About undoing what we accomplished with booting Win 7 and Win XP, reinstalling Jaunty will not do that; if the Jaunty installer misses adding either XP or Win7 to your Grub menu, just add the previous Grub entries you were using to your Jaunty menu.lst, like XP for example would be:
```
title Windows XP
rootnoverify (hd0,1)
chainloader +1
```
And that should be all it takes to boot XP again. I am surprised though that Jaunty didn't add entries for Intrepid in your Jaunty Grub's menu.lst; you should be able to add them manually though:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		108ef78e-3c80-4c1c-bbac-bf4ac062bb55
kernel		/vmlinuz-2.6.27-11-generic root=UUID=40e9c885-3779-4634-9d93-a54cbe0b3970 ro  single
initrd		/initrd.img-2.6.27-11-generic
```
If you run into any problems, again re-run and post the output of the Boot Info Script (make sure to run it from your Jaunty install or the Jaunty Live CD). 

John

---

### Post by webwiller on 2009-05-11
I've done it and, well, we sorted things out! I got my starting grub menu with all my 4 OS's up and running! We did a good job tough!

Now I have to sort-out one more prob, but it's a completely different thing and I'll have to open another 3d, wouldnt I...so, I'll go that way, open a new1.

Thx again for your kind help! Hope to meet you again, see ya :)))

Chris

---

