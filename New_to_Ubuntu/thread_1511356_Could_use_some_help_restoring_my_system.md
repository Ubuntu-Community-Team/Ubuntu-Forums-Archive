---
title: "Could use some help restoring my system"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Edward B. on 2010-06-16
Thanks in advance for any help you can give me.

Today I started up my desktop, it went to the title screen for Ubuntu and just sat there, did nothing. Waited. Waited. Nothing. Physically restarted computer, same thing. Did it several times, same thing.

Went into setup, changed BIOS settings to system default. Honestly, wasn't sure what I was doing, just trying to get it working.

This time, stayed on the black start up screen, said it couldn't load the OS.

Put in the Ubuntu CD, which is what I'm now running. Looked to see if I could access my hard drive - have not been able to do so.

I keep a backup HD, so it's not a huge deal if I have to wipe everything, but I do have several photos and files that I had not backed up yet - so I would like to restore my old system if possible.

1) Any idea on what my original problem might have been?

2) Any idea if I can/how I can access files on my hard drive when I'm running off of the CD?

Thanks!

---

### Post by Chesamo on 2010-06-16
What version of Ubuntu were you running, and did you try manually mounting the HDD while on the LiveCD?

---

### Post by Edward B. on 2010-06-16
> **Chesamo said:**
> What version of Ubuntu were you running, and did you try manually mounting the HDD while on the LiveCD?

Was running 10.04; now running 10.04 off CD.

I am a moron, so forgive my ignorance. How do you manually mount an HDD?

---

### Post by Chesamo on 2010-06-16
No need to degrade yourself.

Make a new directory (mount point) by entering the following command into Terminal: ```
sudo mkdir /media/hdd
``` Then mount the drive by entering *either* ```
sudo mount /dev/sda1 /media/hdd
``` *or* ```
sudo mount /dev/hda1 /media/hdd
``` The first command is for SATA/SCSI drives, and the second command is for IDE drives.

---

