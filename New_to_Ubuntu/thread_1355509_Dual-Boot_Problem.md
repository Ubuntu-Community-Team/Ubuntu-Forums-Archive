---
title: "Dual-Boot Problem"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by john_colorado on 2009-12-15
Hi Folks- Got a problem, and I'm too new to know how to fix it. Hopefully, it is a problem that will have several easy ways to fix for someone more knowledgeable than I am.

My HP computer running Windows XP was having various problems. Not hardware problems, I don't think. I was intending to back things up and restore the computer to like-new one way or another, but I figured I'd see how things go with Linux. I burned a CD of Ubuntu 7.10 to test it out. It seemed pretty cool, so I went ahead and installed it on the computer. It was my understanding that at startup, I'd get the option to choose which OS to boot up. This wasn't an issue with the CD- it would boot Ubuntu from the CD if it was in there, and not if it wasn't. 

But, running Ubuntu on the CD was slow, and otherwise fun, so I decided to load it onto the hard drive.

OK, I loaded Ubuntu, and selected the option to partition things so that both Linux and XP would be on the hard drive. It worked fine- internet, screen resolution, printer, Open Office, the works.

But, when I rebooted, I got the message "GRUB loading" and this message just stayed there for a long, long time. Eventually, I found out that it I waited for something like a couple of hours, and then came back, it had loaded Ubuntu. Hmmm. This was repeatable- same message, same LONG wait, and then eventually Ubuntu. One time, I did catch a screen where I could choose which OS to load. I got into XP fine, backed everything to an external hard drive, and then tried to figure out how to do a system restore. At this point, I'm just hoping to restore XP (and fix the various previous problems I was having prior to loading Ubuntu) then later I can work with Linux.

Ubuntu works, but how to get into Windows XP? The Ubuntu disc checked out OK, but I figured I'd do a re-install. Did the re-install. Twice, actually. 

Now, at boot, I get a different message. It says:
GRUB loading
error: no such disk
grub rescue>

and then I'm stumped, since I don't know what commands to use to get the thing going. 

I'm still able to boot Ubuntu from CD (that's how I'm here) but what I CAN'T do is to access the recovery partition of the hard drive when the boot cycle starts. I can get into the BIOS settings fine, using F1, but pressing F10 for system recovery doesn't do anything, and the computer goes right into the GRUB loading stage and I'm out of luck. 

I've tried to be a bit more careful with a new install of Ubuntu, hoping that the new install would work and actually dual boot. But, this isn't working.  When I get to the disc partition part of the install task (this is in the GUI procedure you get from clicking the install icon on the Ubuntu desktop), there appears to be a problem. It shows the two Windows partitions taking up almost the whole hard drive, with the FAT32 on dev1 and the ntfs on dev2, and then only 7 mb of free space. I can't figure out how to resize the dev2 so there is space for an install. It is puzzling, because I think Ubuntu is still on the hard drive, but it isn't showing up. 

So, what's the best way forward? Perhaps I should see what sort of boot loader is actually on the hard drive (I THOUGHT it was GRUB2, but I'm not having luck working with it much or figuring out much to do with it when I get that "rescue" message). I think just need to get a boot loader that works in there, and then that will allow me to go ahead and begin the boot of XP, and then (presumably) the F10 system restore will work, and I can restore the whole thing to XP.

Actually, the computer is my father's. I may sound like a newbie, but he's REALLY a newbie, and Linux won't wash with him. He has trouble with web browsers. So, I"d like to do an XP system restore (not to a restore point, but back to square one), and then try to get a SUCCESSFUL dual-boot thing going. He'll have just one more step each time he started up (selecting XP) and I'd be able to learn a bit about Linux.

Any suggestions? How do you folks copy and paste things out of the command lines? is there some sort of simple command I can use while I'm in this CD-boot Ubuntu that could get the dang boot program to work, or at least to let Windows work? I know this has been covered similarly before, but I'm REALLY new, so any suggestions I'd need step-by-step instructions. I'm just hoping it isn't rocket science. 
thanks in advance!
John

---

