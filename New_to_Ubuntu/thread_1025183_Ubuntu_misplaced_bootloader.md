---
title: "Ubuntu misplaced bootloader"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by linuxnovice on 2008-12-29
Hi,

I kind of messed up my install. I have a Toshiba satellite with a 100gb hdd. I did not want to burn a CD so I used Unetbootin to create a bootable USB stick. I also chose the "netinstall" version of ubuntu 8.04 (i am sticking with 8.04 for now) so that I dont have to update once I boot into my new system. So everything went fine, I manually partitioned my hdd with 3gb of swap and rest mounted on /. I then choose to install ubuntu-desktop. 

Now, when I boot up, I get a grub error 22. I got a thought and pluged in my USB stick and booted through that. It went into the newly installed system. I then unmounted the USB stick and am working on the new system now. However, I can only boot into using my USB stick. I figured the bootloader for some reason got stuck in the USB stick.

I dont know how to correct this issue. Any help is appreciated.

Thanks.

---

### Post by oilchangeguy on 2008-12-29
> **linuxnovice said:**
> Hi,

I kind of messed up my install. I have a Toshiba satellite with a 100gb hdd. I did not want to burn a CD so I used Unetbootin to create a bootable USB stick. I also chose the "netinstall" version of ubuntu 8.04 (i am sticking with 8.04 for now) so that I dont have to update once I boot into my new system. So everything went fine, I manually partitioned my hdd with 3gb of swap and rest mounted on /. I then choose to install ubuntu-desktop. 

Now, when I boot up, I get a grub error 22. I got a thought and pluged in my USB stick and booted through that. It went into the newly installed system. I then unmounted the USB stick and am working on the new system now. However, I can only boot into using my USB stick. I figured the bootloader for some reason got stuck in the USB stick.

I dont know how to correct this issue. Any help is appreciated.

Thanks.

i'm pretty sure that if you had taken the time to burn a cd you would not be having these problems. also what would make you think you need 3gb of swap? do you understand what swap is? it's virtual ram. you have 4gb of physical ram. you'll never need 3gb of virtual ram.

---

### Post by linuxnovice on 2008-12-29
I am not asking for judgement here. I dont have CD's I only have DVD's. Besides thats not the point of this post. 

Secondly, yes I do know what swap is. I read through some articles and found out that for making suspend/hibernate to work successfully, I would need atleast as much swap as I have ram. They maybe wrong but this is what I read.

---

### Post by barfobulator on 2008-12-29
> **oilchangeguy said:**
> i'm pretty sure that if you had taken the time to burn a cd you would not be having these problems. also what would make you think you need 3gb of swap? do you understand what swap is? it's virtual ram. you have 4gb of physical ram. you'll never need 3gb of virtual ram.

I disagree, I burned a Live CD and used it to install on a USB hard drive, and currently have a similar problem. I think it's linked to the GRUB program. It's probably installed on the USB, but the installation process told the computer to use it instead of the existing program. I am currently looking for a solution, so if you can help it would be great.

---

### Post by linuxnovice on 2008-12-29
> **barfobulator said:**
> I disagree, I burned a Live CD and used it to install on a USB hard drive, and currently have a similar problem. I think it's linked to the GRUB program. It's probably installed on the USB, but the installation process told the computer to use it instead of the existing program. I am currently looking for a solution, so if you can help it would be great.

Umm..it seems what you are trying to do is kind of opposite to what I am trying to do :). Do you have the same problem or "similar"? Could give more details about it?

Thanks.

---

### Post by barfobulator on 2008-12-29
I can't boot without my external drive being present. Isn't that your problem with your USB flash device?

---

### Post by linuxnovice on 2008-12-29
> **barfobulator said:**
> I can't boot without my external drive being present. Isn't that your problem with your USB flash device?

True. But I installed ubuntu on the computer not on the flash drive. I created a bootable flash drive and installed ubuntu on the partitions created on the computer hdd.

---

### Post by boof1988 on 2008-12-29
Can you post the output of:
```
sudo fdisk -l
```

Then we can use the links below (which have some good grub information) to help solve the problem.

References:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> Can you post the output of:
```
sudo fdisk -l
```

