---
title: "Grub error 21"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by zackflash on 2009-05-19
Ok, so every single time I have ever tried to install Ubuntu, I get Grub error 21 upon the reboot after the installation.

This is really starting to get annoying, because now not only will Ubuntu install correctly, I cannot boot into Windows XP.
Next, I tried to do a fresh format and install Ubuntu on my harddrive (I have two partitions, one which I created for Ubuntu) and I still get the Grub error 21.

Don't get me wrong, I've used the search button, and I've tried a lot of troubleshooting techniques, such as going into Grub and typing "root (hd0,0)" etc, and every time I try (I know it is installed on hd0, Grub tells me it can't find any existing hard drive)

I am a COMPLETE noob at Linux and Ubuntu, so if you could please, PLEASE help me out with this problem as easily and pain-free as possible, I would really appreciate it, haha.

Thanks,
Zach

(p.s. the only usability i have right now with my computer is the live ubutnu disc :/)

---

### Post by lindsay7 on 2009-05-19
Ok, I copied this from another post, this will tell what is going on with your drive and what is installed in terms of the mbr and what is in the grub file. This should tell us what is missing and what needs to be done.


Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Results.txt file.

---

### Post by nhasian on 2009-05-19
1. Boot your computer up with Ubuntu CD

2. Open a terminal window or switch to a tty.

3. Go SuperUser (that is, type “sudo -s”). Enter root passwords as necessary.

4. Type “grub”

5. Type “find /boot/grub/stage1&#8243;. You’ll get a response like “(hd0,1)”.

Use whatever your computer spits out for the following lines.

6. Type “root (hd0,1)”, or whatever your hard disk + boot partition numbers are for Ubuntu.

7. Type “setup (hd0)”, to install GRUB to MBR, or “setup (hd0,1)” or whatever your hard disk + partition nr is, to install GRUB to a partition.

8. Quit grub by typing “quit”.

9. Reboot and remove the bootable CD.

Note:- In the above procedure hd0,1 is an example it might be different in your case.

credits go to [http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html)

---

### Post by lindsay7 on 2009-05-19
One more thing, do you have your windows xp install disk with you?

---

### Post by lindsay7 on 2009-05-19
Question for Nhasian, are stage 1 and stage 2 always in the same place?

---

### Post by zackflash on 2009-05-20
Thank you guys so much, I just tried nhasian's version, and if it works I'll be excited :]

---

### Post by mosaabJ on 2009-05-20
> **lindsay7 said:**
> Ok, I copied this from another post, this will tell what is going on with your drive and what is installed in terms of the mbr and what is in the grub file. This should tell us what is missing and what needs to be done.


Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Results.txt file.

[SIZE="5"][COLOR="DarkOrange"]I have the same Problem I followed the steps you told about and these are the results I got[/COLOR][/SIZE]

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e009e00

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     10,924,200   625,137,344   614,213,145   7 HPFS/NTFS
/dev/sda2                  63    10,924,199    10,924,137  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3414533

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   619,900,154   619,900,092   7 HPFS/NTFS
/dev/sdb2         619,900,155   625,137,344     5,237,190   5 Extended
/dev/sdb5         619,900,218   624,783,914     4,883,697  83 Linux
/dev/sdb6         624,783,978   625,137,344       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A438D4F438D4C708" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="2D55-4C0A" TYPE="vfat" 
/dev/sdb1: UUID="FCC42AF2C42AAF38" TYPE="ntfs" 
/dev/sdb5: UUID="5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="494a7c07-e791-43bd-8b83-7927cc6722db" 

=============================== "mount" output: ===============================

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
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde5 during installation
UUID=5b5dc4f1-5bb6-409a-95ec-45ccfdcd77ca /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=494a7c07-e791-43bd-8b83-7927cc6722db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 318.9GB: boot/grub/menu.lst
 317.7GB: boot/grub/stage2
 317.8GB: boot/initrd.img-2.6.28-11-generic
 318.9GB: boot/vmlinuz-2.6.28-11-generic
 317.8GB: initrd.img
 318.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde 
```

---

### Post by lindsay7 on 2009-05-20
To Mosaab,

This is what it looks like to me, your grub menu is looking to load windows xp (on Hd 0,0)and then the windows recovery partition on (hd 0,1), as shown here

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```


type this in the terminal "sudo gedit /boot/grub/menu.lst" that is the letter l not number 1 in lst. Save this file with a different extention at the end so that you can restore it if needed and remember where you put it.  Then delete the lines that read

> title		Windows NT/2000/XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

