---
title: "Grub error ( mary xmas ) lol"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by Olyptic on 2010-12-25
i repartitioned HD2 , formatted and installed after that i get this error at boot

```

error: no such device: 639fc667-c39d-4fd8-98b9-09412feca5fd.
grub rescue>

```troubleshooting is fun

i can manually boot into the hard drives but how do i fix grub ?


HD1 ( SATA ) win 7
HD2 ( IDE ) ubuntu

ubuntu 10.10 64 bit
3.4 GHz Quad Core AMD CPU
NVIDIA GeForce GT 220 1GB
4 GB RAM

---

### Post by Olyptic on 2010-12-25
I think i have 2 copys of grub.
When i manually boot to the second hard drive witch ubuntu is on i see the grub menu then, but i still get the error at boot

---

### Post by Quackers on 2010-12-25
If you have a look in /etc/fstab you may find that it is looking for the UUID quoted in the error message. Replace that with the correct UUID for your new partition and run sudo update-grub might fix it.

---

### Post by Olyptic on 2010-12-25
> **Quackers said:**
> If you have a look in /etc/fstab you may find that it is looking for the UUID quoted in the error message. Replace that with the correct UUID for your new partition and run sudo update-grub might fix it.

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c1648b83-547f-4e26-b66f-dfcf8b36adf0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2fb7f5ff-9d43-4c9c-b0e7-3a3a230c7219 none            swap    sw              0       0

```

ok what do i do i have ubantu on /dev/sdb1

---

### Post by amjjawad on 2010-12-25
> **Olyptic said:**
> im new


I suggest to start reading here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Quackers on 2010-12-25
To edit the file in a terminal use
```
sudo gedit /etc/fstab
```
then have a look to see if the UUID in the grub error message is mentioned in that file. If it refers to say, / root partition and you now have a different /root partition with a different UUID, just edit the old one out and put the new one in there.
To find the new one you can install Gparted through synaptic package manager and then open it up (System > Admin > Gparted) and after it has scanned your hard drive it will give a list of all the partitions. Right-click on the /root partiton (if that's the one mentioned in the error message) and select properties.
The UUID will be in those properties. Put the new one in fstab then save the file and then quit it.

Then in the terminal run ```
sudo update-grub
```
and hopefully you can boot normally.

---

### Post by wilee-nilee on 2010-12-25
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between. This can be run from a installed Ubuntu installation as well.

Post this script and identify if you have any install or recovery cd/dvd for the MS. Do you also have a live cd/thumb of the Ubuntu install?

---

### Post by Quackers on 2010-12-25
As willee-nilee suggests, if you post the boot script output it will confirm things.
I suspect grub is looking for the UUID 639fc667-c39d-4fd8-98b9-09412feca5fd
which is likely to be your new / partition.  But fstab lists the / partition as
UUID c1648b83-547f-4e26-b66f-dfcf8b36adf0, so it can't find the new one.
If you change the numbers over in fstab you should be ok.

Merry Christmas wilee-nilee :-)

---

### Post by wilee-nilee on 2010-12-25
> **Quackers said:**
> As willee-nilee suggests, if you post the boot script output it will confirm things.
I suspect grub is looking for the UUID 639fc667-c39d-4fd8-98b9-09412feca5fd
which is likely to be your new / partition.  But fstab lists the / partition as
UUID c1648b83-547f-4e26-b66f-dfcf8b36adf0, so it can't find the new one.
If you change the numbers over in fstab you should be ok.

Merry Christmas wilee-nilee :-)

Merry Christmas as well. 

I noticed the no matching UUID, hopefully we can see the script sounds like a basic fixable situation.

---

### Post by Quackers on 2010-12-25
Yes, I had to do this fix after deleting a partiton one time :-)

---

### Post by Olyptic on 2010-12-25
i used Dban boot and nuke to zero out the hard dive windows is not on but i still get that error.
i didnt get a chance yet to do the rest but i have some options to ask.

i cant get into windows. im using ubuntu LiveCD

i have widows 7 on the other hard drive with a back up partition so i could format windows easy.

a ) should i format windows 7 ? will i then be able to boot into windows?
b ) should i install linux again first ? im going to put linux on again any way theres no rush for linux since im a gamer
c ) ?

---

### Post by amjjawad on 2010-12-26
> **Olyptic said:**
> i used Dban boot and nuke to zero out the hard dive windows is not on but i still get that error.
i didnt get a chance yet to do the rest but i have some options to ask.

i cant get into windows. im using ubuntu LiveCD

i have widows 7 on the other hard drive with a back up partition so i could format windows easy.

a ) should i format windows 7 ? will i then be able to boot into windows?
b ) should i install linux again first ? im going to put linux on again any way theres no rush for linux since im a gamer
c ) ?

You could a lot before you think to format and install again.

1) Please post the result of Boot Script as [Wilee suggested in post#7]("http://ubuntuforums.org/showpost.php?p=10277754&postcount=7").

2) I'd also recommend to check MD5SUM for your downloaded iso before creating a LiveCD/USB. On my signature (step1), there's howto check md5sum.

3) If you want a working OS, you could restore MBR to boot Windows and then either re-install Ubuntu or just re-install GRUB2, it depends on what issue do you really have. However, it's better to go back to the first suggestion and try the boot script.

4) If you don't need your data and willing to format the whole thing, then that's another story.

---

### Post by Olyptic on 2010-12-26
im on the ubuntu LiveCD and i have the windows 7 cd and there working fine and have been check MD5SUM

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848    84,174,847    83,968,000   7 HPFS/NTFS
/dev/sdb3          84,174,848   625,139,711   540,964,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        DACC62EACC62BFFD                       ntfs       System Reserved               
/dev/sdb2        C6886A89886A77B7                       ntfs                                     
/dev/sdb3        2EFE4181FE414277                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/2EFE4181FE414277  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


```

