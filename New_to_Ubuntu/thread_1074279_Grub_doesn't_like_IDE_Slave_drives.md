---
title: "Grub doesn't like IDE Slave drives?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by JerichoKru on 2009-02-19
Hey all!

As the title says, Grub doesn't work correctly if i try to install something on the IDE slave drive.

I have grub installed on that drive itself(so it doesn't bother any of the other boot loaders), and boot it using the BIOS menu.

I first tried Arch...cause I was curious about it.  Since that didn't work I tried my Xubuntu (8.04.1) CD I had, no go.

It gives me something like this: ```
"Error 15"
"Unable to find volume" 
```
I think it's #15.

I know for sure there is nothing wrong with the Xubuntu install disk, since I had installed it on another PC.  My main Ubuntu install (on the IDE master) is fine...except an annoying message about a wrong screen resolution code...hitting space as prompted gets me by it.

Since I wiped that particular disk (and set it up for a linux install), I cant exactly go check.

---

### Post by caljohnsmith on 2009-02-19
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by JerichoKru on 2009-02-19
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/hdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdf

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

hdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #2
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cca5d

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   187,333,964   187,333,902  83 Linux
/dev/hda2         187,333,965   195,366,464     8,032,500   5 Extended
/dev/hda5         187,334,028   195,366,464     8,032,437  82 Linux swap / Solaris


Drive hdb: _____________________________________________________________________

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/hdb1         108,551,205   117,226,304     8,675,100   5 Extended
/dev/hdb5         108,551,268   117,226,304     8,675,037  82 Linux swap / Solaris
/dev/hdb2                  63   108,551,204   108,551,142  83 Linux


Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9e4f6a8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,466,810   254,710,574   234,243,765   6 FAT16
/dev/sda3         254,710,575   488,392,064   233,681,490   7 HPFS/NTFS


Drive sdf: _____________________________________________________________________

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a8af0

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   624,205,574   624,205,512   7 HPFS/NTFS
/dev/sdf2         624,205,575   625,137,344       931,770  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2E503C8616D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="D8303ED7303EBC76" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="E07868137867E72E" LABEL="DATA" TYPE="ntfs" 
/dev/hda1: UUID="fed319d0-4f3a-4950-ac9f-e092ceb42983" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="c77e34ba-4f21-4a15-bc6e-d47b7d7a8a12" TYPE="swap" 
/dev/hdb2: UUID="74e3c9fc-e21a-44a2-abec-1aaa6cdde106" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="d00d76b5-bccb-46ac-81c4-6950b619cc0a" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: UUID="76AC2196AC2151C3" LABEL="FreeAgent Drive" TYPE="ntfs" 

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


=========================== hda1/boot/grub/menu.lst: ===========================

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
color cyan/black white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro

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
# defoptions=splash vga=798 quiet

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro splash vga=798 quiet
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro splash vga=798 quiet
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro splash vga=798 quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows NT/2000/XP
#root		(hd1,0)
#savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=fed319d0-4f3a-4950-ac9f-e092ceb42983 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=c77e34ba-4f21-4a15-bc6e-d47b7d7a8a12 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/ACER ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/PQSERVICE ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== hda1: Location of files loaded by Grub: ===================


  21.4GB: boot/grub/menu.lst
  21.4GB: boot/grub/stage2
  21.3GB: boot/initrd.img-2.6.24-16-generic
  21.4GB: boot/initrd.img-2.6.24-16-generic.bak
  21.3GB: boot/initrd.img-2.6.24-22-generic
  21.3GB: boot/initrd.img-2.6.24-22-generic.bak
  21.3GB: boot/initrd.img-2.6.24-23-generic
  21.3GB: boot/initrd.img-2.6.24-23-generic.bak
  21.4GB: boot/vmlinuz-2.6.24-16-generic
  21.4GB: boot/vmlinuz-2.6.24-22-generic
  21.4GB: boot/vmlinuz-2.6.24-23-generic
  21.3GB: initrd.img
  21.3GB: initrd.img.old
  21.4GB: vmlinuz
  21.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hdb5

00000000  06 a5 9d 17 36 4e b5 de  be 05 4c 06 bb e9 a5 53  |....6N....L....S|
00000010  29 bb c0 bf 42 6a da 99  9b a6 08 5a fe ab ed a6  |)...Bj.....Z....|
00000020  42 20 ed f6 d6 ed 67 45  f2 36 e1 c3 68 17 ca ba  |B ....gE.6..h...|
00000030  a5 85 23 92 aa e4 b6 e7  ba 94 62 2a 4f bd b7 cd  |..#.......b*O...|
00000040  2a 37 c9 a7 a0 29 53 43  49 d4 09 4e 69 a4 43 77  |*7...)SCI..Ni.Cw|
00000050  24 d3 ed 6a d2 74 d3 a9  6a ae dc c7 5a 46 96 7c  |$..j.t..j...ZF.||
00000060  79 ec aa 85 28 5b e1 0d  70 22 16 c0 8f 21 3f 8d  |y...([..p"...!?.|
00000070  c5 0d 60 98 f2 b9 57 8a  8c 91 ed 32 e0 d9 e9 ad  |..`...W....2....|
00000080  cf 60 a1 65 71 30 ea a0  e3 5c e1 e9 da 06 41 10  |.`.eq0...\....A.|
00000090  b8 24 c2 06 b4 c9 50 2f  19 74 d5 ee 00 a8 8e fc  |.$....P/.t......|
000000a0  d4 3c 42 cf 29 62 72 1b  94 4d 08 38 fc e0 95 12  |.<B.)br..M.8....|
000000b0  4a f1 e0 0e d4 32 52 c7  65 e1 03 59 9e 20 68 68  |J....2R.e..Y. hh|
000000c0  0b 77 1a 7d 1e 40 e1 ff  c4 c0 3e ff 59 74 10 7a  |.w.}.@....>.Yt.z|
000000d0  8a 8a d0 40 9a 5a 4f 4a  08 55 56 e3 22 26 49 6e  |...@.ZOJ.UV."&In|
000000e0  13 e5 ee 5f 30 1a 99 d3  9a 6a a8 be ae c4 a8 a7  |..._0....j......|
000000f0  7f aa 19 36 ae 23 ab 76  a6 ac 44 d6 12 3a 80 21  |...6.#.v..D..:.!|
00000100  dc 34 c8 5c db 7c b9 ee  e8 70 da bf 4b 5d 73 e7  |.4.\.|...p..K]s.|
00000110  ea 9c da b0 49 2b f5 6f  1f d2 ac ba 67 a3 a9 6e  |....I+.o....g..n|
00000120  b6 b1 0b 7c 0a dd 3f 79  21 d5 d1 ee a2 87 77 ba  |...|..?y!.....w.|
00000130  c3 94 b5 d4 c2 7b 6d 74  2a 50 9f be 7e e6 c2 55  |.....{mt*P..~..U|
00000140  6f 5d 91 74 fa c3 f2 15  de ac 49 f1 27 fa a3 2c  |o].t......I.'..,|
00000150  42 e2 da f7 4a a0 af 57  61 1b ab a6 dd 74 7e 71  |B...J..Wa....t~q|
00000160  fc 25 36 e0 da 90 a9 0c  2a 6e 61 d6 ad 4e 22 47  |.%6.....*na..N"G|
00000170  4a a9 2b 86 f2 02 5a cc  16 90 36 15 7a 36 1b 38  |J.+...Z...6.z6.8|
00000180  8e 9b 7b ea 30 d3 6c 72  86 c8 6d 10 dd 08 7e f9  |..{.0.lr..m...~.|
00000190  ec 87 15 d7 aa 4c 45 ec  35 f4 95 3e 5e a6 b4 29  |.....LE.5..>^..)|
000001a0  d0 9f d5 89 5d 2e ee ac  24 ea fa 66 07 54 6b be  |....]...$..f.Tk.|
000001b0  dd 0e 8c 32 73 d9 c0 54  f5 f5 84 c7 2c 41 a4 bd  |...2s..T....,A..|
000001c0  e6 ba e4 54 d2 ae bd fc  27 ce 54 5a e1 ad 2b e8  |...T....'.TZ..+.|
000001d0  74 62 a0 ab c6 2e f9 7f  3b 66 cd 9b 36 6c d9 00  |tb......;f..6l..|
000001e0  e2 0e ff dd 3f a3 2b 4f  3a 1e c7 cd eb 61 50 34  |....?.+O:....aP4|
000001f0  ac 9c 98 0c f6 c9 46 9b  39 aa df 5f 29 b4 55 e1  |......F.9.._).U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

