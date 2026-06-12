---
title: "Ubuntu won't boot!"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Nateck on 2009-01-31
When i try to open up ubuntu it goes to a screen that says: 
grub4DOS 0.4.4 2008-10-27, Memory: 632K/1982M, CodeEnd: 0x42910

any ideas?

---

### Post by caljohnsmith on 2009-01-31
Sounds like you have a Wubi install of Ubuntu, i.e. Ubuntu installed inside of Windows. Is it a fresh install? Also, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by adiwar3 on 2009-02-01
> **caljohnsmith said:**
> Sounds like you have a Wubi install of Ubuntu, i.e. Ubuntu installed inside of Windows. Is it a fresh install? Also, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.


Hi!
 I have the same problem.
 And my ResultTxt. is:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 4. But according to the info from fdisk, 
                       sdb5 starts at sector 872.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x223e960c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,823,654     7,823,592   7 HPFS/NTFS
/dev/sda2           7,823,655     7,871,849        48,195  ef EFI (FAT-12/16/32)


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 8069 MB, 8069677056 bytes
217 heads, 4 sectors/track, 18157 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51de4c2c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 868    15,758,539    15,757,672   f W95 Ext'd (LBA)
/dev/sdb5                 872    15,758,539    15,757,668   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2a1b2a1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            227     3,932,159     3,931,933   b W95 FAT32

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5854DB3354DB131C" TYPE="ntfs" 
/dev/sdb5: UUID="A8A45DD4A45DA59A" TYPE="ntfs" 
/dev/sdc1: UUID="F857-8BF7" TYPE="vfat" 
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
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=c:\wubildr.mbr

[operating systems]

c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft" /noexecute=optin /fastdetect


======================== sdb5/ubuntu/winboot/menu.lst: ========================

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

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


=============================== StdErr Messages: ===============================

/dev/sda2: unknown volume type


Thx man

---

### Post by caljohnsmith on 2009-02-01
**Adiwar3**, I notice from the script results that your Wubi Ubuntu install is on the sdb5 partition while your Windows is on sda1. Since you tried to install Ubuntu to its own drive, is there any particular reason you want it to be a Wubi install instead of a standard install where you could boot Ubuntu independent of Windows? It doesn't look like your Wubi install completed successfully, because you seem to be missing some of the crucial Wubi directories on sdb5. That might be caused by any anti-virus/anti-malware software you could be using in Windows. If you can turn all your anti-virus/anti-malware software off just to install Ubuntu, I think you will have better luck. Or better yet, I would recommend booting the Ubuntu Live CD (the install CD), choose the "try Ubuntu without making changes", and then when you get the Ubuntu desktop, run the Ubuntu installer on the desktop so you can do a standard Ubuntu install to sdb5. It's up to you though, good luck and let me know how it goes.

---

### Post by adiwar3 on 2009-02-01
Sorry for my English.

I have a asus EeePC 900 and I installed ubuntu 8.10 inside windows.

I had done all the configurations for eee pc 900  also crenel 2.6.27-eeepc.

My problem is. I didnt shut down normally the ubuntu.

And now I have this problem boot that tell me  this message:


GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists the possible
completions of a device/filename. ESC at any time exits.]

grub>

when I  push  ESC I see  this :

find /ubuntu/disks/boot/grub/menu.1st
find /ubuntu/install/boot/grub/menu.1st
find /menu.1st
find /boot/grub/menu.1st
commandline
reboot
halt

please help me

And my Results Txt. is:

============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdb
=> Syslinux is installed in the MBR of /dev/sdc

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: __________________________________________________ _______________________

File system:
Boot sector type: Unknown
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''

sdb1: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sdb5: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sdb5 starts
at sector 4. But according to the info from fdisk,
sdb5 starts at sector 872.
Operating System:
Boot files/dirs: /ubuntu/winboot/menu.lst /wubildr.mbr
/ubuntu/winboot/wubildr.mbr

sdc1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive sda: __________________________________________________ ___________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x223e960c

Partition Boot Start End Size Id System

/dev/sda1 * 63 7,823,654 7,823,592 7 HPFS/NTFS
/dev/sda2 7,823,655 7,871,849 48,195 ef EFI (FAT-12/16/32)


Drive sdb: __________________________________________________ ___________________

Disk /dev/sdb: 8069 MB, 8069677056 bytes
217 heads, 4 sectors/track, 18157 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51de4c2c

Partition Boot Start End Size Id System

/dev/sdb1 868 15,758,539 15,757,672 f W95 Ext'd (LBA)
/dev/sdb5 872 15,758,539 15,757,668 7 HPFS/NTFS


Drive sdc: __________________________________________________ ___________________

Disk /dev/sdc: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2a1b2a1

Partition Boot Start End Size Id System

/dev/sdc1 * 227 3,932,159 3,931,933 b W95 FAT32

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: __________________________________________________ __________

/dev/sda1: UUID="5854DB3354DB131C" TYPE="ntfs"
/dev/sdb5: UUID="A8A45DD4A45DA59A" TYPE="ntfs"
/dev/sdc1: UUID="F857-8BF7" TYPE="vfat"
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
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=9 99,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=c:\wubildr.mbr

[operating systems]

c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft" /noexecute=optin /fastdetect


======================== sdb5/ubuntu/winboot/menu.lst: ========================

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

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda2

00000000 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 f6 |................|
*
00000200


=============================== StdErr Messages: ===============================

/dev/sda2: unknown volume type

---

### Post by Nateck on 2009-02-02
ok thanks guys, but i forgot my ubuntu disk at home the last time i came back to school so i will get back to this as soon as i get the disk

---

### Post by Nateck on 2009-02-04
ok, i've got my CD, now...do i reinstall ubuntu or just click the option that says try ubuntu without making any change to your computer?  or is there another option?

---

### Post by Nateck on 2009-02-06
anybody got anything?  anything at all?

---

### Post by caljohnsmith on 2009-02-10
Nateck, to run that script from the Live CD, when you boot the Live CD choose "try Ubuntu without making any changes". Then once you get to the Ubuntu desktop, how about following the directions from post #2. We can work from there.

---

### Post by Nateck on 2009-02-10
when i put that command i got this...


```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

```

---

### Post by Nateck on 2009-02-26
somebody...anybody?

---

### Post by sirishy2k on 2009-10-04
man even i have the same prob.. .I think all this happened because of the disk check in windows .
Here is my results.txt

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb711d865

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   156,299,263   156,297,216   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007ce27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    81,922,047    81,920,000   7 HPFS/NTFS
/dev/sdb2          81,922,048   163,842,047    81,920,000   7 HPFS/NTFS
/dev/sdb3         163,842,048   245,762,047    81,920,000   7 HPFS/NTFS
/dev/sdb4    *    245,762,048   312,578,047    66,816,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="18301A45301A2A70" TYPE="ntfs" 
/dev/sdb1: UUID="52C210D5C210BEE3" TYPE="ntfs" 
/dev/sdb2: UUID="986A08FB6A08D7C0" TYPE="ntfs" 
/dev/sdb3: UUID="6C220141220111AE" TYPE="ntfs" 
/dev/sdb4: UUID="2214F6D914F6AEC3" TYPE="ntfs" 
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


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

---

