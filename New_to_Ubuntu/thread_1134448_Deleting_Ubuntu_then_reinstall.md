---
title: "Deleting Ubuntu then reinstall"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by RandomP on 2009-04-23
Hey guys, I was wondering how to uninstall ubuntu. I know I can install something over that partition, I was just wondering whether there was any way to delete ubuntu and it's partition on the drive?

Something happened to my Ubuntu 8.10 when I tried upgrading to 9.04 so now it does not start up, I even went into the recovery for Ubuntu and that did nothing so I will try to install Ubuntu 9.04 over that partition. If that does not work I want to delete the partition and Ubuntu.

Any suggestions?
------------------------------------------------------------------------------------
Alright, so now I have deleted the ubuntu partition and am left with 26.80GB Unallocated. The thing is, now windows will not start and the PC says error 22 when it is trying to find the grub menu or something.

---

### Post by kanikilu on 2009-04-23
If you want to "delete" it, just choose the option to format the partition(s) during the installation.

---

### Post by cariboo on 2009-04-23
I know it takes very little time to reinstall, but why not describe your problem in a little more detail, there is probably someone online right now that can tell you how to repair the problem.

---

### Post by sleepyjon on 2009-04-23
Do you have another OS installed on other partitions?

---

### Post by alphacrucis2 on 2009-04-23
> **RandomP said:**
> Hey guys, I was wondering how to uninstall ubuntu. I know I can install something over that partition, I was just wondering whether there was any way to delete ubuntu and it's partition on the drive?

Something happened to my Ubuntu 8.10 when I tried upgrading to 9.04 so now it does not start up, I even went into the recovery for Ubuntu and that did nothing so I will try to install Ubuntu 9.04 over that partition. If that does not work I want to delete the partition and Ubuntu.

Any suggestions?

Boot off the liveCD and run System/Administration/Partiton Editor. That will start up gparted. From that you can nuke any partitions on your hard disk(s). As a matter of interest, when you say 9.04 wouldn't start, can you tell us any symptoms? Quite often these problems are caused by graphics driver issues.

---

### Post by RandomP on 2009-04-23
Well, after it said the update was finished it asked me to restart the PC. I did. When it came to choosing which os to start with, I noticed that the kernel was still named 8.10 and the recovery had that too. I thought that maybe it would change after my first run of 9.04. Well, so I clicked it. Regular black screen, that usually happened when I started it up, then nothing, the monitor said "No input signal, going into sleep mode." I was like ok, this happens when I start up with ubuntu, but it only lasts a a few seconds. This time though the screen was off for a good 5 minutes without anything happening. So I restarted the PC, same thing. Then I went into recovery and tried the fix option. Again nothing. So now I want to either install ubuntu again if that works, or just get rid of it if I cannot.


Right now I am running Windows XP which is on the main partition. Ubuntu was on a smaller partition on this drive.

---

### Post by alphacrucis2 on 2009-04-23
> **RandomP said:**
> Well, after it said the update was finished it asked me to restart the PC. I did. When it came to choosing which os to start with, I noticed that the kernel was still named 8.10 and the recovery had that too. I thought that maybe it would change after my first run of 9.04. Well, so I clicked it. Regular black screen, that usually happened when I started it up, then nothing, the monitor said "No input signal, going into sleep mode." I was like ok, this happens when I start up with ubuntu, but it only lasts a a few seconds. This time though the screen was off for a good 5 minutes without anything happening. So I restarted the PC, same thing. Then I went into recovery and tried the fix option. Again nothing. So now I want to either install ubuntu again if that works, or just get rid of it if I cannot.


Right now I am running Windows XP which is on the main partition. Ubuntu was on a smaller partition on this drive.

It sounds like the update failed to update the grub menu.lst. If that is the only problem, you might be able to fix that manually by mounting the hard disk file system from the live CD and editing the menu.lst file. Still it would be safer to reinstall off the LiveCD as other things might have gone wrong.

---

### Post by RandomP on 2009-04-23
I booted the old 8.1 ubuntu CD I had and ran Gparted. Now that space which ubuntu was on is now unallocated. That unallocated space is 26.80GB.

Also, now for some reason windows does not start when I restart the PC so now I have to run the live CD to get online. Does anyone know how to solve this?

---

### Post by drs305 on 2009-04-23
It sounds like you deleted the information in grub needed to direct you back to windows. I don't use windows any longer but I think you use the windows install disk and "fixmbr". Someone here will know. Give them a couple of minutes.