### Post by bumanie on 2009-12-15
Firstly , you should probably install a later version of ubuntu - 7.10 is no longer supported, unless an LTS version, each version is only supported for 18 months. 7.10 was not a LTS version. As you can get into xp fine, I would try to install either 9.04 or 9.10 version of ubuntu and hopefully grub will configure itself properly and will overwrite the mbr so that (in theory) xp and ubuntu will be able to dual boot. 9.04 uses the 'old' grub, known as grub-legacy, 9.10 uses the 'new' grub, known as grub 2. Just tell ubuntu to install over the top of the location that you have 7.10 and things should be fine, unless you have a quirky bios that doesn't take kindly to grub - but that is rare. If a later version of ubuntu doesn't behave properly, post back and someone will help you sort things out, but due to lack of support, 7.10 should not be your choice for ubuntu.

---

### Post by rsgangr on 2009-12-15
Hi John,

If I were you I should certainly start with the Long Term Support (LTS) version. The current Ubuntu LTS version is 8.04 and the next will be 10.04 (2010, April).

I have been running a dual-boot configuration of Windows XP Professional and Ubuntu 8.04 for almost a year now. Recently it paid dividends when my XP crashed 8 times (blue screen of death) while I was busy preparing my tax return. Fortunately I was able complete the work from Ubuntu before the submission deadline and then spend time resurrecting XP. Having both operating systems available is important to me because of software issues.

For fairly good step-by-step instructions you might find the following site helpful:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
Once there, do a search for "dual boot XP"

Good luck!

---

### Post by Bartender on 2009-12-15
You mention the PC was having problems, but you don't think HW problems.  How come?

Hardware problems are on my mind right now.  A friend dropped off his Gateway, built in August of '06, just last night so I could clean it out and apply fresh thermal paste to all heatsinks.  A coupla days earlier we'd worked on the PC in his cramped, dimly lit computer room for several hours and things seemed to be working better, but I still didn't feel good about it.  

Conditions are better in my shop, where I have good lighting and a nice central work "island" recycled from a kitchen remodel.  It took about one minute to find three blown caps on his Intel motherboard.

Blown caps will cause all sorts of weird behavior.  Long stalls, something will work one time then not five minutes later, computer just shutting down and restarting for "no reason", etc.

If you've thoroughly investigated your hunch that the Windows problems weren't hardware-related, well, OK.  But if you haven't, and the problem is something fundamental like failing RAM or power supply or bad capacitors (power supplies have capacitors inside them, so you could have a caps problem even if the motherboard looks good) I guarantee that Linux won't solve your problems.

Come to think of it, people have installed Linux to a spare HDD and run it for a few days or weeks on a Windows PC that's acting funny as a way of determining whether a problem is HW or SW.  If the problem disappears with the Linux HDD, you've got a strong indication that Windows is the problem.  If the problem **continues** with the Linux HDD, well, you know what that indicates...

EDIT:  I'm sorry, by blown "caps" I mean capacitors, the funny little soda-pop can shaped gizmos on your motherboard.  For more details and pictures, visit badcaps.net

---

### Post by john_colorado on 2009-12-15
Ah- my mistake! I have version 9.10, Karmic Koala, so it is running Grub2. Right now, I'm running live from the CD and things are OK but I am not able to boot either Windows XP or Linux from the hard drive. 

Thanks for the comments about hardware problems. I guess once I get Linux installed properly on the hard drive, I should be able to narrow down whether that would be it or not. 

I can think of two options of what to do next:
1- Burn a Windows start-up CD. From what I understand, there are three essential files I'd need to burn to get Windows started. I know this isn't a Windows forum, but any suggestions on where I might download some files to get Windows starting to boot from a cd?

2- Fix whatever the GRUB2 problem is so it works to dual-boot. What is this "no such disk" error I'm getting? 

thanks!

---

### Post by audiomick on 2009-12-15
the "no such disc" error in grub means either

a grub entry is messed up and pointing to the wrong place

or

the computer can't speak to the disc in question. Possible causes include, amongst others, a broken disc or somthing simple like a cable not plugged in properly.

---

### Post by kansasnoob on 2009-12-15
The most helpful thing would be to see the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2009-12-15
Just FYI in reply to:

