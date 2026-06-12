---
title: "Running existing Ubuntu from Windows?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-07
Hello,

I have a dual boot set up with Vista and Ubuntu 8.10. Is there a way to run my existing Ubuntu installation, from the Linux partition, from Windows?

I did some google searching and everything I found talked about installing a fresh linux system as a virtul machine but that's not really what I'm looking for. I'd like to be able to access the Ubuntu system that's already installed from Windows and also be able to boot up into Ubuntu normally.

Thanks.

---

### Post by perlluver on 2008-12-07
There is an ext3 program that makes it so you can open up the hard drive on your system, [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/), but be careful when using it, you will have full access to the hard drive containing Ubuntu.

---

### Post by dracayr on 2008-12-07
yeah, vmware can boot from an existing partition whithout having to make a seperate disk image

dracayr

---

### Post by pedrogfrancisco on 2008-12-07
And VirtualBox.

Anyway, perlluver thought you were talking about accessing your Linux's partitions and not booting the system. You can either boot Linux from Windows or access the partition with an ext3 driver, but not both (at the same time at least).

The same thing applies to your Windows partition. Don't access it from Linux while booting Linux inside Windows or you'll seriously screw the Windows partition's data.

Basically, you can only access one file system from one OS. Accessing it at the same time from two different OS will damage the file system.

I would advise you to be careful since what you intend to do is error prone.

If you still want to do it, read the following threads carefully to ensure you understand the risks and problems you'll be facing. These threads apply to Windows instead of Linux but, besides the stupid Windows activation, the problems you'll face are the same:

[http://ubuntuforums.org/showthread.php?t=769883]("http://ubuntuforums.org/showthread.php?t=769883")
[http://ubuntuforums.org/showthread.php?t=664692]("http://ubuntuforums.org/showthread.php?t=664692")

Good luck :)

---

### Post by dracayr on 2008-12-07
pedro, in virtualbox, you have to create a disk image to boot that partition ( in the howto you linked, thats step 2). Currently only VMware can boot directly from a different partition

dracayr

---

### Post by pedrogfrancisco on 2008-12-07
dracayr, yes but the disk created is a few KBs in size; if you look at the command:

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
```

you'll notice > -rawdisk /dev/sda -partitions 2 which indicates the disk created is no more than a "pointer"/shortcut to the raw disk/partition.

EDIT: Though it isn't as VMware, where you can select the partition where to boot from using the mouse, the final effect is the same.

---

### Post by Chris Hansen on 2008-12-07
> **dracayr said:**
> yeah, vmware can boot from an existing partition whithout having to make a seperate disk image

dracayr

I did download VMware player and took a look at it and I didn't see the windows partition from it.

It sounds like there are some risks involved. Mostly I'm interested in it as a learning experience but it sounds like there might be less risky projects to work on.

It would be nice to access windows from linux so I can use MS Office though. That's really the only thing I need Windows for.

---

### Post by pedrogfrancisco on 2008-12-11
Consider installing Windows on a VM.
Consider using Crossover Office.

If you go through with it on VirtualBox DON'T install VirtualBox tools. Despite people saying it works properly in VirtualBox 2.0 after installing VirtualBox tools I couldn't start Windows neither on Native nor on Virtual Machine; had to use "Last known good configuration"...

---

### Post by anewguy on 2008-12-11
Yes, you can have virtualbox boot and load an OS from a physical partition without needing a virtual disk (at least of any consequence).  The instructions for doing so are in the advanced section of the help that comes with virtualbox, and you can/need to use vboxmanage to do it.  However, I would strongly recommend you not.  At one time I did do this - only in the reverse - booting an existing Windows partition within virtualbox while running virtualbox in Linux.  There are several dangers to this, and I think everyone has summed them up pretty well - you stand a REAL chance of screwing up your disk.  Not physically harming it, but logically harming it so that you would have to completely reinstall.  I didn't like the idea then of dual-booting, and didn't listen to the advice of some very experienced, very knowledgable people on this forum, and it eventually bit me.

If you really want to run an OS in virtualbox or any other virtualization product, it is just my recommendation that you do so by creating a virtual disk within the product as they truely intend, then install the apps and data you want there.  You can copy such things to a removable media - such as usb stick, CD, etc., and load them in the new VM.

Yes, this requires extra work that we normally aren't inclined to want to do - we always want the easiest and fastest way to do it.  And I understand wanting to share data directly with the host OS (don't do it, in my opinion).

All I can say is that it is just my opinion, based on my own experience (and not following some very well intended advice given me that I was rude about at the time - [sorry, and thank you Bohdi.zazen!!]).  I regretted it in the long run.

That's just my opinion - others obviously have theirs that are just as valid.

Dave ;)

---

### Post by pedrogfrancisco on 2009-08-31
Someone was kind enough at VirtualBox forums to make a tutorial:

[Windows XP: In both VM and native (using Linux as host OS)]("http://forums.virtualbox.org/viewtopic.php?t=9697").

I've followed them and they work.
I gotta register there to add some useful pointers later, though.

---

