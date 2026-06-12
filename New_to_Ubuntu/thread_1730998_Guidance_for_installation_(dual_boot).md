---
title: "Guidance for installation (dual boot)"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by sharma.amal on 2011-04-16
Hello!!
 
I am absolutely new to Linux. I have a computer with limited hard disk space of 80 GB. I have WINDOWS-XP installed on it. My disk partition is as:
 
[1] C- drive: NTFS: 14 GB: Primary (system installed)
[2] D- drive: NTFS: 28 GB: Extended-logical
[3] E- drive: FAT32: 28 GB: Extended-logical
[4] F- drive: Unformatted: 10 GB: Extended-logical
 
I want to use the unformatted space (F:) for installing Linux. All the literature/ sites show the steps of shrinking the space of Windows to install (the space with NTFS) and FAT32 can be a common resource for Linux and Win. No guide tells that where I can directly choose the unformatted space for installing the Linux (i.e. first time it will be formatted by Linux itself). Because as I have impression from reading (very limited) that the installation step will show free space (i.e. svd\hda1 etc.). Will it seperately tell the unformatted space? Initially for learning the Linux I want to partition my F: drive as:
 
[1] 4 GB for \root [2] 1.5 GB for swap (I have 1 GB RAM) [3] 4.5 GB for home.
 
Is this partition OK?
 
Please let me know how to partition my disk manualy so that only unformatted space of F: drive can be chosen (no using of D: or E: drive) to install?
 
Thanks and regards,
Amal....

---

### Post by scott-ian on 2011-04-16
Your drive letters don't mean anything to Linux, but the partitions do.  I would use a larger partition, but that is based off of my 250 GB hard disk, running only Linux.  With the set-up you mentioned, it seems you need to select the "advanced" option under partitioning.  I would burn a copy of the Ubuntu installation CD, and then go through the process manually.  The install is very user friendly.  Just be sure to install to the 10 GB partition, and Linux should handle the rest.  If possible, back up all your files before installing.  Considering you are a beginner to Linux, you may want to look into WUBI, but since you already have partitioned your hard drive, it should not be a problem.  You made the right choice deciding to use Linux.  If you have any trouble, feel free to ask me, or other members of the Ubuntu community.  Good luck!

---

### Post by oldfred on 2011-04-16
If you are only doing 10GB, I would not do a separate /home. Having root in 4GB while doable is tight and requires continuous housecleaning and perhaps downsizing some large installs like Firefox & OpenOffice to alternatives that are not such large packages.

My /home is about 1GB without any data and most of that is .wine with Picasa. If not storing much data in /home then it does not need to be large nor separate. While for most it is better to be a separate partition  for reinstalls as both user settings & user data are in /home. You are still able to backup just /home and reinstall if you want to do a new clean install.

---

### Post by scott-ian on 2011-04-16
> **oldfred said:**
> If you are only doing 10GB, I would not do a separate /home.
That is true.  If you were to eliminate the swap and /home partition, the install would be easier.

---

### Post by sharma.amal on 2011-04-17
Thanks Oldfred and Scott......
 
     > Considering you are a beginner to Linux, you may want to look into WUBI
 
          If I use WUBI, will I have access to whole disk (i.e. C: to F:, here F: is unformatted) under booting from Linux (WUBI)? All the data will be safer or still do I need a backup?
 
  Thanks and regards,
  Amal....

---

### Post by oldfred on 2011-04-17
Anytime you so system related things, or really all the time, you need to have good backups. Hard drives/computers fail and it always seems to happen just when you saved a lot of important data.

Wubi is intended for windows users who are not sure they want Ubuntu. It is better than just running the liveCD as you can save data and it runs like a full install. But it is just a file inside windows. It boots via windows and as a file inside windows relies on the NTFS format of your drive. It is easy to uninstall, but is not quite the same as a full dual boot install.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by sharma.amal on 2011-04-17
Thanks a lot, Oldfred.......
 
Regards,
Amal..

---

### Post by sharma.amal on 2011-04-19
I installed sucessfully Ubuntu-64 bit on the said configuration (i.e on 10 GB space). I did it without partitioning seperately  /home (as suggested).
 
  Now when I again tried to install Ubuntu -32bit on one another old machine in my office (with P4-2.4GHz and 256MB RAM), the installation process stops after language selection screen (on which "Try Ubuntu" and "Install Ubuntu" options appear). When I select the Install Ubuntu option, screen hangs and process does not proceed. I chaecked the CD and it has all the files correctly (i.e. no error in burning the CD).
 
  Please help me; how this problem can be resolved?
 
Thanks and regards,
Amal...

---

### Post by sharma.amal on 2011-04-19
I tried F6 also to load acpi=off (I read it on net). But actually pressing F6 also does nothing i.e. system does not come out from frozen state.
 
  Please help me in this matter (chipset is intel 845).
 
 Thanks and regards,
 Amal..

---

