---
title: "Triple Booting Windows 7 using Grub"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by ILessThan3Sarah on 2009-01-14
Okay.  So i just installed Windows 7 yesterday, on a third partition.  My first 2 being Ubuntu and Vista.  At first it overwrote my grub setting (which before gave me options to vista and ubuntu), but using an Ubuntu live disk i restored in and managed to get back into Ubuntu.  Now I've been tampering in the Grub menu.lst to try to get it working again, and allow me to boot into all three OS.  (vista, ubuntu, and 7) Here's my current grub menu.lst.  I ADDED the Windows 7 section down below.  Everything else was left the same.  When i try to boot now, Ubuntu works fine, Windows 7 boots when i choose the Vista option, and the Windows 7 option displays an error message. Any ideas on how to fix this? Thanks.

```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67e2b526-201e-474f-8eb2-640402863270 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67e2b526-201e-474f-8eb2-640402863270 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista
root (hd0,1)
chainloader +1
savedefault
makeactive

title Windows 7
root (hd0,2)
chainloader +1
makeactive
```


Oh and my vista partition is /dev/sda2.....Windows 7 is /dev/sda3...Ubuntu is /dev/sda5

---

### Post by Joeb454 on 2009-01-14
Change it to read

```
title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows 7
root (hd0,1)
chainloader +1
makeactive
```

That sounds like your problem.

Grub starts numbering from 0, and from what it looks like, you've installed Vista, Windows 7, Ubuntu. And I assume, in that order?

---

### Post by ILessThan3Sarah on 2009-01-14
My hardrive is set up a little wierd.  I got a fat32 system backup on 1, vista on 2, windows 7 on 3, and then i have my fourth split, so ubuntu is actually on sda5.

Noted up top on first message now =)

---

### Post by ILessThan3Sarah on 2009-01-14
well......it seems like my entire Vista partition has been erased...including the OS..  Don't know how that happened...it appeared to have data in it yesterday, after the Windows 7 installation.  Well atleast i was smart enough to make a full backup in case this happened! Unfortunatly that means hours of reinstalling programs.....o well.  Even still, this doesnt explain the problem.  The Vista section in Grub should not load Windows 7.  When selected in Grub the Windows 7 section displays "missing boot loader". :confused::confused::confused:

---

### Post by caljohnsmith on 2009-01-14
Before you completely reinstall, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by ILessThan3Sarah on 2009-01-15
Sorry for the late reply.  I have not reinstalled Vista yet, however i have transferred over my backup files which i lost onto the second partition.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     4289354     2144646    b  W95 FAT32
/dev/sda2   *     4289355   265234570   130472608    7  HPFS/NTFS
/dev/sda3       265236480   300269567    17516544    7  HPFS/NTFS
/dev/sda4       300270915   312576704     6152895    5  Extended
/dev/sda5       300286980   311195114     5454067+  83  Linux
/dev/sda6       311195178   312576704      690763+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 2 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6A5F-1690" TYPE="vfat" 
/dev/sda2: UUID="D88CBDEB8CBDC3F2" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda3: UUID="58B4BB37B4BB168A" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda5: UUID="67e2b526-201e-474f-8eb2-640402863270" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="50e90cd5-7027-4824-af63-39a118c9e3d8" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

================================== sda2/Boot: ==================================

total 596
drwxrwxrwx 1 root root   4096 2009-01-13 19:20 .
drwxrwxrwx 1 root root   4096 2009-01-15 15:48 ..
-rwxrwxrwx 1 root root  28672 2009-01-15 16:14 BCD
-rwxrwxrwx 1 root root  25600 2009-01-15 15:51 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-13 19:20 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-13 19:20 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-13 19:20 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-13 19:20 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-13 19:20 da-DK
drwxrwxrwx 1 root root      0 2009-01-13 19:20 de-DE
drwxrwxrwx 1 root root      0 2009-01-13 19:20 el-GR
drwxrwxrwx 1 root root      0 2009-01-13 19:20 en-US
drwxrwxrwx 1 root root      0 2009-01-13 19:20 es-ES
drwxrwxrwx 1 root root      0 2009-01-13 19:20 fi-FI
drwxrwxrwx 1 root root   4096 2009-01-13 19:20 Fonts
drwxrwxrwx 1 root root      0 2009-01-13 19:20 fr-FR
drwxrwxrwx 1 root root      0 2009-01-13 19:20 hu-HU
drwxrwxrwx 1 root root      0 2009-01-13 19:20 it-IT
drwxrwxrwx 1 root root      0 2009-01-13 19:20 ja-JP
drwxrwxrwx 1 root root      0 2009-01-13 19:20 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-12 23:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-13 19:20 nb-NO
drwxrwxrwx 1 root root      0 2009-01-13 19:20 nl-NL
drwxrwxrwx 1 root root      0 2009-01-13 19:20 pl-PL
drwxrwxrwx 1 root root      0 2009-01-13 19:20 pt-BR
drwxrwxrwx 1 root root      0 2009-01-13 19:20 pt-PT
drwxrwxrwx 1 root root      0 2009-01-13 19:20 ru-RU
drwxrwxrwx 1 root root      0 2009-01-13 19:20 sv-SE
drwxrwxrwx 1 root root      0 2009-01-13 19:20 tr-TR
drwxrwxrwx 1 root root      0 2009-01-13 19:20 zh-CN
drwxrwxrwx 1 root root      0 2009-01-13 19:20 zh-HK
drwxrwxrwx 1 root root      0 2009-01-13 19:20 zh-TW

