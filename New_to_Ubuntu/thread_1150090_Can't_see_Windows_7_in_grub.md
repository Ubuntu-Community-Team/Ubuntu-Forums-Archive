---
title: "Can't see Windows 7 in grub"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by vimalv617 on 2009-05-05
Hey everyone,
I installed Ubuntu 9.04 before Windows 7, but cannot see Win 7 in the grub boot menu. What I have done so far is add windows 7 to menu.lst file...the problem is I don't know what partition it was installed on. Here is the read out of fdisk -l and my menu.lst file (also someone please checkover if what i have is right) If someone could tell me how to figure this out it would be great!

FYI, ive used this link to help me out:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

fdisk:
[IMG]http://i42.photobucket.com/albums/e332/vimalv617/fdisk.jpg[/IMG]


menu.lst:
[IMG]http://i42.photobucket.com/albums/e332/vimalv617/menu.jpg[/IMG]

Edit: (hd0,5) was just a guess.

---

### Post by Titan8990 on 2009-05-05
You have wrote grub to a partition instead of the MBR. First, restore the windows boot loaders, then reinstall grub to the MBR.

---

### Post by Sef on 2009-05-05
Windows should be on the first primary partition.

---

### Post by Locutus_of_Borg on 2009-05-05
Windows 7 requires that it be on a primary partition, not necessarily the first, but the installer will not recognize a logical partition.

To load Windows 7 from grub, you need a line similar to the following:
```

title Windows Seven
rootnoverify (hd0,2)
chainloader +1

```


you appear to have windows 7 installed on sda4

your grub entry then should look like the following:
```

title Windows Seven
rootnoverify (hd0,3)
chainloader +1

```

that should work

---

### Post by vimalv617 on 2009-05-05
> **Locutus_of_Borg said:**
> Windows 7 requires that it be on a primary partition, not necessarily the first, but the installer will not recognize a logical partition.

To load Windows 7 from grub, you need a line similar to the following:
```

title Windows Seven
rootnoverify (hd0,2)
chainloader +1

```
you appear to have windows 7 installed on sda4

your grub entry then should look like the following:
```

title Windows Seven
rootnoverify (hd0,3)
chainloader +1

```that should work

Thanks for the reply! I put in the last entry and tried booting and got a message saying "BOOTMGR is missing." Any ideas?

---

### Post by caljohnsmith on 2009-05-05
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup so we can determine how you might boot Windows 7 from Grub.

John

---

### Post by vimalv617 on 2009-05-05
As requested:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dfd62

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,084,024    80,083,962  83 Linux
/dev/sda2          80,084,025   107,426,654    27,342,630   5 Extended
/dev/sda5          80,084,088    99,619,064    19,534,977  83 Linux
/dev/sda6          99,619,128   107,426,654     7,807,527  82 Linux swap / Solaris
/dev/sda3         107,427,840   107,632,639       204,800   7 HPFS/NTFS
/dev/sda4         107,632,640   490,231,807   382,599,168   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="51b5de0d-fce3-4ffd-b631-7f37af843fcf" TYPE="ext3" 
/dev/sda3: UUID="16D81E20D81DFF25" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda4: UUID="C278222778221AA5" TYPE="ntfs" 
/dev/sda5: UUID="61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8" TYPE="ext3" 
/dev/sda6: UUID="cbf0b756-79ef-4a72-b329-37cfb11764e5" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vimal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vimal)


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
# kopt=root=UUID=61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8

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

title        Windows Seven
root        (hd0,3)
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=61d45e5c-640a-4d36-9aeb-ef5cf57ac2e8 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=51b5de0d-fce3-4ffd-b631-7f37af843fcf /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=cbf0b756-79ef-4a72-b329-37cfb11764e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  43.2GB: boot/grub/menu.lst
  43.2GB: boot/grub/stage2
  43.2GB: boot/initrd.img-2.6.28-11-generic
  41.4GB: boot/vmlinuz-2.6.28-11-generic
  43.2GB: initrd.img
  41.4GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-05-05
