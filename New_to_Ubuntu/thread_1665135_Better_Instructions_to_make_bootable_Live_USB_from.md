---
title: "Better Instructions to make bootable Live USB from ISO (Canonical please fix this)"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Andy06 on 2011-01-11
On the official Ubuntu download page [[http://www.ubuntu.com/desktop/get-ubuntu/download]](http://www.ubuntu.com/desktop/get-ubuntu/download]), the instructions ask you to download the pendrivelinux universal usb installer. I have found this tool to be the worst out of the 3 popular utilities to do this task, it is quite buggy, takes longer and often fails with persistence files.

WHY has Canonical mentioned it there when they have an OFFICIAL usb-creator that is super fast and reliable AND is also included in the Ubuntu iso that you download!! (Open the iso file and it is in there as an .exe) :S:S

Can someone familiar with launchpad mark this as a bug?
Thanks

---

### Post by MooPi on 2011-01-11
I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect  internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files.

---

### Post by bodhi.zazen on 2011-01-12
> **Andy06 said:**
> On the official Ubuntu download page [[http://www.ubuntu.com/desktop/get-ubuntu/download]](http://www.ubuntu.com/desktop/get-ubuntu/download]), the instructions ask you to download the pendrivelinux universal usb installer. I have found this tool to be the worst out of the 3 popular utilities to do this task, it is quite buggy, takes longer and often fails with persistence files.

WHY has Canonical mentioned it there when they have an OFFICIAL usb-creator that is super fast and reliable AND is also included in the Ubuntu iso that you download!! (Open the iso file and it is in there as an .exe) :S:S

Can someone familiar with launchpad mark this as a bug?
Thanks

You can report it yourself =)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Or e-mail Canonical

---

### Post by Andy06 on 2011-01-12
> I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files. 

Good point but sort of off track :P

Live USB systems are perfect for people who want to try first (its, simpler, easier n less maintenance than a full install).
Also Live USBs (w/o persistence) make a lot of sense as mobile troubleshooting or emergency use systems since they are essentially reset on each use. You can let kids or newbies goto town on a LiveUSB system and then simply pull it out and plug it back in and everything is pristine again. :D

> 
You can report it yourself =)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Or e-mail Canonical 

I'm kinda hoping someone with "pull" or a dev comes across this and reports it. Of the dozen or so bugs I have filed, none have ever been fixed......and no I didn't just file random, inane bugs, they were mostly things like the one above - no brainers.

It's just that the already HAVE this awesome tool which works perfectly, they also SHIP it by DEFAULT in every iso and yet they advertise someone's else's shoddy, less than ideal competitor!

Oh well.....off to launchpad :)

---

### Post by Andy06 on 2011-01-12
> I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files. 

Good point but sort of off track :P

Live USB systems are perfect for people who want to try first (its, simpler, easier n less maintenance than a full install).
Also Live USBs (w/o persistence) make a lot of sense as mobile troubleshooting or emergency use systems since they are essentially reset on each use. You can let kids or newbies goto town on a LiveUSB system and then simply pull it out and plug it back in and everything is pristine again. :D

> 
You can report it yourself =)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Or e-mail Canonical 

I'm kinda hoping someone with "pull" or a dev comes across this and reports it. Of the dozen or so bugs I have filed, none have ever been fixed......and no I didn't just file random, inane bugs, they were mostly things like the one above - no brainers.

It's just that the already HAVE this awesome tool which works perfectly, they also SHIP it by DEFAULT in every iso and yet they advertise someone's else's shoddy, less than ideal competitor!

Oh well.....off to launchpad :)

---

### Post by Andy06 on 2011-01-12
> I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files. 

Good point but sort of off track :P

Live USB systems are perfect for people who want to try first (its, simpler, easier n less maintenance than a full install).
Also Live USBs (w/o persistence) make a lot of sense as mobile troubleshooting or emergency use systems since they are essentially reset on each use. You can let kids or newbies goto town on a LiveUSB system and then simply pull it out and plug it back in and everything is pristine again. :D

> 
You can report it yourself =)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Or e-mail Canonical 

I'm kinda hoping someone with "pull" or a dev comes across this and reports it. Of the dozen or so bugs I have filed, none have ever been fixed......and no I didn't just file random, inane bugs, they were mostly things like the one above - no brainers.

It's just that the already HAVE this awesome tool which works perfectly, they also SHIP it by DEFAULT in every iso and yet they advertise someone's else's shoddy, less than ideal competitor!

Oh well.....off to launchpad :)

---

### Post by Andy06 on 2011-01-12
> I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files. 

Good point but sort of off track :P

