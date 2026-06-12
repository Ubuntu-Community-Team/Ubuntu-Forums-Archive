---
title: "having trouble booting ubuntu up.."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-01-25
ok i installed windows 7(looks pretty cool btw) and now i cant boot up ubuntu i tried doing what it said in this topic 

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

and when i restart the pc it said loading grub then error 21 :(
can anyone help?

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by lil_kid1333 on 2009-01-25
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2c8e2c8

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *         2,048      411,647      409,600   7 HPFS/NTFS
/dev/sda2            411,648   71,679,999   71,268,352   7 HPFS/NTFS
/dev/sda3         71,682,030  309,572,549  237,890,520  83 Linux
/dev/sda4        309,572,550  312,576,704    3,004,155   5 Extended
/dev/sda5        309,572,613  312,576,704    3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="D22804092803EAF5" TYPE="ntfs" 
/dev/sda2: UUID="E04C02164C01E7DC" TYPE="ntfs" 
/dev/sda3: UUID="669e273a-caf0-4ada-83f2-7c88c6bc206c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9a45697a-2010-48b0-8c92-974b803dac98" TYPE="swap" 
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

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=669e273a-caf0-4ada-83f2-7c88c6bc206c

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		669e273a-caf0-4ada-83f2-7c88c6bc206c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		669e273a-caf0-4ada-83f2-7c88c6bc206c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		669e273a-caf0-4ada-83f2-7c88c6bc206c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		669e273a-caf0-4ada-83f2-7c88c6bc206c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		669e273a-caf0-4ada-83f2-7c88c6bc206c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=669e273a-caf0-4ada-83f2-7c88c6bc206c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9a45697a-2010-48b0-8c92-974b803dac98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location  of files loaded by Grub: ===================


  74.6GB: boot/grub/menu.lst
  74.6GB: boot/grub/stage2
  74.4GB: boot/initrd.img-2.6.27-7-generic
  74.4GB: boot/initrd.img-2.6.27-9-generic
  74.4GB: boot/vmlinuz-2.6.27-7-generic
  74.4GB: boot/vmlinuz-2.6.27-9-generic
  74.4GB: initrd.img
  74.4GB: initrd.img.old
  74.4GB: vmlinuz
  74.4GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```

btw since i installed windows 7 it takes forever in the boot up process and then thats when it goes 2 grub error 21...

---

### Post by caljohnsmith on 2009-01-25
The way your system is set up right now, it looks like you should be able to boot into Ubuntu without any problem. If you press "ESC" repeatedly on start up, do you get the Grub menu or no? If you can boot into Ubuntu, to boot Windows from your Grub menu first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom:
```
title Windows 7
root (hd0,0)
chainloader +1
```
Then reboot, and let me know what happens when you boot Win 7 from Grub, or let me know if you run into problems.

---

### Post by lil_kid1333 on 2009-01-25
nah no menu came up sorry for taking a long time like i said it takes forever loading up.. right now im in the ubuntu live cd and im sorry but i  didnt get that last part you said if you want i can show you the pic of the error i took..

nvm i tried what you said and tried to save it and it sayd could not find the file :(

---

### Post by caljohnsmith on 2009-01-25
Are you sure you have your BIOS set to boot the 160 GB drive before any of your other drives? If so, how about going ahead and post a picture of the error you are getting.

---

### Post by lil_kid1333 on 2009-01-25
umm idk if i do?? how can i check?

the error...

<a href="http://s96.photobucket.com/albums/l180/lil_kid1333/?action=view&current=P012509154431.jpg" target="_blank"><img src="http://i96.photobucket.com/albums/l180/lil_kid1333/P012509154431.jpg" border="0" alt="Photobucket"></a>

where it takes up forever 2 load...
<a href="http://s96.photobucket.com/albums/l180/lil_kid1333/?action=view&current=P012509154246.jpg" target="_blank"><img src="http://i96.photobucket.com/albums/l180/lil_kid1333/P012509154246.jpg" border="0" alt="Photobucket"></a>

---

### Post by caljohnsmith on 2009-01-25
You should be able to press F10, F12, Del, or some other function key on start up to get into your BIOS. Often times when the computer flashes the Intel BIOS screen that you see, it tells you which function key to press to access the BIOS settings. I would check that to make sure your 160 GB drive is set to boot before your other drives. Look for the "boot order" in your BIOS, and that's where it will be. 

Also, how about reinstalling Grub to the MBR (Master Boot Record) by following these steps:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
And please post the output of the commands before doing "quit". If it says it's successful, reboot and let me know what happens.

---

### Post by lil_kid1333 on 2009-01-25
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

their you go... imma try rebooting now ill edit this reply when ive done so...

---

### Post by lil_kid1333 on 2009-01-26
hey dude i got into the settings you were talking about and this came up

<a href="http://s96.photobucket.com/albums/l180/lil_kid1333/?action=view&current=P012509222725.jpg" target="_blank"><img src="http://i96.photobucket.com/albums/l180/lil_kid1333/P012509222725.jpg" border="0" alt="Photobucket"></a>

i went to bios but sorry dude didnt understand one thing...

---

### Post by caljohnsmith on 2009-01-26
So do you still get the Grub error 21 on start up? If so, how about going into the "Standard CMOS Features" menu that you show in that screen shot, and see if there is anything there about "boot order". If not, check the "Advanced BIOS Features" menu for the boot order. I think the boot order should be under one of those menus, but I can't be sure since I don't know your BIOS.

---

### Post by lil_kid1333 on 2009-01-26
thanks i fixed it hehe i just used gparted n wiped off windows :P it still takes forever to load up idk why but it happened since i installed that damn windows.. look at that, i barely install windows and already problems with it :P wish i could fix that but i dnt care at least i got my beautifull ubuntu back :'D

---

