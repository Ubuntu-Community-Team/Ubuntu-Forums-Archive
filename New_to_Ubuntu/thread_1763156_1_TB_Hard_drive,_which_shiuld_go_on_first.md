---
title: "1 TB Hard drive, which shiuld go on first?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-20
Hi folks, I have a brand new 1TB drive.  Which order should I install the OS's?  I want Windows 7 and Ubuntu 11.04.  Depending on the replies, I may split the drive in half.

---

### Post by wildmanne39 on 2011-05-20
> **TAspr said:**
> Hi folks, I have a brand new 1TB drive.  Which order shoukd I install the OS's?  I want Windows 7 and Ubuntu 11.04.  Depending on the replies, I may split the drive in half.

Hi, windows 7

---

### Post by Paqman on 2011-05-20
Windows first, then Ubuntu. The Ubuntu installer is designed to be installed next to another OS. Windows, not so much.

Half and half seems a bit excessive. I'd give Windows 100GB or so, Ubuntu about 20GB, and use the rest as a shared data partition (NTFS is a good filesystem for this)

---

### Post by TAspr on 2011-05-20
> **Paqman said:**
> Windows first, then Ubuntu. The Ubuntu installer is designed to be installed next to another OS. Windows, not so much.

Half and half seems a bit excessive. I'd give Windows 100GB or so, Ubuntu about 20GB, and use the rest as a shared data partition (NTFS is a good filesystem for this)

How do you share the data partition?

---

### Post by TAspr on 2011-05-20
> **wildmanne39 said:**
> Hi, windows 7

This is Random...

---

### Post by wildmanne39 on 2011-05-20
> **TAspr said:**
> This is Random...

Hi, what is random?.

---

### Post by wildmanne39 on 2011-05-20
> **TAspr said:**
> How do you share the data partition?
Hi, this link should give most of the information that you need to install ubuntu. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by coffeecat on 2011-05-20
> **TAspr said:**
> This is Random...

wildmanne39's advice to install Windows 7 first is good. There are many reasons to do this. Why are you saying it's "random". 

> **TAspr said:**
> How do you share the data partition?

Windows will see the shared partition as D: or E: or whatever drive letter it assigns. In Ubuntu 11.04, you will see the partition in the Places left pane of a nautilus browser, and simply clicking on it will mount it. Or you can arrange to have it mounted on bootup with an entry in /etc/fstab. If you want to do the latter, people can help you with this.

---

### Post by jeneverboy on 2011-05-20
Hi,
I followed this site and it works like a charm! 
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1")

should work for Win7 I guess.

---

### Post by eb3ha4el on 2011-05-20
> **coffeecat said:**
> wildmanne39's advice to install Windows 7 first is good. There are many reasons to do this. Why are you saying it's "random". 



Hmm. I never knew that..
I was thinking of installing ubuntu first since I wanted it to be
a kind of primary..


Someone said Ubuntu is designed to be installed alongside other OS, does that mean it is going to be little un-stable when installed alone?

---

### Post by Dondermans on 2011-05-20
> **TAspr said:**
> Hi folks, I have a brand new 1TB drive.  Which  order should I install the OS's?  I want Windows 7 and Ubuntu 11.04.   Depending on the replies, I may split the drive in half.
It depends on which OS you plan on using the most. I started out with a Windows XP/ Ubuntu dual boot. I installed both operating systems on a 160Gb disk with a 1TB external disk, NTFS formatted. As I gradually started using Ubuntu more than Windows XP, I shrank the 1TB NTFS-partition to 30Gb and formatted the remainder in Ext4. While Ubuntu can read and write to NTFS, it is coded in such a way that its full potential is not used. I understood that choice was made because of legal reasons (NTFS is  Microsoft property).


> **Paqman said:**
> Windows first, then Ubuntu. The Ubuntu installer is designed to be installed next to another OS. Windows, not so much.

Half and half seems a bit excessive. I'd give Windows 100GB or so, Ubuntu about 20GB, and use the rest as a shared data partition (NTFS is a good filesystem for this)
What do you intend to share between the two operating systems? As I wrote above, I have got a 1TB external harddrive with only a 30Gb shared partition, currently 29.9 is unused...


> **eb3ha4el said:**
> Hmm. I never knew that..
I was thinking of installing ubuntu first since I wanted it to be
a kind of primary..


Someone said Ubuntu is designed to be installed alongside other OS, does that mean it is going to be little un-stable when installed alone?
If you are referring to Paqman;10839896: I suppose he is only saying that the Windows 7 installer does not play nice when you intend to create a dualboot system. Ubuntu is more accomodating in that perspective.

---

### Post by eb3ha4el on 2011-05-20
> **Dondermans said:**
> 
If you are referring to Paqman;10839896: I suppose he is only saying that the Windows 7 installer does not play nice when you intend to create a dualboot system. Ubuntu is more accomodating in that perspective.



Right, thank you!

---

### Post by TAspr on 2011-05-20
> **coffeecat said:**
> wildmanne39's advice to install Windows 7 first is good. There are many reasons to do this. Why are you saying it's "random". 



Windows will see the shared partition as D: or E: or whatever drive letter it assigns. In Ubuntu 11.04, you will see the partition in the Places left pane of a nautilus browser, and simply clicking on it will mount it. Or you can arrange to have it mounted on bootup with an entry in /etc/fstab. If you want to do the latter, people can help you with this.

I said it was random because the response I got previosly, all it said was, "Hi Windows 7".  Maybe my screen got cutoff or something...  Anyone else see that?

Got the last statement.. Sorry guys.  This ol feeble brain I tell ya.

---

