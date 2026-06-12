---
title: "how to load win and linux on separate hard drives without shutting down to boot"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by 007casper on 2010-03-19
What is the best way to have different operating systems?

I was reading about [unbuntu inside windows using virtualbox, or dual boot with windows]("http://psychocats.net/ubuntu/virtualbox").  I wondered how reliable it will be to have two operating system side by side on the same hard drive.  

Now, the problem xp & ubuntu problem [over here]("http://ubuntuforums.org/showthread.php?p=8995995#post8995995") wants me to keep the different operating system in two separate hard drives.  

Is there a way to have two psychical hard drives with different operating systems and load ubuntu first, and then not need to shutdown to boot the other operating system?

thank you.

---

### Post by Chronon on 2010-03-19
I don't know why it's necessary to have them on different hard drives.  Dual booting will require them to be on different partitions, though.  

I have XP in both a virtualbox and installed as a dual-boot on my desktop computer.  Virtualbox does save you from having to reboot to access another OS, but you don't have direct hardware access in many cases, so you won't get full functionality.  A dual-boot setup will definitely give you the best performance.  Running an OS inside of Vbox has the benefit of convenience but you will not get full performance out of it.

---

### Post by JKyleOKC on 2010-03-19
> **007casper said:**
> Is there a way to have two psychical hard drives with different operating systems and load ubuntu first, and then not need to shutdown to boot the other operating system?The short answer is "no." A longer version is that the operating system is like the driver of an automobile; booting the other system would be like changing drivers while in heavy traffic at 70 MPH, and would have equally catastrophic results.

What you can do, however, to achieve essentially what you're asking, is to install a virtualization program in one of the systems, create a virtual machine in that program, and then install and boot the other system in the virtual machine. To do this well you'll need a dual-core processor and at least 2 GB of RAM; however last October I picked up just such a machine at Office Depot for less than $325 including tax so it's not extremely costly.

You can run the virtualization program in either Windows or Ubuntu; programs for both are available at no cost except the download time. I'm running VirtualBox in Xubuntu 8.04.4, with WinXP in the VM. The WinXP is available instantly with a single mouse click, and I can even have an XP window and a Linux window up side by side on the desktop. With the dual-core processor and adequate RAM, XP runs faster on this setup than it does on my 5-year-old laptop where it's native!

If you're overly concerned about having both on the same drive, you could install a second drive and cause the virtual machine to be stored on it. However I've had no problem at all with interference, with all data on the single 250-GB drive in this system. The VM actually resides in a single set of files on the host system, which appear to the guest system to be a completely separate machine. Thus while my disk's native format is the Linux ext3 version, the VM's virtual disks are XP's standard NTFS format.

---

### Post by a.walker on 2010-03-19
> **007casper said:**
> What is the best way to have different operating systems?

I was reading about [unbuntu inside windows using virtualbox, or dual boot with windows]("http://psychocats.net/ubuntu/virtualbox").  I wondered how reliable it will be to have two operating system side by side on the same hard drive.  

Now, the problem xp & ubuntu problem [over here]("http://ubuntuforums.org/showthread.php?p=8995995#post8995995") wants me to keep the different operating system in two separate hard drives.  

Is there a way to have two psychical hard drives with different operating systems and load ubuntu first, and then not need to shutdown to boot the other operating system?

thank you.


One possible solution, which is the most expensive, is to have a second computer running and use a KVM switch to share one keyboard mouse and monitor. If you have a second mInitor you can use a program called synergy to share your keyboard and mouse between computers.

---

### Post by 007casper on 2010-03-19
the freeway analogy is interesting

my concern is that I am hesitant to load it on the same hard drive due these problems down below 
```

Looking at the image, it appears as though windows put the boot files on my data partition.

over at
[http://ubuntuforums.org/showthread.php?p=8995995#post8995995](http://ubuntuforums.org/showthread.php?p=8995995#post8995995)
```

thats why I thought about putting the win on another drive.  

I have a sata drive for the main drive and then will use this old ide harddrive for windows.  I was thinking of using ide-sata converter for the windows hard drive.

