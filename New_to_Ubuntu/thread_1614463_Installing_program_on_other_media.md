---
title: "Installing program on other media"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by CapnChkn on 2010-11-05
I've been trying to find out how to get a program installed and run from another drive.  I suppose there's a simple explanation because I've looked for years and never found an understandable answer.

In Windows, for example, if I want to install a program to another section of the hard drive or another hard drive, I just point the installer to install there.  I can't see or find anything similar in Ubuntu.

Storage isn't a problem, it's the size of the drive the installer insists on installing to.  Everything I've installed from synaptic also goes to the same place, and I just don't have the room on that one little ssd to put everything.

---

### Post by cariboo on 2010-11-05
All Ubuntu packages are hard coded as to where they're going to be installed. If you open a package with file-roller (the file archiver) you will see where the different parts of the package go.

It is pretty hard to install a package anywhere but where is set in the install script. The only way I can see is to make the package from source and then install it where you want, and even then you are going to run into problems. Linux is no different from Windows in that respect, the main parts of the program are install in c:\Program Files, but there other bits spread through the c:\windows directory.

---

### Post by CapnChkn on 2010-11-05
So what you are saying is, _you don't know._

Yes, I know Windows will put the registry entries in the Registry, pointing to various other files that go to directories and other subdirectories including system files.

From what you are saying here, it suggests whenever I need to add space I am going to have to upgrade my hardware.  This suggests any system that is sold as "optimized for Linux," as my little netbook was, that the system would have to be sold with a super large hard drive.

Because this system is integrated and proprietary, you are telling me the only option I have here is to get rid of my computer and buy a better one.  This doesn't explain all the individuals in these forums that take old systems and install Ubuntu on them.

---

### Post by beew on 2010-11-05
> This suggests any system that is sold as "optimized for Linux," as my little netbook was, that the system would have to be sold with a super large hard drive.

If that is of any help Linux can run off an external drive. You can install the whole system in a drive big enough for you and then use it by plugging it into your computer, or any computer for that matter unless the computer requires say, a proprietary graphic card (it still runs, but you cannot use it on a different computer unless you have removed the proprietary drivers first, but since you are not looking for portability this should not be an issue). So No, you don't need to buy a new computer if size is the only issue.

How big is your hard drive? 

