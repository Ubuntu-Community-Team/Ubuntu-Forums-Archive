---
title: "How can someone mess a computer up this badly?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by mrnogatco on 2009-02-08
How are you doing guys (and gals)?

Where do I start?

I am working on a friend's laptop (HP Pavilion dv5000 64-bit Turion) and I am having a TON of problems.

The problem started with Microsoft Windows XP.  My friend thought it would be OK to delete his C:/Windows folder.... (yes I wish I would have been there to smack him in the face)  So, as you might guess, there were no drivers, no NTLDR, nothing.  He also had somehow deleted the drive letter for the primary C: drive. Anyways, I used Partition Magic to re-label his C: drive and boot into Windows.

When I went into Windows, it was trying to install all of the previous hardware, but without his original Windows XP disc (He said he lost it), I was unable to install everything that needed to be installed.  So that's when I decided to boot up Ubuntu 8.10.

I wanted to boot up Ubuntu because I thought that if I could get a working system, I should be able to just RE-install Windows from the disc that I recieved from him (He ended up finding it)

Problem is, after installing Ubuntu 8.10, there were a ton of missing drivers (USB, CD-ROM (I think), and a few others)

Right now, I am stuck with Ubuntu (Nice OS, but I know my friend is going to want Windows back.)  I cannot boot a Windows XP disc.  I cannot boot a recovery tools disc.  In fact, I cannot even READ CD's or DVD's anymore.  That's because of ANOTHER problem (which I have caused myself) 

When I first installed Ubuntu, I was in a rush, and SOMEHOW moved the CD-ROM icon from the PLACES tab to the Desktop.  For some reason, I was not able to access CD's or DVD's anymore.  Call it a stupid idea (I know it was), but I deleted it form his Desktop thinking when I rebooted there would be no problem.  I was wrong.

No matter what kind of CD or DVD or Data Disk I put in the CD drive, it will not read.  It spins like it is reading something, but I can't seem to load anything up (including booting from CD)
I cannot find the command to remount this cd-rom (I'm GUESSING it was unmounted, but I definetely could be wrong)

I have tried using:
sudo mount /dev/scd0 /media/cd
sudo mount /dev/scd /media/cd

plus a ton of other commands.

I read on this forum that I should type "sudo mount" and print out the output.  So here it is:

[B][I]will@will-laptop:~$ sudo mount 

[sudo] password for will:  

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) 

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 

/proc on /proc type proc (rw,noexec,nosuid,nodev) 

sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 

varrun on /var/run type tmpfs (rw,nosuid,mode=0755) 

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 

udev on /dev type tmpfs (rw,mode=0755) 

tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) 

devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) 

fusectl on /sys/fs/fuse/connections type fusectl (rw) 

lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755) 

securityfs on /sys/kernel/security type securityfs (rw) 

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 

gvfs-fuse-daemon on /home/will/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=will) 

/dev/mmcblk0p1 on /media/NEW VOLUME_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush[/I][/B])


I'm pretty sure that the last command:
***/dev/mmcblk0p1 on /media/NEW VOLUME_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)***
refers to the SD card I have inserted right now, So I don't think that is important.


If anyone knows how to help, it would be greatly appreciated.  I am trying to "Pay it Forward" by helping my buddy with his laptop, so if someone could help me out, that would be great!

Thanks in advance,
Mr Nogatco

P.S.- If I am being too noobish sounding, please let me know.  I am pretty good with command-line and terminal based fixes, so I am not afraid to get my hands dirty.

P.P.S.- I forgot to mention that I DO have Internet access on the Ubuntu Laptop.  If there is a way to reinstall Ubuntu WITHOUT a disc, I would try that.  He has NO important information on Ubuntu, so a fresh install would be great if possible.

---

