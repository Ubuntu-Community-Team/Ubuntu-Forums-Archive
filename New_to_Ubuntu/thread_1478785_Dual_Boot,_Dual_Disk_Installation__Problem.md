---
title: "Dual Boot, Dual Disk Installation  Problem"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by dazz100 on 2010-05-10
Hello
I have a Asus P4P800 Mobo installed with two SATA HDs, one DVD installed on one parallel IDE channel, and one Zip drive on the other parallel IDE channel.  There is also a FD.

I have Win XP installed on one hard drive.  I want to install Ubuntu on the 2nd hard drive.  When I try to install Unbuntu off the CD, the installer shows the flash screen. I then get the boot option.  I hit return and then after about 15 seconds, everything freezes.  The display is blank and no signs of activity.

I suspect that my combination of drives is confusing Ubuntu.  

Just to complicate things slightly, I want to have a 10G FAT32 partition on the same hard drive as Ubuntu.  I will then place the Win XP virtual RAM swap file there to improve Win performance. I have already created a 10GB partition on the 2nd hard drive for this purpose.

So my question is, how do I install Ubuntu onto the 2nd HD???  Do I need to temporarily unplug something??

Any advice would be much appreciated.

---

### Post by Doug11 on 2010-05-10
Is this at the initial install? Meaning it does not go as far as the live cd? It could be a bad burn. Have you tried a different cd. And you could also temporarily unplug one hard drive and see what that does.

---

### Post by dazz100 on 2010-05-10
> **Doug11 said:**
> ...It could be a bad burn. Have you tried a different cd. ..

I tried booting the Linux Rescue Disk (known to be a "good" disk, and the same thing happened.  I got the initial screens, then it froze when trying to load up Linux.

I am writing this post on the same PC with Win XP, so I know the PC is OK.

---

### Post by dazz100 on 2010-05-12
Hi

After selecting the "Install Ubuntu" option, I get to the white Ubuntu symbol.  After about 30sec the screen goes blank for about 90minutes.  There is lots of HD activity during that time.  I then get a message:

(initramfs) Can not mount /dev/loop0
(/cdrom/casper /filesystem.squashfs) on
//filesystem.squashfs

/init:line 1 : can't open /dev/sda : No medium found.

I have found that if I type "help" I get the prompt (initramfs)

I don't understand what this error message means or how to fix the problem.

I have the HDs set to enhanced mode.  Could that be the problem?  If I switch to compatibility mode, the SATA ports are disabled by the BIOS.  WinXP runs OK with the enhanced mode.

---

### Post by dazz100 on 2010-05-13
OK so after a lot of rummaging around on the internet, I think I have found the cause of my problem  [ here ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996").

It looks like there is a Linux bug with the ASUS P4P800 MoBo.  
It seems to have been a common problem back in 2007, but it appears that latter kernels should have fixed the problem.  I am trying to load Ubuntu 9.10.


It looks like one solution is to substitute a PATA HD for a SATA HD.  I don't want to have to buy any more hardware to load Linux. 

I do have a spare PATA 3G drive.  I could load Ubuntu onto that if it is big enough. I wouldn't know how to transfer that onto a SATA HD.

---

### Post by dazz100 on 2010-05-13
I am on the way to solving the problem.

I unplugged the Win XP  SATA HD leaving the CD-ROM, Zip Drive (PATA) and the future Ubuntu (SATA) HD connected.

I switched the BIOS setting to compatible mode which leaves one SATA channel available.  I then successfully installed Ubuntu Desktop 9.10. I plugged in the WinXP SATA HD and set the BIOS back to Enhanced mode. Ubuntu booted without any problems.

At present I can boot either Ubuntu or WinXP by selecting the appropriate HD in the BIOS.  I just have to figure out how to configure GRUB to see the WinXP disk. For that I just need to climb the learning curve.

---

### Post by trevorgeorge on 2011-03-11
> **dazz100 said:**
> I am on the way to solving the problem.

I unplugged the Win XP  SATA HD leaving the CD-ROM, Zip Drive (PATA) and the future Ubuntu (SATA) HD connected.

I switched the BIOS setting to compatible mode which leaves one SATA channel available.  I then successfully installed Ubuntu Desktop 9.10. I plugged in the WinXP SATA HD and set the BIOS back to Enhanced mode. Ubuntu booted without any problems.

At present I can boot either Ubuntu or WinXP by selecting the appropriate HD in the BIOS.  I just have to figure out how to configure GRUB to see the WinXP disk. For that I just need to climb the learning curve.
[COLOR="black"]**Re: How to configure grub to see WinXP**[/COLOR]

I got to this point too, today!
I had two separate SATA drives, one with XP Pro SP3 32-bit installed,  the other with Ubuntu 10.10 64-bit, both straight installs on empty disks, each OS being installed with its Hdd connected, while other Hdd was disconnected (i.e. the power lead pulled from rear of Hdd) until finished.
After installation of separate Oss on each individual drive, disconnected the Windows Hdd & re-connected Linux Hdd & booted into Ubuntu, opened Terminal & updated grub as root with command

sudo update-grub

followed by password when requested.
Win XP drive was visible straight away, & on rebooting the screen gave option to choose which OS to run.

---

