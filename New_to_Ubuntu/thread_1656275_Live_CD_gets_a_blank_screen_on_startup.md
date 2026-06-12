---
title: "Live CD gets a blank screen on startup?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Red Raven on 2010-12-30
OK so first of all, this is my computer: [http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02207161&lang=en&cc=us&taskId=101&prodSeriesId=4149939&prodTypeId=321957](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02207161&lang=en&cc=us&taskId=101&prodSeriesId=4149939&prodTypeId=321957)
 
Im very new.. this is my first attemt to install linux. So today i created a Live CD (its actually a DVD) of Ubuntu (the latest version). I started it up, and went into the boot menu. i picked the DVD/CD drive to boot from, and it gave me a blank screen . ive heard it could be the video card or that the cd wasn't verified. Anyone know what to do?

---

### Post by skyzthelimit230 on 2010-12-30
Try making another ISO disc and verify it.

Also, make sure your disc drive can read DVDs.

---

### Post by sparker1 on 2010-12-30
Is the blank screen after installation or won't it boot from the disk?

---

### Post by Red Raven on 2010-12-30
hey sorry got it fixed on the irc. here's the results.txt file guys:
 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   458,958,847   458,549,248   7 HPFS/NTFS
/dev/sda3         458,958,848   488,183,807    29,224,960   7 HPFS/NTFS
/dev/sda4         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86B09AD2B09AC7D7                       ntfs       SYSTEM                        
/dev/sda2        08C469A3C469942A                       ntfs                                     
/dev/sda3        2A3C9D983C9D5F9D                       ntfs       RECOVERY                      
/dev/sda4        FAFE-1D59                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by wilee-nilee on 2010-12-30
Hey Red Raven I have subscribed to this thread so if you need help just post.

nit-wit

---