### Post by abn91c on 2009-02-08
if the command line you can try ```
sudo apt-get update
sudo apt-get upgrade
``` to reistall the desktop```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by Therion on 2009-02-08
So what exactly do you want to do?  Do you want the PC running Ubuntu or Windows?  It sounds as if, at some point, you need this PC running winXP like it was before.  It that's the case you should just need to insert the Windows install CD and boot to it.  Nothing you can do with an OS can prevent the optical drive from being a bootable device.

If you're not booting from the CD then I would check the BIOS settings and make the optical drive primary in the boot sequence, if it's not already, after resetting the BIOS to factory defaults.  Then back to the Windows install CD for a fresh install.

---

### Post by mrnogatco on 2009-02-08
> **Therion said:**
> So what exactly do you want to do?  Do you want the PC running Ubuntu or Windows?  It sounds as if, at some point, you need this PC running winXP like it was before.  It that's the case you should just need to insert the Windows install CD and boot to it.  Nothing you can do with an OS can prevent the optical drive from being a bootable device.

If you're not booting from the CD then I would check the BIOS settings and make the optical drive primary in the boot sequence, if it's not already, after resetting the BIOS to factory defaults.  Then back to the Windows install CD for a fresh install.


You're right.  He wants to put Windows XP back on the system.
Problem is, it won't boot from CD.  I have it set up in BIOS to boot from CD, but it just boots the GRUB loader.

I even went as far as disabling the HD, the Network, and the floppy boot options in BIOS.  I then booted and it just went to a flashing screen with 2 cursors, one on top and one on bottom.

If I could just boot off a CD, I wouldn't be in this predicament.

Thanks for trying to help though.  It is much appreciated.

---

### Post by mrnogatco on 2009-02-08
> **abn91c said:**
> if the command line you can try ```
sudo apt-get update
sudo apt-get upgrade
``` to reistall the desktop```
sudo aptitude reinstall ubuntu-desktop
```

I am currently downlaoding all updates.

For some reason the code:
```
sudo aptitude reinstall ubuntu-desktop
```
 seems like it going to reinstall, but after it is complete, there is no changes (that I could see) even after restarting

---

### Post by zabien1970 on 2009-02-08
Could th windows cd be scratched or dirty? if it can't be read properly on startup it'll continue on to the harddrive, can you boot a live session off the ubuntu cd?

---

### Post by HermanAB on 2009-02-08
Uhmmm...  It looks like you should get rid of Linux and install Windows.  That is not so easy anymore, since Windows doesn't recognize the Linux partitions.

Boot off a Live Linux CD (eg. Ubuntu or Knoppix).  Open a console, find the disk drive using 'ls /dev/sd*' (probably sda).  Now wipe out the first little bit of the disk drive to get rid of the partitioning information that Windows doesn't understand with 'dd bs=1024 count=1 if=/dev/zero of=/dev/sda'.

Now when you insert a Windows CD and reboot, it should be able to install normally.

Cheers,

Herman

---

### Post by Therion on 2009-02-08
It's the fact you're not BOOTING to the CD that's disturbing.  The install CD won't care what's on the drive or how it's formatted.  You're running off the CD for the install and formatting and partitioning is part of a normal Windows install.  Is this disk your friend has a legitimate Windows install CD?  I don't really care, I'll openly admit to pirating a install disk or two in my day, but if it's not, then we're up against a whole different set of issues.

---

### Post by mrnogatco on 2009-02-08
> **HermanAB said:**
> Uhmmm...  It looks like you should get rid of Linux and install Windows.  That is not so easy anymore, since Windows doesn't recognize the Linux partitions.

Boot off a Live Linux CD (eg. Ubuntu or Knoppix).  Open a console, find the disk drive using 'ls /dev/sd*' (probably sda).  Now wipe out the first little bit of the disk drive to get rid of the partitioning information that Windows doesn't understand with 'dd bs=1024 count=1 if=/dev/zero of=/dev/sda'.

Now when you insert a Windows CD and reboot, it should be able to install normally.

Cheers,

Herman

I cannot boot off a CD (Linux, Windows, or anything for that matter)

And Ubuntu won't recognize a cd that has been put in after Ubuntu has been booted.

Also, the disk is not scratched.  It will boot up in another PC.

I'm letting the updates install, so it should be done in about 10 more minutes.  I'll see how that goes.

BTW, thanks guys for the helpful suggestions.  Sorry if I am sounding a bit rude right now, but you guys know how it is when you have computer problems, lol!;)

---

### Post by nothingspecial on 2009-02-08
You can install Ubuntu or most other linux distros from a usb stick.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

However if the cd wont boot at start up then you`ve either got a faulty cd or a faulty drive and no amount of messing with the command line will fix that.