For exactly the reason that all programs are installed in the /root partition(except for third party apps which are installed in /home) I have a relatively big root partition, when most people suggest a tiny /root partition and a big /home partition to store data (I don't care about personal data as I can easily move them, not so for installed programs) Now I have about 20 G for /root it is quite big and with all kind of crap installed i am only using maybe 6-7 G for the OS and all the programs combined. It doesn't look like I would use all the 20G.

So, I don't know how to solve your problem but it just surprises me that you would run out of space. It is a lot easier for that to happen in Windows but it would be hard in Linux because it is so small to begin with.

P.S. I have a minimalist installation on a 4G external drive, have Skype, open office, CD ripper, music player, video player, CD burner, the Gimp, PDF editing tools and reader, animation making studio and statistical software (and more). It is a demo but more complete than many Windows desktop installations. So I don't think you need a "super large hard drive". A 30G hd is way more than enough if you store data somewhere else.

---

### Post by CapnChkn on 2010-11-05
Thank you!  I was just remarking that the logic cariboo907 is using dictates a ridiculous hardware requirement.

I am running Ubuntu on an old Asus 701 (4g surf.)  I have tried all the stripped down distros, and only regular Ubuntu seems to fit what I need.  The little SSD is 4 gigabytes, with 3 USB slots, and a card reader which I have an 4 gig SDHC plugged.  For around 2 years now I've been using the SDHC for placing user generated files.

I don't see the problem here, I have been placing programs, and running them, in whatever place in the directory tree using Microsoft since the old DOS days.  If I needed to move the program to make space, I would use a re-mapping utility.  If I installed a program, the installer will give me an option to install someplace other than the default.

Does Linux really have this crippling restriction?

I _am_ interested in portability.  It's a Netbook.  An external Hard Drive would only allow me to carry a lot of "personal data."  As for the SSD, I have Gimp, Quanta plus, Open Office, and small tools installed.  I invariably end up trying to remove stuff I am not going to use, like the bluetooth, crashing the system, and having to re-install to get back to where I was.

---

### Post by beew on 2010-11-06
> **CapnChkn said:**
> 

Does Linux really have this crippling restriction?  

What restriction? you can install the whole OS and programs in an external hd or even a USB thumb drive and plug it into any PC and have an instant running Linux system. Windows doesn't even come close.

> I _am_ interested in portability.  It's a Netbook.  An external Hard Drive would only allow me to carry a lot of "personal data." No, my whole point is you can install all the programs in an external drive and run from there if you also install the OS. Then the whole system is portable (except for the graphic driver thing )in that you can run it off computers of completely different specs.

 I have an installation like that on a 40G external drive, my own labtop has only 1G of ram, but when I plug this into the desktop at work suddenly I get 4 G,  so for example I can run virtualbox and watch hd videos when plugged into a more powerful PC while I can plug it into my own laptop for less demanding stuffs (which I don't because I already have another copy of Ubuntu installed internally, but I can if I want to) Can Windows do that?

---

### Post by CapnChkn on 2010-11-06
It's a restriction if you must have the OS installed on the storage media.  If I have to have sda1, the OS, and programs installed it's not portable.  If I need to run an application on another computer by plugging in my External media, rebooting that persons computer and doing my work, only to have to reboot to open their copy of Ubuntu, it's a restriction.

I have portable Windows programs on my flash drives that are usually installed to the hard drive to work.  I can run those programs from any computer that runs WinXP, and some that will run in Win9x.  I _do not_ have to reboot the other computer to get these programs to work.  Having to carry an Operating System along with the needed tools is a restriction.

My point is, using windows, I can install a program on any drive, removable media, or shared folder on a network and still have some functionality.  I can use standalone versions of these programs on any computer running a compatible operating system from removable media, and not have to reboot to an operating system installed on the media to access it.  I have been able to do this since the early 90's when I started with computers, and the computers I was fooling with were built 15 years prior to that.  I could install and run programs from removable disks then.

What you are suggesting is the only way to use programs that are reliant on an operating system that's been in action in one form or another for 12 years longer than Microsoft has been on the market, is to have those programs installed on that storage device along with the parent OS.

Using Wine, I regularly run portable versions of Microsoft based programs in my Ubuntu system(s).  I then can remove that media, plug it into my Windows system(s) and run them there as well.  THAT is portable.  THAT is unrestricted.
[CENTER][IMG]http://www.webweaver.nu/clipart/img/web/bars/newrule.gif[/IMG][/CENTER]
All this is digression.  I am not arguing the merits of portability, I'm talking about installing a program on a different partition, disk, or removable media connected to the computer with Ubuntu installed.  This perceived restriction is that I am incapable of installing and running this software from any drive but the one with the operating system installed on it.

---

### Post by beew on 2010-11-06
What you consider a 'restriction' many Linux user consider a strength, namely the way how softwares are seamlessly integrated into the OS through a centralized program manager. As a result Linux is very lean and efficient.

> Using Wine, I regularly run portable versions of Microsoft based  programs in my Ubuntu system(s).  I then can remove that media, plug it  into my Windows system(s) and run them there as well.  THAT is portable.   THAT is unrestricted.I just have to disagree. Windows itself is very  restricted. You have to pay for every copy you install and it is definitely not portable. You started off complaining that you ran out of disk space because of the programs you installed, I think that would probably be more common in Windows because it is so bloated, but it is not a usual thing to happen in Linux, a several year old cheap netbook typically would have more hd space than 35G and I am running my Lucid comfortably on a laptop with a 35G hdd (and I use only half of it)  So your problem is rather unique from what I know.


As for WINE, it is not a windows technology, it is Linux that makes it possible for you to run your windows based apps in a cross platform way. Now why don't you complain about Windows being restricted  because MS haven't got the technology to run native Linux apps on Windows? Why don't you complain about proprietary softwares that run only on MS Windows? That is restriction.

---

### Post by HermanAB on 2010-11-06
Howdy,

You can install any program anywhere you want.

There are various ways to do that:
Install it the usual way, then find it and move it.
Read the README and INSTALL files and compile from source and isntall where you want.
Mount the /usr or /usr/local or /usr/bin directory elsewhere.
etc...

---

### Post by CapnChkn on 2010-11-06
Thank you Herman.

I don't know how the conversation went from installing progams to other places on the system to, "How great is Ubuntu!"  I never said the OS was junk, I was pointing out that if the OS is 25% older than MS, then it should have the same or more functionality.

I did find a post stating (From you actually!  5 years ago!), "In UNIX you have a single directory tree and drives are simply grafted onto the tree wherever some space is needed."

So what this is stating is I can just move the directories where I have space to move it?

---

### Post by Pbethe on 2010-11-06
> **CapnChkn said:**
> Thank you Herman.

I don't know how the conversation went from installing progams to other places on the system to, "How great is Ubuntu!"  I never said the OS was junk, I was pointing out that if the OS is 25% older than MS, then it should have the same or more functionality.

I did find a post stating (From you actually!  5 years ago!), "In UNIX you have a single directory tree and drives are simply grafted onto the tree wherever some space is needed."

So what this is stating is I can just move the directories where I have space to move it? 

I find it most helpful to think of it as moving the space to any directory that needs it.  Physically, you plug a usb drive into a port.  Using the mount command, you plug it anywhere you want, almost, in your directory tree.  You can mount a drive (actually, the file system on the drive) to /home, for example.  When you do that, all of the files on that drive become visible in /home, and the files that were in /home become hidden.  Unmount the drive, and those files are unhidden.  

I still have trouble wrapping my brain around this concept.  Probably, you can do a better job than I of reading the man pages and figuring out how to do what you want.

It is a feature of Ubuntu that the **default** installation goes all in one partition, but it does have the flexibility to do otherwise.

---

### Post by CapnChkn on 2010-11-28
Well Hello!

Ok!  Herman and Pbethe, you two have gotten me somewhere now.  With the last post I had to do some kind of reading, and discovered the usage of the fstab file.

I did manage to mount /home on the 4gig SDHC card, and have been running from there for some time without actually gaining any space on the SSD.  It's crazy alright!  I lost all the configuration I had before, reset all the bits, and kind of forgot about it until I took the card out just now.

Opening Firefox took me back to this thread!  I see what you mean, I have to free up some space now to install the updates.  Still the disk utilities show I have 3.3 gigs free.

Can't really mark it "solved," because I'm still having space issues, maybe I can mark this thread "Progressed."

---

### Post by Pbethe on 2011-01-21
Keep on plugging away.  That's what I do.  

Cheers,
Paul

---

