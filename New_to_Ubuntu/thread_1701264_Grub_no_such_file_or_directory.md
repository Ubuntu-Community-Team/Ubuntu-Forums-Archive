---
title: "Grub: no such file or directory"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by fat_denim on 2011-03-06
hi everyone, ubuntu lamer coming in!
i have a grub problem like this "no such file or directory"
got that after trying to install smth kinda ubuntu 11.01 distr called  Ubuntu Go! 11.01 and "application not found" and installer crash
i know, my bad, won't do this again

i tried reinstalling original u10.10 in the same directory with  formating but "installing bootloader failed, select another" and another  directories were unacceptable

tried 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cac2cab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       60801   437176814+   f  W95 Ext'd (LBA)
/dev/sda5            6376       25756   155672525    7  HPFS/NTFS
/dev/sda6           33589       60801   218588391    7  HPFS/NTFS
/dev/sda7           25756       26670     7340032   83  Linux
/dev/sda8           26670       26931     2097152   82  Linux swap / Solaris
/dev/sda9           26931       33588    53475328   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /media/sda7
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /media/sda7
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda7 /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet;  avoiding it.  This software may cause boot or other problems in future.   Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

``` in result i've got a boot message saying something like Grub  v.~~9.32.53.532~~,  few lines about it (cant remember) and a command  line. typing 'help'  worked, but wasn't usefull for me. no boot  selection menu

tried win7 recovering - automatic startup troubleshooting, but failed

SO, all i need is to recover win7 till tomorrow or i'll be dead. no data  on ubuntu doesn't matter (it is already purged, i guess). i'll format  it, split in acronis and try 11.04 later.
please, save my life.

and here is info you might ask for :smile:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,414,374   102,414,312   7 HPFS/NTFS
/dev/sda2         102,414,436   976,768,064   874,353,629   f W95 Ext d (LBA)
/dev/sda5         102,414,438   413,759,487   311,345,050   7 HPFS/NTFS
/dev/sda6         539,591,283   976,768,064   437,176,782   7 HPFS/NTFS
/dev/sda7         413,761,536   428,441,599    14,680,064  83 Linux
/dev/sda8         428,443,648   432,637,951     4,194,304  82 Linux swap / Solaris
/dev/sda9         432,640,000   539,590,655   106,950,656  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        16ACA3A3ACA37BBD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8828895C288949E0                       ntfs                                     
/dev/sda6        E42C34FE2C34CCF4                       ntfs       video                         
/dev/sda7        c5ee0448-d7f9-4234-867e-193c4fccd3ea   ext4                                     
/dev/sda8        8c120bd4-9539-41a6-998e-3b8be0f3971e   swap                                     
/dev/sda9        61a4e9de-bd58-456c-8f6f-945252bffdc8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/sda7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /media/sda7              ext4       (rw)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/core.img

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c5ee0448-d7f9-4234-867e-193c4fccd3ea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=61a4e9de-bd58-456c-8f6f-945252bffdc8 /home           ext4    defaults        0       2
# /media/data was on /dev/sda5 during installation
UUID=8828895C288949E0 /media/data     ntfs    defaults,umask=007,gid=46 0       0
# /media/video was on /dev/sda6 during installation
UUID=E42C34FE2C34CCF4 /media/video    ntfs    defaults,umask=007,gid=46 0       0
# /media/windows was on /dev/sda1 during installation
UUID=16ACA3A3ACA37BBD /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda8 during installation
UUID=8c120bd4-9539-41a6-998e-3b8be0f3971e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 280.9GB: boot/grub/core.img
 277.1GB: boot/initrd.img-2.6.35-22-generic
 281.3GB: boot/vmlinuz-2.6.35-22-generic
 277.1GB: initrd.img
 281.3GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c5ee0448-d7f9-4234-867e-193c4fccd3ea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=61a4e9de-bd58-456c-8f6f-945252bffdc8 /home           ext4    defaults        0       2
# /media/data was on /dev/sda5 during installation
UUID=8828895C288949E0 /media/data     ntfs    defaults,umask=007,gid=46 0       0
# /media/video was on /dev/sda6 during installation
UUID=E42C34FE2C34CCF4 /media/video    ntfs    defaults,umask=007,gid=46 0       0
# /media/windows was on /dev/sda1 during installation
UUID=16ACA3A3ACA37BBD /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda8 during installation
UUID=8c120bd4-9539-41a6-998e-3b8be0f3971e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 216.5GB: boot/grub/core.img
 212.6GB: boot/initrd.img-2.6.35-22-generic
 216.8GB: boot/vmlinuz-2.6.35-22-generic
 212.6GB: initrd.img
 216.8GB: vmlinuz
```

