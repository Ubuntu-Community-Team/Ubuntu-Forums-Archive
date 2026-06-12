---
title: "Windows 7, Ubuntu Desktop Edition, and Ubuntu Studio on same computer?"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by taildraggingdog on 2010-12-19
Hello, I've been using Ubuntu Desktop Edition Windows Installer for a couple months and love it. I've been making electronic music with Windows software for years but want to try Linux music software. My question is; can I install Ubuntu Studio on the same computer with Windows 7 and Ubuntu Desktop Edition Windows Installer? I would like to use Ubuntu Desktop for most everything but keep Windows 7 in case I absolutely don't have another option and use Ubuntu Studio only to make music. It sounds straight forward installing Ubuntu Studio alongside Windows 7/Ubuntu Desktop but I wanted to make sure that the 2 versions of Ubuntu wouldn't clash at some level. Any help would be appreciated. Thanks! Bob

---

### Post by CharlesA on 2010-12-19
You can always dual/tri boot.

Since you installed Ubuntu Desktop from inside Windows, you used Wubi, however I'm not sure if you can boot that with GRUB.

---

### Post by ubudog on 2010-12-19
Yes, as long as you have enough space. 

1.  BACKUP EVERYTHING!

2.  Boot the installer and select "Install along with other operating systems".

3.  Reboot, and you should have options to boot into Windows, Ubuntu Desktop, and Ubuntu Studio.  

If you have any questions, just ask, there are many devoted Ubuntuers here that are glad to help.  :p

---

### Post by ubudog on 2010-12-19
I have been beat.  ;)

---

### Post by Sef on 2010-12-19
Depending on your computer's capabilities, you could do virtualizing Ubuntu Studio.

---

### Post by CharlesA on 2010-12-19
> **ubudog said:**
> I have been beat.  ;)
You gave the better answer. ;)

I'm still unsure if you can boot a Wubi install from GRUB, as it uses the Windows boot loader.

@Sef: Valid point as well, and it might be the easiest to do depending on their machine's specs.

---

### Post by ubudog on 2010-12-19
> **Sef said:**
> Depending on your computer's capabilities, you could do virtualizing Ubuntu Studio.

That is also a great idea.  But, you need a really beefy computer if you want it to run fast.

---

### Post by ubudog on 2010-12-19
> **CharlesA said:**
> You gave the better answer. ;)

I'm still unsure if you can boot a Wubi install from GRUB, as it uses the Windows boot loader.

@Sef: Valid point as well, and it might be the easiest to do depending on their machine's specs.

Thanks.

About Wubi, I am not sure either.  It may be possible, to create a grub menu item that points to the Windows boot loader with some options that automatically select Wubi, then starting it.  Just an idea.

---

### Post by taildraggingdog on 2010-12-19
Thanks guys! That's what I'm going to do; just install alongside the Windows7/Ubuntu Desktop system. I'll back things up but already have all my music software and samples on external drives. It's a new computer and has a 1TB hard drive. I'm excited about this.

---

### Post by Eiji Takanaka on 2010-12-19
Has a real-time kernel been released for 10.10 yet? 

Mega low-latency audio engineering is a massive asset to linux systems, normally an external sound-card is required to achieve similar latency times. 

- dan

---

### Post by ubudog on 2010-12-19
> **taildraggingdog said:**
> Thanks guys! That's what I'm going to do; just install alongside the Windows7/Ubuntu Desktop system. I'll back things up but already have all my music software and samples on external drives. It's a new computer and has a 1TB hard drive. I'm excited about this.

Cool.

---

### Post by wilee-nilee on 2010-12-19
> **taildraggingdog said:**
> Thanks guys! That's what I'm going to do; just install alongside the Windows7/Ubuntu Desktop system. I'll back things up but already have all my music software and samples on external drives. It's a new computer and has a 1TB hard drive. I'm excited about this.

Just remember the partition limitations on a single HD. 4 primaries maximum or 3 primaries and one extended that can have a unlimited amount of logicals. So I hope you have the logical wrapped around all the Linux now, not just the swap. Look in gparted and post a screen shot of it if needed.

---

### Post by taildraggingdog on 2010-12-20
Wilee, I think I know what you mean but I want to double check. So right now I have Windows 7 and Ubuntu 10.10 Desktop Edition for which I used the windows installer. At this point I have no partitions because Ubuntu is installed within Windows. I'm going to install Ubuntu Studio on this computer. I'm not going to use any partitioning software. When I'm installing Ubuntu Studio I'm going to chose "install alongside other operating systems". I'll use the Ubuntu installer to "allocate drive space" and have Windows 7/Ubuntu Desktop on one partition and Ubuntu Studio on the other. Then when I turn on the computer I'll be given the choice to go to Windows 7 or Ubuntu Desktop or Ubuntu studio. Is this right? Will this work? Thank you for your help everyone. Bob

---

### Post by CharlesA on 2010-12-20
> **taildraggingdog said:**
> Wilee, I think I know what you mean but I want to double check. So right now I have Windows 7 and Ubuntu 10.10 Desktop Edition for which I used the windows installer. At this point I have no partitions because Ubuntu is installed within Windows. I'm going to install Ubuntu Studio on this computer. I'm not going to use any partitioning software. When I'm installing Ubuntu Studio I'm going to chose "install alongside other operating systems". I'll use the Ubuntu installer to "allocate drive space" and have Windows 7/Ubuntu Desktop on one partition and Ubuntu Studio on the other. Then when I turn on the computer I'll be given the choice to go to Windows 7 or Ubuntu Desktop or Ubuntu studio. Is this right? Will this work? Thank you for your help everyone. Bob