---

### Post by mrnogatco on 2009-02-08
> **Therion said:**
> It's the fact you're not BOOTING to the CD that's disturbing.  The install CD won't care what's on the drive or how it's formatted.  You're running off the CD for the install and formatting and partitioning is part of a normal Windows install.  Is this disk your friend has a legitimate Windows install CD?  I don't really care, I'll openly admit to pirating a install disk or two in my day, but if it's not, then we're up against a whole different set of issues.

Well, his install disk is in fact, not legitimate.
I know that it worked before, because I had to use it to install Windows the first time he got it.

And after I installed Ubuntu, it DID boot off CD originally.  It was after I moved the CD-ROM icon to the Desktop when I started having problems.

Actually, I still have a liscense left on MY Windows XP disc, but I don't want to give him my last one.  As I am doing this for free, I would like to not have to waste my last liscense.

BTW- The USB drivers are not installed.  I cannot even READ a USB stick or anything USB at this point.

And I'm sure the CD drive is still good.  I was just using it yesterday, and I'm pretty sure I couldn't have done anyting to mess it up.

---

### Post by scragar on 2009-02-08
Why are you trying to mount /dev/sdc?
```
mount /dev/cdrom /media/cdrom
```

---

### Post by mrnogatco on 2009-02-08
> **scragar said:**
> Why are you trying to mount /dev/sdc?
```
mount /dev/cdrom /media/cdrom
```

When I type this code in, it replies:
mount: special device /dev/cdrom does not exist

P.S.- I just installed all updates and it did nothing useful.

Is there a command that COMPLETELY reinstalls Ubuntu (or any other distro for that matter)

I just want a fresh install if it's possible

Or even a recovery type command that reverts everything back to normal

---

### Post by HermanAB on 2009-02-08
Wipe the disk partition tables and MBR:
# sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda

Now you can install whatever you want from scratch.

Cheers,

Herman

---

### Post by mrnogatco on 2009-02-08
> **HermanAB said:**
> Wipe the disk partition tables and MBR:
# sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda

Now you can install whatever you want from scratch.

Cheers,

Herman

That just wiped out my HDD.

I now can't even boot Ubuntu.

No CD booting.  No USB Booting.  No Network Booting (unless someone has ian idea)

---

### Post by ibuclaw on 2009-02-08
Go into the Laptop's BIOS settings and ensure that CDROM is enabled as a bootable device.

Regards
Iain

---

### Post by melrokz on 2009-02-08
Looks like you may have trouble with your _BIOS recognising your CD drive_, or your _drive/BIOS is faulty_. If the GRUB loader boots, the system has booted from the hdd already. 
First, get into the BIOS setup screen (press Del immediately after system on). Next, on the first screen, or under the section 'standard bios features'(or something similar, depending on your BIOS), see if your CD drive is listed under the section 'IDE(or SATA) secondary master' or 'IDE(or SATA) primary slave'. If not, press enter in this section and select 'Autodetect'. Still if nothing happens, clear CMOS with the appropriate jumper on the motherboard and try again. (In this case, you have to set all BIOS settings again). Still no hope? Call the nearest service personnel to check your hardware.

---

### Post by photon_man62 on 2009-02-08
My God! That sounds terrible!

But you fiddling with the OS could have absolutely nothing to do with not being able to boot a CD from the BIOS. Maybe the BIOS is corrupt?

Well, not corrupt, but you understand.

---

### Post by Therion on 2009-02-08
> **HermanAB said:**
> Wipe the disk partition tables and MBR:
# sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda

Now you can install whatever you want from scratch.
Sorry I wasn't here to catch that post and tell you not to do it, because yeah, that's gonna wipe your drive and leave you hosed since you can't boot from CD.  Ah well...

At this point you really have no choice but to figure out WHY you can't get your optical drive recognized and working.  Maybe use an external... No, that's not gonna work because it doesn't sound like your PC will boot from USB.  With a blank hard drive, no optical drive and no ability to boot from USB, I don't know what to tell you.  

