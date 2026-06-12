---
title: "Ubuntu 9.04 installation issues"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by kaboose72 on 2009-05-02
Hi

I would like to create a dual booting system with Windows XP.  The system is made up of 4 harddrives (As seen by BIOS):

SATA1 - 200GB Windows (primary OS)
SATA2 - 330GB Windows files
SATA3 - 1TB Windows Files
SATA4 - 80GB Ubuntu installation

Installation was successfull and Ubuntu was installed to SATA4.  However, after restarting, Windows would still boot up as normal with no option to select between OS's.

I also tried booting directly hard drive (SATA4) and I encountered the following error:

Grub 1.5 loading

Error 17...

After reading around and doing a little bit of investigation it seems as if Grub has not numbered the hard  in the same order as the BIOS.  Instead they are identified as:

sda -> SATA3
sdb -> SATA2
sdc -> SATA1
sdd -> SATA4

This is confirmed on the partion GUI when running the OS installation procedure again.

Is re-ordering the harddrives the best course of action to solve this problem?  If so how do would you go about it?

Thanks

(Sorry about the length of the post)

---

### Post by DustyMP on 2009-05-02
First off check your BIOS and make sure the drive with Linux is first in the boot order. If the Windows drive is first it doesn't matter what order Linux lists them.

---

### Post by kaboose72 on 2009-05-02
> **DustyMP said:**
> First off check your BIOS and make sure the drive with Linux is first in the boot order. If the Windows drive is first it doesn't matter what order Linux lists them.


Just tried this and the system attempts to boot Ubuntu however the following error message below is met (same as before):

GRUB Loading Stage 15


GRUB Loading, please wait....
Error 17

---

### Post by DustyMP on 2009-05-02
I read back through your original post and saw saw the error code, sorry I missed it the first time :oops:

Error 17 is GRUB speak for it cannot mount the partition. Usually it's a sign the drive is corrupted. Try following the link below to make UBCD and you can test its integrity with the tools.

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

### Post by kaboose72 on 2009-05-02
I'll let you know how it goes, cheers for the help! :)

---