Save the file and reboot. If this does not fix the problem, try the steps that Nhasian has in his post.  If everything fails to fix you problem. restore your grub menu from the file you saved. and repost the output of your boot info summery and see if someone else can help.

---

### Post by lindsay7 on 2009-05-20
To Mosaab,


I look at this again and if taking out those line in your grub menu does not work. put them back in your grub menu. You can just open the menu by typing sudo gedit /boot/grub/menu.lst and cut and past from the lines shown in your boot info shown above.  Save the file after that.


Then let just try to install grub to your mbr.

in the terminal type.

"sudo grub"

at the grub prompt, type

"find /boot/grub/stage2

this will return something like (hd1,4)

still at the grub prompt type the results of what you get above
as such

"root (hdx,y)"  where x and y are what you got in the above
"setup (hd0)"
"quit"

reboot

---

### Post by zackflash on 2009-05-20
Ok Lindsay, I have the results:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 283656255 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   378,571,724   378,571,662  83 Linux
/dev/sda2         378,571,725   390,716,864    12,145,140   5 Extended
/dev/sda5         378,571,788   390,716,864    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="725626bd-c8fd-4912-b316-66764d5b9fef" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="f6c05715-9603-4c6a-bc63-5df4eb8dffc0" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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
# kopt=root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=725626bd-c8fd-4912-b316-66764d5b9fef /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f6c05715-9603-4c6a-bc63-5df4eb8dffc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda1: Location of files loaded by Grub: ===================


 145.3GB: boot/grub/menu.lst
 145.2GB: boot/grub/stage2
 145.2GB: boot/initrd.img-2.6.22-14-generic
 145.3GB: boot/initrd.img-2.6.22-14-generic.bak
 145.3GB: boot/vmlinuz-2.6.22-14-generic
 145.2GB: initrd.img
 145.3GB: vmlinuz
```

---

### Post by zackflash on 2009-05-20
Ok Lindsay, I have the results:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 283656255 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   378,571,724   378,571,662  83 Linux
/dev/sda2         378,571,725   390,716,864    12,145,140   5 Extended
/dev/sda5         378,571,788   390,716,864    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="725626bd-c8fd-4912-b316-66764d5b9fef" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="f6c05715-9603-4c6a-bc63-5df4eb8dffc0" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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
# kopt=root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=725626bd-c8fd-4912-b316-66764d5b9fef ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=725626bd-c8fd-4912-b316-66764d5b9fef /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f6c05715-9603-4c6a-bc63-5df4eb8dffc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda1: Location of files loaded by Grub: ===================


 145.3GB: boot/grub/menu.lst
 145.2GB: boot/grub/stage2
 145.2GB: boot/initrd.img-2.6.22-14-generic
 145.3GB: boot/initrd.img-2.6.22-14-generic.bak
 145.3GB: boot/vmlinuz-2.6.22-14-generic
 145.2GB: initrd.img
 145.3GB: vmlinuz
```

---

### Post by khelben1979 on 2009-05-20
Since you're a Linux newbie I suggest that you take a look at the LQWiki on [the error 21 message]("http://wiki.linuxquestions.org/wiki/GRUB#Error_21").

---

### Post by lindsay7 on 2009-05-20
Ok, this is what I see, windows in not on this system. Do you have another drive that is not showing up for some reason i.e. external drive that is not plugged in?  The version of Ubuntu that is on the system is 7.10. Is this what you want.

If your answer is "what happened to windows, it must have been overwritten" and no I want a current version of Ubuntu, then what I would do is reformat the drive and partition it into at least two partitions, one for windows and one for Ubuntu. Install windows first and make sure it boots up and you are happy with it. Then install Ubuntu 9.04.

If you just want to have Ubuntu on this system then instead of fixing 7.10, I would just install 9.04 over what is there using the whole disk option in the 9.04 cd install disk.

---

### Post by zackflash on 2009-05-20
Ok, so my friend brought over a copy of 8.04, and I just formatted and installed it, and I got the grub error 21 again.

I know that my Windows is completely gone, so worst case scenario I install Windows and forget about Ubuntu.

---

### Post by lindsay7 on 2009-05-20
Then let just try to install grub to your mbr.

in the terminal type.

"sudo grub"

at the grub prompt, type

"find /boot/grub/stage2

this will return something like (hd0,0)

still at the grub prompt type the results of what you get above
as such

"root (hdx,y)" where x and y are what you got in the above
"setup (hd0)"
"quit"

reboot


Let me know if that worked

---

