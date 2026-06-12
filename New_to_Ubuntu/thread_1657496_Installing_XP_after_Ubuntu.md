---
title: "Installing XP after Ubuntu?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by kramer65 on 2011-01-01
Hello,


Ubuntu 10.04 is the only OS on my pc, but I now want to install Windows XP next to it (to use Ableton). I once did it before and I remember I had to restore Grub somehow, but I have no clue what and how I did that before (was years ago).

Can anybody help me out on what I should do before I install xp? Do I need to backup some kind of specific Grub file or something? And what do I do after I've installed XP?

---

### Post by SonicSteve on 2011-01-01
> **kramer65 said:**
> Hello,


Ubuntu 10.04 is the only OS on my pc, but I now want to install Windows XP next to it (to use Ableton). I once did it before and I remember I had to restore Grub somehow, but I have no clue what and how I did that before (was years ago).

Can anybody help me out on what I should do before I install xp? Do I need to backup some kind of specific Grub file or something? And what do I do after I've installed XP?

During the setup of ubuntu at the end before you commit to it and start copying files there is an advanced option to install grub to a partition. 

A few questions though. 
1. Do you have partitions setup for XP? If not you'll be in trouble. XP can't see any of Ubuntu's file systems at least not during setup.  Which means if you don't have a spare partition for XP's files you'll boot up and have to nuke Ubuntu. 

The prefered method of dual booting is 

Any version of windows first. Setup all needed partitions.
Then any version of Linux second since it knows what windows file systems are. 

Doing it the reverse like your doing is possible but much more tricky.

---

### Post by kramer65 on 2011-01-01
Hi Sonicsteve. I know it's better to first install Ubuntu after XP, but that's not an option now. I've got Ubuntu installed with a separate / and /home partition. Next to tose two I've got a ext3 partition which I don't need anymore. So I want to "nuke" that partition and use it for XP.

So even if it is more dificult, do you know how it is possible to restore Grub after installing XP?


btw, Nice avatar! :-)

---

### Post by alexan on 2011-01-01
Ubuntu Live CD > Gparted > resize ubuntu partition(s) to make space for Windows
Windows CD > Install in the freed space
[print this](https://help.ubuntu.com/community/Grub2) (for reference) > Ubuntu Live CD > restore Grub2



Optionally:
before anything, try with virtualbox*ing* XP in ubuntu (guest addition allow you increase perfomance, having the XP taskbar -transparently- in Ubuntu etc.etc)

Option2:
Ableton 7.0.3 is working [platinum](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113) in Wine (almost perfectly, by sure smoothly)

---

### Post by kramer65 on 2011-01-01
Hi Alexan. Thanks for the information. I didn't know that Ableton works so well under wine. The thing is that I want to use a midi-keyboard as well, and I've been struggeling with Jack and patchage and all that stuff a bit too long. This is why I now just want to boot into XP whenever I want to make music. For the rest I use Ubuntu.

About the third point; "Ubuntu Live CD > restore Grub2". I scrolled through the lin kyou gave, but I'm kinda lost. Could you possibly point me at the part which I need to use..? :-k

---

### Post by presence1960 on 2011-01-01
I don't know why people just do not answer your question. 

First you will need to create an NTFS partition or unallocated space onto which you can install windows. Then boot the windows CD/DVD and install there. After windows is installed make sure it runs fine. next you will need to reinstall GRUB.

To reinstall GRUB2 after installing windows is a 30 second procedure after booting from the ubuntu Live CD by opening a terminal and running these 2 commands:

```
sudo mount /dev/sdxy /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```

of course substitute your partition designations for xy for each command. Mine would be /dev/sda7 for the first command and sda for the second command.

You asked about reinstalling GRUB after installing windows, that is a pretty straightforward request. I will not try to steer you away from windows as there is no shame at all in running windows. Hope this answered your question.

---

### Post by presence1960 on 2011-01-01
> **kramer65 said:**
> Hi Sonicsteve. I know it's better to first install Ubuntu after XP, but that's not an option now. I've got Ubuntu installed with a separate / and /home partition. Next to tose two I've got a ext3 partition which I don't need anymore. So I want to "nuke" that partition and use it for XP.

So even if it is more dificult, do you know how it is possible to restore Grub after installing XP?


btw, Nice avatar! :-)

