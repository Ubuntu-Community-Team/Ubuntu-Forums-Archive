---
title: "Should I even try???"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by littletime on 2011-07-03
I have a custom desktop and am considering installing ubuntu linux.  I tried a mepis installation and never was able to get the video drivers to work.  A friend told me ubuntu was more common and I would have better luck with finding drivers here.  I admit I am to blame for my hardware setup as I built this bugger myself.

I am running an Asus M4A88TD-V EVO (usb 3.0) motherboard.  I don't think RAM drivers should be an issue but in case they are crucial ballistix.  The video cards are two Nvidia GeForce 9600GTs linked via SLI.  Two or three physical hard drives depending on what I am doing, total space about 3TB.

I wanted to either do a dual boot with ubuntu and Windows 7 until I can see if I can get everything crossed over or run win 7 as a virtual machine.  Any input would be appreciated.  Am I crazy???  Is this possible?

---

### Post by littletime on 2011-07-03
O and the processor is an AMD Phenom II X6

---

### Post by jramshu on 2011-07-03
Try running it as a live cd first to see if it works.

---

### Post by littletime on 2011-07-03
OK.  Will try.  I am running three monitors do you know if that can even be supported???

---

### Post by jramshu on 2011-07-03
Nvidia does provide drivers and it is possible that everything will work. You could always just cut out 20 or 30 gigs to set up Ubuntu on. That way you can test it. I have a friend that has a similar machine and he says everything works fine, not sure if he has three monitors though.

---

### Post by littletime on 2011-07-03
Cool.  I am downloading it right now.  I have 8GB of RAM, do I need to go 64bit to support that?  I know I had to do that with windows.

---

### Post by alphacrucis2 on 2011-07-03
> **littletime said:**
> OK.  Will try.  I am running three monitors do you know if that can even be supported???


You will probably have to install the proprietary nvidia driver to get multiple monitors working properly. I'm not sure if you can install the proprietary driver via the live CD as the proprietary driver installation may require a reboot, which will lose the driver ( I vaguely recall that there is some way of getting around having to reboot but I don't know how myself).

---

### Post by dFlyer on 2011-07-03
> **littletime said:**
> Cool.  I am downloading it right now.  I have 8GB of RAM, do I need to go 64bit to support that?  I know I had to do that with windows.

If you install the pae kernel it will support your RAM with a 32bit system.

---

### Post by jramshu on 2011-07-03
Yes, if you want full use of your memory, 32 bit only reads out to 4gigs of ram.

EDIT: Forgot about the pae kernel.

---

### Post by littletime on 2011-07-03
I have backed up all of my info on one of my hard drives.  The other is a 1TB that only has a windows install on it.  I can use a partition to try this.  I am not sure which way to go with grub, but I saw an option to install alongside and downloaded the installer.  So I was hoping to go that way at first.  If I can get it working I would eventually like windows to be a VM.  

My only fear is that I will do this and lose access to the windows install altogether if it fails.

---

### Post by littletime on 2011-07-03
pae kernel?  What is that and how do I use it?

---

### Post by littletime on 2011-07-03
Also should I remove one of the video cards during the initial install, then put it back when I get the system stable?

---

### Post by dFlyer on 2011-07-03
Why not clone your windows install first. This is much easier to restore a clone than spend several days reinstalling windows. Below is a link to a free windows cloning software. I use this to clone my daughter Windows OS.

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by alphacrucis2 on 2011-07-03
> **littletime said:**
> pae kernel?  What is that and how do I use it?

If you have downloaded the 64 bit version then it isn't relevant. PAE only applies if you install the 32 bit version. 

This wiki article explains.