=========================== sda5/boot/grub/menu.lst: ===========================

default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67e2b526-201e-474f-8eb2-640402863270 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=67e2b526-201e-474f-8eb2-640402863270 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista
root (hd0,1)
chainloader +1
savedefault
makeactive

title Windows 7
root (hd0,2)
chainloader +1
makeactive

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=67e2b526-201e-474f-8eb2-640402863270 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=50e90cd5-7027-4824-af63-39a118c9e3d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 37552
drwxr-xr-x  3 root root    4096 2008-07-24 22:07 .
drwxr-xr-x 21 root root    4096 2009-01-13 09:55 ..
-rw-r--r--  1 root root  422607 2008-04-10 09:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-07-11 22:30 abi-2.6.24-19-generic
-rw-r--r--  1 root root   79964 2008-04-10 09:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2008-07-11 22:30 config-2.6.24-19-generic
drwxr-xr-x  3 root root    4096 2009-01-14 16:44 grub
-rw-r--r--  1 root root 7878047 2008-07-24 18:10 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7879339 2008-07-23 01:08 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7917529 2008-07-24 22:07 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7917532 2008-07-24 18:27 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 09:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 2008-07-11 22:30 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1904248 2008-04-10 09:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921432 2008-07-11 22:30 vmlinuz-2.6.24-19-generic

=============================== sda5/boot/grub: ===============================

total 228
drwxr-xr-x 3 root root   4096 2009-01-14 16:44 .
drwxr-xr-x 3 root root   4096 2008-07-24 22:07 ..
-rw-r--r-- 1 root root    197 2008-07-23 01:09 default
-rw-r--r-- 1 root root     15 2008-07-23 01:09 device.map
-rw-r--r-- 1 root root   8056 2008-07-23 01:09 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-23 01:09 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-07-23 01:09 installed-version
-rw-r--r-- 1 root root   8608 2008-07-23 01:09 jfs_stage1_5
-rw-r--r-- 1 root root    673 2009-01-14 17:47 menu.lst
-rw-r--r-- 1 root root    673 2009-01-14 16:51 menu.lst~
-rw-r--r-- 1 root root    635 2008-08-18 19:14 menu.lst_backup
-rw-r--r-- 1 root root    617 2008-08-18 19:06 menu.lst.backup
-rw-r--r-- 1 root root   5183 2008-07-24 18:27 menu.lst_original
-rw------- 1 root root    674 2009-01-14 16:44 menu.lst.save
-rw-r--r-- 1 root root   7324 2008-07-23 01:09 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-07-23 01:09 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-08-18 19:06 splashimages
-rw-r--r-- 1 root root    512 2008-07-23 01:09 stage1
-rw-r--r-- 1 root root 108356 2008-07-23 01:09 stage2
-rw-r--r-- 1 root root   9276 2008-07-23 01:09 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-15
It looks like the Windows 7 put its boot files in your Vista sda2 partition, but the script was not able to identify your sda2 partition as a valid Vista install; so unfortunately you are probably right about losing Vista. In order to get a better idea, how about posting the output of:
```
sudo mkdir /mnt/sda2 /mnt/sda3
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda3 /mnt/sda3
ls -l /mnt/sda2 /mnt/sda3
```
And we can work from there.

---

### Post by ILessThan3Sarah on 2009-01-15
```
matt@matt-laptop:~$ sudo mkdir /mnt/sda2 /mnt/sda3
mkdir: cannot create directory `/mnt/sda2': File exists
mkdir: cannot create directory `/mnt/sda3': File exists
matt@matt-laptop:~$ sudo mount /dev/sda2 /mnt/sda2
fuse: mount failed: Device or resource busy
matt@matt-laptop:~$ sudo mount /dev/sda3 /mnt/sda3
fuse: mount failed: Device or resource busy
matt@matt-laptop:~$ ls -l /mnt/sda2 /mnt/sda3
/mnt/sda2:
total 396
drwxrwxrwx 1 root root   4096 2009-01-13 19:20 Boot
-rwxrwxrwx 1 root root 377151 2008-12-12 23:03 bootmgr
-rwxrwxrwx 1 root root   8192 2009-01-13 19:20 BOOTSECT.BAK
drwxrwxrwx 1 root root  12288 2009-01-14 20:56 Matt
drwxrwxrwx 1 root root      0 2009-01-13 20:42 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 2009-01-13 19:26 System Volume Information

/mnt/sda3:
total 3958901
-rwxrwxrwx 1 root root         24 2008-10-15 09:11 autoexec.bat
drwxrwxrwx 1 root root          0 2009-01-15 15:55 cabs
-rwxrwxrwx 1 root root         10 2008-10-15 09:11 config.sys
drwxrwxrwx 1 root root          0 2008-12-12 15:58 Documents and Settings
-rwxrwxrwx 1 root root 1602887680 2009-01-15 15:41 hiberfil.sys
-rwxrwxrwx 1 root root 2450984960 2009-01-15 15:41 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-12 23:57 PerfLogs
drwxrwxrwx 1 root root       4096 2009-01-14 21:14 ProgramData
drwxrwxrwx 1 root root      12288 2009-01-15 15:55 Program Files
drwxrwxrwx 1 root root          0 2009-01-13 19:40 Recovery
drwxrwxrwx 1 root root          0 2009-01-13 19:40 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2009-01-15 15:51 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-13 19:40 Users
drwxrwxrwx 1 root root      16384 2009-01-15 15:42 Windows

```