It doesn't see the second install cause it's gone already...but it's pre-formatted for re-install.

The drive in question is "sdb", aka the 60.0GB one.

---

### Post by baracuda68 on 2009-02-20
This may sound goofy, but try having the drive(s) set to "cable-select" instead of "slave".
I've read somewhere online that this solves some issues.

---

### Post by caljohnsmith on 2009-02-20
So when you try to install Kubuntu, at what point does it give you a "Error 15: Unable to find volume"? Can you give some more details about the problem installing Kubuntu? Currently your hdb drive doesn't have any OS installed to it, so booting it would certainly give you a Grub error.

---

### Post by JerichoKru on 2009-02-20
> **caljohnsmith said:**
> So when you try to install Kubuntu, at what point does it give you a "Error 15: Unable to find volume"? Can you give some more details about the problem installing Kubuntu? Currently your hdb drive doesn't have any OS installed to it, so booting it would certainly give you a Grub error.
> **JerichoKru said:**
> 
It doesn't see the second install cause it's gone already...but it's pre-formatted for re-install.

Does that answer your first question?  It's **Xubuntu**, btw(Arch Linux did the same).  I will attempt a re-install, if it still doesn't work, I'll try the cable select.

---

### Post by JerichoKru on 2009-02-20
Update: Exact error is as such:
```
Error code 15:  File not found
```

I will now try cable select, if that fails, I'll switch the HDD to the master.

---

### Post by Kellemora on 2009-02-20
Hi JK

When I first started using Ubuntu back in September, nearly all of our machines here had 3 and 4 IDE hard drives in them, and each contained specific data required by each workstation.

I did have a little trouble with drives 3 and 4 on some machines, meaning I had to access them by IP number to the computer.  But they did work.

In my case, rather than setting them to cable select, which didn't work on some of the older drives anyhow.  I had to make sure they were set up as Primary Master and Primary Slave, Secondary master and Secondary slave.

Even now that I'm running a data file server and don't have to look at each computer anymore, we have trouble getting shares to show in nautilus, sometimes they do, sometimes they don't, but we CAN still get to them in nautilus using their actual IP numbers.

I think one of the keys to getting something to show is you MUST have something shared or you don't see it at all.  We chose NOT to share entire drives, just certain main folders on each!  That worked out pretty well for us.  Also, never PUTTING a file onto a drive not in your own machine, if we need to move files we FETCHED them from the computer they were on to the computer we were at, this preserved and fixed all the permission problems we were having.  Now the Data File Server is Full Access to everyone in the smbusers list, so everything works just fine.

Good Luck

TTUL
Gary

---

### Post by JerichoKru on 2009-02-20
I got it to install correctly when I switched the drives(Master <-> Slave).


Would this be considered a bug in GRUB?  Something else?  Not at all?

---