---

### Post by amjjawad on 2010-12-26
> **Olyptic said:**
> im on the ubuntu LiveCD and i have the windows 7 cd and there working fine and have been check MD5SUM

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => **[SIZE=3][COLOR=Red]No boot loader is installed in the MBR of /dev/sda[/COLOR][/SIZE]**
 => [B][COLOR=Red]Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.[/COLOR][/B]

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

**[COLOR=Red] Invalid MBR Signature found[/COLOR]**


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848    84,174,847    83,968,000   7 HPFS/NTFS
/dev/sdb3          84,174,848   625,139,711   540,964,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        DACC62EACC62BFFD                       ntfs       System Reserved               
/dev/sdb2        C6886A89886A77B7                       ntfs                                     
/dev/sdb3        2EFE4181FE414277                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/2EFE4181FE414277  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


```

Ok, first thing first, Ubuntu is NOT installed on your system.
This is what the result of the boot script says.

Second of all, what do you have on sda? is it the HDD where you want to install Ubuntu on?


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


```

On sdb where Windows is installed, you have 3 primary partitions. If you want to install Ubuntu there, you need to create an extended partition and inside that partition, you need to create logical partitions.
However, I don't think you can unless you resize your current partitions.

If you want to install Ubuntu on sda then try again as there's no installation there.
I guess you said something about Nuke disk or something writing? it's kind of Low Level Format if I'm not mistaken (I read it somewhere) and it means there's NO active or valid partition table on sda.

You need to create one, start partitioning and install.

On my signature, there's a guide of HOWTO Install Ubuntu on a Dual-Boot System if you have two HDDs.

---

### Post by amjjawad on 2010-12-26
As of now, if you want at least a working OS, you need to restore the MBR (sdb) so that your PC will boot into Windows. Then, you can fix the other issues.

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by Olyptic on 2010-12-26
i found this post, it worked and it was easy

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

> 
[SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7](http://neosmart.net/blog/2009/windows-7-system-repair-discs/).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

---

### Post by amjjawad on 2010-12-26
Great, good job :)

Let us know if you need any thing else :)

---

### Post by Olyptic on 2010-12-27
> **amjjawad said:**
> Great, good job :)

Let us know if you need any thing else :)

:D thank you all for your help

---

