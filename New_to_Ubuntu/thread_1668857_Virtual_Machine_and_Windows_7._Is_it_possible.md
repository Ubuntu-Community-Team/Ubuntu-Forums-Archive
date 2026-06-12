---
title: "Virtual Machine and Windows 7. Is it possible?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by SebSmith on 2011-01-16
So I just bought an HP Envy 14 Beats Edition. Super sweet. Now on my last laptop (Acer 4000 Ferrari, also super schweet) it was failing me on the Windows XP due to single core AMD overheating issues. Bleh. 

On my failing laptop I installed Ubuntu on a dual boot until the XP would just utterly fail in every aspect. Natural selection, I wiped my hard drive and decided to just run Ubuntu by itself until now.

Being completely in love with Ubuntu, I want to have it at the begining of my HDD on my new Envy laptop. But I also want Windows 7 on dual boot. But i'd like it at the back end of my hard drive.

[B]Heir ist mein kampf..

[/B]In order to do this, I am getting the sneaking suspicion that I need to buy a stand alone copy of Windows 7.

Well hell, I'd really rather have Windows 7 running out of VirtualBox or Virtual Machine or whatever the heck it is. I want the Windows 7 for iPhone application syncing as well as music. the rhythm box method works for the ipod classic, but it never seems to work on iPhones right.

Do I need to buy a seperate Windows 7 OS disc? how do I do this? where can i get it? will an oem version work? if oem will work, will it work on the hdd as well as virtual box?

Solution oriented responses are much appreciated. Thank you.
-SebSmith

---

### Post by 123456789123456789123456 on 2011-01-16
The computer came blank no os on it?

Yes it is possible to dual boot, windows 7 and Ubuntu.  as long as Ubuntu is 10.10. it should work as the main OS on the system.

You will need a copy of windows 7 if you want to start from scratch with the installation.  First install Ubuntu, but use partition manager to seperate partitions, install Ubuntu and swap onto one partition map, the other leave vacent.

install windows 7 on the second partition, note that once you do that, the windows boot loader will replace the grub boot loader in MBR.  Best way to accomplish installations is to partition the hard disk, install windows on the second partition, go back install ubuntu on the first partition.  That way Ubuntu is first and windows second, Ubuntu Grub takes over the MBR and is able to boot both Ubuntu and Windows, if you use the other way, make sure you tell the Ubuntu installation in optional installation method, to install grub on the hard disk partiton and not MBR.  then use a program for windows, cant remember the name, it basically edits the windows boot loader file, so that Ubuntu is added to the boot list, and is linked to the ubuntu partition, so that when the computer stats up, windows boot loader asks what system to start from, choose Ubuntu, it points to the Ubuntu partition and Grub takes over from there and boots the system.

---

### Post by SebSmith on 2011-01-16
> **123456789123456789123456 said:**
> The computer came blank no os on it?


No it did, but it comes stock installed on the small end(front) of hdd. i want windows 7 further back.
 thank you very much for that tutorial on grub. i prefer grub loader

but i still dont understand virtual box.

---

### Post by tgm4883 on 2011-01-16
> **SebSmith said:**
> No it did, but it comes stock installed on the small end(front) of hdd. i want windows 7 further back.
 thank you very much for that tutorial on grub. i prefer grub loader

but i still dont understand virtual box.

I don't understand your questions. You need to purchase 1 copy of Windows 7 for every installation of Windows 7 that you want. For instance, if you want to install Windows 7 as a dual boot option, and also in a virtual box virtual machine, then you will need to purchase 2 copies of Windows 7. Windows 7 can be purchased for most electronic stores or places like amazon.com.

---

### Post by SebSmith on 2011-01-16
> **tgm4883 said:**
> I don't understand your questions. You need to purchase 1 copy of Windows 7 for every installation of Windows 7 that you want. For instance, if you want to install Windows 7 as a dual boot option, and also in a virtual box virtual machine, then you will need to purchase 2 copies of Windows 7. Windows 7 can be purchased for most electronic stores or places like amazon.com.

you answered my question perfectly! thank you! now are you familiar with the oem system builder version of win7?
 apparently if you install it multiple times only one version can be on at a time. does this mean that i can just buy one of those disks and use it on my computer AND the VB?

and just to clarify, i cannot move my stock manufaturer's installation of windows 7 to the back end of my har drive? i want ubuntu up front so its faster

---

