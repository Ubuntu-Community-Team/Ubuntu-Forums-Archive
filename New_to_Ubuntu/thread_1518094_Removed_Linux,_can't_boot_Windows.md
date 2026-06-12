---
title: "Removed Linux, can't boot Windows"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by rogueofmv on 2010-06-26
So I removed Kubuntu from my MacBook the other day due to lack of use, but the GRUB bootloader stuck behind and still wants to manage my booting into Windows.

Which it can't.

Whenever I select Windows at startup, it brings me to a blank GRUB with the "Minimal BASH-like editing is available..." message and grub> prompt.

I figure this might have something to do with the /etc/grub.d/40_custom file, so I edited it to add bootloader entry for Windows XP Professional:

```
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set 723C5AA03C5A5F63
drivemap -s (hd0) $(root)
chainloader +1
}
```

...but I can't use update-grub from my Live CD. It spits out the error: "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)"
So I tried following some chroot instructions I found somewhere, but I can't get past sudo mount --bind /dev /mnt/dev without the error "mount point /mnt/dev does not exist".

I'm not sure if I'm on the right track. Can anyone help me?
I posted part of this in Apple Users as well, but I figure this might be more of an Absolute Beginner type question.

---

### Post by wilee-nilee on 2010-06-26
You need to reload the MS bootloader to the mbr, if this is not a efi setup.

Post the bootscript in my signature in code tags as described.

---

### Post by rogueofmv on 2010-06-26
> **wilee-nilee said:**
> You need to reload the MS bootloader to the mbr, if this is not a efi setup.

Post the bootscript in my signature in code tags as described.

Here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    350526712 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sda. Stage2 looks on partition #3 for 
    /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   402,800,679   402,391,040  af HFS
/dev/sda3    *    403,062,824   488,397,127    85,334,304   7 HPFS/NTFS


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   402,800,679   402,391,040 HFS+
/dev/sda3     403,062,824   488,397,127    85,334,304 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2860-11F4                              vfat       EFI                           
/dev/sda2        38a904d3-c131-39d2-b5fa-9b76e5bd4f0e   hfsplus    Macintosh HD                  
/dev/sda3        723C5AA03C5A5F63                       ntfs                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda1        /mnt                     vfat       (rw)


================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by wilee-nilee on 2010-06-26
I think that is a efi setup, you should report yourself to the mods to move your thread to the apple forum area, I don't know the fix with this sort of setup but I believe there are some on the forum that due. No matter where the thread is though you will still be on the main posted list.

This is fixable but it just takes the right person who knows how to due it.

Do you have a XP install disc? If you don't here is a link to a legit one for repairs just wait for help.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by rogueofmv on 2010-06-26
Thanks. I guess I'll edit my thread in the Apple section and ask how to restore the Win bootloader.

---

### Post by wilee-nilee on 2010-06-26
> **rogueofmv said:**
> Thanks. I guess I'll edit my thread in the Apple section and ask how to restore the Win bootloader.

It may just be a standard fixmbr from the disc but I would rather have somebody who knows for sure cover it we want everything working. In the future always restore the bootloader of what your keeping first. With Linux it isn't a problem generally but the boot was grub and it shows it to be in the mbr, removing the Kubuntu install doesn't remove grub from or revert the mbr to a MS bootloader.

---