So, what do you guys recommend for virtualization and a simple install, how to guide.

Thank you.

---

### Post by 007casper on 2010-03-19
> One possible solution, which is the most expensive, is to have a second computer running and use a KVM switch to share one keyboard mouse and monitor. If you have a second mInitor you can use a program called synergy to share your keyboard and mouse between computers.

I thought about that first.  Then, I figured it could be done maybe through the same computer with separate hard drives.  Maybe it isnt necessary to have separate hard drives. Occasionally, I read a lot of issues people are having two OS on the same drive... so I figured having two separate hard drives is better way to go...

---

### Post by Mark Phelps on 2010-03-21
From personal experience, having done this for years now, having separate hard drives is the best way to go.

With each OS on its own drive, and with GRUB only on the Ubuntu drive, each drive is then bootable in its own right. This allows you to disconnect the other drive when doing boot loader repairs.

You also don't have to deal with partition corruption problems resulting from resizing OS partitions using the wrong tool.

---

### Post by 007casper on 2010-03-22
I agree with you @Mark Phelps 

I am not to crazy about windows.  I need to use it 'cause of set applications I use.  I really dont want to deal with 'wine.'  At the moment, I dont have the time to give it a shot anyhow.

If one OS gets buggy, I can wipe out clean without effecting the other OS since they are separate hard drives.  

There are issues with virtualbox using it of the same hard drive.  The OS are separate in their own partition, yet if the one OS gets buggy, and during reload it might not be a smooth ride.  And of course, there is a partition failure issue... etc

so, I got one hard drive already where I loaded ubuntu + kde.
I have extra drive where I was going to use for windows. 

However, I am not really sure how to go about it.  

Is there an application I am suppose to load? like virtualbox?

I guess I can tell bios to load unix hard drive first.  And when I need to use windows, restart computer, and go back to bios and pick windows hard drive.  Thats what I can think of... is there a better way to utilize this situation?  

My ideal world would be... on the boot, I get to choose kubuntu or windows.  If I dont make a selection under ten seconds, the system will load kubuntu (the hard drive with linux).  And if I need to use windows on the fly I can switch back by logging out of kubuntu and switch to windows (and the system will use the windows hard drive).  

Does that make sense?   Is that possible?

I will be using a third hard drive for main data.  

Please, advise thank you.

---

### Post by readycarpenter on 2010-03-22
> One possible solution, which is the most expensive, is to have a second computer running and use a KVM switch to share one keyboard mouse and monitor. If you have a second mInitor you can use a program called synergy to share your keyboard and mouse between computers.