### Post by rvchari on 2011-04-19
> **sharma.amal said:**
> Hello!!
 
I am absolutely new to Linux. I have a computer with limited hard disk space of 80 GB. I have WINDOWS-XP installed on it. My disk partition is as:
 
[1] C- drive: NTFS: 14 GB: Primary (system installed)
[2] D- drive: NTFS: 28 GB: Extended-logical
[3] E- drive: FAT32: 28 GB: Extended-logical
[4] F- drive: Unformatted: 10 GB: Extended-logical
 
I want to use the unformatted space (F:) for installing Linux. All the literature/ sites show the steps of shrinking the space of Windows to install (the space with NTFS) and FAT32 can be a common resource for Linux and Win. No guide tells that where I can directly choose the unformatted space for installing the Linux (i.e. first time it will be formatted by Linux itself). Because as I have impression from reading (very limited) that the installation step will show free space (i.e. svd\hda1 etc.). Will it seperately tell the unformatted space? Initially for learning the Linux I want to partition my F: drive as:
 
[1] 4 GB for \root [2] 1.5 GB for swap (I have 1 GB RAM) [3] 4.5 GB for home.
 
Is this partition OK?
 
Please let me know how to partition my disk manualy so that only unformatted space of F: drive can be chosen (no using of D: or E: drive) to install?
 
Thanks and regards,
Amal....

for an 80 gb hdd, i would suggest atleast 25 gb for ubuntu system files, twice the ram for swap and a minimum of 10 gb for /home (assuming you will have only one user account).
drive nomenclature for linux is meaningless, its the type of partition and size that counts.

when you boot up the install cd, choose the following options for a fairly good functionality of ubuntu.

erase the logical extended partitions of E and F.
create new partitions with allocations as listed below:
mount point / allocate minimum 25 gb, mount point /home allocate 10 gb, allocate 3 gb for swap. (assuming your ram is 1 gb or 2 gb, safe side is 3 gb swap.)

then make the d partition untouched and make mount point as /media/windows and c as /media/win-c something like that.

once this table is configured (double check lest you lose your data for wwrong confuguration) format the linux allocated partition as displayed (ext3 or ext4) install grub in mbr so your dual boot will show up after restart.

default is always ubuntu... you can change the sequence later if you need.

happy ubuntuing...

---

### Post by sharma.amal on 2011-04-19
Thanks Rvchari for help, I have installed Ubuntu on one machine. There is another problem in another machine.
 
> Now when I again tried to install Ubuntu -32bit on one another old machine in my office (with P4-2.4GHz and 256MB RAM), the installation process stops after language selection screen (on which "Try Ubuntu" and "Install Ubuntu" options appear). When I select the Install Ubuntu option, screen hangs and process does not proceed. I chaecked the CD and it has all the files correctly (i.e. no error in burning the CD).
 
> I tried F6 also to load acpi=off (I read it on net). But actually pressing F6 also does nothing i.e. system does not come out from frozen state.

Please help me in this matter (chipset is intel 845).

 
So I am in need to resolve this problem now...
 
 
 Thanks and regards,
 Amal..

---

### Post by rvchari on 2011-04-19
> **sharma.amal said:**
> Thanks Rvchari for help, I have installed Ubuntu on one machine. There is another problem in another machine.
 

 

 
So I am in need to resolve this problem now...
 
 
 Thanks and regards,
 Amal..

ubuntu (lucid or maverick) needs atleast 512 mb ram for smooth functioning... that may be the hitch.

---

### Post by rvchari on 2011-04-19
if you have a ram slot free in ur motherboard, add another ram chip and check out, your problem will be solved.

---

### Post by sharma.amal on 2011-04-19
Thanks Rvchari,

                There is RAM slot, but I have to seek for SDRAM. Can any other Linux Distos be installed, like Fedora or Suse.......etc with available resources (P4-2.4GHz, 256MB RAM, intel 845 chipset)? Also I want to install with GUI, not only text based (i.e. only command line).

Thanks and regards,
Amal....

---

### Post by blah... on 2011-04-19
> **sharma.amal said:**
> Thanks Rvchari,

                There is RAM slot, but I have to seek for SDRAM. Can any other Linux Distos be installed, like Fedora or Suse.......etc with available resources (P4-2.4GHz, 256MB RAM, intel 845 chipset)? Also I want to install with GUI, not only text based (i.e. only command line).

Thanks and regards,
Amal....Hello, you can try Lubuntu, its based on Ubuntu only using the lighter LXDE, and needs only 128 MB RAM.

---

### Post by oldfred on 2011-04-19
If you just want command line, you need to use alternative install.

Minimum memory is 512 with Desktop and 256MB without.
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Light Linux Distros
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lighter weight Versions use with Chromium browser as it is lighter than firefox:
Firefox 4, Chromium is much faster than FF3.6.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite

8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector

---

### Post by sharma.amal on 2011-04-19
Thanks Blah and Oldfred......

Regards,
Amal...

---