Good luck.

---

### Post by halitech on 2009-02-08
does the machine have a floppy drive? there are ways of doing an install started with a floppy a (wired) network connection

---

### Post by melrokz on 2009-02-08
Mr. Nogatco, did you understand and try what i posted?

---

### Post by mrnogatco on 2009-02-08
Well,
Thanks guys.  You have all given good ideas.  Even the one that wiped the hard drive MBR.  Really, in a perfect world those would have worked.  But, as we all know, the perfect world does not exist.  Only PC HELL!

I have thought of a way to fix it, but I'm not exactly sure of the steps and a little backup would be pretty cool.  Thanks in 
advance.

Idea #1 (Please feel free to add steps if I'm missing something:

1. I have a friend that has an adapter that allows you to connect notebook hard drives to a Desktop very easily.  I was thinking of connecting the laptop hard drive to the adapter as a slave drive.

2. I want to reformat the drive completely.

3. If I can format the drive completely and install Windows back on the drive, it should boot.... hopefully.

Idea #2 (I don't know if it exists... but I'll ask anyway)-

1. Hook the laptop drive up as a slave in that adapter. 

2. Format

3. Add something to allow an autoboot BIOS upgrade from the hard drive the next time it's inserted in the PC.

4. Upgrade the BIOS the next time it's booted from HD



Please feel free to add to the list if you can think of something.

To tell the truth, I won't be pissed if this is asking too much.  If I should take this to another forum, please let me know.

Thanks in advance

---

### Post by halitech on 2009-02-08
> **mrnogatco said:**
> 
Idea #1 (Please feel free to add steps if I'm missing something:

1. I have a friend that has an adapter that allows you to connect notebook hard drives to a Desktop very easily.  I was thinking of connecting the laptop hard drive to the adapter as a slave drive.

2. I want to reformat the drive completely.

3. If I can format the drive completely and install Windows back on the drive, it should boot.... hopefully.

in theory this should work but windows will see all the new hardware and probably barf all over itself trying to install all the new drivers. Instead of installing while its in the desktop, format the drive, make it bootable by installing DOS6 (or PCDos which I believe is now free) and then copy the i386 folder to the drive. Insert the drive back into the laptop and then run the install while it is back in the laptop.

---

### Post by mrnogatco on 2009-02-08
> **melrokz said:**
> Looks like you may have trouble with your _BIOS recognising your CD drive_, or your _drive/BIOS is faulty_. If the GRUB loader boots, the system has booted from the hdd already. 
First, get into the BIOS setup screen (press Del immediately after system on). Next, on the first screen, or under the section 'standard bios features'(or something similar, depending on your BIOS), see if your CD drive is listed under the section 'IDE(or SATA) secondary master' or 'IDE(or SATA) primary slave'. If not, press enter in this section and select 'Autodetect'. Still if nothing happens, clear CMOS with the appropriate jumper on the motherboard and try again. (In this case, you have to set all BIOS settings again). Still no hope? Call the nearest service personnel to check your hardware.

At this point, the GRUB no longer loads.

I can boot into BIOS (Phoenix v. F.54).  As far as I can tell, I don't see an option to select the master or primary drives. Unless there's an alternate BIOS settings screen, I don't see any options like that.

As far as opening the laptop up, I am going to wait until tomorrow where the college has more tools and people.

Thank you for the idea.  Any more ideas?

---

### Post by mrnogatco on 2009-02-08
> **halitech said:**
> in theory this should work but windows will see all the new hardware and probably barf all over itself trying to install all the new drivers. Instead of installing while its in the desktop, format the drive, make it bootable by installing DOS6 (or PCDos which I believe is now free) and then copy the i386 folder to the drive. Insert the drive back into the laptop and then run the install while it is back in the laptop.

YES!
I think this sounds feasable.

I'm not quite understanding how you're explaining WHEN to format the laptop drive.  I'm guessing you mean for me to boot the Desktop into DOS.  Format the drive using the FORMAT command.  Then install the PCDos software to the HD.

