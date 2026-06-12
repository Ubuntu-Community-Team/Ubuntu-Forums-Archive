---
title: "No root file system is defined..."
date: 2010-10-21
forum: New to Ubuntu
---

### Post by mitymows on 2010-10-21
Hello. :)

I'm just going to start by saying that I'm a complete newb at anything besides Windows, and this is my first time trying to install Ubuntu using Wubi (I used UNetbootin before, but it didn't really work out for me, mostly because it kept resetting everything when I restarted). So my problem, simply put: I started Wubi, selected username and all that, finished installation, and then restarted and selected Ubuntu at the boot menu. It starts with a window saying "Verifying the Installation Configuration" where it stops at 271%, followed by a window saying (going by my terrible memory), 

"No root file system is defined. 

Please correct this from the partitioning menu". 

I've read that setting the mount point to / should fix it, but I have no idea how to do that or where the partitioning menu is. I've looked for hours on how to fix this but so far I've found no solution (maybe I'm not looking hard enough).

Any help is appreciated. :wink: Thanks.

---

### Post by GabrielYYZ on 2010-10-21
i might be wrong, but when you install ubuntu using wubi isn't windows still the default boot os and ubuntu works inside windows?

edit:i was wrong, but try checking this and see if it works: [https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")

edit 2: also, this might help a bit more: [https://answers.launchpad.net/wubi/+question/60110](https://answers.launchpad.net/wubi/+question/60110)

---

### Post by mitymows on 2010-10-21
Hey. Thanks for the reply. :)

I tried everything in the "Cannot boot into Ubuntu" section from your first link, but no luck. So I followed the instructions at this link: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), and atm I'm "Trying" Ubuntu since the actual installation won't work (same problem as before). Hopefully the attached picture will help.
[IMG]http://ubuntuforums.org/[IMG]http://i55.tinypic.com/2m4oto1.jpg[/IMG][IMG]http://tinypic.com/view.php?pic=2m4oto1&s=7[/IMG]

---

### Post by Rubi1200 on 2010-10-21
Since you are already on the LiveCD, please post the results of the boot-script linked at the bottom of my post.

Paste the results in a new post and wrap the text with code tags by clicking on the # in the menu.

Thanks.

---

### Post by mitymows on 2010-10-21
Here ya go. :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/pdc_bcgbjjffba

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

pdc_bcgbjjffba1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_bcgbjjffba2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

pdc_bcgbjjffba3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,929,783,295 1,929,576,448   7 HPFS/NTFS
/dev/sda3       1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS


Drive: pdc_bcgbjjffba ___________________ _____________________________________________________

Disk /dev/mapper/pdc_bcgbjjffba: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_bcgbjjffba1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_bcgbjjffba2            206,848 1,929,783,295 1,929,576,448   7 HPFS/NTFS
/dev/mapper/pdc_bcgbjjffba3      1,929,785,344 1,953,122,303    23,336,960   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_bcgbjjffba1 42283F60283F5261                       ntfs       SYSTEM                        
/dev/mapper/pdc_bcgbjjffba2 C04A33364A332894                       ntfs       HP                            
/dev/mapper/pdc_bcgbjjffba3 2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/mapper/pdc_bcgbjjffba: PTTYPE="dos" 
/dev/sda1        42283F60283F5261                       ntfs       SYSTEM                        
/dev/sda2        C04A33364A332894                       ntfs       HP                            
/dev/sda3        2408CF7908CF488E                       ntfs       FACTORY_IMAGE                 
/dev/sda                                                promise_fasttrack_raid_member                               
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by SavageWolf on 2010-10-21
Uh, I looked at the attached picture, and it looks like you have not set up anything in that box thing directly behind the alert.

---

### Post by mitymows on 2010-10-21
> **SavageWolf said:**
> Uh, I looked at the attached picture, and it looks like you have not set up anything in that box thing directly behind the alert.

I figured it wasn't supposed to be empty, except I'm not exactly sure what's supposed to be there or how to get anything there. It won't let me select anything like "New Partition Table" etc. Like I said, I'm a complete newb at Ubuntu. :(

