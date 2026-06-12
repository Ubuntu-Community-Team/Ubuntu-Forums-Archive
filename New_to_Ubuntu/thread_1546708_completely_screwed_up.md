---
title: "completely screwed up"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Jaimie Dunford on 2010-08-05
Hi everyone,
 
just a quickie. Had ubutu 10.4, got a bit cocky and managed to delete most of the root directories. The upshot of this is i now have no os as ubuntu wouldn't load, couldn't format the hard drive from the installation disk so had the disk formatted at pc world, tht that would be ok, however when booting up pc displays "unknown file format" "grub recover" I have looked on here for a solution, but nothing works; should i just ditch the hard drive and install a new one?
 
Thanks for yr help guys,
 
 
Jaimie

---

### Post by TCHebb on 2010-08-05
That shouldn't be necessary. What happens when you try to boot from a LiveCD?

---

### Post by Jaimie Dunford on 2010-08-05
Hi TC,  nothing, just the grub recover legend.

---

### Post by TCHebb on 2010-08-05
Hmm... Are you sure that you have your BIOS set to boot from the CD before the hard drive?

---

### Post by sidzen on 2010-08-05
" . . . should i just ditch the hard drive and install a new one?"

No.  See if you can start the live CD, do a Ctrl-Alt-F2 to console and type the command
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]This will fill the hdd (use "of=/dev/hda" for IDE hdd) with zeros and allow a clean install.  One can do this with any live CD normally.

Got to go for a while.

---

### Post by Jaimie Dunford on 2010-08-05
hi sidzen, no luck i'm afraid it just goes to the pci device listing screen where it says "verifying pool data update success error:unknown file system. grub rescue>
 
control alt f2 does nothing either....
 
any other ideas?
 
ty . J.

---

### Post by Ozymandias_117 on 2010-08-05
> **Jaimie Dunford said:**
> hi sidzen, no luck i'm afraid it just goes to the pci device listing screen where it says "verifying pool data update success error:unknown file system. grub rescue>
 
control alt f2 does nothing either....
 
any other ideas?
 
ty . J.

Sounds like it's either not booting from the CD, or it's a bad cd.

---

### Post by jtarin on 2010-08-05
I use [this]("http://www.paragon-software.com/home/pm-express/") to partition, backup,recover and/or prepare my disk. Can be used from a USB flash. FREE

---

### Post by Jaimie Dunford on 2010-08-05
think the cd is good, any thing else I can do?

---

### Post by Palanthas on 2010-08-05
Does the CD start up at all? Being 10.04, you will have to hit enter(or any other key) while the CD is booting to get into the CD's menu. (or at least one that I am used to from the older versions of Ubuntu) Run the check disk function to make sure the CD is good. You may need/want to run this on another computer if you can to make sure its just a bad CD and not something going amiss with the computer just reading the CD wrong.

Your probably right but I had a similar issue where it wouldn't install the OS correctly. Everything looked right, ran right, installed right, etc... but it was like one file was missing or something and after two days of scratching my head, I ran the check disk just for kicks and found out I had burned a bad disk. Could also have a scratch/dirt... Just some thoughts. ;)

---

### Post by jtarin on 2010-08-05
> **Jaimie Dunford said:**
> think the cd is good, any thing else I can do?Yes as I suggested above or with any tool you want. Format the drive and the MBR...then if your bios is set to boot from the cd and it won't......bad disk.
[Utilities and methods]("http://www.bootdisk.com/pendrive.htm") for formating and creating a bootable USB flash and others.

---

### Post by sidzen on 2010-08-06
Here's what I'd do:
If you have another machine, take the hard drive out and physically place it in another, working PC.  Then use the dd command after booting any live CD or another good option is to prepare it with SystemRescueCD 1.3.4 or 1.3.5 from [http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/)
The original PC could have a BIOS problem.

While you're at the other machine, check the md5sum of the burnt iso, too.  See
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Keep at it -- you'll get it!

---

