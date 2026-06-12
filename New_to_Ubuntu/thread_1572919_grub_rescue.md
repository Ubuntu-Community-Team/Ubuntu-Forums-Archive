---
title: "grub rescue"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by ghostnet623 on 2010-09-11
I have tried at least a dozen times and variations to setup dual boot on my laptop.  My desktop was a snap as it set it up automatically from the setup cd, however my laptop no matter how I install it I get "out of disk" error and grub rescue>  Pulling my hair out here.  What am I doing wrong?   Thank you in advance

---

### Post by -kg- on 2010-09-12
First thing, let's see what partitions already exist on your laptop's hard drive.  Boot to the desktop on the Live CD, open a terminal window (under "Applications/Accessories/Terminal") and copy and paste (if you have Internet access from the Live CD) or type in the following command:

```
sudo fdisk -l
```
(that's a lower case "-L", not a one)

Then post the results here in your next post.  That command will tell us what partitions you have on your hard drive.  I have a feeling that, since you've tried to install Ubuntu multiple times, you have several on it, and that's why you're unable to do any more installations.

When you install automatically for dual boot, the installer automatically shrinks a partition (usually a Windows partition) and creates the required partitions without your guidance.  If you try to install automatically several times, it will shrink a partition and create more instead of using the same partitions again.  The only way you can use partitions that are already created is to use "Manual partitioning", select those partitions, and set them to be formatted and mark the mount points.

Likely, you're going to need to go in with GParted and delete a few of the extraneous partitions before attempting to install again.  If you want to use automatic partitioning options, you'll have to delete all except for your Windows (or other OS) partition(s).

---

### Post by bigpayne69 on 2010-09-12
Are you by chance, using a Toshiba laptop?

---

### Post by ghostnet623 on 2010-09-12
-kg-
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ce4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15447   124077152+   7  HPFS/NTFS
/dev/sda2           15448       30402   120120321    5  Extended
/dev/sda5           15448       29789   115195904   83  Linux
/dev/sda6           29789       30402     4923392   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


and bigpayne69 no it is a dell

Also, I have used gparted each time to kill all partitions and recreate.  I have tried 1 partition to load windows (then let live cd do the rest)
I have tried creating the partitions manually for the swap, ext, logical, and primary each different way nets the same result Grub Rescue

---

### Post by wilee-nilee on 2010-09-12
This link may be helpful with a Dell computer.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

So it seems you have a unbootable laptop, you can reload the MS bootloader back to the MBR to boot windows and look for this Dell Data Safe.

From a install disc booted or a recovery run the highlighted command.
Here is a W7 recovery link as well.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Instructions.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Notice the http link to the W7 forums for instructions on getting to the command line, that parallel the ones given here.

You have not really given us much information and have not posted for almost 23 hrs, so I am just working off what we have here. This will restore the MS bootloader we can put grub back in easily if the Dell program is the problem.

---

### Post by ghostnet623 on 2010-09-12
wilee-nilee
  this is windows xp pro mc same as dell desktop that loaded perfectly.  I do plan to get rid of ms as soon as I can migrate and learn enough of this to work for me.  I own 15 licenses for vista ultimate and win 7 and hate all of them

I can scrub the whole thing and just load Ubuntu and it works just fine, but dual boot it will not


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   248,154,367   248,154,305   7 HPFS/NTFS
/dev/sda2         248,156,158   488,396,799   240,240,642   5 Extended
/dev/sda5         248,156,160   478,547,967   230,391,808  83 Linux
/dev/sda6         478,550,016   488,396,799     9,846,784  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        305E16BA6FFAD716                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43   ext4                                     
/dev/sda6        f359e1d8-7849-403f-827c-56341216a6d4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cbba0ae0-eab6-4ed6-b5c3-f4687d3dfa43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f359e1d8-7849-403f-827c-56341216a6d4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 200.2GB: boot/grub/core.img
 200.2GB: boot/grub/grub.cfg
 200.2GB: boot/initrd.img-2.6.32-24-generic
 200.2GB: boot/vmlinuz-2.6.32-24-generic
 200.2GB: initrd.img
 200.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ca df 23 59 ef e0 97 a5  21 47 74 6b 79 05 a0 f3  |..#Y....!Gtky...|
00000010  a0 f4 a0 2c 90 52 ed 85  a3 86 40 0c ce 97 0a 25  |...,.R....@....%|
00000020  24 bb f5 9f bc 30 a0 7a  16 9b dc 7d 28 10 3c 5d  |$....0.z...}(.<]|
00000030  63 37 e7 ba 51 44 52 c2  d4 13 17 de 27 dd 3d 29  |c7..QDR.....'.=)|
00000040  77 90 2b 62 5d 9e c8 28  9c 59 ea 6b 99 66 ff 12  |w.+b]..(.Y.k.f..|
00000050  64 76 28 3c 97 6e cf 62  2e 94 8e 04 dc 2c 42 28  |dv(<.n.b.....,B(|
00000060  ce 5b 6b ae 0a 09 64 87  84 f2 d0 58 bb da 99 fc  |.[k...d....X....|
00000070  88 15 6d ac 31 e5 24 f9  96 fa bb 86 c8 48 6f f6  |..m.1.$......Ho.|
00000080  3e 76 24 57 a6 82 a9 0d  09 75 75 bc 0b 8f ac 9c  |>v$W.....uu.....|
00000090  05 7a 24 a2 69 26 db 6b  82 a0 e0 49 25 97 85 c7  |.z$.i&.k...I%...|
000000a0  d8 bd 7a 5a 52 08 ce b6  9d eb 12 0a 78 8a 47 30  |..zZR.......x.G0|
000000b0  58 0a 32 78 fb d5 d1 21  21 e1 65 f4 49 24 90 84  |X.2x...!!.e.I$..|
000000c0  f0 4b eb 61 21 4b 6c 6d  89 7f 04 61 bc bd 50 32  |.K.a!Klm...a..P2|
000000d0  5b af 29 14 a8 44 c2 d4  84 86 32 2a 2d 08 da 43  |[.)..D....2*-..C|
000000e0  ca 14 66 b2 26 40 a1 4c  68 68 a5 27 55 62 13 11  |..f.&@.Lhh.'Ub..|
000000f0  10 8b 03 23 03 84 6b 39  c2 ef 1c 29 88 69 b4 d1  |...#..k9...).i..|
00000100  0d 6a 49 65 31 3c a1 09  56 56 42 84 86 ab 16 52  |.jIe1<..VVB....R|
00000110  4c 45 d5 6d 88 a1 a1 14  a4 31 c2 31 0b 03 4e 14  |LE.m.....1.1..N.|
00000120  22 04 f3 88 72 c8 44 24  f3 5a 20 e8 49 a1 36 c9  |"...r.D$.Z .I.6.|
00000130  58 6c 47 50 d6 bf 4c 8a  63 af 0b 02 03 48 70 24  |XlGP..L.c....Hp$|
00000140  85 c4 c8 64 2c b8 32 92  62 1d 36 5a ac 8a 84 fa  |...d,.2.b.6Z....|
00000150  89 48 2a de 44 dd 34 43  ca 1c 0d 0e 04 95 6a 1c  |.H*.D.4C......j.|
00000160  94 a4 32 19 3d 79 59 c0  a0 17 02 95 97 75 89 08  |..2.=yY......u..|
00000170  42 62 99 90 f2 73 69 1c  30 43 ac d2 39 92 09 99  |Bb...si.0C..9...|
00000180  8d f1 e5 27 63 de ef 01  5a cc cd 4b 94 bd 5b 3a  |...'c...Z..K..[:|
00000190  ce f0 15 ac cc d4 b9 4b  d5 b3 ac 6d 2b 54 d2 e2  |.......K...m+T..|
000001a0  14 32 ae 52 ec 3a 46 3a  5c 14 b8 88 02 09 c1 b1  |.2.R.:F:\.......|
000001b0  6b 8b 05 6b 7f a3 40 fc  fc d6 7b 2c c5 71 00 fe  |k..k..@...{,.q..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 bb 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  bb 0d 00 48 96 00 00 00  |...........H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Did not know if you wanted all of this.  I am very new to this and am trying really hard to separate what I am used to with ms.

---

### Post by psusi on 2010-09-12
It could be because your root partition is inside the extended partition instead of being a primary partition.  Instead of creating the partitions with gparted, delete them and let the installer create them.  Just tell it to install to the remaining free space after you get rid of all partitions other than the Windows one.

---

### Post by ghostnet623 on 2010-09-12
psusi  
the partition structure i pasted was letting the cd create everything


I even created the win partition and left the rest unallocated and instructed live cd to use the rest of the free space same outcome

---

### Post by wilee-nilee on 2010-09-12
Generally the bootscript in my signature can give us about everything we need to know, post it in code tags as described if you can.

It being XP I am not sure when the dell data safe stuff started, so it sounds like it probably isn't on there.

---

### Post by oldfred on 2010-09-12
Script looks normal. For whatever reason the grub in the MBR that says it looks in sda5 or search by UUID is not finding the rest of grub in sda5.

Sometimes just reinstalling grub2 to the MBR works.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by ghostnet623 on 2010-09-13
oldfred
 I followed those instructions and still received grub rescue upon reboot

---

### Post by oldfred on 2010-09-13
Lets try the full chroot version and update system while we are at it. Do not copy anything after a # as that is just comment/explanation. Copy each line separately.

kansasnoob' one line version of chroot using sda5 as correct partition
```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

```
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

```sudo dpkg-reconfigure grub-pc

---

