---
title: "Have some annoying isues with ubuntu.  (cant reinstall)"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by mr.bobbles on 2009-05-13
Hi all,

Theres been quite a few things going wrong on my pc.  it stared with my nvidia graphics card not working (still not working)  and Im stuck in this low graffics mode. I also cant do ANY updates. 
 
So what im trying to do is a fresh install,  (100% ubuntu have all my stuff backed up)  but when i tryed to do a cd reinstall I get this  "busy box buil in shell initramfs"  this happens with v 9.04, v8.02 and v7.10.

also when i try and do it with the update manager i get "not all updates can be installed, Run partial upgrade"

  Remove package in bad state

The package 'linux-image-2.6.27-11-generic' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?
Package in inconsistent state

The package 'linux-image-2.6.27-11-generic' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

Any help would be really  appreciated.

---

### Post by Jazzy_Jeff on 2009-05-13
Are you trying to use the live cd to install? I had problems with the busybox errors as well. Go back and download the alternate install cd and burn that to disk. You should not have any problems installing with that. Just follow the instructions when you go to install. Not hard at all.

---

### Post by 123456789123456789123456 on 2009-05-13
How did you install Ubuntu before?

The update manager problems can be a result of a bad install,  I have never ran into that sort of error with update manager.  Nvidia drivers, you need to go to the hardware drivers section, and have it enable the Nvidia driver, this requires download, and installation of the driver.  I don't know why the live cd's are not working, the last time I had that error, it was unable to reconize the cd drive, thought it was not there.  But that was a Motherboard BIOS issue.  Try this, boot from live cd, 8.10 preferably, and under boot options, either F4, for F6, tell it safe graphics mode, and load the live desktop.

If live desktop does not boot, under the second option, install, without going into live desktop, see if the installer starts.  Alternit install cd, Text mode is also an option, I would hate for you to search for that cd, since it is hard for me to find it.  I understand that some times, the graphics cards, are not included with all live cd's, and that can cause problems, having Ubuntu fall back into safe graphics mode should work.

---

### Post by mr.bobbles on 2009-05-13
thanks ill give that a try

---

