---
title: "Can't build bootable HD install of 9.04"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by paulbyr on 2009-06-17
Hi, I have a Gigabyte MB desktop with an AMD Athlon 64 X2, 3GB RAM, several SATA HDs one of which is called disk 1 by my PartitionMagic 8.0.  It had nothing on it before I tried to install 9.04 from the LiveCD.  Now, after "install" from Live CD it has a Linux X3 partition with 143GB and 6GB of Linux swap partition.   (What PartitionMagic calls disk 2 is my C:\ with XP on it and an E:\partition for data).  BTW, using LiveCD-Games let me play blackjack for a long time before I tried to install - fun!. 

When I tried rebooting to use the (what I thought was) installed UBUNTU, I clicked on UBUNTU instead of Windows XP and immediately got the following message:

MISSING or CORRUPT
Windows.root>\System32\hal.dll
Please Reinstall a copy

I can reboot and select Windows XP and continue as normal with no trouble.

In reading these posts, I find myself getting more and more confused.  I didn't understand how to do the checksum - should I use the value for AMD64 or for i386?  Should I have done something with GRUB or not?   I didn't see how to do anything with GRUB, just that it was for boot partitions. There doesn't seem to be a step by step that I can make work.  Yes, I did write my CD at X2 speed - I used my ImgBURN software + verify and it seemed to work fine.

Should I use BootMagic to create the bootable partition before I install UBUNTU from my LivecCD?

I think the install is harder than using the many available apps is going to be.  I am looking forward to the exploration.

Thank you for your help.

Paul

---

### Post by LewRockwell on 2009-06-17
you'll use the checksum from whichever version you downloaded

in terminal, what's the output of:

```
sudo fdisk -l
```

that's a little "L" and not a one, btw

---

### Post by gn2 on 2009-06-17
> **paulbyr said:**
> Should I use BootMagic 

If it's anything like the version of it that I dabbled with in 2005/6 you should remove it from your system completely.

Fairly comprehensive information on setting up a dual-boot at [Hermanzone]("http://members.iinet.net/~herman546/index.html"), it's the best resource for information on dual-booting that I know of.

---

### Post by paulbyr on 2009-06-17
I am really one of the people for whom this "Absolute Beginner Talk" was designed.  I appreciate the time and good intentions of the first two replies but I have no idea where to type in the command line suggested nor why I would do it.  I went to the suggested Herman link and this is part of what it told me to do:

[I]First, let me explain the main thing you'll need to understand. Remember back when you installed Ubuntu? I don't know about you, but I always choose to install the 'IPL' for the GRUB bootloader to [MBR]("http://members.iinet.net.au/%7Eherman546/p6.html#What_does_an_IPL_really_look_like") on my hard disk during the install. The MBR is in the first sector of our hard disks. One sector of  a hard disk is 512 bytes in size. 
   The MBR contains three important parts. One is the hard disk's 64 byte partition table,  and another is the 2 byte 55aa signature to indicate to the BIOS that it is a bootable device. [/I]

Since I have not yet been able to install Ubuntu I don't know how to choose the IPL (what does that mean?) for the GRUB bootloader.  I think MBR is main(?) Boot Record.

