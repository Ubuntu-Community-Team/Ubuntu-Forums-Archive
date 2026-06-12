---
title: "Cannot boot into Vista!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by muddatrucker on 2009-02-09
I wanted to try out Ubuntu again after uninstalling it before (I needed the space and I had to use Windows then).  So I created a partition in Vista through Disk Management (I'm guessing this is where I went wrong), installed Ubuntu using "Guided - use the largest continuous free space" and the installation went fine.  

Then, while in Ubuntu, I tried to access my VistaOS partition but it said "Unable to mount volume."  I thought it was weird so I restarted and tried to go to Vista but all I got was a big screen that said "ERROR" and "Cannot open Recovery.DAT" on the title bar.

What's wrong?  Did I lose the files on my Vista partition forever? :(

---

### Post by LowSky on 2009-02-09
Well you didn't loose it but I hope you have a Vista Installation CD, You may need to repair your install.
What you did wrong was not running disk defragement before shrinking and creating the Ubuntu Partition.

---

### Post by muddatrucker on 2009-02-09
THanks for the quick reply.  I don't have a Vista installation CD since it's OEM but I have the manufacturer's recovery CD.  Will that work?

---

### Post by LowSky on 2009-02-09
it should, be prepared you will need to repair you GRub file after repairing vista, as Vista will reinstall its own MBR

---

### Post by BrandonBan6 on 2009-02-09
> [ubuntu] Cannot boot into Vista! 

Sounds like a good problem to have :D

Just kidding, I really hope you can fix it!

---

### Post by Mark Phelps on 2009-02-09
Be careful with the Recovery CD.  They generally boot you into a Recovery environment that then completely reformates and writes the hard drive.  They're intended to recover the Vista installation, not repair the installation.

If you get the option to do a Startup Repair, you can try that.  But if you get any other option, make sure you have your files and data backed up first, because you'll likely lose everything during the recovery.

---

### Post by muddatrucker on 2009-02-09
> **BrandonBan6 said:**
> Sounds like a good problem to have :D
I actually wouldn't have cared if only I didn't have a lot of important stuff there.

I ran Startup Repair from the CD.  It found an error (I forgot what it was but its solution was to run chkdsk), fixed it then made me restart.  I restarted, ran the repair again and this time it found no errors.  But when I tried to boot Vista, I got the same error. :(

---

### Post by caljohnsmith on 2009-02-09
Before you seriously consider reinstalling Vista, I think it would help to get a clearer picture of your setup to see if Vista might be fixable or not; how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

### Post by muddatrucker on 2009-02-09
caljohnsmith:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
138 heads, 12 sectors/track, 141571 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ff2eb43

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,242,047    10,240,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     10,242,048   150,759,423   140,517,376   7 HPFS/NTFS
/dev/sda3         150,759,424   213,958,647    63,199,224   7 HPFS/NTFS
/dev/sda4         213,960,168   234,441,575    20,481,408   5 Extended
/dev/sda5         213,960,180   233,472,815    19,512,636  83 Linux
/dev/sda6         233,472,828   234,441,575       968,748  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="9417-721B" TYPE="vfat" 
/dev/sda2: UUID="5AC60179C60156A3" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda3: UUID="76FC760EFC75C93F" LABEL="HD2" TYPE="ntfs" 
/dev/sda5: UUID="de183b02-43ad-42ed-8eba-39b67b2378c6" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="e2d53939-dd1e-461f-bfc6-e84cca2fe29c" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paolo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paolo)
/dev/sda2 on /media/VistaOS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

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
# kopt=root=UUID=de183b02-43ad-42ed-8eba-39b67b2378c6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de183b02-43ad-42ed-8eba-39b67b2378c6

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
uuid		de183b02-43ad-42ed-8eba-39b67b2378c6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de183b02-43ad-42ed-8eba-39b67b2378c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		de183b02-43ad-42ed-8eba-39b67b2378c6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de183b02-43ad-42ed-8eba-39b67b2378c6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		de183b02-43ad-42ed-8eba-39b67b2378c6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=de183b02-43ad-42ed-8eba-39b67b2378c6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e2d53939-dd1e-461f-bfc6-e84cca2fe29c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 111.4GB: boot/grub/menu.lst
 111.4GB: boot/grub/stage2
 111.5GB: boot/initrd.img-2.6.27-7-generic
 111.4GB: boot/vmlinuz-2.6.27-7-generic
 111.5GB: initrd.img
 111.4GB: vmlinuz

```

EDIT: I just realized you said LiveCD.  I'm at work right now and left the CD at home.  I'll run the Boot Info Script again later.

---

### Post by caljohnsmith on 2009-02-09
It's OK, you don't have to run that script from the Live CD; you can do it from your Ubuntu install just as well. Sorry, I should have made that clear. But about your Vista booting issue, it looks like the problem is that your Vista entry in your menu.lst is configured to boot your sda1 recovery partition rather than your sda2 Vista partition. While you are in your Ubuntu install, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Then change your Vista entry at the bottom of that file to:
```
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
Then reboot, and let me know exactly what happens when you boot Vista from Grub. We can work from there if necessary.

---

### Post by muddatrucker on 2009-02-09
That fixed it.  Thank you so much.

---

### Post by caljohnsmith on 2009-02-09
Glad that worked OK; cheers and enjoy Ubuntu and Vista.

---

### Post by unplugged23 on 2009-02-09
> **BrandonBan6 said:**
> Sounds like a good problem to have :D

Just kidding, I really hope you can fix it!

lol

What problem ?!?
I Dont see a problem !!!

---