Not that this is related, but is there a reason Ubuntu keeps resetting all of my Firefox settings and deleting all my downloads when I restart or shut down my computer? It basically does a clean install whenever I restart.

---

### Post by mitymows on 2010-10-21
Gonna bump, there has to be a way to fix this. :???: It doesn't seem like it would be too complicated of a problem to fix... Is there any alternatives or is Ubuntu forever off-limits to me? :( Feel free to ask any questions if needed...

---

### Post by Rubi1200 on 2010-10-21
I think your problems may have something to do with the fact that you have a RAID setup.

Unfortunately, I am not an expert in this area, but I do know that this is an issue in 10.04 (and possibly the latest version 10.10 as well).

There are ways to install Ubuntu in this type of situation, but I am not familiar with them.

Right now, all I can suggest is that you give the Alternate CD a try.

By the way, I think you should also look into the fact that the partitions on sda are not being mounted.

Are you still able to boot into Windows normally?

---

### Post by mikewhatever on 2010-10-21
> **mitymows said:**
> Hey. Thanks for the reply. :)

I tried everything in the "Cannot boot into Ubuntu" section from your first link, but no luck. So I followed the instructions at this link: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), and atm I'm "Trying" Ubuntu since the actual installation won't work (same problem as before). Hopefully the attached picture will help.

I suspect that Ubuntu doesn't boot for you because it's not yet installed, at least according to the screenshot.
Please read the Windows installer FAQ -> [http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)
> 256 MB RAM and an 1 GHz or faster Intel/AMD processor is recommended for optimal performance, though Xubuntu might work on less. As for disk space, the installation requires a minimum of 5GB free. This space is mostly used by the virtual hard disk file. Most computers purchased within the last 3 years should be able to run Ubuntu fine, and Xubuntu is suitable for older computers. Software raids (aka fakeraid) are not supported. Encrypted disks are not supported.


---

### Post by ronparent on 2010-10-22
I've look thru all the posts and there is inadequate information on what you are dealing with. There is obviously a raid array involved. Also, here are too many hard disk to be account for by a simple two disk raid. This hints at a more advanced raid like a raid 10 which would require 4 disks. If you are using a release 9.10 or later the raids should be automatically detected. In that case try opening a terminal and running the command 'sudo dmraid -ay' and posting the output.

The fact that the raid doesn't show up in the installer hints that you may be using a 10.04 live cd. If this were the case, you couldn't install without a workaround. After booting to the live cd, open a terminal and type 'sudo apt-get install kpartx'. Then in the header menu bar start System >Administration >Gparted. Does your raid show up now? Theoretically you are ready to install from the desktop icon now. But since you already seem to have three primary partitions, this could get tricky. You would need an extended with unallocated space to proceed with a near normal install. And, the unallocated space would probably best be created by Windows (Vista or 7?). Maybe before continuing we need a screen shot of the raid setup in gparted. Since you are an admitted noob you shouldn't try to install yet, because proceeding could easily hose your system unless you know exactly what you are doing. I'll watch for your post.

To be honest, you might be better off tying to install to a disk separate from the raid (internal, external usb, etc). It is your choice and we'll try to help.

---

### Post by mitymows on 2010-10-22
> **Rubi1200 said:**
> Right now, all I can suggest is that you give the Alternate CD a try.

By the way, I think you should also look into the fact that the partitions on sda are not being mounted.

Are you still able to boot into Windows normally?

Yes, I can boot into Windows normally. And according to GParted the partitions are mounted just fine (attached another picture). Will be sure to try the Alternate CD, thanks. :)