If you noticed, I was asking how do I get a boot record on my HD.  I thought the graphic installer (I may have forgotten exactly it's called) on the LiveCD would create the boot record but it apparently didn't.

Anyhow, if this isn't the real Abosolute Beginner Talk forum, please route me to it as I obviously need it's help.

Thank you so much.

By the way, I have never been a UNIX programmer although I programmed in FORTRAN IV many years ago.  I used VAX 11-780  long ago too.  Since then, it's been sorry old Microsoft:(

---

### Post by gn2 on 2009-06-17
Did you already have Boot Magic installed when you installed Ubuntu and did you use Boot Magic at any time during the installation process?

---

### Post by Jazzy_Jeff on 2009-06-17
I am not sure what you are doing. Let us get some information. Did you reboot your system and run the Live CD to do your install? Or did you run the disk from within Windows? 

You should have just booted from the live cd and installed from there. You would have been able to set up the partitions during the install. Let us know how you did the install.

---

### Post by Therion on 2009-06-17
I'm a little confused myself on what you have and where you are so yeah, lets try and keep this simple.

It sounds like you have a hard drive you can wipe totally and install Ubuntu on.  Doesn't matter what's on it now as long as you're willing to wipe it totally and run nothing but Ubuntu on it.  This drive... Install it.  If it already is, so much the better.

Put your Ubuntu LiveCD in drive and boot from it.  Select "Install Ubuntu" from the main menu, follow the prompts and just take the defaults as they are offered.  Don't worry about fancy partitioning schemes and bootloaders and all that, just follow the prompts.  

Select the install option for "**Guided - Use entire disk**" when you're asked and when everything is said and done you should have a fully operational Ubuntu OS running your PC.

---

### Post by paulbyr on 2009-06-17
Therion, thank you, I will first uninstall BootMagic from my computer (although I never used it) and then I will use PartitionMagic 8.0 to clean the disk of everything.  Then I will follow your instructions.  Again, thank you.
Paul

---

### Post by gn2 on 2009-06-18
You don't need to use Partition Magic or Boot Magic.
The Ubuntu installer will wipe the drive for you if you use the "Guided - Use entire disk" option as suggested by Therion.

---

### Post by paulbyr on 2009-06-18
Well, I followed the directions and Therion's guidance and got the exact same results as before.  (see above). 

Can it be that I need to change my BIOS settings for booting to do something else to recognize HD #1 (the Ubuntu disk) when I select Ubuntu on the boot up screen?

---

### Post by LewRockwell on 2009-06-18
> **paulbyr said:**
> Well, I followed the directions and Therion's guidance and got the exact same results as before.  (see above). 

Can it be that I need to change my BIOS settings for booting to do something else to recognize HD #1 (the Ubuntu disk) when I select Ubuntu on the boot up screen?

I think you should make a super grub disk and attempt to boot into Ubuntu with it.

You'll find the download and documentation here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by paulbyr on 2009-06-18
OK, I solved the problem, I don't know why though.
I went into BIOS (AWARD) and switched the priority of the HD booting order so now the HD with Ubuntu on it is first and the one with Windows XP is second.  

It now starts up with GRUB and several choices of Ubuntu and then at the bottom is Windows XP.  

Of course I've been playing with Ubuntu and haven't tried to boot the Win XP yet.  Hope it works.

Thank you for all the support - I am sure I will ask for more soon.

Paul

---

### Post by paulbyr on 2009-06-19
> OK, I solved the problem, I don't know why though.
I went into BIOS (AWARD) and switched the priority of the HD booting order so now the HD with Ubuntu on it is first and the one with Windows XP is second. 
 
Sure enough, XP wouldn't boot so I had to change the boot sequence back to Win XP first to use Win XP. (Now Ubuntu won't boot, as described above.)
 
Maybe I am going to have to build a Ubuntu Only box? I would hate to have to devote office space to another box. 
 
I can't be the only beginner who has had trouble setting up dual boot on a box that already had Win XP installed.
 
Any sugestions based on previous experience would be very welcome.
 
thank you all for you support and assistance,
 
Paul

---

### Post by oldfred on 2009-06-19
I am booting from several hard drives. You have two choices. Install Grub on your windows hard drive or boot from the Ubuntu drive and modify the menu.lst to logically change (map) the windows drive back to disk 0.

I would suggest modifying the grub (with the BIOS change to make it boot) on your Ubuntu - second drive.

The windows command in my menu.lst, when I installed the drive was the 4th drive as I was copying data from an old drive. In your case the 3s - hd3 should be hd1.
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
rootnoverify    (hd3,0)
savedefault
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1

---

### Post by snakeman21 on 2009-06-19
Hmmm... that's weird.  I have installed many dual boots in the past and never had this issue.  I do have one suggestion, though.  I have no idea if it will work, but it's worth a shot.  Go into your BIOS settings.  Somewhere in there will be an option for "default operating system" or something similar.  Change that value to "other".  Save, exit, and reboot, and (hopefully) you will be able to boot either operating system.  Good luck!

---

### Post by paulbyr on 2009-06-19
does it matter that my Partition Magic calls the Ubuntu HD disk 1 and the Win XP HD disk 2?

---