### Post by An Sanct on 2011-05-20
> **Paqman said:**
> Windows first, then Ubuntu. The Ubuntu installer is designed to be installed next to another OS. Windows, not so much.

Half and half seems a bit excessive. I'd give Windows 100GB or so, Ubuntu about 20GB, and use the rest as a shared data partition (NTFS is a good filesystem for this)

+1

Install Windows first and Ubuntu later, this will be much easier then the other way around. I installed windows after Ubuntu and had to reinstall GRUB and faced other boot related problems with Windows (7, 64bit ultimate edition)

Edit: I saw, that people say windows cannot see Ubuntu drives (EXT2, EXT3, EXT4) ... [install a driver for that]("http://www.fs-driver.org/") :) also Ubuntu can handle NTFS without any problems.

---

### Post by oldfred on 2011-05-20
Much better to only set other system partitions as read only. Windows does not like much writing from anything else into its system partition. The shared data NTFS partition then is the read/write partition.

When first converting from XP, I was trying to learn Ubuntu but my wife kept wanting to check email or go on web with all the bookmarks from XP. Once I created shared partition with Firefox & Thunderbird profiles in the shared I was able to continue in Ubuntu for most things. I still have not moved profiles from shared although I rarely boot XP anymore.

---

### Post by TAspr on 2011-05-20
> **An Sanct said:**
> +1

Install Windows first and Ubuntu later, this will be much easier then the other way around. I installed windows after Ubuntu and had to reinstall GRUB and faced other boot related problems with Windows (7, 64bit ultimate edition)

Edit: I saw, that people say windows cannot see Ubuntu drives (EXT2, EXT3, EXT4) ... [install a driver for that]("http://www.fs-driver.org/") :) also Ubuntu can handle NTFS without any problems.

When you say *also Ubuntu can handle NTFS without any problems*, is it built into Ubuntu?

---

### Post by underdog512 on 2011-05-20
> **TAspr said:**
> When you say *also Ubuntu can handle NTFS without any problems*, is it built into Ubuntu?

I believe you still have to install the ntfs packages in Ubuntu.  I don't think they are installed by default.  

```
sudo apt-get install ntfs-3g
```

Its been a while since I had to use it after doing a fresh install so i could be wrong about that.

---

### Post by egalvan on 2011-05-20
> **An Sanct said:**
> +1
Install Windows first

> Edit: I saw, that people say windows cannot see Ubuntu drives (EXT2, EXT3, EXT4) ... [URL="http://www.fs-driver.org/"]
install a driver for that[/URL] :) also Ubuntu can handle NTFS without any problems.

from the web site...

> Large inodes

**The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.**

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

sadly *Ext2 Installable File System for Windows* has not been updated.

and when you try to access that drive, MS will show an empty drive, and kindly offer to format it for you. Beware!

---

### Post by An Sanct on 2011-05-20
> **egalvan said:**
> from the web site...



sadly *Ext2 Installable File System for Windows* has not been updated.

and when you try to access that drive, MS will show an empty drive, and kindly offer to format it for you. Beware!

Yes, beware !!!!! ... Windows will try to format for you ... don't let it do it!

In other releases of EXT2FS I have seen no problems ... I don't know what is happening with this ... the author is out there, reachable ...

---

### Post by wildmanne39 on 2011-05-20
Hi, also from what I see with that program to let windows see ubuntu files it is outdated ubuntu uses an udated file system now.

---

### Post by TAspr on 2011-05-20
> **oldfred said:**
> Much better to only set other system partitions as read only. Windows does not like much writing from anything else into its system partition. The shared data NTFS partition then is the read/write partition.

When first converting from XP, I was trying to learn Ubuntu but my wife kept wanting to check email or go on web with all the bookmarks from XP. Once I created shared partition with Firefox & Thunderbird profiles in the shared I was able to continue in Ubuntu for most things. I still have not moved profiles from shared although I rarely boot XP anymore.

So you actually moved these to a share folder so all could access?  Or was it just you wives profiles?  I did not realize that you could do this.  Does everyone who has access to the PC have the access to her profile as well?

---

### Post by TAspr on 2011-05-20
Well, lucky for me, there was a disk wizard similar to DD and DDrescue as well as  EASEUS Todo Backup Home that came with the new Hard Drive (Although, EASEUS did not work on the existing drive) and used the Seagate cloning tool to perform the transfer of Windows to the new drive.  Once I format the old drive, I will use it for Linux specifically.  I will let you know if I run into problems though :)

---

### Post by oldfred on 2011-05-20
I do not have two users except in Thunderbird for email. But I copy the entire profiles from XP to a shared NTFS partition. Then in Ubuntu modifed the profile.ini to look at the mount point/path to find the same profiles. I also rsync the same profiles to my laptop when we travel and  have the same shared partition on the laptop.

This has worked from Tb2 to Tb3 and all the versions of Firefox for the last 3-4 years. I do try to update XP & Ubuntu with new versions about the same time, but have opened same profile with slightly different versions.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by An Sanct on 2011-05-21
> **wildmanne39 said:**
> Hi, also from what I see with that program to let windows see ubuntu files it is outdated ubuntu uses an udated file system now.

Well, as to my knowledge ... EXT2, EXT3 and EXT4 are compatible, 3 and 4 are just upgrades. so for read and write operations, one has to support EXT2

---

### Post by Paqman on 2011-05-21
> **underdog512 said:**
> I believe you still have to install the ntfs packages in Ubuntu.  I don't think they are installed by default.  

```
sudo apt-get install ntfs-3g
```

Its been a while since I had to use it after doing a fresh install so i could be wrong about that.

Ntfs-3g has been installed by default for several years now.

---

