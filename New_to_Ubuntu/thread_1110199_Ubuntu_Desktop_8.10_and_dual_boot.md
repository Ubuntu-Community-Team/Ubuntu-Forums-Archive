---
title: "Ubuntu Desktop 8.10 and dual boot"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by voxmagna on 2009-03-29
Hi, this is my first post. I decided I wanted to 'wet my feet' with Ubuntu. I'm fairly knowledgable with MSDOS and XP but have zero knowledge with a Linux platform, but willing to learn.

I installed a Ubuntu image on a pen drive and after setting the bios boot order for my laptop, was amazed to see a Ubuntu desktop load. Even a usb wifi adapter was recognised and I could browse.

Then I wanted to install a driver for the internal Realtek wifi adapter and realised after a while that since I was using a CD image this wouldn't work and thought I'd have to install Ubuntu to a hard drive partition. 

I have a stable (working!) XP and at the moment this is my first choice of OS and I didn't want the installation compromised by a Ubuntu install. I use Acronis Image Home (AIH) to image the XP partitions and MBR and backed up my HDD before starting.

I went ahead and installed Ubuntu to a separate HDD partition and the pc booted with the Linux menu. I would have prefered XP to be my first choice in the list to autoboot, but that's life! Both XP and Ubunto appeared to be working OK in dual boot mode.

What followed was mega concern: I tried afterwards to do an incremental backup of my hard drive using AIH which runs MS CHKDSK first. If ANY errors are found, the original archives will not be backed up. I've seen similar with Norton Ghost and when a 'diagnostics partition' is installed as on most laptops. The errors cannot be fixed running the CHKDSK /F option.

The MS CHKDSK reported errors to do with the MBR and empty space descriptors not being correct. I recovered the original MBR wiping out the option to run Ubuntu at startup, the disc geometry errors went away and the HDD could be backed up.

My first question is was there an option in the Ubuntu install I missed which would have stopped it modifying my original MBR and preventing later disc backups (MS CHKDSK errors)? Is there an option to install to a partition without modifying the MBR?

I now have Ubuntu Desktop fully installed on a separate partition but can't boot it. I think I need to know in simple terms if and how I can boot it from a flash card/pen drive (it is supported by my bios), as going back to the Ubuntu MBR loader is not an option if my disk geometry becomes non-MS compatible.

I make apologies now for introducing Microsoft syntax in my post, but I am keen to do more with Ubuntu provided I am not compromising my XP setup.

Please help.

---

### Post by fly-by-night on 2009-03-29
If you get no help here try:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

That's the Installation etc section.

---

### Post by Elfy on 2009-03-29
I've never done it that way - but it can apparently be done - have a look here
[http://ubuntuforums.org/showthread.php?t=528181](http://ubuntuforums.org/showthread.php?t=528181)

Now that you have reinstalled the win boot you will have to reinstall grub so that it can be started - boot with the livecd/usb to the ubuntu desktop you installed from then use this to reinstall grub 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

BUT when you get here

grub> setup (hd0)

don't do it - if for example the find grub command gave you 

(hd0,2) use that in the grub> setup command

That will install grub to the partition that ubuntu is installed to.

---

### Post by voxmagna on 2009-03-30
Thanks I'll work through these. I guessed that wiping out grub from the MBR might be part of the problem.

As well as problems with MS backup software, I also couldn't use any MS partition applications - same reason , all do an MS checkdisk before they let you start. I have tried the Gparted utility in Ubuntu and was impressed the GUI looked 'familiar' to me. 

Gparted doesn't seem to worry about MS structure errors or the MBR. Unfortunately, on the large hard drives we have these days, it ran at about the speed of MSDOS partion apps (very very slow) and about the speed before MS added the memory manager to work with bigger chunks and use a larger memory block above the DOS 640K boundary.

Is there a faster partitioning App running under Linux, or can Gparted be configured differently to run faster? 

Thanks

---

