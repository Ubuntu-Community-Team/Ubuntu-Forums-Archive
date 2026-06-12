---
title: "cannot boot into Ubuntu"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by erjoalgo on 2010-02-18
I have been trying to get Ubuntu setup for the past 8 hours, and I am about to give up on it altogether. The lack of 

The first time I installed Ubuntu (about 3 months ago).
-It was installed from Windows (wubi) not from a bootable disc
-It had sound

Today I booted to Ubuntu, and did all the updates.
Upon reboot, ubuntu would not boot any longer. The error message was something like:
"kernel panic not syncing vfs" and something about being unable to mount the root drive.

After booting into the previous version of Ubuntu, I found that the system was slow, had no sound, and wireless connection could not be enabled. I decided to reinstall Ubuntu.

I install Ubuntu from Windows again (wubi), do updates. Upon reboot, Im thrown into a command prompt, something like:
"grub,. 1.97~ minimal bash capabilities"
wtf? I have no idea what this is and I dont understand why Ubuntu would put users in this frustrating position.

After messing around with it a bit, I type "boot" and the response is:
"error no loaded kernel"
Doing ls shows several partitions I think, so I dont know which one would contain the Ubuntu installation. 

I then decided to install Ubuntu 8 from a bootable disc. No difference, after doing the updates, the grub prompt would appear and I would be unable to boot into the OS.

How can I know which partition to use, and how can I successfully boot into Ubuntu?
The issue with the sound I will address later, but I decided to mention it here in case it is related.
My system is a Dell Studio 64bit with Windows 7 preinstalled.

Im laying out all the possibly unrelated details and clues, hoping some smart Linux person, or just someone who've had this before, can figure out the problem. Please help me become a user of Ubuntu and member of the community.

---

### Post by Peter09 on 2010-02-18
Make sure that you have burned the disk at the slowest speed possible. Burning a data disk is different to an audio disc in that any dropped bit is a fault for a data disk where as it doesn't matter for an audio disc.

---

### Post by erjoalgo on 2010-02-18
[@Peter09]("http://ubuntuforums.org/member.php?u=300963"):
The issue happened with wubi, which requires no disc at all, so its not that.
Do you know what commands from grub will let me boot into Ubuntu?

---

### Post by presence1960 on 2010-02-18
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by erjoalgo on 2010-02-20
sorry I have been so busy, I will try that now I hope you are still with me.
Also, I heard the problem is related to the 9.10 grub, that I need to install a different version of grub. Anyway, I will try what you say

---

### Post by erjoalgo on 2010-02-20
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd63850c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   976,771,119   945,969,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2f8f037f-d99c-4cba-aac6-c86dcdcd7bb6   ext4                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        78304C2F304BF324                       ntfs       RECOVERY                      
/dev/sda3        6A104E2D104E0115                       ntfs       OS                            

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

---

### Post by samantha_ on 2010-02-20
> **erjoalgo said:**
> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________
[B]
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd63850c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   976,771,119   945,969,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2f8f037f-d99c-4cba-aac6-c86dcdcd7bb6   ext4                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        78304C2F304BF324                       ntfs       RECOVERY                      
/dev/sda3        6A104E2D104E0115                       ntfs       OS                            

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
you have a corrupted wubi virtual disk.
try installing ubuntu again in its own seperate partition.

---

### Post by erjoalgo on 2010-02-20
[@samantha_]("http://ubuntuforums.org/member.php?u=1009806")
I installed ubuntu on a separate partition, and it worked!
Now the grub loader seems more sophisticated, I can select the OS I want to boot to through a GUI.
I have yet to try updates, which in the past has been the precedent to my problem.

---

### Post by erjoalgo on 2010-02-21
[samantha_]("http://ubuntuforums.org/member.php?u=1009806")
Thank you I solved my problem!
Can I give you stars (or beans) in this forum? idk how this works lol

---

### Post by L33tCh on 2010-05-16
Thank you samantha... it is a great work around but to whomever marked this post as solved, boxes that don't have another partition to install into (hence the use of Wubi as a last resort when Winedows is still relied upon) still are stuck at this point...  so it's not actually solved. I have reinstalled twice onto this machine with exactly the same result after updating.

Anyone know a way to get this working? Surely updating after a Wubi install shouldn't corrupt your disks?

---

### Post by erjoalgo on 2010-05-22
Wow, I thought I had replied 5 days ago but my reply was never posted.
To the last poster:
It is much cleaner to install Ubutnu on a different partition as your other OS.
I really dont understand what you mean by, do not have other partition, if you have enough free space in disk the Ubuntu installer can make a new partition out of that free space.
If you are getting errors with the partitioner in the ubuntu installer, just defragment your disk in Windwos and try again.
Why cant you make another partition?

---

