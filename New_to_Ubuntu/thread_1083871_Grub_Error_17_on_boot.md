---
title: "Grub Error 17 on boot"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by neptor on 2009-03-01
I'm a newbie to the Unbuntu software. I performed an install on the disk and rebooted and I get a Grub error 17. I tried the Super Grub Disk, but it did not appear to correct the issue. Looked for a cure in multiple locations. Is there a step by step instruction on how to fix this issue? Since I'm a newbie it would have to be fairly detailed. I don't have windows on the drives; I clobbered that messing with the partitions. It's no big since this is my old machine. I figure I could install this and play with it to learn more about Linux. 

Thanks!

---

### Post by ptn107 on 2009-03-01
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)

You just need to reinstall GRUB.  It needs to be done from a live CD:

```
sudo grub-install hd0
sudo update-grub
```

This assumes that GRUB will be installed on your first hard disk (hd0).  You can make sure which drives are which in GRUBs notation by viewing the device map (from a terminal):
```
cat /boot/grub/device.map
```

---

### Post by neptor on 2009-03-01
Thanks! Tried the information provided. Not sure if this means I made progress or not. I see in the CAT command that the floppy is listed first.

ubuntu@ubuntu:~$ sudo grub-install hd0
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install hd1
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ cat /boot/grub/device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
ubuntu@ubuntu:~$ 

Thanks!

---

### Post by caljohnsmith on 2009-03-01
Are you getting the Grub error 17 before you see a Grub menu, or before seeing the text "press ESC for menu", or do you get the error after you select Ubuntu to boot from the Grub menu? In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by neptor on 2009-03-02
Thanks for your help!!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000bcae

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,168,134    75,168,072  83 Linux
/dev/sda2          75,168,135    78,172,289     3,004,155   5 Extended
/dev/sda5          75,168,198    78,172,289     3,004,092  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1a13daf

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="23977a24-7af3-4fd1-bc34-0cb806636f96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="edaa674f-828c-4812-aa9d-990722f41887" TYPE="swap" 
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
# kopt=root=UUID=23977a24-7af3-4fd1-bc34-0cb806636f96 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=23977a24-7af3-4fd1-bc34-0cb806636f96

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
uuid		23977a24-7af3-4fd1-bc34-0cb806636f96
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=23977a24-7af3-4fd1-bc34-0cb806636f96 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		23977a24-7af3-4fd1-bc34-0cb806636f96
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=23977a24-7af3-4fd1-bc34-0cb806636f96 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		23977a24-7af3-4fd1-bc34-0cb806636f96
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=23977a24-7af3-4fd1-bc34-0cb806636f96 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=edaa674f-828c-4812-aa9d-990722f41887 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  37.1GB: boot/grub/menu.lst
  37.1GB: boot/grub/stage2
  37.0GB: boot/initrd.img-2.6.27-7-generic
  37.1GB: boot/vmlinuz-2.6.27-7-generic
  37.0GB: initrd.img
  37.1GB: vmlinuz
