---
title: "Bad start!"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by symphony1010 on 2010-08-22
Today I installed Ubuntu for the first time and attempted to overwrite my secondary OS which was Vista. This went ok but on restart I received no dual-boot screen to allow access to my primary OS, Windows 7 (64 bit). 

To cut a long (very long) story short I ended up having to reinstall W7 after many attempts at reconfiguring the bootmanager. I was left unable to access any OS!
Presently I have had to disconnect the physical hard drive with Ubuntu on as, if I attach it, the PC reports a 'miising operating system'. My new installation of Windows 7 boots fine when this hard drive is not attached.

2 questions:-

1)How do I get the use of my other hard drive back? Presumably there is still some kind of issue there with the bootmanager.
2) This was a very bad first experience with Linux - how should I safely set about configuring a dual boot system on two hard drives?

Thanks for any suggestions. Excuse my newbie status - this is my first post!

---

### Post by lykeion on 2010-08-22
Hi,
that was not a great start with Ubuntu =)

I can't say why the windows os was not available after installation of ubuntu. 
This is normally the way you do to setup a dual boot system:
1) install win os
2) install ubuntu (it should pick up the win os and put it in the boot menu)

you should read this document:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
especially the part with mbr and recovery of grub after win install

---

### Post by symphony1010 on 2010-08-22
I have now managed to reformat the offending drive through changing to drive order in the BIOS. I'm not sure how this became changed! Before deleting the partitions they appeared as unavailable in disk manager in W7.
I undertook the original install as you described but I wonder if I did something when I decided to choose a partition. About 10 hours ago(!) I decided to let Ubuntu format by Vista partition and remember having to choose / within one of the options. I thought it would be the 'boot' option but this wouldn't work. Ubuntu installed fine but I never saw a boot menu when I later restarted. I also wondered if my Asus motherboard had anything to do with it as it in itself has a Linux interface which runs on startup (but didn't once Ubuntu was on board).

I am somewhat scared to try this again but have downloaded Easy BCD in case I feel the urge! Can I do better than this?

Many thanks for your help.

> **lykeion said:**
> Hi,
that was not a great start with Ubuntu =)

I can't say why the windows os was not available after installation of ubuntu. 
This is normally the way you do to setup a dual boot system:
1) install win os
2) install ubuntu (it should pick up the win os and put it in the boot menu)

you should read this document:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
especially the part with mbr and recovery of grub after win install

---

### Post by lykeion on 2010-08-23
I'd say the best way to learn is from your mistakes. I've had my share of struggling with OS installations and partitioning, 
and from that experience I got confidence and a sense of being in control rather than be scared of errors and mistakes.
A non-booting computer can be very stressful, but you only need patience and not freaking out. Some things I learned to do though is:
1) always backup your important data
2) to make sure you have installation CD (in case of failure)

Normally in a dual-boot setup you set each OS to have its own partition. What is a partition? See _[this]("https://help.ubuntu.com/community/HowtoPartition")_
In your case (with two HDDs?) this would be something like this:

/dev/sda -> Vista
/dev/sdb -> Ubuntu

The recommended procedure to setup is to start off from a Vista installation, then install Ubuntu. The reason for this is that Ubuntu can detect the Windows OS and setup dual-boot. 
If you do it the other way around Windows is unable (not willing maybe?) to detect Ubuntu, and will overwrite the MBR, which could cause boot errors. What is MBR? See _[this]("http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm")_
If you find yourself in that situation it's good to know beforehand that there are remedies. See _[this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_

When you install Ubuntu you are asked to setup partitioning. What is a partition? See _[this]("https://help.ubuntu.com/community/HowtoPartition")_
Partitioning during installation could be setup automatically or manually. The automatic option sets up a single partition and a swap partition. 
Automatic partitioning is ok, but after you've gained confidence of installations you'd prefer to manually set it up to have root boot and home in different partitions. 
There are many benefits of this. You could also setup space on the hard drive which could be read by both Ubuntu and Windows (FAT32 formatted) to easily share data between them.

Ok, this was some info on dual-booting OS. This is not a guide, there are lots of good guides with pictures as well on the web.
Just google around and you'll find them. A tip if you're after good Ubuntu guides is to include "ubuntu documentation" in your search string.

Good luck and feel free to post if you have any questions/problems

---

### Post by eriktheblu on 2010-08-23
Lucid has had a rather bad reputation for detecting Windows installs. This is actually quite a simple fix if you know what to do.

Simply enter the command
```
sudo update-grub
```
in the terminal (or alt + F2 for the run command box) and your Windows installs should appear in the boot loader.

---