Then we can use the links below (which have some good grub information) to help solve the problem.

References:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Here is output:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f090f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           11798       12161     2923830   82  Linux swap / Solaris
/dev/sda2               1       11797    94759371   83  Linux

Partition table entries are not in disk order

```

Also, I followed the instructions given here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Now, instead of error 22 I get error 21 "disc not found" or something.

Thanks.

---

### Post by boof1988 on 2008-12-29
Can you start grub by using the following (GrUB will indicate a "grub" prompt when you are in it:
```
sudo grub
```

And post the output of:
```
find /boot/grub/stage1
```

You can then quit grub (for now) or just keep the terminal open for the next steps:
```
quit
```

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> Can you start grub by using the following (GrUB will indicate a "grub" prompt when you are in it:
```
sudo grub
```

And post the output of:
```
find /boot/grub/stage1
```

You can then quit grub (for now) or just keep the terminal open for the next steps:
```
quit
```

Hey,

Here is the output:

```
grub> find /boot/grub/stage1
 (hd0,1)

```

Thanks.

---

### Post by boof1988 on 2008-12-29
I suspect these might be the next few commands to use to fix the grub problem.

```
sudo grub # If you are not in grub anymore
root (hd0,1) # Since your Ubuntu partition is sda2 (hd0,1)
setup (hd0)
quit
```

If you have a Super Grub Disk, it has an option to fix the boot automatically.  If you don't want to fix manually.

---

### Post by boof1988 on 2008-12-29
When you're able (before or after trying the above code) please post:

```
cat /boot/grub/menu.lst
```

and maybe:

```
sudo blkid
```

This will let us to check where the grub menu.lst indicates the boot files are located.  caljohnsmith has a good script that gets all this needed info and puts in in a txt file, but I'm too lazy to try to find it now.

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> I suspect these might be the next few commands to use to fix the grub problem.

```
sudo grub # If you are not in grub anymore
root (hd0,1) # Since your Ubuntu partition is sda2 (hd0,1)
setup (hd0)
quit
```

If you have a Super Grub Disk, it has an option to fix the boot automatically.  If you don't want to fix manually.

I already did that (from the previous post). Anyway, I did it again and its giving me the same here. It says, "grub is loading..." and says "error 21: selected disk does not exist, press enter to continue". It then gives me the grub menu..but whatever I select, I get error 21. Then I plugged in my USB drive and booted from it. It booted without any problems. Here is the weird part, as soon as the ubuntu logo appeared I unplugged the flash drive and it did not have any problems booting into the system..

Thanks.

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> When you're able (before or after trying the above code) please post:

```
cat /boot/grub/menu.lst
```

and maybe:

```
sudo blkid
```

This will let us to check where the grub menu.lst indicates the boot files are located.  caljohnsmith has a good script that gets all this needed info and puts in in a txt file, but I'm too lazy to try to find it now.

Here is my menu.lst. 

```
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
# kopt=root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Here is the output for blkid:

```
/dev/sda1: TYPE="swap" UUID="f2443e53-cd06-490f-928a-fbc1199d8112" 
/dev/sda2: UUID="a49b4002-28ef-4374-9f03-ed9db49f4534" TYPE="ext3" 

```

Thanks.

---