It is not "better" to install windows first! That is a "myth" perpetrated by those who do not understand what happens when you install windows after ubuntu.

The only thing that happens when you install windows after ubuntu on the same hard disk is that windows overwrites GRUB on the MBR leaving you not able to boot linux. The fix is a 30 second procedure which after booting the ubuntu Live CD/USB you run 2 commands in terminal and GRUB is back on the MBR and your dual boot or multiboot setup is functional.

Another reason people think it is better to install windows first is that some install linux on  computer that has windows preinstalled and they think that because they did it this way that is the "better" way!

---

### Post by SonicSteve on 2011-01-01
> **presence1960 said:**
> It is not "better" to install windows first! That is a "myth" perpetrated by those who do not understand what happens when you install windows after ubuntu.

The only thing that happens when you install windows after ubuntu on the same hard disk is that windows overwrites GRUB on the MBR leaving you not able to boot linux. The fix is a 30 second procedure which after booting the ubuntu Live CD/USB you run 2 commands in terminal and GRUB is back on the MBR and your dual boot or multiboot setup is functional.

Another reason people think it is better to install windows first is that some install linux on  computer that has windows preinstalled and they think that because they did it this way that is the "better" way!

I almost don't want to respond to this since it will seem defensive. 

It is far easier to install windows first since Linux will see it and take care of the boot options for you. As the first post points out most people don't know about the live CD option to restore grub. Nor do they know the command line options. While those aren't really harder to use their far less known. That's why "we" recommend windows first.

---

### Post by waynefoutz on 2011-01-01
> **SonicSteve said:**
> I almost don't want to respond to this since it will seem defensive. 

It is far easier to install windows first since Linux will see it and take care of the boot options for you. As the first post points out most people don't know about the live CD option to restore grub. Nor do they know the command line options. While those aren't really harder to use their far less known. That's why "we" recommend windows first.

I've been using Ubuntu since 7.04, I had no idea that they added a "restore grub2" option to  the live CD. I've always used the command line to do this. This is nice to know. Did they add this to 10.10 recently?

---

### Post by kramer65 on 2011-01-01
Hi Guys. I decided to go ahead and install windows. I've got 4 partitions on my hard disc;
sda1 (/ with ubuntu)
sda2 (/home partition)
sda3 (swap)
sda4 (ext3 storage, not needed anymore)

I wanted to install XP on sda4, so I booted the XP disc and deleted the sda4 partition in order to install XP on it. It then said that it couldn't create a new partition since the maximum number of partitions was already in place (so I guess the max is 3?).

So now I'm stuck. I don't know how to proceed with the installation of XP, and even worse; I can't boot into Ubuntu anymore (I'm now using the live CD to write this). When I now boot my pc it says that it cannot load the operating system.

Does any of you know what to do from here? Is there any way that I can install XP anyway without touching the Ubuntu installation? And more importantly, how to get it to boot Ubuntu again (but I guess that should be done after the XP installation)?

All help is welcome!

---

### Post by waynefoutz on 2011-01-01
> **kramer65 said:**
> Hi Guys. I decided to go ahead and install windows. I've got 4 partitions on my hard disc;
sda1 (/ with ubuntu)
sda2 (/home partition)
sda3 (swap)
sda4 (ext3 storage, not needed anymore)

I wanted to install XP on sda4, so I booted the XP disc and deleted the sda4 partition in order to install XP on it. It then said that it couldn't create a new partition since the maximum number of partitions was already in place (so I guess the max is 3?).

So now I'm stuck. I don't know how to proceed with the installation of XP, and even worse; I can't boot into Ubuntu anymore (I'm now using the live CD to write this). When I now boot my pc it says that it cannot load the operating system.

