---
title: "grub problem in ubuntu"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by AhdSaid on 2011-08-09
Hi every one 
 Thank you for the great efforts. 
The problem i face now is once i open the ubuntu a black screen appears and a massage appeared of the form is shown as

[ Minimal BASH-like line editing is supported. For the first word, TAB ............. ]
grub > 
 

The file . [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") required in link

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 

is shown below




  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda6 and looks at sector 1843272790 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #6 for /boot/grub/menu.lst.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000976e9

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,248,189   156,248,127  83 Linux
/dev/sda2         156,248,190 1,953,520,064 1,797,271,875   5 Extended
/dev/sda5         156,248,253   167,959,574    11,711,322  82 Linux swap / Solaris
/dev/sda6         167,959,638 1,953,520,064 1,785,560,427  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        92c12379-0ee6-414f-90c0-ce7e5b7c25ca   ext3       
/dev/sda5        3cf4f0ef-3b0e-4802-bb11-c53fb4a25f1e   swap       
/dev/sda6        3c819056-c286-4bd0-a514-dfe080b35a81   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/92c12379-0ee6-414f-90c0-ce7e5b7c25ca ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda6        /media/3c819056-c286-4bd0-a514-dfe080b35a81 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sr0         /cdrom                   iso9660    (rw)


=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/stage2                               2

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in








thanks 
Ahdsaid

---

### Post by Ad1217 on 2011-08-09
I would guess that menu.lst is not configured. if you have a live cd you could boot into it, open up a terminal and type

```
sudo grub-install /dev/*whatever*
```

and check out [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by amjjawad on 2011-08-09
What release of Ubuntu are you using? seems 9.04 or even older because it has GRUB legacy not GRUB2.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

