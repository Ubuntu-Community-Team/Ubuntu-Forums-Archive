---
title: "winxp partiton missing NEED HELP!!!!"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by junior09 on 2010-11-26
I tried to install Ubuntu along side my winxp (dual boot) using usb install. When I restarted the pc it gave me the option to dual boot but when I selected either os they wouldnt load. I put the usb stick back in to run live so i could mnt the device and back up the data but I got an error message saying that it cannot mnt the device. I need to get windows back up so that I can get the files off please help. Thank you in advance.. These are the results from boot info script


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1994 MB, 1994292736 bytes
64 heads, 32 sectors/track, 1901 cylinders, total 3895103 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     3,885,055     3,885,024   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   296,849,069   296,849,007   7 HPFS/NTFS
/dev/sdb2         296,849,070   305,269,814     8,420,745  1c Hidden W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C42-E580                              vfat       HDDREG                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FA2C24752C242ED7                       ntfs       jEstEr                        
/dev/sdb2        A429-150F                              vfat       HDDRECOVERY                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=============================== StdErr Messages: ===============================

ls: reading directory sdb1/: Input/output error

---

### Post by sandyd on 2010-11-26
```

sudo mount -t ntfs /dev/sdb1 /mnt
nautilus /mnt

```

---

### Post by junior09 on 2010-11-26
Thank you sandy for your quick response. I ran the command you gave and this is what I got

ntfs_mst_post_read_fixup: magic: 0x00300031  size: 4096  usa_ofs: 45  usa_count: 48: Invalid argument
Actual VCN (0x3a003900300020) of index buffer is different from expected VCN (0x1).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by junior09 on 2010-11-26
I fixed the issue I took the hdd out and connected it to an external case and ran chkdsk (drive letter) /f/r

---