this is what I do I have windows xp box for my htpc running Media Portal on my tv
while my main box runs ubuntu, I use a kvm & synergy, if ubuntu box is off i just hit the kvm switch to control my htpc,(I don't use the video on my kvm)
if ubuntu box is on, then I just have an extended desktop via synergy

so many choices, virtual box is great if you have a real fast pc

---

### Post by 007casper on 2010-03-23
Building another computer would be the simplest choice.  I was wondering if I could do it without having a second computer, and at the same keep the two OS separate from each other.

I got 64bit, 8gig ram, quad... so it can handle it.  I was looking at virtualbox, and it seems as one operation system is host of another.  So, one OS runs on top of the other.  I am not sure if you can separate the OS from each other.

I guess the most annoying way would be is that you have two separate hard drives.  And when you want to use win, you would shut down.  Hook up windows hard drive, and disconnect the linux hd.  Then, when you want to switch to linux, shutdown, plug the linux hd, disconnect win. :shock:


thats why I am looking for a better way to utilize the situation by having one computer, two OS drives separate from each other, and one more drive for data:D

Has anyone done this?

thank you so much

---

### Post by doorknob60 on 2010-03-23
> **007casper said:**
> 
I guess the most annoying way would be is that you have two separate hard drives.  And when you want to use win, you would shut down.  Hook up windows hard drive, and disconnect the linux hd.  Then, when you want to switch to linux, shutdown, plug the linux hd, disconnect win. :shock:




I can't think of **any** situation where that'd be neccesary, don't worry :P Grub can handle all you need, whether or not it's on a different HD,

---

### Post by sxmaxchine on 2010-03-23
long answer very short you can not run boot an OS without restarting your pc

---

### Post by JKyleOKC on 2010-03-23
> **007casper said:**
> There are issues with virtualbox using it of the same hard drive.  The OS are separate in their own partition, yet if the one OS gets buggy, and during reload it might not be a smooth ride.  And of course, there is a partition failure issue... etc.I don't think you have grasped how virtualization works. When you create a virtual machine (VM) in any of the virtualization programs, that VM doesn't know anything at all about the host system. In particular, its operating system is NOT installed on a separate partition; the whole VM is contained in a set of files, which do exist on the host system, but which are just data files there.

The details differ from one virtualization program to another, so I'll use VirtualBox as the specific example here: when you install it on your system, it creates a hidden directory named ".VirtualBox" in your home directory. Inside that directory are two subdirectories, one for virtual machines and the other for virtual hard disks. When you create a new VM, the VBox program writes a data file into the virtual machine directory, and also creates another data file in the hard disks directory but you can specify that it be placed anywhere else that the host system can access. This second data file IS the VM's hard disk. However the data stored on it can only be accessed through the created VM itself and cannot interfere with the host system operation.

In practice, the VM behaves as if it were a totally separate box and the only connections to the host system are through the VBox program (which allows you to share directories between the host and guest, and which routes network traffic between the two).

What you will see if you go this route is that the host system will have less RAM available to it when the guest is running, since the two must share it. Also, as your VM's "disk" file grows in size, you'll have less space available on the host's file system. However other interaction between the systems won't happen. The most visible effect will be that everything slows down if your CPU is single core and you have less than 2 GB of RAM; this happens because both the host and guest systems will be forced to swap memory out much more frequently. Getting good performance from VMs almost requires at least dual-core CPU and 2 GB of RAM, so that each system has all the resources it needs -- but some of the advantages include the ability to switch between systems with a single mouse click, and the ability to back up the guest systems quite easily by making snapshots of them. You can also move the entire VM to another physical machine by simply copying the hidden .VirtualBox directory over, if need be; no re-installation of the guest will be required!

As others have noted, switching between conventional operating systems requires that you reboot. No fiddling with hardware is necessary, since GRUB can take care of it all for you -- but the forums are full of messages telling of troubles with dual boot installations. I've tried both ways, and most of my machines still have dual-boot installations -- but I use VMs in practice because they are much simpler to work with. Your mileage may vary...

---

### Post by Calash on 2010-03-23
Just to expland a bit on how Virtualbox, and other Virtualization applications, work.

My work setup is running Ubuntu on the host system, with two Virtual machines at the same time.  One is a development VM for patch deployment and the other is for Outlook and work communication.  Both of these, as noted above, exist as a set of files on the host operating system.  Both run at the same time as independent systems, borrowing resources from the main computer.

In use they are each contained in a separate window.  This system runs 2, but I have done many more on different hardware.  They have no contact with each other or with the host OS outside of networking (shared drives and such).

For maintaining specific applications while in Ubuntu Virtualizing is the best choice.  If you are going to be doing more, such as gaming or high level CAD I would reccomend the dual boot path.

---

### Post by 007casper on 2010-03-23
on kde software management I put virtualbox... I got... 
```

virtualbox-ose-qt-3.0.8-dfsg-1ubuntu1 (amd64)
x86 virtualization solution - Qt based user interface

virtualbox-ose-guest-source-3.0.8-dfsg-1ubuntu1 (all)
x86 virtualization solution - guest addition module source

virtualbox-ose-3.0.8-dfsg-1ubuntu1 (amd64)
x86 virtualization solution - base binaries

virtualbox-ose-guest-utils-3.0.8-dfsg-1ubuntu1 (amd64)
x86 virtualization solution - non-X11 guest utilities

virtualbox-ose-guest-x11-3.0.8-dfsg-1ubuntu1 (amd64)
x86 virtualization solution - non-X11 guest utilities

virtualbox-ose-source-3.0.8-dfsg-1ubuntu1 (all)
x86 virtualization solution - kernel module source

virtualbox-guest-additions-3.0.8-1 (all)
guest additions iso image for virtualbox

virtualbox-ose-dbg-3.0.8-dfsg-1ubuntu1 (amd64)
x86 virtualization solution - debugging symbols
```

I got 64bit computer... so, I am planning to load 
virtualbox-ose-3.0.8-dfsg-1ubuntu1(amd64)
x86 virtualization solution - base binaries

is that the right one?  I am going to have ubuntu as host.

---

### Post by JKyleOKC on 2010-03-23
Go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and get the one listed for your version of Ubuntu; click on the AMD64 link on that line. The OSE version in the repositories does not support any USB stuff; the one from the vbox site does, and is still free of any cost for personal use (even in a one-man business). The current version is 3.1.4, which is several releases later than those in your list. The "Ubuntu" versions work with all flavors of *buntu. I use Xubuntu here.

That page also tells you how to add their site to your list of repositories, so that you get automatic notification of updates. It's well worth doing!

---

### Post by 007casper on 2010-03-24
Thank you JKyleOKC.  

I installed virtual box.  

I was playing around with it.  It is giving me an option to create another hard disk or to use existing hard disk.  I will install another hard drive and see how it goes.

It will be awesome if I can use linux on one drive, and win on the other.  I am planing on using ide hard drive for win with a sata adapter. Kubuntu and data will be on sata on their own hd.

It could be nice to have two OS on the same hard drive.  However, too many horror stories on the forums.  Either, they arent experienced in proper installation or windows is a hit or miss on virtual machine.  Also, I will have firewall for win, so the other hesitation comes from dealing with malware, and registry issues on the win.  This way if win gets buggy, I can careless take out the drive and deal with it at anytime I want, and still continue to rock on with linux.

In the mean time, I read through the manual for the virtual box.  I will really appreciate it if the community can give me pointers on the best way to tackle this project in order to have a smooth ride.  Thank you all once again.

---

### Post by -grubby on 2010-03-24
> **007casper said:**
> 
I installed virtual box.  

I was playing around with it.  It is giving me an option to create another hard disk or to use existing hard disk.  I will install another hard drive and see how it goes.


You sound confused about this. VirtualBox doesn't want you to install a physical hard drive, it's going to create the "set of files" for the virtual machine, which will be on whatever hard drive the host operating system is on.

---

### Post by JKyleOKC on 2010-03-24
Actually it's possible to create the VDI file (the virtual hard drive) on another physical drive if you're running low on space, but it's a little more complicated than one might think at first. For the initial attempts, using the defaults will be the simplest way to go.

In the VBox setup dialogs, it's easy to get confused; they refer to "existing" and "new" drives, but they are talking about VIRTUAL drives (VDI files) rather than PHYSICAL ones. First time out, choose "new" from this option. That will bring up a dialog where you specify the drive's size and a few other characteristics. For the first time out I usually set the size to 20 GB. Another choice is whether to make the file full size from the start or let it grow as necessary. I set it to grow as necessary; it then won't go over the 20 GB I set but won't take up that space until it needs to do so.

The "existing" on this choice lets you use an already existing virtual disk on another machine. It came in handy for me a couple of weeks ago when I goofed up while in a WinXP VM and it quit listening to the mouse and keyboard. I eventually got control back to Xubuntu and killed the VM's running process, but it would not start again. I then created a new VM, told it to use the existing virtual disk of the old one, and it came right up. This let me kill the runaway process in XP and do a normal shutdown, after which the original VM worked again. I could never have done this with a physical installation of XP; I would have to have re-installed it and thus lost all the data it contains!

The manual can be quite intimidating; it was written for enterprise-level system administrators and goes into great detail -- but you won't need to use most of that information. There's a group of forums at [http://forums.virtualbox.org/](http://forums.virtualbox.org/) which can be quite helpful, too, although I've not found them quite so helpful as the forums here...

---