### Post by linuxnovice on 2008-12-29
I found the script. Here is the contents of results.txt:

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       swap

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f090f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       189518805   195366464     2923830   82  Linux swap / Solaris
/dev/sda2              63   189518804    94759371   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="swap" UUID="f2443e53-cd06-490f-928a-fbc1199d8112" 
/dev/sda2: UUID="a49b4002-28ef-4374-9f03-ed9db49f4534" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sudarshan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sudarshan)

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=f2443e53-cd06-490f-928a-fbc1199d8112 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 17656
drwxr-xr-x  3 root root    4096 2008-12-29 20:25 .
drwxr-xr-x 21 root root    4096 2008-12-29 20:07 ..
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-29 20:25 grub
-rw-r--r--  1 root root 7502625 2008-12-29 20:25 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7067205 2008-12-29 19:45 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda2/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2008-12-29 20:25 .
drwxr-xr-x 3 root root   4096 2008-12-29 20:25 ..
-rw-r--r-- 1 root root    197 2008-12-29 20:25 default
-rw-r--r-- 1 root root     30 2008-12-29 20:25 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 20:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 20:25 fat_stage1_5
-rw-r--r-- 1 root root     18 2008-12-29 20:25 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 20:25 jfs_stage1_5
-rw-r--r-- 1 root root   4271 2008-12-29 20:25 menu.lst
-rw-r--r-- 1 root root   7324 2008-12-29 20:25 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 20:25 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 20:25 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 20:25 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 20:25 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by boof1988 on 2008-12-29
Here's [Hermanzone's Grub error 21](http://users.bigpond.net.au/hermanzone/p15.htm#21) page.

So I think we can fix the problem by changing the drives to the correct ones in grub's menu.lst.

I say the script you posted, but I'm not sure if it's the one I was thinking of.  If you like you can run it and post the output txt file:

```
sudo bash boot_info_script.txt
```

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> Here's [Hermanzone's Grub error 21](http://users.bigpond.net.au/hermanzone/p15.htm#21) page.

So I think we can fix the problem by changing the drives to the correct ones in grub's menu.lst.

I say the script you posted, but I'm not sure if it's the one I was thinking of.  If you like you can run it and post the output txt file:

```
sudo bash boot_info_script.txt
```

Sorry :D My bad..i posted the stuff the script itself instead of the results. But I edited it right away. 

Anyway, I read through the page of the link. I am not sure about a couple of things. First, my USB flash drive was just a bootable drive..it did not have the operating system in it. Second I installed the ubuntu on the hdd on the computer not on flash drive. So that means, my computer has stage2 and stage1 is on the flash drive and not the other way round (as given in the page). Is that right or am i missing something?

Thanks.

---

### Post by boof1988 on 2008-12-29
The post [here](http://ubuntuforums.org/showthread.php?t=1025013#5) has the thing I was thinking of.

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

This code will download the latest and also create the output.  Check out the post (I linked to above) if you like.

I just ran this code on my machine and it seems to work pretty well:

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  83  Linux
/dev/sda2   *       96390    41062139    20482875   83  Linux
/dev/sda3        41062140   976768064   467852962+   5  Extended
/dev/sda5        41062203    45158714     2048256   82  Linux swap / Solaris
/dev/sda6        45158778   454751954   204796588+  83  Linux
/dev/sda7       454752018   864345194   204796588+  83  Linux
/dev/sda8       864345258   920556629    28105686   83  Linux
/dev/sda9       920556693   976768064    28105686   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="gx270grub" UUID="1f54a6c3-b6a1-47d8-a8a6-c72f632d7399" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="fa9a454f-3ccc-4aa4-866f-774317b4fa82" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bc2521ae-0ebb-4dbc-a28a-35702d77a833" 
/dev/sda6: LABEL="gx270data" UUID="7c7b09e1-cd00-41e7-add1-e73d3c9785d2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="gx270databak" UUID="bbe4a711-7d66-4522-a6c9-4ac7a0089cf8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="gx270os01" UUID="62e16869-ca0e-403f-ba6b-0a9978060726" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: LABEL="gx270os02" UUID="f32f6dbe-a64d-4363-81e8-d72c85315452" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bs)

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
timeout		5

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

title		Xubuntu 8.10
root		(hd0,1)
kernel		/vmlinuz root=/dev/sda2 ro quiet splash
initrd		/initrd.img
savedefault
quiet

title		Chainload Xubuntu 8.10 GrUB menu.lst
configfile	(hd0,1)/boot/grub/menu.lst

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
# kopt=root=UUID=afb6e160-7756-4e53-af12-ba185dc6e23f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=afb6e160-7756-4e53-af12-ba185dc6e23f

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

### END DEBIAN AUTOMAGIC KERNELS LIST

================================== sda1/boot: ==================================

total 3
drwxr-xr-x 3 root root 1024 2008-12-28 07:53 .
drwxr-xr-x 4 root root 1024 2008-12-28 07:52 ..
drwxr-xr-x 2 root root 1024 2008-12-28 07:54 grub

=============================== sda1/boot/grub: ===============================

total 193
drwxr-xr-x 2 root root   1024 2008-12-28 07:54 .
drwxr-xr-x 3 root root   1024 2008-12-28 07:53 ..
-rw-r--r-- 1 root root    197 2008-12-28 07:53 default
-rw-r--r-- 1 root root     15 2008-12-28 07:53 device.map
-rw-r--r-- 1 root root   8108 2008-12-28 07:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-28 07:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 07:53 installed-version
-rw-r--r-- 1 root root   8712 2008-12-28 07:53 jfs_stage1_5
-rw-r--r-- 1 root root   3923 2008-12-28 08:00 menu.lst
-rw-r--r-- 1 root root   4708 2008-12-28 07:53 menu.lst~
-rw-r--r-- 1 root root   4792 2008-12-28 07:54 menu.lst.bak
-rw-r--r-- 1 root root   7352 2008-12-28 07:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-28 07:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-28 07:53 stage1
-rw-r--r-- 1 root root 121460 2008-12-28 07:53 stage2
-rw-r--r-- 1 root root   9556 2008-12-28 07:53 xfs_stage1_5

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bc2521ae-0ebb-4dbc-a28a-35702d77a833 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 36384
drwxr-xr-x  3 root root    4096 2008-12-29 15:18 .
drwxr-xr-x 21 root root    4096 2008-12-29 15:11 ..
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-29 15:11 grub
-rw-r--r--  1 root root 7492728 2008-12-29 15:11 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7882958 2008-12-29 14:31 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7493142 2008-12-29 15:18 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7493168 2008-12-29 15:11 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda2/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-12-29 15:11 .
drwxr-xr-x 3 root root   4096 2008-12-29 15:18 ..
-rw-r--r-- 1 root root    197 2008-12-29 14:32 default
-rw-r--r-- 1 root root     15 2008-12-29 14:32 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 14:32 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 14:32 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 14:32 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 14:32 jfs_stage1_5
-rw-r--r-- 1 root root   4703 2008-12-29 15:11 menu.lst
-rw-r--r-- 1 root root   4617 2008-12-29 15:11 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-29 14:32 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 14:32 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 14:32 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 14:32 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 14:32 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> The post [here](http://ubuntuforums.org/showthread.php?t=1025013#5) has the thing I was thinking of.

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

This code will download the latest and also create the output.  Check out the post (I linked to above) if you like.

I just ran this code on my machine and it seems to work pretty well:

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  83  Linux
/dev/sda2   *       96390    41062139    20482875   83  Linux
/dev/sda3        41062140   976768064   467852962+   5  Extended
/dev/sda5        41062203    45158714     2048256   82  Linux swap / Solaris
/dev/sda6        45158778   454751954   204796588+  83  Linux
/dev/sda7       454752018   864345194   204796588+  83  Linux
/dev/sda8       864345258   920556629    28105686   83  Linux
/dev/sda9       920556693   976768064    28105686   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="gx270grub" UUID="1f54a6c3-b6a1-47d8-a8a6-c72f632d7399" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="fa9a454f-3ccc-4aa4-866f-774317b4fa82" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="bc2521ae-0ebb-4dbc-a28a-35702d77a833" 
/dev/sda6: LABEL="gx270data" UUID="7c7b09e1-cd00-41e7-add1-e73d3c9785d2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="gx270databak" UUID="bbe4a711-7d66-4522-a6c9-4ac7a0089cf8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="gx270os01" UUID="62e16869-ca0e-403f-ba6b-0a9978060726" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: LABEL="gx270os02" UUID="f32f6dbe-a64d-4363-81e8-d72c85315452" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bs)

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
timeout		5

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

title		Xubuntu 8.10
root		(hd0,1)
kernel		/vmlinuz root=/dev/sda2 ro quiet splash
initrd		/initrd.img
savedefault
quiet

title		Chainload Xubuntu 8.10 GrUB menu.lst
configfile	(hd0,1)/boot/grub/menu.lst

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
# kopt=root=UUID=afb6e160-7756-4e53-af12-ba185dc6e23f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=afb6e160-7756-4e53-af12-ba185dc6e23f

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

### END DEBIAN AUTOMAGIC KERNELS LIST

================================== sda1/boot: ==================================

total 3
drwxr-xr-x 3 root root 1024 2008-12-28 07:53 .
drwxr-xr-x 4 root root 1024 2008-12-28 07:52 ..
drwxr-xr-x 2 root root 1024 2008-12-28 07:54 grub

=============================== sda1/boot/grub: ===============================

total 193
drwxr-xr-x 2 root root   1024 2008-12-28 07:54 .
drwxr-xr-x 3 root root   1024 2008-12-28 07:53 ..
-rw-r--r-- 1 root root    197 2008-12-28 07:53 default
-rw-r--r-- 1 root root     15 2008-12-28 07:53 device.map
-rw-r--r-- 1 root root   8108 2008-12-28 07:53 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-28 07:53 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 07:53 installed-version
-rw-r--r-- 1 root root   8712 2008-12-28 07:53 jfs_stage1_5
-rw-r--r-- 1 root root   3923 2008-12-28 08:00 menu.lst
-rw-r--r-- 1 root root   4708 2008-12-28 07:53 menu.lst~
-rw-r--r-- 1 root root   4792 2008-12-28 07:54 menu.lst.bak
-rw-r--r-- 1 root root   7352 2008-12-28 07:53 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-28 07:53 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-28 07:53 stage1
-rw-r--r-- 1 root root 121460 2008-12-28 07:53 stage2
-rw-r--r-- 1 root root   9556 2008-12-28 07:53 xfs_stage1_5

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fa9a454f-3ccc-4aa4-866f-774317b4fa82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=bc2521ae-0ebb-4dbc-a28a-35702d77a833 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 36384
drwxr-xr-x  3 root root    4096 2008-12-29 15:18 .
drwxr-xr-x 21 root root    4096 2008-12-29 15:11 ..
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-29 15:11 grub
-rw-r--r--  1 root root 7492728 2008-12-29 15:11 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7882958 2008-12-29 14:31 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7493142 2008-12-29 15:18 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7493168 2008-12-29 15:11 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda2/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-12-29 15:11 .
drwxr-xr-x 3 root root   4096 2008-12-29 15:18 ..
-rw-r--r-- 1 root root    197 2008-12-29 14:32 default
-rw-r--r-- 1 root root     15 2008-12-29 14:32 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 14:32 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 14:32 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 14:32 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 14:32 jfs_stage1_5
-rw-r--r-- 1 root root   4703 2008-12-29 15:11 menu.lst
-rw-r--r-- 1 root root   4617 2008-12-29 15:11 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-29 14:32 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 14:32 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 14:32 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 14:32 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 14:32 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

Yes. I ran it too. Here is the ouput:

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       swap

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f090f08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       189518805   195366464     2923830   82  Linux swap / Solaris
/dev/sda2              63   189518804    94759371   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="swap" UUID="f2443e53-cd06-490f-928a-fbc1199d8112" 
/dev/sda2: UUID="a49b4002-28ef-4374-9f03-ed9db49f4534" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/sudarshan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sudarshan)

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=f2443e53-cd06-490f-928a-fbc1199d8112 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 17656
drwxr-xr-x  3 root root    4096 2008-12-29 20:25 .
drwxr-xr-x 21 root root    4096 2008-12-29 20:07 ..
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-12-29 20:25 grub
-rw-r--r--  1 root root 7502625 2008-12-29 20:25 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7067205 2008-12-29 19:45 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic

=============================== sda2/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2008-12-29 20:25 .
drwxr-xr-x 3 root root   4096 2008-12-29 20:25 ..
-rw-r--r-- 1 root root    197 2008-12-29 20:25 default
-rw-r--r-- 1 root root     30 2008-12-29 20:25 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 20:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 20:25 fat_stage1_5
-rw-r--r-- 1 root root     18 2008-12-29 20:25 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 20:25 jfs_stage1_5
-rw-r--r-- 1 root root   4271 2008-12-29 20:25 menu.lst
-rw-r--r-- 1 root root   7324 2008-12-29 20:25 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 20:25 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-29 20:25 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 20:25 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 20:25 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by boof1988 on 2008-12-29
Grub's menu.lst indicates the wrong drive (as shown in red below).

```
title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd[COLOR="Red"]1[/COLOR],1)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet
```

I don't know how to properly change anything inside of the "Automagic Kernel" area so I would recommend adding the following part (in red) between the blue parts in grub's menu.lst.  Note the change from (hd1,1) to (hd0,1).

```
[COLOR="Blue"]# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/COLOR]

[COLOR="Red"]title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet[/COLOR]

[COLOR="Blue"]### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below[/COLOR]
```

This should let you boot without the flash drive installed.  Though I think this will be somewhat of a temporary fix.  Maybe someone else will chime in to say how to fix the "Automagic Kernel" part properly.