### Post by Jazzy_Jeff on 2009-05-13
Here is a link for the alternate cd. [http://mirror.anl.gov/pub/ubuntu-iso/CDs/jaunty/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/jaunty/)

---

### Post by mr.bobbles on 2009-05-13
I tried using  8.10 and starting it in low graphics mode i got the same busy box.  Ill try the other cd.  

Thanks

---

### Post by mr.bobbles on 2009-05-14
Ok so i tried the alternate cd and it was working just fine,  no busybox.  But i got a error saying "can not detect and mount cd-rom"  This is how i installed ubuntu in the first place so i sont see why it wont work.  I am using my dvd drive,  should i burn it to a cd and use my cd drive?

Thanks

---

### Post by 123456789123456789123456 on 2009-05-14
ok, I need some information from you.  Under your current Ubuntu installation, what drives/devices are listed.  Does it read the cd drive, and the dvd drive?

Next, start the computer up, and see if the drives are listed under BIOS, under the connections of IDE contollers.
See if the they are both listed correctly.
Determine which drive is considered IDE master.
Make sure that the BIOS is set to boot from that drive.
Insert the disk in that drive and attempt to install, the reason the Busy box error is comming up is because Ubuntu can't detect the cd drive, that the cd is located in.
If it still continues, do the following, open the case, unplug the IDE cables to the drives, determine if the drives are jumpered Master/slave, or just cable select(CS).  If they are master slave configuration, you need to make the slave drive master, and plug the IDE cables back up, and restart the computer with the cd in the other drive.  if cable select, you don't have to worry about jumpering the drive.  I only say this because some BIOS's don't allow boot from secondary cd drives.

If your computer BIOS does allow this, don't worry about re jumpering the drives.
The only thing I can think of is that A, if the version of Ubuntu was before 7.10 originally, and you upgraded through update manager, to current, the versions of Ubuntu after 7.04 for some reason are not compatable with the BIOS.  Or B, which seems the most likely at the moment, the drive you booted the live cd from, is having troubles, it is most likely that the drive is giving out after it loads the first parts of the OS into ram.

Test this, get a copy of windows, or a linux live cd, like slax, see if it boots all the way into those systems.  If it does, then the problem is not with the drive, but may have something to do with the BIOS.

If slax works, you need to be able to boot into windows or DOS.  I suggest you google windows xp live cd.  You will also need to know what BIOS you have, and download the BIOS flash/upgrade program, and flash the BIOS.

It is entirely possible that the BIOS has become corrupted.  flashing the BIOS will erase all information you stored in CMOS, the BIOS memory, such as boot priority, the sequence the boot will take part, for instance, cd first, hard drive second, so on.  and any BIOS password you may have set.  But it will also upgrade the BIOS, and fix any problems that may have accurred with it.

The only other thing I can determine would be a problem with the IDE controller, and the Ubuntu interface,

Please post.
I can attempt to help you as much as I can.
IF you don't understand what I wrote tell me, what parts, and I will attempt to explain
I am a computer tech, so I know some terms, and procedures may be difficult to perform.

---

### Post by mr.bobbles on 2009-05-14
I checked my IDE and my dvd drive is the master.  Sorry i dont know much of anyting on how to check my bios or how to re flash it. If i were to get my hands on a windows cd and refomat the hard dive with that would it maybe fix the problem?

---

### Post by 123456789123456789123456 on 2009-05-14
not with Ubuntu.  I had a very simular problem with a Motherboard that I was using to build a computer for someone.  The problem was that even though, 8.10 actually went through and installed on the hard disk, after upgrading to 9.04, the dvd drive was not there anymore.  The live cd of 9.04 would not boot, always entered busy box.  the alternate cd informed me that it can not locate cd drive.

There was some sort of error with how the BIOS handled the communication with the drive, and with Ubuntu.  It is very possible that Windows may install, but that does not mean that Ubuntu will be able to work.

This is what you do, step by step.
Get a Slax cd, live cd, see if the computer boots off of it.
That will tell me if it is a hardware problem with the drive, or a BIOS problem with Ubuntu.
to flash the BIOS, note the model of computer you have.  Go and search Google for BIOS upgrade for that computer.
When you find a link for it, download the file.
Note that some files are meant to run from DOS.  However the newer ones can be run through windows.
If slax boots up.
Then you can get a copy of Windows Live cd, it is not one made by microsoft, someone made one of there own.  with the BIOS program saved to cd, or floppy, or even from an accessable partition on hard disk, such as a NTFS, or FAT32 partition.  Use the Windows Live cd to run the program, follow prompts, and after it is done, the BIOS would have been at the very least reset.  The Ubuntu Live cd's should boot.

---

### Post by GMachine_24 on 2009-05-14
Mr. Bobbles:

Hi. Before you set about flashing your BIOS and all that other stuff, perhaps you want to read this thread:

[http://ubuntuforums.org/showthread.php?t=1053939](http://ubuntuforums.org/showthread.php?t=1053939)


I tried to do an install, along with many others, and had trouble getting "busybox" and other errors until we did a complete hard drive wipe with something other than Ubuntu or Windows - some possibilities are "dban" and "killdisk" - they will kill all partition, system etc. information. Then you should be able to install Ubuntu cleanly.

GM

---

### Post by 123456789123456789123456 on 2009-05-14
> **GMachine_24 said:**
> Mr. Bobbles:

Hi. Before you set about flashing your BIOS and all that other stuff, perhaps you want to read this thread:

[http://ubuntuforums.org/showthread.php?t=1053939](http://ubuntuforums.org/showthread.php?t=1053939)


I tried to do an install, along with many others, and had trouble getting "busybox" and other errors until we did a complete hard drive wipe with something other than Ubuntu or Windows - some possibilities are "dban" and "killdisk" - they will kill all partition, system etc. information. Then you should be able to install Ubuntu cleanly.

GM

I am not the one who you were writing this to, but I read the entire post you posted, It would seem that at the current time, that post is also unsolved.  I don't understand what that post could be helpful.  I would deffinatly not suggest reformatting, and zeroing out the hard drive to attempt to get a unable to locate cd error fixed.  I mean no disrespect to you, but let me bring this to light

Busy box errors can be caused from several areas, this could be a damaged disk, error reading hard disk, a failing cd drive, or in the case I had, incompatability with the BIOS and Ubuntu.  However concluding that this person, used a alternate install cd, and it gave back an error that Ubuntu could not locate the cd drive.

Assuming that Ubuntu installed fine at one point before, and no version of Ubuntu will load from live cd, I find it hard to believe that simply wiping the disk would fix the problem.  If however he wants to attempt this, I would suggest that having the BIOS flash program safe and handy would be a good idea, just in case wiping the disk does not work, and even if it does, having the program for maintence purposes would be a good idea.

---

### Post by 3startuna on 2009-05-14
> **mr.bobbles said:**
> I tried using  8.10 and starting it in low graphics mode i got the same busy box.  Ill try the other cd.  

Thanks

busy box and a blank screen?

There is a problem with your display drivers. 

There might be some hardware that unbuntu is conflicting with. 

Try this open your computer pull out the graphics card it will switch to the on board. 

Plug in the CD go into bios set the primary boot to the CD or DVD drive.

you can disable booting from the harddrive all together.

Start up the computer to boot from the CD when the screen pops up go to "check cd for errors"

If your install disc is corrupted your gonna have alot of problems

If all is well proceed with the installation, follow the instructions from there on out.

Once he installation is complete and the computer starts booting up press 

ctrl-alt-f1

this will bring you to the terminal 

type in your login info then the following

sudo apt-get install ubuntu-desktop

or 

sudo apt0get upgrade ubuntu

run that then try to restart it will configure everything then restart your desktop should load

I had a simular problem with my install, the problem was I had a ATi TV card i forgot about that was creating problems, also for some reason it wouldnt run on my onboard card until i did the update.

hope this helps

after you get it running restart plug in the nvidia card reboot.

---

### Post by 123456789123456789123456 on 2009-05-14
> **3startuna said:**
> busy box and a blank screen?

There is a problem with your display drivers. 

There might be some hardware that unbuntu is conflicting with. 

Try this open your computer pull out the graphics card it will switch to the on board. 

Plug in the CD go into bios set the primary boot to the CD or DVD drive.

you can disable booting from the harddrive all together.

Start up the computer to boot from the CD when the screen pops up go to "check cd for errors"

If your install disc is corrupted your gonna have alot of problems

If all is well proceed with the installation, follow the instructions from there on out.

Once he installation is complete and the computer starts booting up press 

ctrl-alt-f1

this will bring you to the terminal 

type in your login info then the following

sudo apt-get install ubuntu-desktop

or 

sudo apt0get upgrade ubuntu

run that then try to restart it will configure everything then restart your desktop should load

I had a simular problem with my install, the problem was I had a ATi TV card i forgot about that was creating problems, also for some reason it wouldnt run on my onboard card until i did the update.

hope this helps

after you get it running restart plug in the nvidia card reboot.

here is a dumb question, what if the video card that is causing the problem is the built in video card.  When I had the busy box error, the video card was built in.

---

### Post by 3startuna on 2009-05-14
mine did that with my onboard card. The procedure i laid out worked for me. 

My computer also wouldnt run live CD with the onboard card

---

### Post by 123456789123456789123456 on 2009-05-14
so you purchased either a AGP for PCIe video card and used it then?

I had a simular problem to this one, however I concluded it was a motherboard problem, it would not boot live or alternate 9.04, but did boot and install 8.10
however when 9.04 was installed after it upgraded from 8.10, the dvd drive was not listed.

the graphics, and sound worked perfectly.
In an attempt to fix it, I converted the IDE dvd drive to SATA, and the BIOS refused to boot from the dvd drive, at any case, I even told it to not boot from hard drive at all, and it still booted from the hard disk.

But I would hate to say that the motherboard or BIOS is going out.  But if the disks worked on the current configureation before, why would they not work now?

that is the confusing part I am trying to understand

---