> I can think of two options of what to do next:
1- Burn a Windows start-up CD. From what I understand, there are three essential files I'd need to burn to get Windows started. I know this isn't a Windows forum, but any suggestions on where I might download some files to get Windows starting to boot from a cd?

You can recover XP's mbr with your Ubuntu Live CD by installing the package "mbr" and then running the command "install-mbr /dev/sda" assuming that sda is the correct disc designation. I can determine that once I see the output of the Boot Info Script.

And:

> 2- Fix whatever the GRUB2 problem is so it works to dual-boot. What is this "no such disk" error I'm getting?

That is not an uncommon error with grub2, I can advise you once I see the output of The Boot Info script.

---

### Post by john_colorado on 2009-12-15
> **kansasnoob said:**
> Just FYI in reply to:

 You can recover XP's mbr with your Ubuntu Live CD by installing the package "mbr" and then running the command "install-mbr /dev/sda" assuming that sda is the correct disc designation. I can determine that once I see the output of the Boot Info Script.

And:

That is not an uncommon error with grub2, I can advise you once I see the output of The Boot Info script.

That looks like great info! I imagine either way would work for me. I only got so far, unfortunately, before I showed my massive inexperience.

1- How do I install the package "mbr"? I looked in the "Ubuntu Software Center" and did not find it, so it must be found elsewhere.

2- I downloaded the Boot Info Script. How do I run it? I found where Firefox put it, in the downloads folder, then I double-clicked to open it. Geedit opened it. Lots of info, fine. But how do you actually run it? Again, I'm stuck in Windows-land, where you double-click on an executable file to run it. I can tell it has been downloaded but not run/installed because when I type in the "sudo bash ~/Desktop/boot_info_script*.sh" into the terminal, I get. "No such file or directory."

---

### Post by oldfred on 2009-12-15
The default location of downloads changed from desktop to Downloads directory.
so its not /desktop but /Downloads
sudo bash ~/Desktop/boot_info_script*.sh

or  just (capital D in downloads)

cd to directory saved to: 

cd Downloads
chmod 755 boot_info_script041.sh 
sudo ./boot_info_script041.sh
sudo ./boot_info_script*.sh
or sudo bash /boot_info_script041.sh
current version is 041.

On my computer the script was in Downloads but the results.txt was in my home directory.

---

### Post by john_colorado on 2009-12-15
OK, here's what the script returned:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6e410dbe-c5a2-43f5-838c-14ef323edcda)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f8c6f8c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,054,799    10,054,737   b W95 FAT32
/dev/sda2    *     10,054,800   312,560,639   302,505,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="505B-0E44" TYPE="vfat" 
/dev/sda2: UUID="0440409240408BFC" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 





> **oldfred said:**
> The default location of downloads changed from desktop to Downloads directory.
so its not /desktop but /Downloads
sudo bash ~/Desktop/boot_info_script*.sh

or  just (capital D in downloads)

cd to directory saved to: 

cd Downloads
chmod 755 boot_info_script041.sh 
sudo ./boot_info_script041.sh
sudo ./boot_info_script*.sh
or sudo bash /boot_info_script041.sh
current version is 041.

On my computer the script was in Downloads but the results.txt was in my home directory.

---

### Post by kansasnoob on 2009-12-15
> **john_colorado said:**
> That looks like great info! I imagine either way would work for me. I only got so far, unfortunately, before I showed my massive inexperience.

1- How do I install the package "mbr"? I looked in the "Ubuntu Software Center" and did not find it, so it must be found elsewhere.

2- I downloaded the Boot Info Script. How do I run it? I found where Firefox put it, in the downloads folder, then I double-clicked to open it. Geedit opened it. Lots of info, fine. But how do you actually run it? Again, I'm stuck in Windows-land, where you double-click on an executable file to run it. I can tell it has been downloaded but not run/installed because when I type in the "sudo bash ~/Desktop/boot_info_script*.sh" into the terminal, I get. "No such file or directory."

It's all explained in that link. After downloading just go to Accessories > Terminal and run:

```
sudo bash ~/Downloads/boot_info_script*.sh
```

Just copy-n-paste commands by double-clicking, then right clicking and selecting copy, then go to Terminal, right-click and select paste. Then hit enter.