According to the Boot Info Script results, your Windows 7 boot files are actually in your sda3 NTFS partition even though Windows 7 is installed to sda4. Therefore, how about trying the following entry to boot Win 7:
```
title Windows 7
rootnoverify (hd0,2)
chainloader +1
```
Reboot and try that entry from your Grub menu, and let me know exactly what happens. We can work from there if you want. 

John

---

### Post by vimalv617 on 2009-05-05
Wow, it works like a charm. Thanks a lot John! :)

---

### Post by caljohnsmith on 2009-05-05
> **vimalv617 said:**
> Wow, it works like a charm. Thanks a lot John! :)
You're welcome, I'm glad that worked OK; cheers and enjoy your dual-boot setup. :)

John

---

### Post by micke090 on 2009-05-21
> **vimalv617 said:**
> Thanks for the reply! I put in the last entry and tried booting and got a message saying "BOOTMGR is missing." Any ideas?

Hey, i am having the exact same problem. My menu.lst have this entry for w7
```
title Windows 7
rootnoverify (hd0,0)
map (0x81) (0x80)
map (0x80) (0x81)
chainloader +1
```

And the script reports this

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.1 
                       (Official) for i586 Kernel 2.6.29.3-desktop586-1mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7f7770f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   731,011,071   730,804,224   7 HPFS/NTFS
/dev/sda3         731,021,760   928,806,479   197,784,720   5 Extended
/dev/sda5         731,021,823   735,013,439     3,991,617  82 Linux swap / Solaris
/dev/sda6         735,013,503   796,521,599    61,508,097  83 Linux
/dev/sda7         796,521,663   928,806,479   132,284,817  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="286EC4546EC41D06" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="4C4CC6D64CC6B9CA" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="53ed9f1f-5641-478e-9be9-b2682c207815" 
/dev/sda6: UUID="da589564-3435-4d14-a608-4290f44e1d8e" TYPE="ext4" 
/dev/sda7: UUID="628515a3-98ea-4188-96cb-a826886aa93c" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,commit=600)
none on /proc type proc (rw)
/dev/sda7 on /home type ext3 (rw,noatime,commit=600)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /home/mco/disk1 type fuseblk (rw,allow_other,blksize=4096)


============================== sda2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD/



timeout 10

color black/cyan yellow/cyan

gfxmenu (hd0,5)/boot/gfxmenu

default 0



title linux

kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=da589564-3435-4d14-a608-4290f44e1d8e splash=silent vga=788

initrd (hd0,5)/boot/initrd.img



title linux-nonfb

kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=da589564-3435-4d14-a608-4290f44e1d8e 

initrd (hd0,5)/boot/initrd.img



title failsafe

kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=da589564-3435-4d14-a608-4290f44e1d8e failsafe

initrd (hd0,5)/boot/initrd.img



title Windows

root (hd0,0)

map (0x81) (0x80)

map (0x80) (0x81)

makeactive

chainloader +1



title Windows 1

root (hd0,1)

map (0x81) (0x80)

map (0x80) (0x81)

makeactive

chainloader +1



title Windows 2

root (hd0,2)

map (0x81) (0x80)

map (0x80) (0x81)

makeactive

chainloader +1



title desktop586 2.6.29.1-4mnb

kernel (hd0,5)/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=da589564-3435-4d14-a608-4290f44e1d8e splash=silent vga=788

initrd (hd0,5)/boot/initrd-2.6.29.1-desktop586-4mnb.img



title desktop586 2.6.29.3-1mnb

kernel (hd0,5)/boot/vmlinuz-2.6.29.3-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.29.3-1mnb root=UUID=da589564-3435-4d14-a608-4290f44e1d8e splash=silent vga=788

initrd (hd0,5)/boot/initrd-2.6.29.3-desktop586-1mnb.img





# All your boot are belong to NeoSmart!
=========================== sda6/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,5)/boot/gfxmenu
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=da589564-3435-4d14-a608-4290f44e1d8e splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=da589564-3435-4d14-a608-4290f44e1d8e 
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=da589564-3435-4d14-a608-4290f44e1d8e failsafe
initrd (hd0,5)/boot/initrd.img