---

### Post by linuxnovice on 2008-12-29
> **boof1988 said:**
> Grub's menu.lst indicates the wrong drive (as shown in red below).

```
title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd[COLOR="Red"]1[/COLOR],1)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet
```

I don't know how to properly change anything inside of the "Automagic Kernel" area so I would recommend adding the following part (in red) between the blue parts in grub's menu.lst.  Note the change from (hd1,1) to (hd0,1).

```
[COLOR="Blue"]# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/COLOR]

[COLOR="Red"]title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=a49b4002-28ef-4374-9f03-ed9db49f4534 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet[/COLOR]

[COLOR="Blue"]### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below[/COLOR]
```

This should let you boot without the flash drive installed.  Though I think this will be somewhat of a temporary fix.  Maybe someone else will chime in to say how to fix the "Automagic Kernel" part properly.

Ok that worked. Although, now after the ubuntu logo is displayed, it prints out a bunch of stuff (normal booting stuff) and then boots into the system.

I dont understand what automagic kernel is. Secondly, like I changed added that bit of code in menu.lst, why cant I change hd1 to hd0 for the stuff below? Wouldnt that fix the problem?

Thanks.

---

### Post by boof1988 on 2008-12-29
> **linuxnovice said:**
> Ok that worked. Although, now after the ubuntu logo is displayed, it prints out a bunch of stuff (normal booting stuff) and then boots into the system.

