---
title: "Frustrated GRUB.CONF totally ignored :("
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Minolas on 2009-01-12
I have been trying this for hours and hours, I just can't find the problem, very drustrating:

I followed the instructions here
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)

And created a bootable USB stick.

But when I boot the USB stick I get to "grub>" prompt. Then I have to manually write
```

default         0
timeout         10

title           Ubuntu (Live)
root            (hd0,0)
kernel          /boot/vmlinuz boot=casper file=/preseed/ubuntu.seed persistent
initrd          /boot/initrd.gz

```

Although that information is in the /boot/grub/grub.conf !!!

Grub just totally ignores that file and I have to manually enter these commands and at the end execute 'boot'. 

I don't understand why grub.conf isn't run. It's frustrating in each boot to type the root,kernel & initrd command all over again and then manually 'boot'.

Any help would be appreciated. it seems like something stupid.

---

### Post by cdtech on 2009-01-12
You need to make the USB device bootable. I see you said you did (Make the first partition bootable).

---

### Post by caljohnsmith on 2009-01-12
It might be the issue is that Grub is looking for a menu.lst and not a grub.conf, but it's hard to say without getting some more info about your setup. Do you have a Live CD that you can boot and use for troubleshooting? If so, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do the following while the USB stick is connected:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Minolas on 2009-01-12
> **cdtech said:**
> You need to make the USB device bootable. I see you said you did (Make the first partition bootable).

Thanks but I don't think that's the problem. The USB boots fine. If it weren't to boot I think I would have not got the "grub>" prompt.

---

### Post by niteshifter on 2009-01-12
Hi,

It is as caljohnsmith said, grub wants a menu.lst file, not a a grub.conf file in ../boot/grub

Here is the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). Nary a mention of a grub.conf file.

---

### Post by Minolas on 2009-01-12
> **caljohnsmith said:**
> It might be the issue is that Grub is looking for a menu.lst and not a grub.conf, but it's hard to say without getting some more info about your setup. Do you have a Live CD that you can boot and use for troubleshooting? If so, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do the following while the USB stick is connected:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

Thanks for the reply. I tried to put the command into menu.lst  but it didn't read it either. Again, the USB boots and gives the "grub>" prompt and I always have to manually enter the root,kernel,initrd and boot each time.

I booted another Ubuntu I have in VMware.
I downloaded the[Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") that you suggested.
And did the following with the USB stick connected:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

Here is the contect of the RESULTS.txt file
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /Boot /boot 
                       /BOOT /boot/grub

sdb2: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb2 already mounted or sdb2 busy
mount: according to mtab, /dev/sdb2 is mounted on /media/Ubuntu 8.10 i386

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4ccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    11936294     5968116   83  Linux
/dev/sda2        11936295    12578894      321300    5  Extended
/dev/sda5        11936358    12578894      321268+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 16.4 GB, 16416315904 bytes
64 heads, 32 sectors/track, 15655 cylinders, total 32063117 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007e8b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30107647    15053808    b  W95 FAT32
/dev/sdb2        30107648    32061439      976896   83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4d910271-93b9-47b6-924b-75d8da7acec8" TYPE="ext3" 
/dev/sda5: UUID="3c168ef9-1ec3-4a62-9905-c3182db822ef" TYPE="swap" 
/dev/sdb1: LABEL="UBUNTULIVE" UUID="496A-10D2" TYPE="vfat" 
/dev/sdb2: LABEL="Ubuntu 8.10 i386" TYPE="iso9660" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
.host:/ on /mnt/hgfs type vmhgfs (rw,ttl=5)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/administrator/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=administrator)
/dev/sdb1 on /media/UBUNTULIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb2 on /media/Ubuntu 8.10 i386 type iso9660 (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8)

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
# kopt=root=UUID=4d910271-93b9-47b6-924b-75d8da7acec8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4d910271-93b9-47b6-924b-75d8da7acec8

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4d910271-93b9-47b6-924b-75d8da7acec8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d910271-93b9-47b6-924b-75d8da7acec8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4d910271-93b9-47b6-924b-75d8da7acec8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d910271-93b9-47b6-924b-75d8da7acec8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4d910271-93b9-47b6-924b-75d8da7acec8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4d910271-93b9-47b6-924b-75d8da7acec8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3c168ef9-1ec3-4a62-9905-c3182db822ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software

================================== sda1/boot: ==================================

total 11964
drwxr-xr-x  3 root root    4096 2009-01-11 07:03 .
drwxr-xr-x 20 root root    4096 2009-01-11 06:40 ..
-rw-r--r--  1 root root  507665 2008-10-24 13:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 13:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-11 06:40 grub
-rw-r--r--  1 root root 8193265 2009-01-11 07:03 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 01:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 13:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 13:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 13:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-11 06:40 .
drwxr-xr-x 3 root root   4096 2009-01-11 07:03 ..
-rw-r--r-- 1 root root    197 2009-01-11 06:40 default
-rw-r--r-- 1 root root     15 2009-01-11 06:40 device.map
-rw-r--r-- 1 root root   8108 2009-01-11 06:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-11 06:40 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-11 06:40 installed-version
-rw-r--r-- 1 root root   8712 2009-01-11 06:40 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-11 06:40 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-11 06:40 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-11 06:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-11 06:40 stage1
-rw-r--r-- 1 root root 121460 2009-01-11 06:40 stage2
-rw-r--r-- 1 root root   9556 2009-01-11 06:40 xfs_stage1_5