Then do I copy the i386 folder from the desktop?  Or do I browse the install disc and add them?

The rest is pretty self-explanatory.  Thank you for the suggestion.

---

### Post by melrokz on 2009-02-08
Now your hdd is wiped clean! To install Windows, You CANNOT expect a copied NTFS partition from a laptop to work for the hardware configuration of your desktop! Anyway, you have connected you laptop hdd according to idea #1. Try setting the laptop hdd to 'master' configuration, so that u can see if it boots! IF there are no problems, you can set your clean hdd to 'slave' and use partition copy or image creation software to create an NTFS partition on the clean drive (of larger size than the laptop's partition) and copy the laptop's NTFS partition to your friend's hdd. This is only for Trying, no guarantee.
        You really need a working BIOS and optical drive, friend.

---

### Post by zabien1970 on 2009-02-08
Have you tried a recovery cd like Trinity Rescue Kit or Supergrub, if you have blank cds these and others are always good to have on hand

---

### Post by mrnogatco on 2009-02-08
> **melrokz said:**
> Now your hdd is wiped clean! To install Windows, You CANNOT expect a copied NTFS partition from a laptop to work for the hardware configuration of your desktop! Anyway, you have connected you laptop hdd according to idea #1. Try setting the laptop hdd to 'master' configuration, so that u can see if it boots! IF there are no problems, you can set your clean hdd to 'slave' and use partition copy or image creation software to create an NTFS partition on the clean drive (of larger size than the laptop's partition) and copy the laptop's NTFS partition to your friend's hdd. This is only for Trying, no guarantee.
        You really need a working BIOS and optical drive, friend.

Let's say I'm a pretty optimistic person.  I'm HOPING that by runnning the command:
```
sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda
```

I didn't delete the BIOS (which is stored in ROM correct?)
Seeing as the CD drive was JUST working last night when I installed Ubuntu, I'm also hoping that the CD drive is still functional.(Which I'll be able to test tomorrow at college.)

In your example, when you refer to the "clean drive", I'm assuming you're talking about the Desktop Hard drive, correct?
So I need to copy the new NTFS partition made on the Desktop hard drive to the laptop hard drive using Partition Magic?

Thank you very much for your help.

---

### Post by jimv on 2009-02-08
Nm

---

### Post by halitech on 2009-02-08
> **mrnogatco said:**
> YES!
I think this sounds feasable.

I'm not quite understanding how you're explaining WHEN to format the laptop drive.  I'm guessing you mean for me to boot the Desktop into DOS.  Format the drive using the FORMAT command.  Then install the PCDos software to the HD.

Then do I copy the i386 folder from the desktop?  Or do I browse the install disc and add them?

The rest is pretty self-explanatory.  Thank you for the suggestion.

PCDos isn't software, its an operating system that will allow you to boot the drive (same as DOS back pre windows) so that once the drive is back in the laptop, you can boot from it and then install windows.

You will need to copy the i386 folder from the install disk, not the desktop computer

---

### Post by txcrackers on 2009-02-08
If you BIOS is hosed enough that it doesn't "see" the CD to boot from, booting from a USB is likely to be ineffective. You've got to get into the BIOS and determine if it can actually access the CD and hard-drive. **If** it's got a floppy drive, you might also consider making a BIOS-upgrade disk (see BIOS manufaturer for that).

Pulling the drive out and installing Windows on it from another machine won't work - the Windows installation will be specific to the hardware on *that* machine and I'd give it a less than 10% chance of working back in the original.

---

### Post by -kg- on 2009-02-08
OK, I've been reading this thread and I haven't heard this mentioned yet.

I'm assuming that you can see the CD drive listed in BIOS.  When you set the CD drive to be checked for being bootable, did you put it _before_ the hard drive in the list?

It might be that it checks the hard drive, finds a bootable partition, but isn't able to boot it, so fails.  If this is the case, it will never check the CD drive to boot from it, because it finds the hard drive first.  The CD drive must be before the hard drive in the boot list in BIOS.

Also, if you have a floppy drive, there are versions of DOS that you can boot into from a floppy drive.  Of course, the floppy drive will have to be in the list before the hard drive, as well.

---

