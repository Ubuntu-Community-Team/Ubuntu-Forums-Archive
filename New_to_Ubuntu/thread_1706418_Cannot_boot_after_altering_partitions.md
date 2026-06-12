---
title: "Cannot boot after altering partitions"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by eduardosl on 2011-03-13
I installed Ubuntu through Wubi successfully. By trying to mount the Windows partition (following the steps at [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)) I ended up being unable to boot into Windows, and then when trying to repair the damage I ended up being unable to boot into Ubuntu as well. :(

What should I do?

Any help is appreciated!

--Eduardo

PS--This is what I get when I ran Boot Info Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2             206,848 1,935,429,631 1,935,222,784   7 HPFS/NTFS
/dev/sda3       1,935,430,875 1,953,520,064    18,089,190   5 Extended
/dev/sda5       1,935,430,938 1,953,520,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       53c1341b-ba6b-46e9-9ee0-92490877c340   ext4                                     
/dev/sda2        8E247C74247C60DF                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        53e51f8c-810e-4169-896e-78a9a88ea4a1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by mikewhatever on 2011-03-14
What exactly did you do when trying to repair the damage? Have you deleted partitions? /dev/sda1, perhaps?

---

### Post by eduardosl on 2011-03-14
I think I may have done just that. Am I out of luck?

---

### Post by Rubi1200 on 2011-03-14
Whether this can be easily fixed depends, in part, on what was on sda1. Do you remember by any chance?

Do you have the Windows installation/recovery CD?

In any event, you are missing essential boot files that Windows needs:
```
/bootmgr /Boot/BCD
```As I see it, you have 2 options worth trying:

1. try and fix/restore the Windows bootloader with the Windows recovery CD:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

2. install a basic Windows-like bootloader using the Ubuntu LiveCD:
go to System > Administration > Synaptic > Repositories and make sure universe is checked (enabled).

Then from the terminal (Applications > Accessories):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```Ignore any warnings, we just want lilo in the mbr.

Reboot.

---