=========================== sdb1/boot/grub/menu.lst: ===========================

default 0
timeout 10

root (hd0,0)
kernel /boot/vmlinuz boot=casper file=/preseed/ubuntu.seed persistent
initrd /boot/initrd.gz
boot

========================== sdb1/boot/grub/grub.conf: ==========================

default 0
timeout 10

root (hd0,0)
kernel /boot/vmlinuz boot=casper file=/preseed/ubuntu.seed persistent
initrd /boot/initrd.gz
boot

================================== sdb1/Boot: ==================================

total 10472
drwx------ 3 administrator root    8192 2009-01-11 20:16 .
drwx------ 4 administrator root    8192 1970-01-01 04:00 ..
drwx------ 2 administrator root    8192 2009-01-12 15:57 grub
-rwx------ 1 administrator root 8448174 2009-01-11 20:16 initrd.gz
-rwx------ 1 administrator root 2244272 2009-01-11 20:16 vmlinuz

================================== sdb1/boot: ==================================

total 10472
drwx------ 3 administrator root    8192 2009-01-11 20:16 .
drwx------ 4 administrator root    8192 1970-01-01 04:00 ..
drwx------ 2 administrator root    8192 2009-01-12 15:57 grub
-rwx------ 1 administrator root 8448174 2009-01-11 20:16 initrd.gz
-rwx------ 1 administrator root 2244272 2009-01-11 20:16 vmlinuz

================================== sdb1/BOOT: ==================================

total 10472
drwx------ 3 administrator root    8192 2009-01-11 20:16 .
drwx------ 4 administrator root    8192 1970-01-01 04:00 ..
drwx------ 2 administrator root    8192 2009-01-12 15:57 grub
-rwx------ 1 administrator root 8448174 2009-01-11 20:16 initrd.gz
-rwx------ 1 administrator root 2244272 2009-01-11 20:16 vmlinuz

=============================== sdb1/boot/grub: ===============================

total 264
drwx------ 2 administrator root   8192 2009-01-12 15:57 .
drwx------ 3 administrator root   8192 2009-01-11 20:16 ..
-rwx------ 1 administrator root    197 2009-01-11 20:11 default
-rwx------ 1 administrator root     30 2009-01-11 20:11 device.map
-rwx------ 1 administrator root   8108 2009-01-11 20:11 e2fs_stage1_5
-rwx------ 1 administrator root   7856 2009-01-11 20:11 fat_stage1_5
-rwx------ 1 administrator root    133 2009-01-12 15:57 grub.conf
-rwx------ 1 administrator root    111 2009-01-12 02:46 grub.conf~
-rwx------ 1 administrator root     16 2009-01-11 20:11 installed-version
-rwx------ 1 administrator root   8712 2009-01-11 20:11 jfs_stage1_5
-rwx------ 1 administrator root    133 2009-01-12 15:57 menu.lst
-rwx------ 1 administrator root      0 2009-01-12 15:57 menu.lst~
-rwx------ 1 administrator root   7352 2009-01-11 20:11 minix_stage1_5
-rwx------ 1 administrator root   9756 2009-01-11 20:11 reiserfs_stage1_5
-rwx------ 1 administrator root    512 2009-01-11 20:11 stage1
-rwx------ 1 administrator root 121460 2009-01-11 20:11 stage2
-rwx------ 1 administrator root   9556 2009-01-11 20:11 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

```

Please refer to the USB Stick only as that is where the problem is.

Thanks a lot

---

### Post by caljohnsmith on 2009-01-12
OK, so according to the script results, the Grub on your sdb drive (which I assume is your USB stick) is actually looking for a menu.lst and not a grub.conf, so that's good you have a menu.lst now on the USB stick. Maybe Grub doesn't like that the Ubuntu entry in the menu.lst doesn't include a title line, so how about trying:
```
default 0
timeout 10

[COLOR="Blue"]title Ubuntu on USB stick[/COLOR]
root (hd0,0)
kernel /boot/vmlinuz boot=casper file=/preseed/ubuntu.seed persistent
initrd /boot/initrd.gz
boot

```
And see if that makes any difference. If it doesn't and you still get dumped into the Grub prompt on start up, how about trying the following at the Grub prompt:
```
grub> cat (hd0,0)/boot/grub/menu.lst
```
And does that print your menu.lst?

---

### Post by Minolas on 2009-01-12
> **caljohnsmith said:**
> OK, so according to the script results, the Grub on your sdb drive (which I assume is your USB stick) is actually looking for a menu.lst and not a grub.conf, so that's good you have a menu.lst now on the USB stick. Maybe Grub doesn't like that the Ubuntu entry in the menu.lst doesn't include a title line, so how about trying:
```
default 0
timeout 10