> **mikewhatever said:**
> I suspect that Ubuntu doesn't boot for you because it's not yet installed, at least according to the screenshot.
Please read the Windows installer FAQ -> [http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

That's the problem I'm having though. I can't install it because "No root file system is defined". :( I'm on LiveCD atm.

> **ronparent said:**
> I've look thru all the posts and there is inadequate information on what you are dealing with. There is obviously a raid array involved. Also, here are too many hard disk to be account for by a simple two disk raid. This hints at a more advanced raid like a raid 10 which would require 4 disks. If you are using a release 9.10 or later the raids should be automatically detected. In that case try opening a terminal and running the command 'sudo dmraid -ay' and posting the output.

The fact that the raid doesn't show up in the installer hints that you may be using a 10.04 live cd. If this were the case, you couldn't install without a workaround. After booting to the live cd, open a terminal and type 'sudo apt-get install kpartx'. Then in the header menu bar start System >Administration >Gparted. Does your raid show up now? Theoretically you are ready to install from the desktop icon now. But since you already seem to have three primary partitions, this could get tricky. You would need an extended with unallocated space to proceed with a near normal install. And, the unallocated space would probably best be created by Windows (Vista or 7?). Maybe before continuing we need a screen shot of the raid setup in gparted. Since you are an admitted noob you shouldn't try to install yet, because proceeding could easily hose your system unless you know exactly what you are doing. I'll watch for your post.

To be honest, you might be better off tying to install to a disk separate from the raid (internal, external usb, etc). It is your choice and we'll try to help.

I use Win7, and I'm fairly certain I downloaded a 10.10 LiveCD (32-bit if it matters). So yeah, I entered 'sudo dmraid -ay' in the terminal and it just said "RAID set "pdc_bcgbjjffba" was not activated". 'sudo apt-get install kpartx' apparently installed correctly, but no luck with the raid showing up in GParted. And I'm not exactly sure where the raid setup is in GParted, but maybe the attached pic is what you're looking for. :-k

Also, I guess I should have mentioned in my original post that although I'm most experienced with Windows, I'm not exactly the most computer savvy person out there (which I'm guessing is not good when trying to install Ubuntu). I'm usually gaming or on the internet, so anything about raid or raid arrays goes right over my head. I will do some research if need be though. That being said, I'm pretty much willing to try any method of installing Ubuntu, but I might need a little walkthrough or something, especially if it has to do with a 'raid'. :oops:

---

### Post by ronparent on 2010-10-22
The raid bios should show you what your raid setup is. Because there are an odd number of disk I suspect a raid5. If it is it would be bad news for you because dmraid does't support a pdc raid5 - Ubuntu would not be installable to a pdc raid5 array. Until you identify it you need to be careful because it could be easy to wipe all data. A raid5 would be more robust and harder to wipe from action on one disk. The nest move is up to you.

---

### Post by mitymows on 2010-10-22
Sorry if this is a stupid question... where is the raid bios in Win7? :( I searched for an answer but can't seem to find anything.

---

### Post by ronparent on 2010-10-22
The bios is included on the motherboard and is first to boot when the system is turned on or rebooted. There are boot sequence variations depending on the manufacturer or bios provider but generally the raid bios will write to the screen after the rest of the bios has loaded. When engaged, the raid bios leaves you about 5 seconds to strike a key before proceeding to booting the OS. It will tell you what key to hit to enter the raid bios. That screen may also tell you what your raid configuration is. Don't make any changes, just report back the contents.

---

### Post by mitymows on 2010-10-22
Alright, so apparently I had to use Ctrl+F to get into RAID Option ROM Utility (which is hopefully what we're looking for), and basically there were four options: View Drive Assignments, Define LD, Delete LD, Controller Configuration.

Not exactly sure what I was supposed to be looking for specifically, but in both Define/Delete LD, under "RAID Mode" it said RAID READY and under "Total Drv" it said 1. That's all I really saw that I thought might be related to what you were looking for.

---

### Post by ronparent on 2010-10-23
Yes, the raid option utility is exactly what we are looking for. 

This is hard to believe. You apparently have '1' drive in a raid 'set' and 4 more drives that are unused? What are we trying to use a raid for?

Maybe you need to check the 'view drive assignments' before we do anything else. What are the drives sdb, sdc, sdd and sde. Maybe the answer is a simple as installing to one of those?

---

### Post by mitymows on 2010-10-23
I went into View Drive Assignments, but saw nothing about sdb, sdc, sdd or sde. :confused:

---

