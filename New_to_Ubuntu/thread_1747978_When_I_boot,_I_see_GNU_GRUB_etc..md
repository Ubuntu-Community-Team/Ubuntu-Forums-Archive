---
title: "When I boot, I see GNU GRUB etc."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by reivann on 2011-05-03
When I boot, the GNU GRUB version 1.98+20100804-5ubuntu3 screen appears. I can write commands at " grub> " but if I type, for instance " linux ", it shows, error: no kernel specified. @__@. I'm lost. Please help. X__X.

---

### Post by reivann on 2011-05-03
Anyone? :S

---

### Post by cipherboy_loc on 2011-05-03
Try booting the LiveCD and posting the result of the script (link and instructions in my signature).

Cipherboy

---

### Post by reivann on 2011-05-03
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          39,086,208   156,344,579   117,258,372   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1A69-1E00                              vfat       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img


```

thanks cipherboy :S... uh.. so, what to do from here? :S

---

### Post by cipherboy_loc on 2011-05-03
It looks like you are booting Ubuntu from FAT32 on an 80GB hard drive while the partition is ~111MB? Something doesn't add up. Are you running a Wubi install (though Windows would have been detected)?



CIpherboy

---

### Post by reivann on 2011-05-03
Nope, not wubi. >_<

---

### Post by Quackers on 2011-05-03
Why is grub installed? 
Have you deleted a Linux installation from this system?

---

### Post by reivann on 2011-05-03
I just re-installed Ubuntu and gave all the updates it asked for. I  ran testdisk and was running foremost when a short power outage came. When I restart the computer, there was an error which said 

error: unknown filesystem
grub rescue>

I googled some solutions and followed some instructions [which I forgot]. I think one includes reinstalling grub.

---

### Post by Quackers on 2011-05-03
Ubuntu does not appear to be installed on your system.

---

### Post by reivann on 2011-05-03
Err.. Weird. >__<. Uh.. I also did fsck earlier, and there were alot of errors.

Ugh. Maybe I'll just reinstall it again. Thanks Quakers. 

X__X.

---

### Post by idoitprone on 2011-05-03
To use grub rescue prompt 
[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html)
[https://help.ubuntu.com/community/Grub2#Using CLI to Boot](https://help.ubuntu.com/community/Grub2#Using CLI to Boot)

---

### Post by Quackers on 2011-05-03
You're welcome :-)
Better luck next time then :wink:

---