[COLOR="Blue"]title Ubuntu on USB stick[/COLOR]
root (hd0,0)
kernel /boot/vmlinuz boot=casper file=/preseed/ubuntu.seed persistent
initrd /boot/initrd.gz
boot

```
And see if that makes any difference. If it doesn't and you still get dumped into the Grub prompt on start up, how about trying the following at the Grub prompt:
```
grub> cat (hd0,0)/boot/grub/menu.lst
```
And does that print your menu.lst?


Thanks a lot! Adding the 'title' made it work! In fact I did include the 'title' line but it was only included in the grub.conf file and I forgot to put it in the menu.lst file. Interensingly the article that I worked through (link mentioned earlier) step-by-step mentioned the file should be grub.conf and not menu.lst that mistake in the original article cost me many hours. I thank you for pointing that out!

---

### Post by caljohnsmith on 2009-01-12
Glad to hear that the missing title line was the only problem; cheers and enjoy your new Ubuntu install. :)

---

### Post by IoganeGambaPuti on 2009-01-12
Hello people!I have problems with grub too.
```

grub> find /boot/grub/stage1
 (hd1,6)
grub>root(hd1,6)
 Error 27
grub>setup(hd1)
 Error 27 

```
Then I corrected file menu.lst by hand.There what showed out Boot Info Script:
```

                                                                   
                                                                     
                                                                     
                                             
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00277678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1465144064   732572001   42  SFS

sfdisk -V /dev/sda:

partition 1: end: (c,h,s) expected (1023,254,63) found (64,254,63)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47654764

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   544635629   272317783+   7  HPFS/NTFS
/dev/sdb2       544635630   625137344    40250857+   5  Extended
/dev/sdb5       544635693   621747629    38555968+  83  Linux
/dev/sdb6       621747693   625137344     1694826   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D6001E31001E18D7" TYPE="ntfs" 
/dev/sdb1: UUID="64C0D433C0D40D64" TYPE="ntfs" 
/dev/sdb5: UUID="38409401-13ee-4a18-b104-b8cb93a5ece6" TYPE="ext3" 
/dev/sdb6: UUID="7645dc73-7624-4cf4-8aab-105c605986f3" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional RU" /execute /fastdetect

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=38409401-13ee-4a18-b104-b8cb93a5ece6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=38409401-13ee-4a18-b104-b8cb93a5ece6

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd1,4)
uuid		38409401-13ee-4a18-b104-b8cb93a5ece6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=38409401-13ee-4a18-b104-b8cb93a5ece6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd1,4)
uuid		38409401-13ee-4a18-b104-b8cb93a5ece6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=38409401-13ee-4a18-b104-b8cb93a5ece6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root            (hd1,4)
uuid		38409401-13ee-4a18-b104-b8cb93a5ece6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional RU
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=38409401-13ee-4a18-b104-b8cb93a5ece6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=7645dc73-7624-4cf4-8aab-105c605986f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2009-01-11 02:28 .
drwxr-xr-x 20 root root    4096 2009-01-11 02:28 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-11 02:28 grub
-rw-r--r--  1 root root 8183374 2009-01-11 02:28 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb5/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-11 02:28 .
drwxr-xr-x 3 root root   4096 2009-01-11 02:28 ..
-rw-r--r-- 1 root root    197 2009-01-11 02:28 default
-rw-r--r-- 1 root root     30 2009-01-11 02:28 device.map
-rw-r--r-- 1 root root   8108 2009-01-11 02:28 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-11 02:28 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-11 02:28 installed-version
-rw-r--r-- 1 root root   8712 2009-01-11 02:28 jfs_stage1_5
-rw-r--r-- 1 root root   4730 2009-01-12 23:11 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-11 02:28 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-11 02:28 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-11 02:28 stage1
-rw-r--r-- 1 root root 121460 2009-01-11 02:28 stage2
-rw-r--r-- 1 root root   9556 2009-01-11 02:28 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.


```
What needs to be done in oder that to recover grub?
P. S. Sorry for my bad language.:)

---

### Post by caljohnsmith on 2009-01-12
IoganeGambaPuti, are you sure the Grub find command returned (hd1,6)? Because that would be sdb7, and you don't have an sdb7 partition. How about instead trying:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Please post the output of all the above commands prior to doing "quit". Also note there is a space between root and (hd1,4), also a space between setup and (hd1). If the above commands are successful, how about rebooting, set your BIOS to boot the Ubuntu sdb drive, and you should get a Grub menu on start up. Trying to boot any of the Ubuntu entries unfortunately won't work yet until we tweak your Grub's menu.lst; see if you can get as far as getting the Grub menu first, and we can work from there.

---

### Post by IoganeGambaPuti on 2009-01-14
Very sorry.The command gave out certainly: (hd1,4) (I entered this in my menu.lst: "root (hd1,4)".Thank you for note about space.
I entered command root (hd1,4) without a space and got Error 27.Now I in other town,but the day after tomorrow I`ll come back and do all without errors.

---