title Windows 7
rootnoverify (hd0,0)
map (0x81) (0x80)
map (0x80) (0x81)
chainloader +1

=============================== sda6/etc/fstab: ===============================

# Entry for /dev/sda6 :
UUID=da589564-3435-4d14-a608-4290f44e1d8e / ext4 defaults 1 1
# Entry for /dev/sda7 :
UUID=628515a3-98ea-4188-96cb-a826886aa93c /home ext3 noatime 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=53ed9f1f-5641-478e-9be9-b2682c207815 swap swap defaults 0 0
# Entry for /dev/sda2 ntfs
/dev/sda2    /home/mco/disk1    ntfs-3g    defaults,force,umask=000    0 0

=================== sda6: Location of files loaded by Grub: ===================


 376.4GB: boot/grub/menu.lst
 377.8GB: boot/grub/stage2
 379.4GB: boot/initrd-2.6.29.1-desktop586-4mnb.img
 379.5GB: boot/initrd-2.6.29.3-desktop586-1mnb.img
 379.5GB: boot/initrd-desktop586.img
 379.5GB: boot/initrd.img
 379.4GB: boot/vmlinuz
 378.0GB: boot/vmlinuz-2.6.29.1-desktop586-4mnb
 379.4GB: boot/vmlinuz-2.6.29.3-desktop586-1mnb
 379.4GB: boot/vmlinuz-desktop586
```

Don't worry about the easybcd entries, they are supposed to come in after the windows loader has loaded, and should not affect anything.

---

### Post by h.blas on 2009-06-09
Hi,
I'm having some trouble booting to windows 7, 
i followed the instructions and did all i could to boot up windows 7 but it seems im making a mistake, as the pc would reboot when trying to boot up windows everything seems to be fine to me.

this is what boot info shows

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbba67b35

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    163,848,192   409,608,191   245,760,000   7 HPFS/NTFS
/dev/sda2         409,608,192   976,769,023   567,160,832   7 HPFS/NTFS
/dev/sda3                  63   156,248,189   156,248,127  83 Linux
/dev/sda4         156,248,190   163,846,934     7,598,745  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5a4c7f65

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,953,784   476,953,722   7 HPFS/NTFS
/dev/sdb2         476,953,785   976,768,064   499,814,280   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="984066A740668BB6" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="24287CA7287C799E" LABEL="DOCUMENTS" TYPE="ntfs" 
/dev/sda3: UUID="8377985e-083a-45ee-bdd7-8c181c8e389a" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="a23eda72-aeab-4651-bc8e-a94b10876be8" 
/dev/sdb1: UUID="8A9C66DC9C66C275" LABEL="VIDEOS" TYPE="ntfs" 
/dev/sdb2: UUID="2E5C7C5D5C7C222F" LABEL="PROJECTS & GAMES" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hernan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hernan)


=========================== sda3/boot/grub/menu.lst: ===========================

splashimage (hd0,2)/boot/grub/splashimages/86161-watch.xpm.gz
default 0
timeout 10
color white/black light-red/black

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
# kopt=root=UUID=8377985e-083a-45ee-bdd7-8c181c8e389a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8377985e-083a-45ee-bdd7-8c181c8e389a

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

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8377985e-083a-45ee-bdd7-8c181c8e389a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8377985e-083a-45ee-bdd7-8c181c8e389a ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows 7 x64
root (hd0,0)
chainloader (hd0,2)+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=8377985e-083a-45ee-bdd7-8c181c8e389a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=a23eda72-aeab-4651-bc8e-a94b10876be8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  47.7GB: boot/grub/menu.lst
  47.8GB: boot/grub/stage2
  47.8GB: boot/initrd.img-2.6.28-11-generic
  47.8GB: boot/vmlinuz-2.6.28-11-generic
  47.8GB: initrd.img
  47.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

thanks

---