```

---

### Post by neptor on 2009-03-02
I get the error 17 message on Boot it appears to start the grub loader, than displays the error on the next line

---

### Post by caljohnsmith on 2009-03-02
According to the script, Grub is configured correctly to boot, so to get a Grub error 17 under those circumstances is usually due to an issue with how your HDD is set up in BIOS. How about going into your BIOS and let me know what HDD-related settings you have, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. We can work from there.

---

### Post by neptor on 2009-03-02
Award BIOS 
In the standard CMOS features the drive are configured as
IDE Primary Master [NONE]
IDE Primary Slave  [NONE]

IDE HDD Auto-Detection [Press Enter]
IDE Primary Master [Auto]
Access Mode        [Auto]

IDE HDD Auto-Detection [Press Enter]
IDE Primary Slave [Auto]
Access Mode       [Auto]

Advanced BIOS Features

RAID & SCSI Boot Order [Raid,SCSI] Nothing current configured to the Highpoint Raid controller.

First Boot Device  [CDROM]
Second Boot Device [HDD-0]
Third Boot Device  [HDD-1]
Boot Other Device  [Enabled]

VIA OnChip IDE Device
Onchip IDE Channel0 [Enabled]
Onchip IDE Channel1 [Enabled]
IDE Prefetch Mode   [Enabled]
Primary Master PIO    [Auto]
Primary Slave  PIO    [Auto]
Secondary Master PIO  [Auto]
Secondary Slaver PIO  [Auto]
Primary Master UDMA   [Auto]
Primary Slave  UDMA   [Auto]
Secondary Master UDMA [Auto]
Secondary Slaver UDMA [Auto]

Intergrated Peripherals
IDE Block Mode        [Enabled]

Power Management 
HDD Powerdown         [Disabled]

I've had a second drive in the machine for a while is it possible that there is a conflict between the drives? It was working fine when I has Windows 2003 installed.
Thanks again!

---

### Post by caljohnsmith on 2009-03-02
What settings are under:
```

IDE Primary Master [Auto]
Access Mode [Auto]
Primary Master UDMA [Auto]
```
In other words, what other choices are there other than "auto"?

EDIT: It looks like sda and sdb were configured as a RAID array at some point; are they still configured with your RAID controller in BIOS?

---

### Post by neptor on 2009-03-02
The following is listed under the headings:

```

IDE Primary Master (OPTIONS)
NONE
AUTO
MANUAL

Access Mode (OPTIONS)
CHS
LBA
LARGE
AUTO

Primary Master UDMA (OPTIONS)
DISABLE
AUTO

```

---

### Post by neptor on 2009-03-02
I have an option to disable the Raid controller. I have it enabled, but have not configured the drives to use the raid.

---

### Post by caljohnsmith on 2009-03-02
> **neptor said:**
> I have an option to disable the Raid controller. I have it enabled, but have not configured the drives to use the raid.
OK, definitely disable RAID, see if that cures the Grub error 17, and if not, try changing the access mode to "LBA". Let me know if that works or not.

---

### Post by russet_wolf on 2009-03-02
I was having a similar error when I installed Ubuntu to my father's laptop. I'm sorry I cannot provide a link because it has been a few days, but I found a forum where somebody suggested turning off the "quick boot" in BIOS to force the machine to rescan all your drives. I'm too new to all this to even know what RAID is, but I notice nobody has given this suggestion and it worked for me. It's straight forward and the machine hasn't had a GRUB error since. since (even after quickboot was turned back on).

---

### Post by neptor on 2009-03-02
Disabled Raid now I get a disk boot error insert system disk and press enter

---

### Post by neptor on 2009-03-02
I guess I should try a new install.

---

### Post by neptor on 2009-03-02
I guess by quick boot you mean the power on self test. Thanks. Tried it, but no cigar.

---

### Post by neptor on 2009-03-02
Can I reformat my drive in UBUNTU to get back to sqaure one? It looks real close at this point. I really do appreciate the help!!

---

### Post by russet_wolf on 2009-03-02
I suggest using GParted for reformating, it's a lot nicer to use (I find) than Windows' partition editor. You can access it from the LiveCD by going to System > Administration > Partition editor

---

### Post by caljohnsmith on 2009-03-02
Did you try changing the access mode to "LBA"? If you have to turn RAID back on for your drives to be recognized, you can do that first.

---

### Post by neptor on 2009-03-03
Yep. I did the change with just disabling the RAID controller Non-sys disk. Raid disable with Access mode set to LBA; non-sys disk. Raid enabled and Access Mode set to LBA; Error 17

Previous configed as Raid enabled Access Mode auto; Error 17.

Thanks!

---

### Post by neptor on 2009-03-09
Whiped the drive and reinstalled Windows 2003 and VMware player and installed an appliance of Ubuntu. Runs fine.

---