---

### Post by ILessThan3Sarah on 2009-01-15
It seems that those two partitions are mounting correctly.  Maybe i logged out of Windows 7 incorrectly, because so far i have been able to mount and access the data on those two disks. and I cant now.  I'll try relogging in and out of Windows 7.

---

### Post by ILessThan3Sarah on 2009-01-15
I did it again.  This time it mounted, however it says file exists? Where would that be?? Do u want that file?


```
mkdir: cannot create directory `/mnt/sda2': File exists
mkdir: cannot create directory `/mnt/sda3': File exists
matt@matt-laptop:~$ sudo mkdir /mnt/sda2 /mnt/sda3
mkdir: cannot create directory `/mnt/sda2': File exists
mkdir: cannot create directory `/mnt/sda3': File exists
matt@matt-laptop:~$ sudo mount /dev/sda2 /mnt/sda2
matt@matt-laptop:~$ sudo mount /dev/sda3 /mnt/sda3
matt@matt-laptop:~$ ls -l /mnt/sda2 /mnt/sda3
/mnt/sda2:
total 396
drwxrwxrwx 1 root root   4096 2009-01-13 19:20 Boot
-rwxrwxrwx 1 root root 377151 2008-12-12 23:03 bootmgr
-rwxrwxrwx 1 root root   8192 2009-01-13 19:20 BOOTSECT.BAK
drwxrwxrwx 1 root root  12288 2009-01-14 20:56 Matt
drwxrwxrwx 1 root root      0 2009-01-13 20:42 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 2009-01-13 19:26 System Volume Information

/mnt/sda3:
total 3958901
-rwxrwxrwx 1 root root         24 2008-10-15 09:11 autoexec.bat
drwxrwxrwx 1 root root          0 2009-01-15 15:55 cabs
-rwxrwxrwx 1 root root         10 2008-10-15 09:11 config.sys
drwxrwxrwx 1 root root          0 2008-12-12 15:58 Documents and Settings
-rwxrwxrwx 1 root root 1602887680 2009-01-15 16:57 hiberfil.sys
-rwxrwxrwx 1 root root 2450984960 2009-01-15 16:57 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-12 23:57 PerfLogs
drwxrwxrwx 1 root root       4096 2009-01-14 21:14 ProgramData
drwxrwxrwx 1 root root      12288 2009-01-15 15:55 Program Files
drwxrwxrwx 1 root root          0 2009-01-13 19:40 Recovery
drwxrwxrwx 1 root root          0 2009-01-13 19:40 $Recycle.Bin
drwxrwxrwx 1 root root       4096 2009-01-15 15:51 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-13 19:40 Users
drwxrwxrwx 1 root root      16384 2009-01-15 15:42 Windows

```

---

### Post by caljohnsmith on 2009-01-15
It looks like the only thing of interest left in your sda2 Vista partition is the directory called "Matt", so maybe you might want to check if that has any of your personal files. I think you might as well move the Windows 7 boot files in sda2 to the Windows 7 sda3 partition so you can boot Win 7 directly from its own partition. To make that work, you'll also need to run some commands from the Windows 7 Install CD, so make sure you have that handy. How about doing:
```
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda3 /mnt/sda3
sudo mv /mnt/sda2/Boot /mnt/sda2/bootmgr /mnt/sda3
```
If the above mount commands tell you the partitions are all ready mounted on those mount points, that fine. Next, how about booting your Windows 7 Install CD, go to the command line and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
That should list the drive letters of your partitions, so find the drive letter for your Win 7 partition and proceed with:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
And replace "C" with the drive letter of the Win 7 partition. Next reboot, choose Win 7 from your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by ILessThan3Sarah on 2009-01-19
Hey, I'm sorry, caljohnsmith...I'm like swamped with finals right now.  I haven't had time to work on this lately, and probaly won't for the next week or so.  I REALLY REALLY appreciate your time with this, and I'd love to pick this up in a week or so, if that would be cool with you... Thanks so much for the continued effort!! =)

---

### Post by mrbiggbrain on 2009-01-19
boot useing your vista recovery disk, or vista install disk. open the recover console if you can and run 


```
chkdsk /r
```

you can also try running 

```
bootfix 
```

to rewrite your bootloader for vista

or use the boot fixer under repair for windows vista, that shou

or if you can get into windows 7, try adding the windows vista option to the bootloader for windows 7.


NOTE: this will leave windows 7 UNBOOTABLE! (likely)

---

