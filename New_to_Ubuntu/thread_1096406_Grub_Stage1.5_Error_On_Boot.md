---
title: "Grub Stage1.5 Error On Boot"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by conryf on 2009-03-14
Hi, I was planning on doing a dual boot with XP and I kept getting the blue screen of death mid install, so I instead decided just to install the new Ubuntu.

So I made a boot CD and installed. One thing that might be relevant is, I formatted a ntfs partition on the side and was trying to leave it alone with a view towards eventually puttin XP on that. 

In any case, the solution I read about numerous times doesn't work. Namely
<code>
sudo grub
find /boot/grub/stage1
</code>

here I get (hd0,4)

<code>
root (hd0,4)
setup (hd0,4)
</code>

at which point, before quitting, I get 

<code>
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,4) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
</code>

when I reboot, I get the same error.

Also here is the output of fdisk -l

<code>
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad894c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         285     2289231   83  Linux
/dev/sda2   *       16574       19457    23165730    7  HPFS/NTFS
/dev/sda3             286       16573   130833360    5  Extended
/dev/sda5             286       15906   125475651   83  Linux
/dev/sda6           15907       16573     5357646   82  Linux swap / Solaris

Partition table entries are not in disk order
</code>

Here is the result of the boot_info_script as well:

<code>
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 48192796 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 48192796 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad894c6d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     4,578,524     4,578,462  83 Linux
/dev/sda2    *    266,245,245   312,576,704    46,331,460   7 HPFS/NTFS
/dev/sda3           4,578,525   266,245,244   261,666,720   5 Extended
/dev/sda5           4,578,588   255,529,889   250,951,302  83 Linux
/dev/sda6         255,529,953   266,245,244    10,715,292  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="86d4362c-97ac-45ea-af36-76be99e26eae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="c8f56ab4-91ad-4673-b7f1-3b203f5abe04" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="3d37787c-25d9-42fb-a58e-ad34aaaa8c8f" TYPE="swap" 
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
# kopt=root=UUID=c8f56ab4-91ad-4673-b7f1-3b203f5abe04 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c8f56ab4-91ad-4673-b7f1-3b203f5abe04

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
uuid		c8f56ab4-91ad-4673-b7f1-3b203f5abe04
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8f56ab4-91ad-4673-b7f1-3b203f5abe04 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c8f56ab4-91ad-4673-b7f1-3b203f5abe04
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8f56ab4-91ad-4673-b7f1-3b203f5abe04 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c8f56ab4-91ad-4673-b7f1-3b203f5abe04
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c8f56ab4-91ad-4673-b7f1-3b203f5abe04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3d37787c-25d9-42fb-a58e-ad34aaaa8c8f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  24.7GB: boot/grub/menu.lst
  24.6GB: boot/grub/stage2
  24.6GB: boot/initrd.img-2.6.27-7-generic
  24.6GB: boot/vmlinuz-2.6.27-7-generic
  24.6GB: initrd.img
  24.6GB: vmlinuz
</code>
 
Oh and I'm using a Thinkpad X61 with an external DVD/CD. Thanks in advance.

---

### Post by meierfra. on 2009-03-14
Reinstall Grub with

```

sudo grub
root (hd0,4)
setup [COLOR="Red"](hd0)[/COLOR]
quit

```


Also it seems that you installed grub to the boot sector of your NTFS partition /dev/sda2.   That makes the partition unusable.  Is that the  ntfs partition you just formated? If yes, just format it again. But if it contains some data, let me know and I can show you how to repair the boot sector.

---

### Post by conryf on 2009-03-15
Awesome that worked.

Thank alot. The NT partition is empty, I'll just reformat it. Thanks again!

---

### Post by meierfra. on 2009-03-15
> Awesome that worked.
Great. Have fun with Ubuntu.

---

