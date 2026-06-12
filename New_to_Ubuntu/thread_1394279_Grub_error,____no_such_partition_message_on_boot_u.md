---
title: "Grub error,    no such partition message on boot up"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by shaunfromthewildwoods on 2010-01-30
getting this message on bootup after trying to use live cd to resize some partitions,  the live cd didn't work,  restarted without live cd and get this error message,  

dual booting with macbook,  mac os x still boots fine,  

can anyone walk me through the steps to fix this? or reinstall grub?

---

### Post by shaunfromthewildwoods on 2010-01-30
am i not providing enough information?

---

### Post by theozzlives on 2010-01-30
Do you know if your using GRUB2 or GRUB Legacy? If not what version of Ubuntu you running?

---

### Post by shaunfromthewildwoods on 2010-01-30
believe it says boot from legacy os, from reflt,  9.10 Karmic Koala

---

### Post by theozzlives on 2010-01-30
Karmic uses GRUB2 if you did a fresh install, do you know what partition your GRUB is on (ie: sda1)?

---

### Post by shaunfromthewildwoods on 2010-01-30
this happened after deleting a partition to create more space,  i have no idea what partition grub is on

---

### Post by theozzlives on 2010-01-30
post the output of```
sudo fdisk -l
```

---

### Post by shaunfromthewildwoods on 2010-01-30
fdisk invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK  Change partition table
           fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
           fdisk -s PARTITION  Give partition size9s) in blocks
           fdisk -v                   Give fdisk version

Here DISk is something like /dev/hdb or /dev/sda
and PARTITIon is something like /dev/hda7

-u: give Start and End in sector (instead of cylinder) units
-b: 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by theozzlives on 2010-01-30
no, that's a small L not a 1

---