Does the kernel line in menu.lst have the "quiet" and "splash" at the end?

> **linuxnovice said:**
> I dont understand what automagic kernel is. Secondly, like I changed added that bit of code in menu.lst, why cant I change hd1 to hd0 for the stuff below? Wouldnt that fix the problem?

I don't know enough about grub yet to give a good answer to this one.  I do believe that when something (I'm not sure what though) updates, the information in that region of the grub menu is used during the automatic update process.

I use a [dedicated grub partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_) so I can mess with it (without touching grub on the Ubuntu partition).  When I screw it up, I can just use the Super Grub Disk to boot to Ubuntu and then fix whatever I messed up.

---

### Post by linuxnovice on 2008-12-29
```
Does the kernel line in menu.lst have the "quiet" and "splash" at the end?
```

Yes. Its got both.

---

### Post by boof1988 on 2008-12-29
There might be some sort of "update grub" thing maybe.  I'm out of ideas and really tired.

Sorry I don't have any more ideas.  I hope someone else will chime in and answer the remaining questions.

If you haven't looked at it yet, I recommend [Hermanzone's Grub Page](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by boof1988 on 2008-12-30
*Bump*

---

### Post by linuxnovice on 2008-12-30
> **boof1988 said:**
> *Bump*

Thanks for the bump. I downloaded the entire live cd version (as opposed to the mini version for a alternate install) and used the graphical partitionar to set everything upcorrectly (this is also from the usb using unetbootin) and there were no problems. I guess I must have messed up the alternate install partitioner...although I would still like to find the solution for this.

---

### Post by RealG187 on 2008-12-30
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That page says how to restore grub. The instructions are for people who have lost the boot loeader by installing Windows, but the instructions should be similar.

---

### Post by linuxnovice on 2008-12-30
> **RealG187 said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That page says how to restore grub. The instructions are for people who have lost the boot loeader by installing Windows, but the instructions should be similar.

We already tried that earlier. No luck.

---

