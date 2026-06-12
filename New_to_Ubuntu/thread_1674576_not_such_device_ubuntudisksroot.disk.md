---
title: "not such device: /ubuntu/disks/root.disk"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Willye on 2011-01-24
Hi friends, i have ubuntu 10.04, i have installed it with wubi, it was working perfectly, the lastest software installed was compiz-extra, suddenly when i powered on the system is appearing the next message: error: not such device: /ubuntu/disks/root.disk
grub>  

what could i do to recover my ubuntu and info in it ????

thanks for your valuable comments

---

### Post by bioterror on 2011-01-24
This might be worth of reading [http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by Willye on 2011-01-24
I have read the link, i have loaded the ubuntu  live-cd, i mounted the device: 
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win 
i try to mount: 
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
it's appearing: /media/win/ubuntu/disks/root.disk: Input/output error

# cd /media/win/ubuntu/disks
# ls -l 
# d??????? ? ? ?     ?         ? disks
...
...

if i try to get into disks "cd disks" is showing: 
cd disks:Input/output error

i cannot to do: cd or rm -r or ls -l <disks>


so, how to repair that directory to edit root.disk ??????

---

### Post by Willye on 2011-01-24
some suggestion ??????

---

### Post by drs305 on 2011-01-24
If the file got corrupted, it's possible running these commands from the LiveCD may fix it:

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win 
sudo fsck /media/win/ubuntu/disks/root.disk

```

---

### Post by Willye on 2011-01-24
> **drs305 said:**
> If the file got corrupted, it's possible running these commands from the LiveCD may fix it:

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win 
sudo fsck /media/win/ubuntu/disks/root.disk

```

fsck does not work
fsck.ext2 Input/output error while trying to open ......
neither:
e2fsck -b 8193 <device> 

i found in other cases: replace the c:\wubildr, i downloaded the file and replaced it, but did not work


what other thing could i do ?

---

### Post by Rubi1200 on 2011-01-24
Hi,
post the results of the boot info script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Willye on 2011-01-25
> **Rubi1200 said:**
> Hi,
post the results of the boot info script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


```
Here the RESULTS.txt
====================
                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr
                       /ubuntu/winboot/wubildr.mbr /wubildr
                       /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,125,039    78,124,977   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        666806DD6806ABBD                       ntfs
/dev/sda: PTTYPE="dos"
               
============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="IBM Client for e-business Windows XP v2.18" /noexecute=alwaysoff /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by Rubi1200 on 2011-01-25
Thanks for the results.

You are missing the root.disk and swap.disk.

If Windows did a chkdsk it may have moved the files to a hidden folder (you need to enable this in folder views) called C:\FOUND.000 (or something similar).

Have a look and if it is there just move it back to the Ubuntu folder on C.

---

### Post by Willye on 2011-01-25
> **Rubi1200 said:**
> Thanks for the results.

You are missing the root.disk and swap.disk.

If Windows did a chkdsk it may have moved the files to a hidden folder (you need to enable this in folder views) called C:\FOUND.000 (or something similar).

Have a look and if it is there just move it back to the Ubuntu folder on C.


```

I have not found hidden or not hidden,  folders or files related with fixed files or lost files or recovered and so on, i searched in all windows system (root* and swap*) did not find nothing, in fact the last time i was working with ubuntu, not windows, i mean previously to the error, windows did not run chkdsk

what can i do now ??? 

```

---

### Post by Rubi1200 on 2011-01-25
Well, if the files are gone then you have little choice but to reinstall.

Just in case I missed anything, wait for some other opinions.

---

### Post by Willye on 2011-01-25
> **Rubi1200 said:**
> Well, if the files are gone then you have little choice but to reinstall.

Just in case I missed anything, wait for some other opinions.


Thanks for your help Ruby, i have a lot of info saved there, but as i see, how complicated is for recover the ubuntu, I won't have another option more that install again,  but i don't want to lost my windows partition and now i don't trust in wubi ......

---

### Post by Rubi1200 on 2011-01-25
Wubi is not the problem, the updates for GRUB breaking Wubi installs is where the problem can be found.

You could try using file recovery software to try and find and recover the data from Wubi. But, to be honest, the chances are not that good.

If you want to help us, please add your voice to the list of those unhappy about this situation:
[http://ubuntuforums.org/showpost.php?p=10357636&postcount=68](http://ubuntuforums.org/showpost.php?p=10357636&postcount=68)

Even though Wubi is installed inside Windows, I don't think I have heard of a situation where a Windows install was affected by this to the extent of data being lost.

In that respect, Wubi is "safe."

I recommend you reinstall Wubi and then avoid this problem by locking the grub-pc and grub-common packages.

---

### Post by Willye on 2011-01-25
I'm Installing ubuntu again with wubi, i'll report the incidence, i tried to recover lost files from windows, but  actually it's very complicated, it's very sad 'cause i have to reinstall all software that i had installed and reconfigure compiz etc etc etc etc, so nothing to do, good luck my friend 

:-({|=:-({|=

---

### Post by neilscrim on 2011-01-25
I had a similar problem and I posted a question about this yesterday:

[http://ubuntuforums.org/showthread.php?t=1674821](http://ubuntuforums.org/showthread.php?t=1674821)

The only way i could recover the boot menu was to install another copy of Vista (or you could use Windows 7) on a different partition. This then rebuilds the mbr (or at least it did for me) and I got my dual boot menu back (XP and Vista).

The only problem is you need another partition to do this so I'm not sure if it would help in your situation.

---

### Post by Willye on 2011-01-25
Thanks nail, but the thing was that root.disk and swap.disk dissapeared mysteriously after an upgrade  of compiz-extra, so i have to install ubuntu again, and i must reinstall  a lot of software and restore configurations, jooo :-({|=

---

### Post by drs305 on 2011-01-25
> **Willye said:**
> Thanks nail, but the thing was that root.disk and swap.disk dissapeared mysteriously after an upgrade  of compiz-extra, so i have to install ubuntu again, and i must reinstall  a lot of software and restore configurations, jooo :-({|=

It's a bit late this time but making a copy of root.disk is the easiest way to backup Wubi. You would reinstall it, then copy the backup copy of root.disk into the /ubuntu/disks folder and you would have all your old settings back.

---

### Post by Rubi1200 on 2011-01-25
> **drs305 said:**
> It's a bit late this time but making a copy of root.disk is the easiest way to backup Wubi. You would reinstall it, then copy the backup copy of root.disk into the /ubuntu/disks folder and you would have all your old settings back.
+1 to that.

It is not the ideal solution since you are saving the whole root.disk rather than specific settings/data, but it will work if something like this happens again (which we hope won't be the case).

Obviously, place the copy somewhere safe like an external medium.

---

### Post by bcbc on 2011-01-25
> **Willye said:**
> 
# cd /media/win/ubuntu/disks
# ls -l 
# d??????? ? ? ?     ?         ? disks
...
...

That looks like ntfs corruption, not on the root.disk itself. Did you run chkdsk on windows?

---