[http://en.wikipedia.org/wiki/Physical_Address_Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

It is a method where a 32bit OS can address more than 4GB of RAM. It does incur a small performamce hit hit IIRC. In any case 64bit is the way to go.

---

### Post by littletime on 2011-07-03
Not sure it is worth doing at this point.  The install is buggy anyway.  That is part of why I am doing this now.  If I lose it I still have the laptop to use.  I think I just want to proceed.  I will keep the link though.  May come in handy for later use.  If I can ever get it NOT to be buggy.  I don't think Win 7 likes my setup.

---

### Post by littletime on 2011-07-03
On the 32 bit VS 64 bit.  Why do they usually recommend 32 bit?  I see it with windows even.  I downloaded both (or more accurately am downloading both).  Still got a while on the download and want to find out as much as I can before I actually do this.

---

### Post by dFlyer on 2011-07-03
I would say a few years back 32bit was better supported with software. Today I would say 64bit software support is just as good including flash support. The choice is yours. If you do install the 64bit OS, you still can use 32bit programs by install the 32bit libs.

---

### Post by alphacrucis2 on 2011-07-03
> **littletime said:**
> On the 32 bit VS 64 bit.  Why do they usually recommend 32 bit?  I see it with windows even.  I downloaded both (or more accurately am downloading both).  Still got a while on the download and want to find out as much as I can before I actually do this.

I think it is because they are worried that someone with a 32bit cpu will try and download the 64bit version and wonder why it wont install. There were problems in the past with some stuff (particularly adobe flash) not supporting 64bit but there isn't really any reason these days. Especially if you want to do video transcoding you will notice the performance boost with 64bit.

---

### Post by littletime on 2011-07-03
Sweet.  I think I am going to go with 64 bit.  So do you think I should remove a video card to start with?  I know that when I do a windows 7 install I have to do that or the computer goes bonkers.  I kind of wish I was not addicted to all the landscape it gives me.  It is a pain from a software standpoint.

---

### Post by alphacrucis2 on 2011-07-03
> **littletime said:**
> Sweet.  I think I am going to go with 64 bit.  So do you think I should remove a video card to start with?  I know that when I do a windows 7 install I have to do that or the computer goes bonkers.  I kind of wish I was not addicted to all the landscape it gives me.  It is a pain from a software standpoint.


The Live CD has an option to try before install. Give that a go. If it doesn't barf on the dual video cards then you should be ok to go ahead and install. Once the OS is installed you can then install the Nvidia properietary driver.

---

### Post by littletime on 2011-07-03
Hmmmm.... no spewing on my video cards.  So if it fails to go on live first thing would be take one card out and try again.  If it fails with one, then its the video drivers needing to be installed?  And if so what should I do in that case.  FYI still at least 15 min on the download before I can try anything.  Been perusing some of the other posts trying to get an idea what I am in for.

---

### Post by rosencrantz on 2011-07-03
You might need the nvidia drivers to get SLI to work (I don't know how well the open source nouveau drivers are up to this), which aren't on the LiveCD. How about installing to an empty flash drive (4-8 GB should be plenty) that you have set as the primary boot device? That way you can try stuff on the driver issue before you do anything drastic.

---

### Post by littletime on 2011-07-04
Got a drive I can do that with.  Will disconnect my data drive before launching this for fear of somehow screwing up and wiping out years of work.

---

### Post by alphacrucis2 on 2011-07-04
> **littletime said:**
> Hmmmm.... no spewing on my video cards.  So if it fails to go on live first thing would be take one card out and try again.  If it fails with one, then its the video drivers needing to be installed?  And if so what should I do in that case.  FYI still at least 15 min on the download before I can try anything.  Been perusing some of the other posts trying to get an idea what I am in for.

If the worst comes to the worst you should be able to boot into recovery mode by selecting that from the grub boot menu. If the boot menu isn't displaying you should be able to force it by holding down the SHIFT key on boot.

---

### Post by littletime on 2011-07-04
Burning to optical now.  Will start the laptop up in a few and log in from that terminal.  Wish me luck.

---

### Post by littletime on 2011-07-04
OK.  I am actually on the live CD now.  Little issues here.  Won't recognize secondary screens but no surprise there.  I think I am going to try the actual install with the card in.  Aiming at a flash drive first.

---

### Post by littletime on 2011-07-04
Wont let me install on the flash drive.  I can seem to define it as the root drive.  O well installing next to windows on the hard drive.  So far so good.  The reboot will be the real test.

---

### Post by wildmanne39 on 2011-07-04
> **littletime said:**
> OK.  I am actually on the live CD now.  Little issues here.  Won't recognize secondary screens but no surprise there.  I think I am going to try the actual install with the card in.  Aiming at a flash drive first.Hi, there has been a problem with nvidia using more  then one video card but there is a fix for it , I do not have it in front of me, but it is on the forum, and you should install the video driver from additional drivers. If you run into problems, start a new thread with a title that shows the problem, also mark this thread solved when you start a new one.

---

### Post by littletime on 2011-07-04
OK.  Will do.  Have to get past a problem before getting to that though.  I initially tried installing to flash by selecting "something else"on the menu screen.  I told the install to put the bootloader on my flashdrive, and was attempting to install ubuntu on the flashdrive altogether.  When that failed I backed up and chose instal next to windows and left the flashdrive plugged in.  Well... it put the bootloader on the flashdrive.  even if I boot from the flashdrive it won't boot up.  I get an error message saying that I do not have the required equipment to run it and should run in a mode which it specified and I now can not recall.  Should I try just reinstalling it without the flash drive in?

---

### Post by wildmanne39 on 2011-07-04
> **littletime said:**
> OK.  Will do.  Have to get past a problem before getting to that though.  I initially tried installing to flash by selecting "something else"on the menu screen.  I told the install to put the bootloader on my flashdrive, and was attempting to install ubuntu on the flashdrive altogether.  When that failed I backed up and chose instal next to windows and left the flashdrive plugged in.  Well... it put the bootloader on the flashdrive.  even if I boot from the flashdrive it won't boot up.  I get an error message saying that I do not have the required equipment to run it and should run in a mode which it specified and I now can not recall.  Should I try just reinstalling it without the flash drive in?Hi, you should be able to log in to classic mode, that is just saying that because you do not have your video card driver installed yet, but I would still fix the boot grub problem, I would go ahead and install ububtu to the hard disk including the grub boot loader, the way it is now is a mess. You can also put ubuntu on a drive by itself if you want to, you just have to choose manual partition it is called something else in ubuntu 11.04

---

### Post by cariboo on 2011-07-04
For you it would be easier to install without the flash drive plugged in. If you had any experience at all, I'd suggest using the Live CD to install grub2 in a chrooted environment.

---

### Post by littletime on 2011-07-04
OK.  I got it installed (all on the hard drive now - though not sure what partition I am on).  At startup there was not a menu asking me if I wanted to go to windows so I suspect my windows install may have gone bye bye.   NBD.  Anyway it came up with the same error as it did last time saying I did not have the required equipment so I kept hitting ctrl  and the alt button (along with a few attempts at esc) and it worked.  I am assuming I need the video drivers, so I will try that next.  I chose install next to windows (11.04 version).  It should give me a boot menu next time, right???

---

### Post by littletime on 2011-07-04
I am crashing out for the night.  I tried downloading the drivers but when I double click on them gedit says it can't find them.  I am hoping my computer starts back up in the morning.  Will see.  Thanks for all the help so far!  

Shy

---

### Post by wildmanne39 on 2011-07-04
> **littletime said:**
> I am crashing out for the night.  I tried downloading the drivers but when I double click on them gedit says it can't find them.  I am hoping my computer starts back up in the morning.  Will see.  Thanks for all the help so far!  

ShyHi, to get the driver for your video card hit alt+f2 and in the window that opens type additional drivers and it will show you the icon click on it and install the one that is there for your card, you will need to be connected to the internet, and leave gedit alone you could mess up bad with it on your first time booting ubuntu. Hopefully your windows will be listed in the boot screen when you reboot, if not we can get more information from you to help you fix it,but again please start a new thread with a good title so you can get the help for that particular problem.

---

### Post by Fougner on 2011-07-04
If you download a binary driver you're supposed to execute it, not open with Gedit (texteditor).

---

### Post by jrev on 2011-07-04
If you have a prepared partition to install Ubuntu everything will go fine. 
We can always take care of grub if anything fails ...

---

### Post by littletime on 2011-07-04
It gave the option this time.  I guess I will close this thread and open one about the video drivers.  :popcorn:

---

### Post by littletime on 2011-07-04
I hope this is how you mark it solved.

---