### Post by bruno9779 on 2011-01-16
Win7 will not install anywhere else than the beginning of the disk. At least it did when it borked my system 1.5 years ago.
Vista was just the same I reckon (but can't remember clearly).

Be careful with the recovery partition it creates. Legacy partitioning is limited to 4 primary partitions. Win7 will create 2 and WILL not tell you about it during the install process. 
If you don't have enough free partitions, it will just choose another partition and will overwrite it.

---

### Post by CharlesA on 2011-01-16
> **SebSmith said:**
> you answered my question perfectly! thank you! now are you familiar with the oem system builder version of win7?
 apparently if you install it multiple times only one version can be on at a time. does this mean that i can just buy one of those disks and use it on my computer AND the VB?

That's not how it works. It is only good for one copy on one machine. IIRC OEM copies cannot be virtualized, but I could be wrong, haven't read up on it in a while.

> and just to clarify, i cannot move my stock manufaturer's installation of windows 7 to the back end of my har drive? i want ubuntu up front so its faster

There is no difference where a partition is located. Just resize the Windows 7 partition and install Ubuntu side-by-side. Backup your data first.

---

### Post by rvchari on 2011-01-16
Originally Posted by SebSmith  
No it did, but it comes stock installed on the small end(front) of hdd. i want windows 7 further back.
thank you very much for that tutorial on grub. i prefer grub loader

but i still dont understand virtual box.


dont use virtual box OSE that is installed from ubuntu software center. it is good to install from virtualbox site, 3.2.10 / 12.
its nice to virtualise and installation is a breeze. OSE gave me lots of nightmares so i resorted to virtualbox site and installed the deb. dont forge to install the guest additions to access ur ubuntu part or data partition which must be in ubuntu part....

virtualbox forums did help me a lot in fine tuning...

---

### Post by 3rdalbum on 2011-01-16
I don't know if the EULA legally prevents OEM copies from being run in a virtual machine, but I have done just that and it works without issues. Windows 7 Home Premium.

Moving anything to "the front of the disk" won't make its access faster. If you're running Ubuntu at the "end of the disk" the hard disk head will stay towards where all your data is anyway.

---

### Post by Spr0k3t on 2011-01-16
> **CharlesA said:**
> That's not how it works. It is only good for one copy on one machine. IIRC OEM copies cannot be virtualized, but I could be wrong, haven't read up on it in a while.

You are correct.  The OEM licensed version of 7 can not be used in a virtual machine (legally).  There are stop points in the installation that prevent it from completing an installation.  Nevertheless, there are hacks to get around it... but that's way outside the scope of these forums as well as code of conduct.

The retail version of 7 on the other hand works very well in a VM.

---

### Post by CharlesA on 2011-01-16
> **Spr0k3t said:**
> You are correct.  The OEM licensed version of 7 can not be used in a virtual machine (legally).  There are stop points in the installation that prevent it from completing an installation.  Nevertheless, there are hacks to get around it... but that's way outside the scope of these forums as well as code of conduct.

The retail version of 7 on the other hand works very well in a VM.

That's what I thought. Thanks. :)

@rvchari: They have VirtualBox 4.0 out and it's pretty nice. :)

---

### Post by slooksterpsv on 2011-01-16
If you use a retail DVD of Windows 7, you can install it and use the CD Key that came with your computer. The only thing you have to do though is you have to call to activate it. It won't activate over the internet.

I don't like the "OEM" software licensing, cause technically, if I'm running it on a VM, the VM is software that is technically using the hardware it was originally installed on. I won't start a fight or a war, but I've installed my Windows 7 that came with my machine in a VM, so I could do Netflix.

---

### Post by 1clue on 2011-01-16
I answered a question awhile back here:  [http://ubuntuforums.org/showpost.php?p=10314280&postcount=3](http://ubuntuforums.org/showpost.php?p=10314280&postcount=3)

An OEM Windows will not work.  You need a separately purchased license, and moreover if you duplicate the VM and then run both copies, you need one license for each.  I go into that more in that link.  I think that thread applies to a whole lot of people, and it seems to be a fairly good discussion on it.

Good luck and have fun.

---

### Post by srs5694 on 2011-01-16
On the issue of start/end of the disk, I personally wouldn't worry about it, but there may be some small disk performance effects. I've seen it go both ways, though -- front faster and end faster -- so you'd need to run some tests to find out what you've got with your specific drive. You could use hdparm for this. Create two partitions of a few megabytes each, one at the front and one at the end of the disk (or use existing partitions, if they're suitably placed); then test them:

```

sudo hdparm -t /dev/sda1
sudo hdparm -t /dev/sda1
sudo hdparm -t /dev/sda1
sudo hdparm -t /dev/sda2
sudo hdparm -t /dev/sda2
sudo hdparm -t /dev/sda2

```

Note that the above example tests performance three times for each location. This minimizes the chance that you'll get bogus results because of some random system activity or other factor that might affect just one test. Average the results, but if one is wildly out of whack with the others, run another couple of tests just to be sure what's what and discard the outlier(s).

If you find differences that are significant enough to concern you, you can move the existing Windows 7 installation to the end of the disk; however, you should *not* use GParted to do this. The reason is that Windows is very finicky about its boot partition, and it won't boot after you move its start point with GParted. I'm not positive, but I think it'll be OK if you use the Windows partitioning tools. Another option is to use a Windows backup utility to back up the Windows partition, then repartition and use the same tool to restore. I used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) to do this once,[/url] and it worked fine. (I needed to create a bootable Windows emergency CD-ROM; the DriveImage XML site has a [page with basic instructions and links.](http://www.runtime.org/peb.htm)) Even if you don't end up moving your Windows partition, IMHO it's well worth putting together the necessary tools and creating a suitable backup; that way, if your drive dies or your Windows installation becomes badly corrupted, you'll be able to restore it without using the manufacturer's recovery disc, which might trash your Linux installation or require you to jump through your initial setup hoops all over again.

---

### Post by Jerry N on 2011-01-17
> **bruno9779 said:**
> 
Be careful with the recovery partition it creates. Legacy partitioning is limited to 4 primary partitions. Win7 will create 2 and WILL not tell you about it during the install process. 
If you don't have enough free partitions, it will just choose another partition and will overwrite it.

If you partition the hard drive BEFORE starting the Win 7 install, Win 7 installs using only one partition.  In my case, I have two computers each running Win XP and Win 7 in dual boot.  Using gparted, I created 3 NTFS partitions, the first for XP, the second for Win 7, and the third for data.  No problems and Win 7 did not create any extra partitions during install. I always us manual partitioning for Linux installs too. 

To the OP:  I don't see the problem.  If Win 7 is already installed, just use Win 7s manager to shrink its partition and use gparted to create the partitions for Ubuntu.  I can't see any benefit to buying a new copy if Windows just to run it in a VM if Windows is already working.  I think you are just asking for trouble.

Jerry

---

