---
title: "Virtual Box v. Parallel Installation"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-13
I have been experimenting with both Debian and Ubuntu and am developing a real appreciation for Ubuntu.  I have it running on my desktop with a dual boot configuration with Windows XP on one hard drive and Windows XP and Ubuntu on the second hard drive, each in a different partition - those partitions were created before I installed XP on that hard drive for use in the event of a system failure on the primary hard drive.  That set up seems to be working well for me.

I also have a netbook - 160gb harddrive with 1 gb RAM that came with Windows XP installed.  It has a small (7gb) partition which I presume is a reinstallation utility and the rest of the hard drive is a single, primary partition.  I am considering configuring this computer as a dual boot machine - I am reluctant to make it straight Ubuntu primarily because I have a couple of mapping programs on the computer which I use in combination with a Garmin gps and, based on my initial attempts, those applications are not yet compatible with Ubuntu.

Based on what I have read, the Ubuntu installation can be used to create a partition within an existing partition in which Windows XP is already installed - assuming that I have done a scandisk and defrag of that drive prior to the Ubuntu installation.  I also have found information about downloading and installing VirtualBox into Windows XP and then installing Ubuntu within VirtualBox.  Assuming that my understanding is correct, what are the relative merits of running Ubuntu in a parallel installation vs. running it in VirtualBox?

---

### Post by ikisham on 2009-10-13
The merits of running in a parallel (dual-boot) installation are:
- faster (in VB the machine has to take care of both systems, no problem if it's a powerful machine).
- if Windows break down, you still have Ubuntu.

The merits of running in VirtualBox:
- you have both systems at once.

---

### Post by swoody on 2009-10-13
With VirtualBox (or any other virtualization program) you're really not going to get the full performance that you would with a parallel install. Setting up a dual-boot setup with XP and Ubuntu will allow Ubuntu to run natively on your hardware, and again, you're going to see improved performance from this method. I find virtualbox is a great program to test out different OS'es but if I'm wanting to use an OS as more than just testing/previewing I will install it to the hard drive.

The method you mentioned about installing to an existing Windows partition is Wubi:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Wubi is another great option, but my preference is still to setup a dual-boot setup if I plan on using an OS more in-depth. Again, this is just my opinion though, it's up to you to look through the different options available and decide which one you feel will suit your needs best :)

---

### Post by Schendje on 2009-10-13
Yeah, the main disadvantage of VM's is that it's a lot slower and takes up a lot of RAM. Also, hardware acceleration doesn't work, so no 3D or fancy effects. (either that or it's very experimental).

---

### Post by OlsenCNC on 2009-10-13
I'd recommend dual boot. The Ubuntu installer will partition your existing XP Partition and you can choose how much space can be used for XP and how much for Ubuntu by just moving a slider left and right; it's very easy.

---

### Post by ikisham on 2009-10-14
Also Windows runs very well inside Ubuntu in VirtualBox. With time you could try this setup (specially if you need it only to run this or that software).

---

### Post by jmundinger on 2009-10-14
> **swoody said:**
> With VirtualBox (or any other virtualization program) you're really not going to get the full performance that you would with a parallel install. Setting up a dual-boot setup with XP and Ubuntu will allow Ubuntu to run natively on your hardware, and again, you're going to see improved performance from this method. I find virtualbox is a great program to test out different OS'es but if I'm wanting to use an OS as more than just testing/previewing I will install it to the hard drive.

Thanks to you and to the others for the thoughtful responses.  That's the information that I was looking for.

It sounds line the dual boot option is the way to go.  But, I think I will wait to do it until the "official" version of 9.10 is released.  That will also give me another couple of weeks to get more familiar with the installation that I have running on my desktop.

---

### Post by Merk42 on 2009-10-14
Seems you've already made up your mind.  That's good

Do you plan on going from Windows XP to Windows 7? If you do that will most likely ruin any dual booting you have configured and you'll have to fix it.

---

### Post by louieb on 2009-10-14
You should try VirtualBox. If it slow (and with just 1GB ram it will be slow and slow down your machine all around). But for setting up an environment for testing or just goofing around its hard to beat.  

I have it on both a Linux an a Windows host. There may be better VMs out there faster and more features than  [VirtualBox]("http://www.virtualbox.org/") but its very easy to set up and use.

---

### Post by Merk42 on 2009-10-14
> **louieb said:**
> You should try VirtualBox. If it slow (and with just 1GB ram it will be slow and slow down your machine all around). But for setting up an environment for testing or just goofing around its hard to beat.  

I have it on both a Linux an a Windows host. There may be better VMs out there faster and more features than  [VirtualBox]("http://www.virtualbox.org/") but its very easy to set up and use.
I really would not recommended a VM on a netbook, the lower specs would possibly make either unusable.

---

### Post by blur xc on 2009-10-14
I do both, dual boot and run vbox.  Garmin software, though I have not yet tried it as my edge 305 is broken, is small and lightweight and should run fine in vbox.

Some 3d graphics can run in vbox, but I've had poor luck with it.  USB support can be spotty, depending on the device and it's software.  For example, I have not been able to run my kids' sanza fuses software in vbox- even though the devices are mounted in the virtual machine, the firmware updater and media converter wont see them.

So, I'd reccomend you get another gig of ram if your computer has room for it, as it will help everything run better/faster anyway, and try vbox.  You need the peul edition, not the ose version, since it won't support usb ports.  

Firing up a virtual machine is way more convenient than having to reboot all the time.

BM

---

### Post by Xalor on 2009-10-14
I wouldn't go the VM route, and I would keep the windows partition. If it doesn't work as well as it does in Windows I would keep the partition even if its just for the maps. The VM you make in something like Virtualbox is great for systems with a bit more power. I think a netbook would benefit from a dual-boot, but it may be a little bit of a space issue if you work with a lot of media files. I think you should get rid of the recovery partition unless you need it and install ubuntu side by side. 

I still use a VM on Vista for trying out different distros, just for fun, but dual-booting was the best option for me, because it uses your computer to the full potential. I just installed Ubuntu 4 days and I've been using it ever since, only booted Vista to check if everything went fine during the Ubuntu installation. 

By the way Ubuntu is probably gonna be faster on the netbook, and maybe a little bit nicer on the graphics end, just cause XP kinda looks ugly >.>

---

### Post by NightwishFan on 2009-10-14
I agree, Xp on a netbook is absurd. I cannot believe they still try to sell it.

On a related note, I would say if you are fond of Ubuntu on the whole, to try to see if your mapping software runs in Wine or a Virtual Windows under Ubuntu. If so, then run your machine as an Ubuntu host and a Windows virtual guest.

Dual-booting is another option, but unless you use both systems heavily (and not just one) it seems to be a waste of time.

---

### Post by jmundinger on 2009-10-14
> **Merk42 said:**
> Do you plan on going from Windows XP to Windows 7? If you do that will most likely ruin any dual booting you have configured and you'll have to fix it.

If I make the transition to Windows 7, it won't be on either my desktop or the netbook.  To be honest, part of my purpose for experimenting with Ubuntu now is the possibility of abandoning Windows altogether if/when I make another computer purchase.

I had an older lap-top dedicated to Linux.  It went from windows (with two primary partitions) to dual boot windows-debian to dual boot debian-ubuntu.  It was working pretty well for me - within the limitations of that particular machine - but its new life as a Linux machine was more fun than it could handle and the motherboard eventually gave out.  So, now, in addition to running Ubuntu in a dual boot configuration, I'm looking for ways to extent the learning experience by also have it running from my netbook.

---