Regarding the mbr package it's in the repos but I don't yet know the proper drive designation to be able to tell you where the mbr should be installed. I'll know once you post the output of that Boot Info Script or you could just post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

But I'd really like to try and get grub working for you.

---

### Post by kansasnoob on 2009-12-15
> **john_colorado said:**
> OK, here's what the script returned:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6e410dbe-c5a2-43f5-838c-14ef323edcda)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f8c6f8c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,054,799    10,054,737   b W95 FAT32
/dev/sda2    *     10,054,800   312,560,639   302,505,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="505B-0E44" TYPE="vfat" 
/dev/sda2: UUID="0440409240408BFC" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf

Have you already deleted the Ubuntu install?

Regardless to get Win XP to boot you should be able to run the following from the Terminal in the Ubuntu Live CD:

```
sudo apt-get install mbr
```

Note if that fails try:

```
sudo apt-get update && sudo apt-get install mbr
```

Then:

```
sudo install-mbr /dev/sda
```

Did you perhaps do a Wubi install like this:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If so I'm woefully ignorant regarding Wubi.

---

### Post by john_colorado on 2009-12-15
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x6f8c6f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         665     5027368+   b  W95 FAT32
/dev/sda2   *         666       20672   151252920    7  HPFS/NTFS

=========================================

Looks like there is just Windows, nothing partitioned for Ubuntu... but I think Ubuntu is still in there...

---

### Post by presence1960 on 2009-12-15
> **john_colorado said:**
> OK, here's what the script returned:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6e410dbe-c5a2-43f5-838c-14ef323edcda)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f8c6f8c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,054,799    10,054,737   b W95 FAT32
/dev/sda2    *     10,054,800   312,560,639   302,505,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="505B-0E44" TYPE="vfat" 
/dev/sda2: UUID="0440409240408BFC" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf
You have no Ubuntu partition on your hard disk! So of course GRUB can't find it hence the no disk message. See from the script output:

```
============================= Boot Info Summary: ==============================
[COLOR="Red"]
=> Grub 1.97 is installed in the MBR of /dev/sda and looks for
(UUID=6e410dbe-c5a2-43f5-838c-14ef323edcda)/boot/grub.[/COLOR]

sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: HP Recovery
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM
/ntdetect.com

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f8c6f8c

Partition Boot Start End Size Id System

[COLOR="Red"]/dev/sda1 63 10,054,799 10,054,737 b W95 FAT32
/dev/sda2 * 10,054,800 312,560,639 302,505,840 7 HPFS/NTFS[/COLOR]


```

---

### Post by john_colorado on 2009-12-15
Hey, that seemed to load OK! Rebooting now to see what happens.

> **kansasnoob said:**
> Have you already deleted the Ubuntu install?

Regardless to get Win XP to boot you should be able to run the following from the Terminal in the Ubuntu Live CD:

```
sudo apt-get install mbr
```Note if that fails try:

```
sudo apt-get update && sudo apt-get install mbr
```Then:

```
sudo install-mbr /dev/sda
```

---

### Post by john_colorado on 2009-12-15
> **kansasnoob said:**
> Have you already deleted the Ubuntu install?

Regardless to get Win XP to boot you should be able to run the following from the Terminal in the Ubuntu Live CD:

```
sudo apt-get install mbr
```



Wonderful! That worked! I'm now back in XP (slow :() and I'll be checking to see if I can get the restore partition to clean this thing up, then try to get the dual-boot option set up correctly the next time around.

thanks to all for the good help, especially kansasnoob!

---

### Post by presence1960 on 2009-12-15
> **kansasnoob said:**
> H

If so I'm woefully ignorant regarding Wubi.

Me to! I know a tad but definitely not enough about it.

I don't think he did a wubi install there is no reference in his boot.ini. Maybe he removed it already though.

---

### Post by kansasnoob on 2009-12-15
> **presence1960 said:**
> Me to! I know a tad but definitely not enough about it.

I don't think he did a wubi install there is no reference in his boot.ini. Maybe he removed it already though.

I guess I should make a point of trying Wubi more thoroughly but power outages are common here and what little I did fool with it, every time the power would go out I'd have to reinstall Ubuntu.

---

