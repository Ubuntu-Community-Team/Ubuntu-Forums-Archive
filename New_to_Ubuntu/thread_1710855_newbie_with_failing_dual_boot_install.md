---
title: "newbie with failing dual boot install"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by misfit54 on 2011-03-20
Hi there. I would like to learn to use Ubuntu but I have failed installs for the last day now. I have read many threads with no solutions. I have "tried" Ubuntu then tried to install from it, nada. I have tried installing from iso cd, nada. I have tried installing from files on hd, nada. I've been using Wubi with 10.10 amd 64 iso. Everything goes fine till I reboot and then I get error message that it can't find the iso. Any help would be greatly appreciate.

---

### Post by fabricator4 on 2011-03-20
> **misfit54 said:**
>  with 10.10 amd 64 iso. Everything goes fine till I reboot and then I get error message that it can't find the iso. Any help would be greatly appreciate.

It seems that a few people have been experiencing problems with 10.10.  There's a known problem with the dual boot installer when used on a Windows machine.  The Wubi installer _should_ have worked and it's a good way to get your feet wet.  You were booting Windows, then letting the autorun install into Windows weren't you?

Apart from that, if you're having problems I suggest you get the ISO for 10.04 LTS and trying that.  It's very stable and works well.  In addition, seriously consider using the 32 bit version for now.  While the 64 bit versions are much more mainstream now than they were two years ago the 32 bit version in the conservative approach.

Chris

---

### Post by wilee-nilee on 2011-03-20
If you have tried from the try it mode you booted the media correct? You have to preformat the space for it, and you have to be aware of several things, such as partition types and the limitations of how many. You also want to be aware of where the Ubuntu bootloader goes.

Sounds daunting if you don't know these things, it is understandable though with a little explanation.

So decide whether you want the wubi or a real dual boot from the booted media. If you want the dual boot, then boot the live Ubuntu media and take a screen shot of the gparted partitioner in the Ubuntu menu-system-admin.

---

### Post by misfit54 on 2011-03-20
OK I downloaded 10.04 LTS 32 bit and booted to it. I am running of the cd. When I go to Gparted, it doesn't recognize any devices. I have a 75gb ntfs partition that has been formatted and chkdsk. Any suggestions?

---

### Post by wilee-nilee on 2011-03-20
> **misfit54 said:**
> OK I downloaded 10.04 LTS 32 bit and booted to it. I am running of the cd. When I go to Gparted, it doesn't recognize any devices. I have a 75gb ntfs partition that has been formatted and chkdsk. Any suggestions?

So gparted shows the whole hd as unallocated?

---

### Post by misfit54 on 2011-03-20
> **wilee-nilee said:**
> So gparted shows the whole hd as unallocated?

Gparted shows no devices at all.

---

### Post by DougieFresh4U on 2011-03-20
> **wilee-nilee said:**
> 

So decide whether you want the wubi or a real dual boot from the booted media. If you want the dual boot, **then boot the live Ubuntu media and take a screen shot of the gparted partitioner in the Ubuntu menu-system-admin.**

> **misfit54 said:**
> Gparted shows no devices at all.
See above quote
And please post 'screen shot'

---

### Post by misfit54 on 2011-03-20
I tried to take a screenshot. It locked up and said something was missing for a screenshot. Gparted shows no drives.

---

### Post by cmcanulty on 2011-03-20
Are you sure you hve set the computer to boot to the CD? Try f2 or f10 as soon as you power up.Thwn you should put boot to cd 1st, save changes  and restart

---

### Post by misfit54 on 2011-03-20
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][ATTACH]186681[/ATTACH]

---

### Post by misfit54 on 2011-03-20
When I try to install from the cd, it goes through the clock, the keyboard layout and then it gets to the "Prepare partitions" window. On that window it shows nothing as well. The screenshot above if from running from the cd is the "try it" option.

---

### Post by cmcanulty on 2011-03-20
I had that happen on an old machine, fixed it with booting from flash stick with Unetbootin real easy to create an image just set it to boot to Usb drive or ext drive there is a flash drive startup utility in Ubuntu also but this one works better for me
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by misfit54 on 2011-03-20
Right now I'm downloading Gparted live so I can make my partition in linux form. I'm thinking this is why it's not recognizing any devices. I didn't see any info on doing this before installing Ubuntu.

---

### Post by fabricator4 on 2011-03-21
> **misfit54 said:**
> [IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][ATTACH]186681[/ATTACH]

Weirdest thing I've seen yet!

---

### Post by cmcanulty on 2011-03-21
This freeware works in windows and will do ext3 I used it then used gparted from Ubuntu to change to ext4
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by misfit54 on 2011-03-21
> **cmcanulty said:**
> This freeware works in windows and will do ext3 I used it then used gparted from Ubuntu to change to ext4
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Thanks for the reply and the information. So I go to your link and when you click on DONWLOAD, all it does is refresh the page, go figure. I downloaded and booted to the boot cd for this partitioner and when it's loading it gives me the error message that 
"This bootable CD does not support Windows server." 
Well I'm not running a server. I am including a screenshot of my disk management window. Maybe this will help in my dilemma.

[IMG]file:///F:/Users/Drew/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///F:/Users/Drew/AppData/Local/Temp/moz-screenshot-1.png[/IMG][IMG]file:///F:/Users/Drew/AppData/Local/Temp/moz-screenshot-2.png[/IMG]

---

### Post by misfit54 on 2011-03-21
Ok I can understand why I see posts of people getting frustrated. I've been searching and downloading different programs so that I can install Ubuntu with Windows 7. I still am unable to create or mount any Linux partitions never mind installing Ubuntu. So if anyone has ANY  suggestions for a dual boot for this please let me know. Thanks in advance. I think I'll go grab a beer.

---

### Post by Hero1969 on 2011-03-21
Just curious, are you trying to triple boot?   In your disk management screen, I see winxp and win7.

---

### Post by misfit54 on 2011-03-21
> **Hero1969 said:**
> Just curious, are you trying to triple boot?   In your disk management screen, I see winxp and win7.

Well I don't use xp anymore and it was just laying there. Today I started moving all docs and pics over from the xp partition and I will be formatting that. I know that I'll have to change the boot record.

---

### Post by Quackers on 2011-03-21
What pc are you using please? What motherboard and sata controller? Are you using a raid array?

---

### Post by misfit54 on 2011-03-21
> **Quackers said:**
> What pc are you using please? What motherboard and sata controller? Are you using a raid array?

It's a small built pc.
AMD 9500 Quad-core
Nvidia 8600GT
4 gig Ram
I'm not running RAID.
Don't know the MB or the SATA controller.

---

### Post by oldfred on 2011-03-21
Be aware that windows combines all its boot files for multiple installs into the one install that has the boot flag. If that is the install you delete, then you cannot boot the other as its boot files are gone. You then have to repair the second install. But if the second install is in a logical partition, windows will not repair it.

Since you have used all 4 partitions, you will have to delete one to create the extended partition for all the logicals needed to install Ubuntu.

Do not create partitions in windows as it will convert to type SFS or dynamic which is a proprietary Microsoft type that does not work with Ubuntu.

My XP install was booting without issue. But gparted would not see it. After I ran chkdsk then gparted saw it. Try chkdsk on all NTFS partitions.

---

### Post by misfit54 on 2011-03-30
Ok I figured out why none of the linux partitioning programs could see my hard drives.
It was in the BIOS. Under **Onboard Devices Settings, **the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there was my hard drives. I now have a dual boot with Ubuntu and Win7.

---

### Post by Quackers on 2011-03-30
Excellent :-)  That's a new one on me!

---