---

### Post by RandomP on 2009-04-23
> **drs305 said:**
> It sounds like you deleted the information in grub needed to direct you back to windows. I don't use windows any longer but I think you use the windows install disk and "fixmbr". Someone here will know. Give them a couple of minutes.

I still have the windows recovery partition if I use recovery from the bios. I also have recovery CD's, but since this PC came with windows pre-installed, I do not have the Windows installation CD.

Also, if I get windows to work again, will the unallocated space go back to the old partition or will I have to merge the partitions?

---

### Post by Didius Falco on 2009-04-23
The reason that windows isn't loading is because you still have the GRUB bootloader in your MBR, but there is no other partition that contains stage 1.5 and 2 of the loader.

To get Windows booting again, use a windows bootable disk (your windows install cd will work just fine) and use the fixmbr command.

If you are using your Windows install cd, wait until it gets to the screen that offers choices and pick the recovery console. After the RC loads, type ```
fixmbr
``` and it will rewrite the main boot record.

Quit the cd and reboot and Windows should load.

Then you are ready to reinstall Ubuntu.

Here are a couple of links to help you with understanding the Grub Bootloader.

This is a fantastic resource. Bookmark it, read it, love it. If you ever need to find it on the web from your Live CD, it comes up as the #1 hit when I search for "Grub page".

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There is also a bootable CD called the Super Grub Disk that is very popular:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

This should get you back into windows, get you ready for your Ubuntu reinstall and give you some resources for understanding and using Grub to it's full potential.

If you have any other questions, c'mon back and ask.

---

### Post by Didius Falco on 2009-04-23
Okay, I'm a slow typist, and the situation changed a little while I was typing out my last post.

Here is a website with windows xp boot disc and CD images that you can burn and use.

[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by RandomP on 2009-04-23
Hmm... I have boot CDS though.

---

### Post by Didius Falco on 2009-04-23
> **RandomP said:**
> Hmm... I have boot CDS though.

Then you should be able to just load the boot CD and fixmbr from that.

---

### Post by RandomP on 2009-04-23
> **Didius Falco said:**
> Then you should be able to just load the boot CD and fixmbr from that.

It gives me the options to format my hard drive and restore factory settings, or to restore windows. So I just choose the restore one right since formatting will format the drive?

---

### Post by RandomP on 2009-04-23
I am not sure what I did, but I got the PC to start with windows after clicking the restore button in the recovery CD's then pressing restart.

---

### Post by Didius Falco on 2009-04-23
Good. Now you can reinstall Ubuntu if you want.

---

### Post by RandomP on 2009-04-23
Are there any free partition editors that I can use to put that unallocated space back into the main partition that houses XP?

---

### Post by drs305 on 2009-04-23
> **RandomP said:**
> Are there any free partition editors that I can use to put that unallocated space back into the main partition that houses XP?

Gparted on the ubuntu LiveCD can do it. It's under System, Administration, Partition Editor. I believe the latest versions all are automatically compatible with NTFS operations without having to install "ntfsprogs".

---

### Post by RandomP on 2009-04-23
> **drs305 said:**
> Gparted on the ubuntu LiveCD can do it. It's under System, Administration, Partition Editor. I believe the latest versions all are automatically compatible with NTFS operations without having to install "ntfsprogs".
Is there anywhere where I can read how to do it. Since when I ran it I could only delete partitions, but then those partitions became unallocated space and I could not merge it into any existing partition.

---

### Post by drs305 on 2009-04-23
> **RandomP said:**
> Is there anywhere where I can read how to do it. Since when I ran it I could only delete partitions, but then those partitions became unallocated space and I could not merge it into any existing partition.

Glad you asked. This might provide the answers you are looking for:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

If I were to guess, the problem is often trying to move space from or to a primary partition directly to or from an extended partition. That gets to be a bit tricky but once you understand the principle it isn't difficutl.

---

### Post by babloo75 on 2009-04-24
> **drs305 said:**
> It sounds like you deleted the information in grub needed to direct you back to windows. I don't use windows any longer but I think you use the windows install disk and "fixmbr". Someone here will know. Give them a couple of minutes.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
[http://ubuntuforums.org/showthread.php?t=245959](http://ubuntuforums.org/showthread.php?t=245959)
ttp://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/
[http://www.youtube.com/watch?v=4nqvCQd3bLI](http://www.youtube.com/watch?v=4nqvCQd3bLI)

I think these should help.

---