Live USB systems are perfect for people who want to try first (its, simpler, easier n less maintenance than a full install).
Also Live USBs (w/o persistence) make a lot of sense as mobile troubleshooting or emergency use systems since they are essentially reset on each use. You can let kids or newbies goto town on a LiveUSB system and then simply pull it out and plug it back in and everything is pristine again. :D

> 
You can report it yourself =)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Or e-mail Canonical 

I'm kinda hoping someone with "pull" or a dev comes across this and reports it. Of the dozen or so bugs I have filed, none have ever been fixed......and no I didn't just file random, inane bugs, they were mostly things like the one above - no brainers.

It's just that the already HAVE this awesome tool which works perfectly, they also SHIP it by DEFAULT in every iso and yet they advertise someone's else's shoddy, less than ideal competitor!

Oh well.....off to launchpad :)

---

### Post by HermanAB on 2011-01-12
Hmm, I dunno why the Ubuntu ISO files are so behind the times. On pretty much every other distro, all you need to do is use Data Definition to copy the ISO file to the USB stick:
dd if=isofile of=/dev/sdb

and then it Just Works (TM), but don't try that with buntu.
:(

---

### Post by C.S.Cameron on 2011-01-12
> **MooPi said:**
> I don't understand why there is this fascination with persistent flash drive install when you can do a normal install to a flash drive. I have two flash drives dedicated to Ubuntu for diagnostic purposes and they work flawlessly. I generally disconnect  internal hard drives when I do a flash install so they don't affect the grub config. That is the only step that I suggest to make a flash drive install versus a normal hard drive.
I carry the flash drive with a USB wireless dongle and a separate flash drive for files.

You don't need to carry a separate flash drive for files if you make the first partition FAT32 and make the second partition /.

I agree that Startup Disk Creator, (usb-creator), is the best and easiest to use of all the disk image installers.

---

### Post by oldfred on 2011-01-12
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

If I click on showme how with Ubuntu it says to use startup disk creator. Only with windows does it say to download pen drive.

> Ubuntu

   1. Insert a USB stick with at least 2GB of free space
   2. In the main menu, go to System > Administration and open 'Startup Disk Creator'


---

### Post by Andy06 on 2011-01-13
Yep, sorry should have clarified that.
That would be close to 100% of the first time users though :D

---

### Post by topher-t-mill on 2011-01-14
Does MooPi  mean when talking about an ordinary install to a flash drive, that one can build a system with extra software, which does not disappear in the way that Andy06 alludes to when he talks of the flash drive regaining its pristine state?
I want to have a flash drive with useful stuff like fully working evolution and Xiphos with downloaded extras up and running so when I plug into a laptop it is all up and running,. I have tried using g4l to produce an iso to no avail and I cannot find out how to use partimage.

---

### Post by topher-t-mill on 2011-01-14
Does MooPi  mean when talking about an ordinary install to a flash drive, that one can build a system with extra software, which does not disappear in the way that Andy06 alludes to when he talks of the flash drive regaining its pristine state?
I want to have a flash drive with useful stuff like fully working evolution and Xiphos with downloaded extras up and running so when I plug into a laptop it is all up and running,. I have tried using g4l to produce an iso to no avail and I cannot find out how to use partimage.

---

### Post by topher-t-mill on 2011-01-14
Does MooPi  mean when talking about an ordinary install to a flash drive, that one can build a system with extra software, which does not disappear in the way that Andy06 alludes to when he talks of the flash drive regaining its pristine state?
I want to have a flash drive with useful stuff like fully working evolution and Xiphos with downloaded extras up and running so when I plug into a laptop it is all up and running,. I have tried using g4l to produce an iso to no avail and I cannot find out how to use partimage.

---

### Post by madjr on 2011-01-14
this might be a simple papercut. check the link in my sign to report it.

unless something gets marked as a bug, it rarely gets fixed.

also developers rarely frequent the forums.

---

### Post by I2k4 on 2011-01-15
"I want to have a flash drive with useful stuff like fully working evolution and Xiphos with downloaded extras up and running so when I plug into a laptop it is all up and running,"

The Pendrive installer being criticized here has actually worked great for me from XP as I've experimented with different Ubuntu versions on a netbook and large laptop, over the last few weeks.  It is slow, and maybe there is a better one, but it certainly seems to work. 

_The one important step that the Ubuntu site download instruction doesn't include is to set "Persistence" during the installatio_n:  I'm finding Lubuntu 10.10 runs quite well and saves all settings with 1GB of Persistence on a 2GB USB drive as well as 3GB on a larger drive.  There are so many versions, even of just Ubuntu, that setting Persistence seems necessary to get a real feel for the GUI and how well it responds - running off a USB drive is a good acid test for OS efficiency on a low power system.

---

