---
title: "Problem with booting from HDD"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by miragex on 2008-12-21
Hi. I was searching for an answer on my problem from few days without luck so I guess I'll try here to describe you what's going on.

I've got Asus Eee PC. Downloaded Ubuntu Eee and installed it from a pendrive. Everything is working fine except the fact that I need to have pendrive to start the system. When I was installing Ubuntu I made two partitions - first ext3, second swap on my ssd drive. Now, when I am starting my netbook without pendrive I get a message to reboot cause there's no system on my pc, blah blah blah. So what I did was plugging the pendrive and entering this menu where you can choose to start system or start it in emergency mode. I've edited boot from hd(0,0) to hd(1,0) and then it's starting. Great. Then I've edited from Ubuntu menu.lst file, changed those three starters to hd(1,0), savind and rebooting without pendrive. Still it's the same situation. Of course I was changing settings in BIOS but any configuration isn't working good either. Any guess?

---

### Post by northern lights on 2008-12-21
Are you certain the pendrive is (hd0,0)? This should point to the first partition of the internal harddrive (which is where you're Ubuntu resides.)

"This menu" is the GRUB bootloader. What exactly happens step-by-step if you fire up your netbook without the flashdrive plugged in?

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by miragex on 2008-12-21
> **northern lights said:**
> Are you certain the pendrive is (hd0,0)? This should point to the first partition of the internal harddrive (which is where you're Ubuntu resides.)

"This menu" is the GRUB bootloader. What exactly happens step-by-step if you fire up your netbook without the flashdrive plugged in?

After the Eee screen I see: Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key. When I insert pendrive, restart and press ESC I see GRUB loader. The only configuration from which I can start Ubuntu here is hd(1,0). After I choose it I unplug pendrive and everything is working fine. Changing menu.lst to hd(1,0) doesn't change anything cause still I must plug pendrive and choose to start system from this menu.

---

### Post by northern lights on 2008-12-21
Apart from following through with Californian request, please post the output of ```
sudo fdisk -l
```Ignore if information is redundant.

---

### Post by carml on 2008-12-21
In my humble opinion the problem is that you didn't install Grub on on the MBR(Master Boot Record),where it's stored the list of your installed OS,so on boot the PC gives that message.Maybe that installing Grub on the hard drive you resolve the problem. :)

---

### Post by miragex on 2008-12-21
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

```
No known boot loader is installed in the MBR of /dev/sda
Windows is installed in the MBR of /dev/sdb

sdb1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04.1 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2:
    File system:  swap


Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f065f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    29575664    14787801   83  Linux
/dev/sdb2        29575665    31519529      971932+  82  Linux swap / Solaris
/dev/sdb1: UUID="2a5e7fa5-0453-42b6-ab34-085018fa62ab" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="5f146a1a-5a9b-4a86-a74e-2b0ec7820b98" 
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 29575602, Id=83
/dev/sdb2 : start= 29575665, size=  1943865, Id=82
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

sdb1/boot/grub/menu.lst

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
# kopt=root=UUID=2a5e7fa5-0453-42b6-ab34-085018fa62ab ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=2a5e7fa5-0453-42b6-ab34-085018fa62ab ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=2a5e7fa5-0453-42b6-ab34-085018fa62ab ro single
initrd		/boot/initrd.img-2.6.24-21-eeepc

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sdb1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=2a5e7fa5-0453-42b6-ab34-085018fa62ab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=5f146a1a-5a9b-4a86-a74e-2b0ec7820b98 none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdb1/boot

total 12844
drwxr-xr-x  3 root root    4096 2008-12-21 15:57 .
drwxr-xr-x 21 root root    4096 2008-12-21 15:56 ..
-rw-r--r--  1 root root   67648 2008-08-22 22:03 config-2.6.24-21-eeepc
drwxr-xr-x  2 root root    4096 2008-12-21 13:58 grub
-rw-r--r--  1 root root 5092923 2008-12-21 15:57 initrd.img-2.6.24-21-eeepc
-rw-r--r--  1 root root 5092625 2008-12-20 18:50 initrd.img-2.6.24-21-eeepc.bak
-rw-r--r--  1 root root  103204 2008-08-22 22:03 memtest86+.bin
-rw-r--r--  1 root root  879903 2008-08-22 22:03 System.map-2.6.24-21-eeepc
-rw-r--r--  1 root root 1850200 2008-08-22 22:03 vmlinuz-2.6.24-21-eeepc

sdb1/boot/grub

total 212
drwxr-xr-x 2 root root   4096 2008-12-21 13:58 .
drwxr-xr-x 3 root root   4096 2008-12-21 15:57 ..
-rw-r--r-- 1 root root    197 2008-12-20 18:50 default
-rw-r--r-- 1 root root     30 2008-12-20 18:50 device.map
-rw-r--r-- 1 root root   8056 2008-12-20 18:50 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-20 18:50 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 18:50 installed-version
-rw-r--r-- 1 root root   8608 2008-12-20 18:50 jfs_stage1_5
-rw-r--r-- 1 root root   4259 2008-12-21 13:58 menu.lst
-rw-r--r-- 1 root root   4259 2008-12-20 20:04 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-20 18:50 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-20 18:50 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 18:50 stage1
-rw-r--r-- 1 root root 108356 2008-12-20 18:50 stage2
-rw-r--r-- 1 root root   9276 2008-12-20 18:50 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sda


hexdump: /dev/sda: No medium found
hexdump: /dev/sda: No medium found
/dev/sda: No medium found

sfdisk: cannot open /dev/sda for reading
```

---

### Post by miragex on 2008-12-21
> **northern lights said:**
> Apart from following through with Californian request, please post the output of ```
sudo fdisk -l
```Ignore if information is redundant.

```
sudo fdisk -l

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f065f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1841    14787801   83  Linux
/dev/sdb2            1842        1962      971932+  82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-12-21
It looks like all you need to do is install Grub to the MBR of the sdb Ubuntu drive, because currently sdb has a Windows MBR. How about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the sdb drive, and then you should be able to boot Ubuntu. Let me know how it goes or if you run into problems.

---

### Post by miragex on 2008-12-21
> **caljohnsmith said:**
> It looks like all you need to do is install Grub to the MBR of the sdb Ubuntu drive, because currently sdb has a Windows MBR. How about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the sdb drive, and then you should be able to boot Ubuntu. Let me know how it goes or if you run into problems.

Great! It works. "root (hd1,0)" didn't work but with "root (hd0,0)" it's ok now. Thanks to all of you.

---

### Post by northern lights on 2008-12-21
> **miragex said:**
> ```
No known boot loader is installed in the MBR of /dev/sda
```

> **carml said:**
> In my humble opinion the problem is that you didn't install Grub on on the MBR(Master Boot Record),where it's stored the list of your installed OS,so on boot the PC gives that message.Maybe that installing Grub on the hard drive you resolve the problem. :)

This is exactly it.

Run```
sudo grub
``` to get a grub prompt.

Now run```
root (hd1,0)
makeactive
setup (hd1)
```

and reboot. You should be sorted.

---

### Post by caljohnsmith on 2008-12-21
Glad it's fixed now; since (hd1,0) didn't work, it sounds like for some reason your drive letter is changing from sdb to sda. Anyway, cheers and have fun with your Ubuntu install. :)

---

