---
title: "Problem booting"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Mandingus on 2011-02-16
Hello, two weeks ago when booting normally I found myself with this messege:
 
"mount: mounting /dev on /root/dev failed: No such file or directory
 mount: mounting /sys on /root/sys failed: No such file or directory
 mount: mounting /proc on /root/proc failed: No such file or directory
 Target filesystem doesn't have /sbin/init.
 No init found. Try passing init= bootarg."
 
and then I'm in a sort of Terminal where it says "(inittramfs)" where I can write.
 
I have seen in many forums but I did not understand many things.
I´ve tried with the live-on CD (USB) but had a similar problem and I can't boot from it nor install a new partition. If this has no solution, please tell me how can i get all the information from the disk so i can reinstall Ubunbtu.
Note: Windows runs normally.
 
Thanks, Mariano

---

### Post by Rubi1200 on 2011-02-17
Hi and welcome to the forums :-)

Have you tried booting the computer with either Knoppix or Slax?

Both are available here:
[http://distrowatch.com/](http://distrowatch.com/)

If you are able to boot, then run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

---

### Post by jroa on 2011-02-17
I am assuming that you are using Fedora, but it would be nice to know some more detail, like the version that you are trying and the desktop enviroment that you are using.

Al;so, are you using fstab, or when do these messages come up?

---

### Post by Mandingus on 2011-02-17
Thanks for replying.
Rubi: today I'll get those programs.

jroa: I'm using Ubuntu 10.04

---

### Post by Rubi1200 on 2011-02-17
Mandingus,
you can use either Knoppix or Slax as a LiveCD, so you need to burn them to CD.

Your first priority, assuming you can get the computer to boot, is to try and save your data. This means to another hard-drive, USB stick, whatever you can.

Then run the boot script I mentioned and we will see if there is a way to get things up and running again.

Good luck!

---

### Post by Mandingus on 2011-04-30
Hi, i hope you're still there :-P
I've run the script and i think the result atached above is not good for me, ha.

Thanks,
Mandingus.

---

### Post by Rubi1200 on 2011-04-30
Thanks for the results. Okay, so there seems to be a problem with sda5 which I assume is/was the Ubuntu install.

This is what you can try from the LiveCD:

```
 sudo e2fsck -f -y -v /dev/sda5
```

If the command completes without any problems, reboot taking out the CD and hopefully you will be back up and running.

If there are errors, copy them exactly and post them here please.

Good luck!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b20c7bb

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS
/dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS
/dev/sda3          42,149,888   220,407,807   178,257,920   7 HPFS/NTFS
/dev/sda4         220,409,854   488,396,799   267,986,946   5 Extended
/dev/sda5         220,409,856   468,865,023   248,455,168  83 Linux
/dev/sda6         468,867,072   488,396,799    19,529,728  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,646,719    15,638,656   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80D84D23D84D18B4                       ntfs       RECOVERY                      
/dev/sda2        CC04C6B704C6A3B4                       ntfs       SYSTEM                        
/dev/sda3        1E56508D56506813                       ntfs                                     
/dev/sda5        783b4df8-31d3-499c-9d7c-ed52578ae1c0   ext4                                     
/dev/sda6        acf784de-7c6f-4ae2-86aa-0c53769677b6   swap                                     
/dev/sdb1        280D-9EB0                              vfat       MANDINGUS                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=c3956d00,xino=/mnt/live/memory/xino/.aufs.xino,nowarn_perm)
/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda3        /mnt/sda3                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)


=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/initrd.gz
    .2GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file
```

---

### Post by Mandingus on 2011-04-30
Thank you very much man, it worked perfectly.

I'm a linux user again :D

---

### Post by Rubi1200 on 2011-05-01
> **Mandingus said:**
> Thank you very much man, it worked perfectly.

I'm a linux user again :D

Excellent! No problem for the help by the way :-)

---