Windows 7 usually has 2 partitions, a boot partition and a partition for the rest of the OS. If your machine is from an OEM, you probably have a recovery partition as well.

In any case, that's fine, as using the Install Side-By-Side will resize the Windows partition and install Ubuntu. Just be sure to backup your data before you mess with partitions.

---

### Post by cchhrriiss121212 on 2010-12-20
A few tips:

[LIST=1]
[*] There is no point installing Studio on a separate partition alongside regular Ubuntu as every piece of software in Studio can be installed and used on Ubuntu. Just pick one or the other, they are essentially the same OS with a different theme and extra packages.
[*]You can even upgrade an Ubuntu install into Ubuntu Studio, just search for the meta-package in the software center.
[*]It is always better to use a "real" install instead of WUBI
[*]Virtualising an OS to do audio work is not a good idea, you will not get acceptable performance or stability.
[*]Other things to know about Studio: it does not use the same installer as Ubuntu, it is text-based and you might find it more difficult; it has no network manager so it will not pick up any wireless network.
[/LIST]
There is no downside to doing what you have planned, but I just thought you should know this stuff.

---

### Post by Jerry N on 2010-12-20
> **CharlesA said:**
> Windows 7 usually has 2 partitions, a boot partition and a partition for the rest of the OS. If your machine is from an OEM, you probably have a recovery partition as well.

Just for information, Win 7 does not require 2 partitions.  The two computers on which I installed Win 7 from scratch have only one partition for Win 7 and I don't even recall being asked if I wanted a boot partition.  On the other hand, my HP netbook has a boot partition, a Win 7 partition, a recovery partition, and an HP partition.  A proper dual boot on that machine would require removal of one of the partitions, although I probably won't bother because the tiny screen on that machine doesn't enthuse me much anyway.

Jerry

---

### Post by CharlesA on 2010-12-20
> **Jerry N said:**
> Just for information, Win 7 does not require 2 partitions.  The two computers on which I installed Win 7 from scratch have only one partition for Win 7 and I don't even recall being asked if I wanted a boot partition.

32-bit or 64-bit? On all the machines I have installed Win7 on, the installer has reserved a 100MB partition for the boot files.

---

### Post by cchhrriiss121212 on 2010-12-20
> **CharlesA said:**
> On all the machines I have installed Win7 on, the installer has reserved a 100MB partition for the boot files.
I can vouch for this as well, it is all done automatically whether you would like it or not.

---

### Post by Jerry N on 2010-12-20
> **CharlesA said:**
> 32-bit or 64-bit? On all the machines I have installed Win7 on, the installer has reserved a 100MB partition for the boot files.

I just rechecked to make sure I wasn't lying - I even booted PartedMagic on my secondary computer.  These installations are 32 bit Windows 7 and both Win 7s disk manager and PartedMagic report the same:  Sda1 is an NTFS partition with Windows XP installed, Sda2 is an NTFS partition with Windows 7 installed, and Sda3 is an NTFS data partition.  Mint and Ubuntu are on a different drive in my secondary computer so with the present setup I use the F12 key during bootup to select which drive to boot from.  Quad boot.

No Win 7 boot partition anywhere I can find it.  Do you suppose the fact that I used PartedMagic to pre-partition the drive rather than letting Win 7 do the partitioning has anything to do with it?  On the older computer, I used PartedMagic to shrink the Win XP partition and created a new NTFS partition for Win 7.  On the newest computer, I used PartedMagic to create the three NTFS partitions to start with, installed Win XP, and then installed Win 7.

PS - I just did a bit of googling and it does seem that the boot partition can be avoided by partitioning the drive before Win 7 is installed.  I wonder if my Win 7 installs are in some kind of danger?? :o

Jerry

---

### Post by CharlesA on 2010-12-20
> **Jerry N said:**
> 
PS - I just did a bit of googling and it does seem that the boot partition can be avoided by partitioning the drive before Win 7 is installed.  I wonder if my Win 7 installs are in some kind of danger?? :o

Lol I doubt it's in any danger. ;)

Kinda makes sense if you already have a partition in place.

Thanks for confirming. :)

---

### Post by wilee-nilee on 2010-12-20
If you have a pre-formatted partition NTFS for windows, built by say gparted and a boot flag W7 installs to one partition.

Here is my sda1 per the bootscript, the boot that would be in the extra 100-200mib partition is highlighted.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

I pre-formatted sda1 it installed in it completely.

---

### Post by Jerry N on 2010-12-20
> **wilee-nilee said:**
> If you have a pre-formatted partition NTFS for windows, built by say gparted and a boot flag W7 installs to one partition.

How about that - I was doing something right and didn't even know it!!!  Serendipity strikes again;);););)  

Actually, I started pre-partitioning and formatting drives for Windows installs primarily because gparted does it much faster than Windows.

Jerry

---

### Post by ubudog on 2010-12-21
> **Jerry N said:**
> How about that - I was doing something right and didn't even know it!!!  Serendipity strikes again;);););)  

Actually, I started pre-partitioning and formatting drives for Windows installs primarily because gparted does it much faster than Windows.

Jerry

Lol, nice.

---

