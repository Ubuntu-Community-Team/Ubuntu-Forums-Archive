---
title: "GRUB - Error 22: No such partition!"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by KosmicheCam on 2009-01-26
Hello people of the forum.

I am having a scary problem, and I fear I've lost all my partitions. Here's some background:

[LIST]
[*]I have a dual boot setup - XP and Ubuntu 8.10
[*]I'm running with an ASUS P4P800 board
[*]Seagate 250GB SATA hdd
[*] The tower had been on the floor for a while - quite dusty
[/LIST]

I moved the computer back up onto the desk today, and opened it up to have a look at dust levels. Before tinkering with anything I switched the machine on and during boot I got a message saying "Overclocking failed". I selected to proceed with default settings and this time booted up XP.

Now on restarting I can't get either operating system to boot at GRUB. Ubuntu gives me an "Error 22: No such partition" and XP gives me "Ntloader is missing".

Can anyone help to diagnose the problem I'm having? I have checked all leads within the box and have done a careful vacuum to remove dust.

Please help!

---

### Post by caljohnsmith on 2009-01-27
Do you have a Live CD you can boot to do troubleshooting with? If so, how about booting that, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by KosmicheCam on 2009-01-28
Thank you for the help caljohnsmith. Thank goodness for the live CDs. Interestingly I can still access my file system(s) when I boot this way. Here is the output for boot info script:

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
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 373348968 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04ea04e9

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   78,140,159   78,140,097   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc5bfc5b

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63  120,953,384  120,953,322   7 HPFS/NTFS
/dev/sdb2        120,953,385  488,392,064  367,438,680   5 Extended
/dev/sdb5        120,953,448  145,532,834   24,579,387  83 Linux
/dev/sdb6        482,335,623  488,392,064    6,056,442  82 Linux swap / Solaris
/dev/sdb7        145,532,898  482,335,559  336,802,662  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0AE4F6C7E4F6B3D3" LABEL="MUSIC" TYPE="ntfs" 
/dev/sdb1: UUID="32647D00647CC7DD" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb5: UUID="710dc4aa-b6e8-4227-8682-6c2a03974cfe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="5de3a351-1b8e-4532-92c5-fa9827db1cfd" TYPE="swap" 
/dev/sdb7: LABEL="Hernandez" UUID="2e2e150f-f53b-4834-b879-82158e758959" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb7 on /media/Hernandez type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# color cyan/blue white/blue
splashimage=(hd0,4)/boot/grub/splashimages/grub_mandalas.xpm.gz

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
# kopt=root=UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Microsoft Windows XP
root		(hd0,0)
makeactive
chainloader    +1

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=710dc4aa-b6e8-4227-8682-6c2a03974cfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=5de3a351-1b8e-4532-92c5-fa9827db1cfd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb7 /home ext3 nodev,nosuid,relatime 0 2

=================== sdb5: Location  of files loaded by Grub: ===================


  63.5GB: boot/grub/menu.lst
  64.5GB: boot/grub/stage2
  64.5GB: boot/initrd.img-2.6.24-19-generic
  64.5GB: boot/initrd.img-2.6.24-19-generic.bak
  63.7GB: boot/initrd.img-2.6.27-9-generic
  64.5GB: boot/vmlinuz-2.6.24-19-generic
  63.7GB: boot/vmlinuz-2.6.27-9-generic
  63.7GB: initrd.img
  63.7GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-28
It looks like the issue is that in the course of your tinkering, somehow the boot order was changed. Both your sda and sdb drives have Grub installed to the MBR (Master Boot Record), so booting either of those drives will give you the Grub menu; but your Grub's menu.lst is only configured to boot correctly from the 250 GB sdb drive that has Ubuntu and Windows. If you can change your BIOS so that it boots the 250 GB drive again, I think you should be all set. How about giving that a shot and let me know how it goes.

---

### Post by KosmicheCam on 2009-01-29
Yay, I'm back in business! Thank you very much for your suggestions and for reading over that report.

You were correct. It was trying to boot an empty drive as the main drive. I wasn't aware that grub was present on it...

I wonder if when I received the "overclocking failed" message, the boot order in BIOS was somehow interfered with?

Thank you again!

---

### Post by caljohnsmith on 2009-01-29
I'm really glad to hear changing your boot order is all it took to get Ubuntu and Windows booting again, because it's always nice when the solution turns out to be something simple. Cheers and enjoy Windows and Ubuntu. :)

---