### Post by drs305 on 2010-01-30
Running this boot info script and posting the RESULTS.txt contents will tell us what we need to know to fix your system. You can run it from the LiveCD. Please post the contents within 'code tags' (use the # symbol in the menu).

Corrected Link Address:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by shaunfromthewildwoods on 2010-01-30
sorry, 

WARNING: GPT (GUID partition Table) detected on '/dev/sda'!~The util fdisk doesn't support GPT. use GNU parted.

Disk /dev/sda: 500.1 GB 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

  Device Boot   Start          End         Blocks    Id     System
/dev/sda1        52078       52078        977       ef     EFI (FAT -12/16/32)
/dev/sda2   *     26        47527  381550592     af      HFS     /HFS+
/dev/sda3       47543     48919    11049738+   b       W95 FAT32
/dev/sda4       54012       54012   977             0        Empty

Partition table entries are not in disk order

---

### Post by meierfra. on 2010-01-30
drs305 accidentally gave you the wrong link for the boot info script. Here is the correct one:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by theozzlives on 2010-01-30
K, run the bootinfo script as posted above, you shouldn't have an HFS partition. I wanna see more.

---

### Post by shaunfromthewildwoods on 2010-01-30
trying to get driver for broadcom wireless card,  error trying to activate,  now hardware driver window is frozen,   gonna be a moment

---

### Post by drs305 on 2010-01-30
Thanks meierfra!  You just have too many good links. 

> **meierfra. said:**
> drs305 accidentally gave you the wrong link for the boot info script. Here is the correct one:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by theozzlives on 2010-01-30
> **shaunfromthewildwoods said:**
> trying to get driver for broadcom wireless card,  error trying to activate,  now hardware driver window is frozen,   gonna be a moment

can you get a wired connection? To activate the driver you have to reboot, then the live CD forgets everything.

---

### Post by shaunfromthewildwoods on 2010-01-30
computer just froze trying to start firefox . . .

---

### Post by shaunfromthewildwoods on 2010-01-30
now trying to reboot with live cd just getting blank screen with blinking underscore . . .

---

### Post by theozzlives on 2010-01-30
> **shaunfromthewildwoods said:**
> now trying to reboot with live cd just getting blank screen with blinking underscore . . .

Check to make sure the CD ain't dirty.

---

### Post by shaunfromthewildwoods on 2010-01-30
okay, 3rd time,   activating driver,  screen slowly goes white with bunch of black dots,

I have to go back to  mac for now,  too many essays in school,  sorry,

thanks for your time though

---

### Post by shaunfromthewildwoods on 2010-01-30
had to burn another install cd,  here you go,  

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 919252696 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #11 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1         836,624,099   836,626,052         1,954   0 Empty
/dev/sda2    *        409,640   763,510,823   763,101,184  af HFS
/dev/sda3         763,774,976   785,874,452    22,099,477   b W95 FAT32
/dev/sda4         867,687,616   867,689,569         1,954   0 Empty


GUID Partition Table detected,but does not seem to be used.

Partition           Start           End          Size System
/dev/sda1     836,624,099   836,626,052         1,954 Linux or Data
/dev/sda2         409,640   763,510,823   763,101,184 HFS+
/dev/sda3     763,774,976   785,874,452    22,099,477 Linux or Data
/dev/sda4     867,687,616   867,689,569         1,954 Linux or Data
/dev/sda5     867,689,570   890,851,741    23,162,172 Linux or Data
/dev/sda6     972,222,774   976,773,134     4,550,361 Linux Swap
/dev/sda7     836,626,053   864,038,162    27,412,110 Linux or Data
/dev/sda8     813,146,810   836,624,098    23,477,289 Linux or Data
/dev/sda9     865,340,170   867,687,615     2,347,446 Linux Swap
/dev/sda10    919,252,696   919,254,649         1,954 Linux or Data
/dev/sda11    919,254,650   969,940,196    50,685,547 Linux or Data
/dev/sda12    864,038,163   865,340,169     1,302,007 Linux Swap
/dev/sda13    890,851,742   890,853,695         1,954 Bios Boot Partition
/dev/sda14    890,853,696   917,963,071    27,109,376 Linux or Data
/dev/sda15    917,963,072   919,252,695     1,289,624 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda11       e2719bec-4a43-4c22-b7cf-cf635daafc2f   ext4                                     
/dev/sda12       22c11baa-4b3d-4d5c-bec0-a88b402613d5   swap                                     
/dev/sda14       6d92b52c-d554-4c73-bc5e-9317d93d89c0   ext4                                     
/dev/sda15       d502b81c-09e9-4f81-ad4f-58a887f303d0   swap                                     
/dev/sda2        561843e1-912a-3a37-a732-179538368381   hfsplus    Macintosh HD                  
/dev/sda3        302E-13F3                              vfat       BOOTCAMP                      
/dev/sda5        63a4100d-47ed-402e-b5b1-9fa447580908   ext4                                     
/dev/sda6        8d59ffaa-5474-44f2-a7c3-881e5a70a0cc   swap                                     
/dev/sda7        bd51ddd3-e8f8-48ff-a28a-42532b9f02f3   ext4                                     
/dev/sda8        f4142bc2-f4d1-4736-8b6b-8dad646693f9   ext4                                     
/dev/sda9        cc9a1258-aa9b-46ed-960d-fd6387cd6e37   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda14       /target                  ext4       (rw,errors=remount-ro)
/dev             /target/dev              none       (rw,bind)
/dev             /target/dev              none       (rw,bind)
/dev             /target/dev              none       (rw,bind)
/dev             /target/dev              none       (rw,bind)

```

---

### Post by shaunfromthewildwoods on 2010-01-30
can anyone help me out here?

---

### Post by shaunfromthewildwoods on 2010-01-30
bump

---

### Post by shaunfromthewildwoods on 2010-01-30
anyone?

---

### Post by drs305 on 2010-01-31
> **shaunfromthewildwoods said:**
> anyone?

Sorry you aren't getting responses to this thread. Are you using GPT (note the fdisk reference)?  I don't know anything about macbooks or how you tried to set up your partitions. There is a module (part_gpt.mod) that you can load in Grub. Since you didn't mention it previously I'm under the impression that you aren't attempting to use GPT.

It looks like what you really have is an  partition problem. People that can offer assistance may not be reading this thread due to the number of posts and also the "grub" reference in the title.

Although double posting is discouraged, you may want to start a new thread referencing the partition table and not specifically Grub. I'd include the RESULTS.txt output and the fdisk error message in any new thread.

---

### Post by jpdamigaman on 2010-01-31
HI I have u tried super grub disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I can be use to boot linux until u get grub reinstalled

i used to use it to fix grub but with grub 2 its not working so well!

---