---

### Post by oldfred on 2011-03-06
the 11.04 is still alpha. It should only be installed for testing.

You have installed parts of grub to your windows partition which will cause windows grief. You will have to repair your windows.

sda1: ________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/grldr /grub/core.img
[/COLOR]
Remove the files/folder in red.

The flexnet warning is just that you have installed some Win7 software that uses DRM and hides the info in sector 32.

these look like you copied your NTFS partitions as they say they start at sector 63. NTFS partitions have to have a valid NTFS boot sector. Also Ubuntu cannot install to a NTFS partition unless you are using wubi.
sda5: ______________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at [COLOR=Blue]sector 63[/COLOR].
    Operating System:  
    Boot files/dirs:   

sda6: _________________
    File system:       ntfs
    Boot sector type:  [COLOR=Cyan]Windows XP[/COLOR]
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at [COLOR=Blue]sector 63[/COLOR].
    Operating System:  [COLOR=Red]Ubuntu 10.10[/COLOR]
    Boot files/dirs:   [COLOR=Red]/etc/fstab /boot/grub/core.img[COLOR=Black]

You may have to use testdisk to repair NTFS boot sectors.

To repair win7 in sda1:

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You seem to be missing grub.cfg in sda7 which grub's boot loader in the MBR is looking for.

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd0,7) or sda7
sh:grub>ls (hd0,7)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,7)/vmlinuz root=/dev/sda7
sh:grub>initrd (hd0,7)/initrd.img
sh:grub>boot

If you can then boot ubuntu run this:
sudo update-grub

It will not find windows until you fix the problem of grub files in the windows folder.


[/COLOR][/COLOR]

---

### Post by fat_denim on 2011-03-06
well thanks alot for your help, but i've solved it in another way
i was just reading threads here around and found solution i didnt met in any help guides i've read.
some awsome guy adviced someone to install "lilo" fixing utility. i tried those two commaands, got some warning and error message, rebooted and loaded directly into windows!
than burned ubuntu go onto dvd to fix error and successfully installed it.
im curious why i couldn't find this simple solution (literally two commands in terminal) before.
maybe u should mention this somewhere [here]("http://grub.enbug.org/Manual") or [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
though it doesnt fix grub, it fixes winloader and this could be extremly useful for me to save 6 hours of googling this trouble.

---

### Post by oldfred on 2011-03-06
Glad you got it working.

I have regularly posted lilo for those who want to repair windows and do not need to do other windows repairs. But if you need to do other windows repairs it may be better to run the windows repairs. You should have a windows repair CD as long as you run windows, just like you should have an Ubuntu (or other Linux) repair Cd to repair your Linux system.

Lilo is another boot loader just like grub is a boot loader. It is just that lilo uses the boot flag (just like windows) to jump to the partition boot sector. Grub, grub2, lilo & the standard windows boot loader all chainload to the windows partition to continue the windows boot.

Just for grins, I did a Google search of Ubuntu forums, oldfred & lilo and got 
About 12,900 results  (0.39 seconds)
Obviously I have not posted it that many times.:)

---