Does any of you know what to do from here? Is there any way that I can install XP anyway without touching the Ubuntu installation? And more importantly, how to get it to boot Ubuntu again (but I guess that should be done after the XP installation)?

All help is welcome!

You have to install Grub2 again, since Windows wiped it out. The other posters are saying there is a "restore grub2" item in the menus on the Live CD. If it is, use that, if not, use this guide:


[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by brookie on 2011-01-01
Hope you can get it all sorted but just an fyi, this site helped me out much when I did some dual boots, linux first then xp.
cheers, 
brook

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

ps...that link is older and dealing with grub not grub2 as  in lucid but it may still be of help. grub2 configuration is different than grub. no more menu.lst file in grub2. lots of posts on grub2 in the forums though.

---

### Post by SonicSteve on 2011-01-01
QUOTE=waynefoutz;10304221]I've been using Ubuntu since 7.04, I had no idea that they added a "restore grub2" option to  the live CD. I've always used the command line to do this. This is nice to know. Did they add this to 10.10 recently?[/QUOTE

Sorry guys I would have to boot up the older versions to see if things have changed. The 10.10 install does have an advanced option but it only allows you to choose which disk grub will be installed to. You have to install ubuntu over top of itself to use this option. So it's not really an option to get this done for you. 

The live CD is a great way to install grub again but not through the installer like I thought. 

Sorry.

---

### Post by kramer65 on 2011-01-01
Ok, I restored Grub again and I am able to boot into Ubuntu again. 

I still want to install Windows onto my pc though. Attached you see two photos I made of my screen. On the first you see the partitions I have. I want to install XP on the selected Unpartitioned Space. On the second photo you see the error which I am getting. I understand that this is not a Windows forum, but I would really really appreciate it if anybody knows how I can solve this? :-?

Any tips or ideas are welcome..

---

### Post by kramer65 on 2011-01-01
Ok, I now [found]("http://forums.anandtech.com/archive/index.php/t-1795220.html") that the limitation I'm bumping into isn't really OS specific. Appearently there are only four lines in the partition table so you can only have 4 primary partitions.

However, I obviously only have 3 partitions (/, /home and swap) so a fourth one shouldn't make any trouble. Anybody any idea what to do now..? Any tips, hints directions I could look for? :S

---

### Post by gmenfan83 on 2011-01-01
> **kramer65 said:**
> Ok, I now [found]("http://forums.anandtech.com/archive/index.php/t-1795220.html") that the limitation I'm bumping into isn't really OS specific. Appearently there are only four lines in the partition table so you can only have 4 primary partitions.

However, I obviously only have 3 partitions (/, /home and swap) so a fourth one shouldn't make any trouble. Anybody any idea what to do now..? Any tips, hints directions I could look for? :S
this may be of help to you....you can do it using gparted from your live ubuntu cd,,,,,,,i am no expert but i THINK you can create an extended partition for your linux and put /swap in it then have / home on its own the create your ntsf partition for windows..heres the link

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by kramer65 on 2011-01-01
Alright. I solved the issue by booting into Ubuntu and creating a ntsf-partition in the unused space using Gparted. After that I could install XP on it which ran perfectly well. I then booted back into the Ubuntu live-cd and restored grub using the commands presence1960 gave before: "sudo mount /dev/sda1 /mnt" and "sudo grub-install --root-directory=/mnt/ /dev/sda".

The problem is now that it again automatically boots into Ubuntu. I just see a black screen with a blinking cursor for a couple moments after which it boots into Ubuntu. Any idea what's wrong with grub here?

---

### Post by ac7nj on 2011-01-01
I'm reluctant to respond but here goes:

When Microsoft any version from DOS 1.1 to Windows 7 installs the drive needs a partition table and it has to be in the specific location or it will not work at all.

Linux can not only see the windows partition it's partition can be located at any mount point on the disk. Hense the Windows first recommendation. 

what to do:

First you will need to learn what windows needs for space and where it has to go. Next you will have to re-partition the disk.

Lastly set up a boot manager to choose between Linux and Windows

Randy
ac7nj

---

### Post by presence1960 on 2011-01-01
> **kramer65 said:**
> Alright. I solved the issue by booting into Ubuntu and creating a ntsf-partition in the unused space using Gparted. After that I could install XP on it which ran perfectly well. I then booted back into the Ubuntu live-cd and restored grub using the commands presence1960 gave before: "sudo mount /dev/sda1 /mnt" and "sudo grub-install --root-directory=/mnt/ /dev/sda".

The problem is now that it again automatically boots into Ubuntu. I just see a black screen with a blinking cursor for a couple moments after which it boots into Ubuntu. Any idea what's wrong with grub here?

Need to see your setup & boot process. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by presence1960 on 2011-01-01
> **ac7nj said:**
> I'm reluctant to respond but here goes:

[B][U]When Microsoft any version from DOS 1.1 to Windows 7 installs the drive needs a partition table and it has to be in the specific location or it will not work at all.

Linux can not only see the windows partition it's partition can be located at any mount point on the disk. Hense the Windows first recommendation. [/U][/B]

what to do:

First you will need to learn what windows needs for space and where it has to go. Next you will have to re-partition the disk.

Lastly set up a boot manager to choose between Linux and Windows

Randy
ac7nj

Not true, I have had versions of XP, Vista, 7 & w2k on sda1, sda2, sda3 & sda4 at various times in tandem with ubuntu & sabayon. The only requirement is that it be a primary partition and a windows file system. Currently on my daughter's machine she has ubuntu  on sda1, win 7 on sda2 & XP on sda3. All boot fine with GRUB 2.

---

### Post by ac7nj on 2011-01-03
> **presence1960 said:**
> Not true, I have had versions of XP, Vista, 7 & w2k on sda1, sda2, sda3 & sda4 at various times in tandem with ubuntu & sabayon. The only requirement is that it be a primary partition and a windows file system. Currently on my daughter's machine she has ubuntu  on sda1, win 7 on sda2 & XP on sda3. All boot fine with GRUB 2.

Maybe you didn't understand what I was saying so here is a graph of what I was trying to say windows has to look like this

Structure of a master boot record 					
Address			Description		Size in bytes
Hex	Oct	Dec			
0	0	0	code area		440
(max. 446)
01B8	670	440	disk signature (optional)		4
01BC	674	444	Usually nulls; 0x0000		2
01BE	676	446	Table of primary partitions
(Four 16-byte entries, IBM partition table scheme)		64
01FE	776	510	55h	MBR signature;
0xAA55	2
01FF	777	511	AAh		
MBR, total size: 446 + 64 + 2 =					512

Randy AC7NJ

---

### Post by presence1960 on 2011-01-03
> **ac7nj said:**
> Maybe you didn't understand what I was saying so here is a graph of what I was trying to say windows has to look like this

Structure of a master boot record 					
Address			Description		Size in bytes
Hex	Oct	Dec			
0	0	0	code area		440
(max. 446)
01B8	670	440	disk signature (optional)		4
01BC	674	444	Usually nulls; 0x0000		2
01BE	676	446	Table of primary partitions
(Four 16-byte entries, IBM partition table scheme)		64
01FE	776	510	55h	MBR signature;
0xAA55	2
01FF	777	511	AAh		
MBR, total size: 446 + 64 + 2 =					512

Randy AC7NJ

Sorry Randy, I definitely misinterpreted what you originally said. I guess that is my fault because I am appalled at the "myth" that a lot perpetrate on here, namely that you "must" install windows before linux to set up a dual boot. I almost always set up linux first after partitioning the hard disk exactly how I want it laid out. I get linux tweaked the way I want then install windows. Installing GRUB to MBR after installing windows is a "hassle" that takes all of 30 seconds.

I realize that a good number in here installed linux on a machine that had windows pre-installed and decided to opt for a dual boot set up. However just because those people were obliged to install linux "after" windows does not mean that you "must" do it in that order nor is it "harder" to install windows after linux. A quote I love says "There is a principle that will forever keep a man in everlating ignorance and that is a bar to all information. That principle is contempt prior to investigation.

---