### Post by caljohnsmith on 2009-05-02
Actually your partitions are probably just fine, you can get a Grub error 17 if Grub attempts to mount the wrong partition (like an NTFS partition for example). In order to get a better idea of the true cause of your Grub error 17 and how to fix it, how about downloading the **Boot Info Script** to your Ubuntu desktop (can be your Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Cheers,
John

---

### Post by kaboose72 on 2009-05-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b5a53f8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed2bd778

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   150,288,074   150,288,012  83 Linux
/dev/sdb2         150,288,075   156,296,384     6,008,310   5 Extended
/dev/sdb5         150,288,138   156,296,384     6,008,247  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd88bd88

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   390,700,799   390,700,737   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.0 GB, 320069031424 bytes
16 heads, 63 sectors/track, 620173 cylinders, total 625134827 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0881b0b9

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   625,134,383   625,134,321   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="160470F90470DD65" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb1: UUID="5299ed67-1a6b-44e4-a3ea-99056d2e172f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="956b73f0-258a-4da8-884e-f9daa5ed1dad" 
/dev/sdc1: UUID="68A4CAE1A4CAB13C" TYPE="ntfs" 
/dev/sdd1: UUID="04700D09700D0362" LABEL="Local Disk" TYPE="ntfs" 

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


=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=5299ed67-1a6b-44e4-a3ea-99056d2e172f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5299ed67-1a6b-44e4-a3ea-99056d2e172f

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5299ed67-1a6b-44e4-a3ea-99056d2e172f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5299ed67-1a6b-44e4-a3ea-99056d2e172f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5299ed67-1a6b-44e4-a3ea-99056d2e172f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5299ed67-1a6b-44e4-a3ea-99056d2e172f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5299ed67-1a6b-44e4-a3ea-99056d2e172f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5299ed67-1a6b-44e4-a3ea-99056d2e172f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=956b73f0-258a-4da8-884e-f9daa5ed1dad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  48.6GB: boot/grub/menu.lst
  48.6GB: boot/grub/stage2
  48.6GB: boot/initrd.img-2.6.28-11-generic
  48.7GB: boot/vmlinuz-2.6.28-11-generic
  48.6GB: initrd.img
  48.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  b9 b0 81 08 00 00 80 01  |................|
000001c0  01 00 07 0f ff ff 3f 00  00 00 f1 ca 42 25 00 00  |......?.....B%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```This is the output file as requested in the previous post hope this helps. BTW just to confirm I did test the hard drive and no faults were found :)

---

### Post by caljohnsmith on 2009-05-03
According to the results of the Boot Info Script, it looks like you definitely have an issue with Grub trying to mount the wrong partition when Grub tries to load its boot files on start up. Can you go into your BIOS and change the boot order so your Ubuntu 80 GB sdb drive boots first? If so, that is the most ideal solution, because then you could re-install Grub to the MBR (Master Boot Record) of your sdb drive and you should be able to boot Ubuntu just fine after that. And you should be able to boot Windows from your Grub menu too, but we might have to tweak your Windows entry in Grub's menu.lst file for it to work (it might work without any tweaking though, it all depends on the boot order of your drives). 

So if you can set your sdb drive to boot first in your BIOS boot order, you can reinstall Grub to its MBR with:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then if you boot the Ubuntu sdb drive on start up, you should be able to boot into Ubuntu without any problems from Grub. Let me know how that goes or if you run into problems, and we can work on booting your Windows drive from Grub (or it may all ready work) after you get Ubuntu booting OK. 

Cheers,
John

---

### Post by kaboose72 on 2009-05-03
Unfortunately when swapping the boot order in the Bios (Sdb being moved to the top of the list) the Grub loading stage 1.5 error 17 appears again.  

Would it be worth re-installing Ubuntu with the revised hard drive order in the Bios to see if this makes any difference???

---

### Post by caljohnsmith on 2009-05-03
> **kaboose72 said:**
> 
Would it be worth re-installing Ubuntu with the revised hard drive order in the Bios to see if this makes any difference???
Reinstalling Ubuntu is usually not the most efficient way to try and fix Grub problems, because the Ubuntu installer uses the same Grub commands that are available to us and that we are using. When you ran the Grub commands from my last post, did they say they were successful? How about doing the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
That will restore a Windows MBR to your sda drive, so if you reboot and get a "NTLDR missing" error rather than a Grub error 17, that would mean your BIOS is still booting the sda drive before the sdb drive on start up. Please let me know if that happens, or if you still get the Grub error 17 even after running the above commands.

John

---

### Post by kaboose72 on 2009-05-03
Sorry I miss read your last post.  After entering the commands correctly this time (i.e sudo grub >> root (hd1,0)...)  Ubuntu does now boot correctly from startup and as you expected an option for using my Windows installation is also available; this does not work however.

Any ideas on possible changes to the menu.lst file???

Thanks for all the help, its much appreciated.

---

### Post by caljohnsmith on 2009-05-03
Glad to hear you can boot Ubuntu OK now, and about booting Windows, how about first pulling up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Windows entry (near the bottom of that file) with the following two entries:
```
title        Microsoft Windows XP Professional (hd1)
rootnoverify    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title        Microsoft Windows XP Professional (hd3)
rootnoverify    (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1
```
Save, reboot, and try each Windows entry from your Grub menu; one of them should work, but if not, let me know exactly what happens when you choose each one. 

John

---

### Post by kaboose72 on 2009-05-03
Brilliant, the first entry works correctly and everything boots as required.  Thanks for the help getting this to work

---

### Post by caljohnsmith on 2009-05-03
> **kaboose72 said:**
> Brilliant, the first entry works correctly and everything boots as required.  Thanks for the help getting this to work
You're welcome, and I'm glad your dual-boot setup is working OK now. Cheers and enjoy Ubuntu and Windows. :)

John

---