### Post by mapes12 on 2010-06-17
If the above posts do not resolve the problem then try moving /home to a separate partition on your machine like this:- [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Then install your system but make sure you select Manual at the partitioning stage. Change the options so that your system knows where you want to install / and format it. Do the same for /home but DO NOT format that. SWAP will be there as well.

Once your system reinstalls you should then be back to where you were before the crash. Run Update Manager then install the application packages you want. I also install ubuntu-restricted-extras and the codecs from Medibuntu for media viewing after a fresh install.

I did the above this morning to upgrade from 9.04 to 10.04 and everything working fine with all my /home stuff safe and sound. 

Mark

---

### Post by Edward B. on 2010-06-17
> **Chesamo said:**
> No need to degrade yourself.

Make a new directory (mount point) by entering the following command into Terminal: ```
sudo mkdir /media/hdd
``` Then mount the drive by entering *either* ```
sudo mount /dev/sda1 /media/hdd
``` *or* ```
sudo mount /dev/hda1 /media/hdd
``` The first command is for SATA/SCSI drives, and the second command is for IDE drives.

Hopefully, my hard drive has not been wiped out.

When I try the above I get this message: "special device /dev/sda1 (/dev/hdal) does not exist"

Thanks for the additional suggestion mapes - I will try this when I have more time.

---

### Post by nothingspecial on 2010-06-17
For one reason, or another, /dev/sda1 or hda1 may not be the drive you want.

From the live cd type ```
sudo fdisk -l
``` which will give you a list of drives connected to your machine (mounted, or not).

Try to figure out which one has your stuff on it then try the mount command again with the correct /dev/sd?? again.

---

### Post by Edward B. on 2010-06-17
> **nothingspecial said:**
> For one reason, or another, /dev/sda1 or hda1 may not be the drive you want.

From the live cd type ```
sudo fdisk -l
``` which will give you a list of drives connected to your machine (mounted, or not).

Try to figure out which one has your stuff on it then try the mount command again with the correct /dev/sd?? again.

Hmmm... did this but nothing happened. I entered "-1" instead of "-l" and got a partition menu of some kind.

---

### Post by eriktheblu on 2010-06-17
The fdisk-l (lower case L) is what nothingspecial was looking for.

To avoid typing errors, you might try selecting the text in the code box, copy to your clipboard with control+C, then paste to your terminal with control+shift+V.

Looks like you had a similar mixup with the 1/l from the mounting section. Try again by copying the code.

If you're still having trouble, look for the hard disk in your places menu from the live CD.

When you say "title screen for Ubuntu" do you mean the splash screen with "Ubuntu" in big letters and little boxes underneath, the login screen where you select your username, or the Grub2 boot loader that has a menu ending with Memtest somethingorother?

---

### Post by nothingspecial on 2010-06-17
> **Edward B. said:**
> Hmmm... did this but nothing happened. I entered "-1" instead of "-l" and got a partition menu of some kind.

I had not realised, on first reading that you hadn`t tried, the previous suggestions first.

They are quite valid.

If they dont work, the fdisk command should give you enough information in respect of which partition you want to mount ....... size, file system etc

/dev/sda1 is the one, in all probability, but may not be, hence my post.

I`m sorry (not wishing in any way to be condescending) if that has confused you.

---

### Post by Edward B. on 2010-06-17
> **nothingspecial said:**
> I had not realised, on first reading that you hadn`t tried, the previous suggestions first.

They are quite valid.

If they dont work, the fdisk command should give you enough information in respect of which partition you want to mount ....... size, file system etc

/dev/sda1 is the one, in all probability, but may not be, hence my post.

I`m sorry (not wishing in any way to be condescending) if that has confused you.

I did try the previous suggestion first. I also copied and pasted the code. When doing so did not produce results, I tried typing in a one in place of the letter l as I thought you may have made a mistake in typing the code.

Going through the Terminal this moment:

[QUOTE=Code]sudo mkdir /media/hdd[/QUOTE]

Result: mkdir: cannot create directory `/media/hdd': File exists

[QUOTE=Code]sudo mount /dev/sda1 /media/hdd[/QUOTE]

Result: mount: special device /dev/sda1 does not exist

[QUOTE=Code]sudo mount /dev/hda1 /media/hdd[/QUOTE]

Result: mount: special device /dev/hda1 does not exist

[QUOTE=Code]sudo fdisk -l[/QUOTE]

Result: ubuntu@ubuntu:~$: (in other words - nothing happens) 


[QUOTE=eriktheblu]If you're still having trouble, look for the hard disk in your places menu from the live CD.

When you say "title screen for Ubuntu" do you mean the splash screen with "Ubuntu" in big letters and little boxes underneath, the login screen where you select your username, or the Grub2 boot loader that has a menu ending with Memtest somethingorother?
[/QUOTE]

Tried looking for the hard disk, erik, and have not been able to locate.

When I say "title screen" I mean the splash screen. When I first had this problem the splash screen came up and did nothing. Waited for several minutes, perhaps five or six during the longest time, nothing happened. Had to physically shut down the PC. At this point the little circles below the "Ubuntu" title flickered and turned into loading boxes like you might see on a website that does not load properly. Then the PC turned off. I turned it back on, had the same problem.

At this point, I entered BIOS upon startup and reset my settings to default. Then I restarted the PC. At this point I was taken to the black startup screen where it goes through system memory check, etc. However, nothing would load. It did display a message. I forget what that message was, but it was something along the lines of there being a failure of some kind.

Thanks again for trying to help me out. Appreciate it.

---

### Post by eriktheblu on 2010-06-17
OK, your original problem sounds like a software issue, in which case my first guess would have been that you had a bad kernel update (really just a guess but a starting point). Should you find yourself back there, try to load a previous kernel from the Grub2 menu.

Now you have a bigger problem that seems more likely to be hardware related. Your hard disk is not being recognized by the live CD and also doesn't seem to be recognized by your BIOS. Unfortunately, I think your resetting to default may be the culprit.

I would advise to go into your BIOS, and see if you can figure out how to get your internal HDD recognized again. Make sure your ports are enabled and look for the HDD in the boot priority (do you have more than one hard disk?)

---

### Post by Edward B. on 2010-06-17
> **eriktheblu said:**
> OK, your original problem sounds like a software issue, in which case my first guess would have been that you had a bad kernel update (really just a guess but a starting point). Should you find yourself back there, try to load a previous kernel from the Grub2 menu.

Now you have a bigger problem that seems more likely to be hardware related. Your hard disk is not being recognized by the live CD and also doesn't seem to be recognized by your BIOS. Unfortunately, I think your resetting to default may be the culprit.

I would advise to go into your BIOS, and see if you can figure out how to get your internal HDD recognized again. Make sure your ports are enabled and look for the HDD in the boot priority (do you have more than one hard disk?)

How do you enable ports?

Here is the message I receive when I switched all three of my boot slots to HDD.

[QUOTE=Start Up]Verifying DMI Pool Data...

Boot from CD
Boot from CD

Disk Book Failure, Insert System Disk and Press Enter[/QUOTE]

Also, when I load up the Live CD, I get this prompt box. After I hit okay, Ubuntu loads up from the CD.

[QUOTE=Live CD Start Up]Installer encountered unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.[/QUOTE]

---

### Post by eriktheblu on 2010-06-17
Unfortunately each manufacturer will set up their BIOS in a different manner. I couldn't tell you with any accuracy where these options might be on your computer. Go in, look around, try to find something that says IDE, ATA, or SATA. 

If you have a spare internal disk, try swapping it put and see if you can access it from the live CD. If that works, your original disk may be done for.

This might be a good time to crack open your case and give it a good dusting (with air). Check to see that all your connectors are in place (i.e. hard drive is still plugged in).

---

### Post by libssd on 2010-06-17
Before resorting to the command line interface:

1. Boot from Ubuntu 10.04 LiveCD
2. Open a Nautilus file manager window; e.g. Places > Home

Does anything that looks like your HDD appear in the left hand panel? If so, doubleclick on it. If you can get to the Documents folder on your HDD this way, you can rescue the documents that aren't backed up, and copy them to another device, such as a USB flash drive.

If this doesn't work, you probably need to dive under the surface and explore from the command line. If you are able to retrieve your latest files, I would just do a fresh install of Ubuntu from the LiveCD.

It was a little difficult to install, but I have had good luck with Remastersys for creating a bootable DVD to re-install from a backup. This makes it *much* less stressful to experiment.

Backups are golden; restores are priceless.

---

### Post by Edward B. on 2010-06-17
Opened the case. Hard drive is connected. I had just cleaned out the interior with air not long ago, so everything still looks good.

I can not find any of my files by going to Places-Home and looking around on there. There is something that says "File System" with a pic of a hard drive on the left hand of the screen but none of my files are in there.

Eric - if I find something listing IDE, ATA, or SATA, any idea what I want to do there?

EDIT: Is there a way I can reinstall Ubuntu while maintaining my files?

---

### Post by eriktheblu on 2010-06-18
If/when you find the ports, make sure they are enabled. Some years back I was trying to get a serial device working. After several days of installing and configuring drivers and software, I discovered that the serial port had been disabled (by me in fact; I had just forgotten about it).

You might try the motherboard manufacturer's website to see if you can get some sort of manual (or perhaps one came with the equipment).

If you have spare ports on your motherboard, you might try to connect your HDD to an alternate one. I suspect this will have a low probability of success.

Trying a new disk will be the easiest way to tell if the drive is bad. I do of course realize that not everyone has 4 spare hard disks laying about as I do.

If you can get your hard disk recognized *and* your data is on a separate /home partition, a reinstall should be fairly simple. The problem here is that your machine does not seem to recognize your internal disk. I think this is either a failure of the disk, or more likely (due to the reset) a misconfiguration of the BIOS.

---

### Post by Edward B. on 2010-06-18
> **eriktheblu said:**
> If/when you find the ports, make sure they are enabled. Some years back I was trying to get a serial device working. After several days of installing and configuring drivers and software, I discovered that the serial port had been disabled (by me in fact; I had just forgotten about it).

You might try the motherboard manufacturer's website to see if you can get some sort of manual (or perhaps one came with the equipment).

If you have spare ports on your motherboard, you might try to connect your HDD to an alternate one. I suspect this will have a low probability of success.

Trying a new disk will be the easiest way to tell if the drive is bad. I do of course realize that not everyone has 4 spare hard disks laying about as I do.

If you can get your hard disk recognized *and* your data is on a separate /home partition, a reinstall should be fairly simple. The problem here is that your machine does not seem to recognize your internal disk. I think this is either a failure of the disk, or more likely (due to the reset) a misconfiguration of the BIOS.

Good news is that I reconfigured BIOS so that it will boot from the hard drive.

Now, don't ask me how I did this. Yes, I know I should have been paying more attention, but I was getting aggravated and just started changing settings... I think I may have finally hit the restore fail safe settings or something.

In any case, it will now boot from the hard drive.

Bad news is that I am now having the same problem with the splash screen, with the Ubuntu logo displayed but nothing happening.

Any idea on how I could work around this now that I can boot from the hard drive again or am I still in the same spot?

---

### Post by eriktheblu on 2010-06-18
Great news!

Try to boot Ubuntu with a an older kernel from the Grub boot loader.

You may need to hold shift while it loads.

---

### Post by Edward B. on 2010-06-18
> **eriktheblu said:**
> Great news!

Try to boot Ubuntu with a an older kernel from the Grub boot loader.

You may need to hold shift while it loads.

I know this is going to surprise you. It's really going to blow your mind. Ready?

I don't know how to use the Grub boot loader. In fact, I'm not entirely sure what that is – all I need to do is hold shift down while the PC goes through the system start up?

---

### Post by eriktheblu on 2010-06-18
Grub is a boot loader; it initializes your operating system. It should present as a black screen with white text with the top line highlighted.

It will say something along the lines of Ubuntu followed by a kernel version (2.6. I don't really pay attention)

The next line will be a recovery mode for that kernel version

The next line will be an older kernel.

The last 2 lines should be memory tests.

If you don't normally see this list, hold shift during boot until it does.

---

### Post by Edward B. on 2010-06-20
> **eriktheblu said:**
> Grub is a boot loader; it initializes your operating system. It should present as a black screen with white text with the top line highlighted.

It will say something along the lines of Ubuntu followed by a kernel version (2.6. I don't really pay attention)

The next line will be a recovery mode for that kernel version

The next line will be an older kernel.

The last 2 lines should be memory tests.

If you don't normally see this list, hold shift during boot until it does.

Thanks. I actually got my hard drive to boot up and everything's fine. I still don't know what I did, though. When the start up came on, it said press "esc" to enter the Grub. I did so, but nothing happened and it went to the splash screen and locked up again.

So I reset the PC and just started hitting "esc" a ton. Just kept pressing it. Some text came up on the start up, but I just kept pressing "esc" and it loaded into my old desktop off of the hard drive!

I'm going to make back-ups of everything before I turn the PC off again, but hopefully problem is solved.

Thanks again to everyone who helped me out.

---

