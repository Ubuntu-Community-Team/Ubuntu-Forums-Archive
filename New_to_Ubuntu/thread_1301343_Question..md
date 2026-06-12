---
title: "Question."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Ion Lowell on 2009-10-25
When i install ubuntu, will i have to reinstall my Motherboard drivers, or will it keep them?

---

### Post by snkiz on 2009-10-25
In linux most hardhare is supported in the kernel. Only propritiy drivers like nvidia need to be installed.

---

### Post by Ion Lowell on 2009-10-25
Ok, thanks.

Because when i reinstalled Win98 i had to put the driver for my network adapter on two floppy disks then install it from there.
So VIA stuff will be fine?

---

### Post by themusicalduck on 2009-10-25
In theory it should all be fine, but a good way to test hardware is to boot with an Ubuntu CD and then select the first option on the menu, to try Ubuntu without any changes to your computer. This'll run Ubuntu off the CD, and although it'll be a little slow, you can test everything from there.

Then again if you're computer is quite old, it'll probably need a minimum of 512MB of ram for it to load off the CD.

---

### Post by fancypiper on 2009-10-26
I have found Linux to have better hardware support (I build my own desktop computers) than Microsoft products. Try the live disk without installing and see how it works first.

[Ubuntu Hardware Support]("https://wiki.ubuntu.com/HardwareSupport/")

---

### Post by martrn on 2009-10-26
> **Ion Lowell said:**
> When i install ubuntu, will i have to reinstall my Motherboard drivers, or will it keep them?.

The Ubuntu has a linux kernel which is a Monolithic kernel. (all bolted together and unloadable).  Other operating systems may have a different type of kernel such as a micro kernel or a hybrid kernel (unloadable and re-loadable), depending on which OS you have a present, (you do not state).

Motherboard drivers are generally talked about when running microkernels or hybrid kernels.  The motherboard drivers in a micro-kernel would be diffrent type of driver because it would be run in user space, as a seperate process, where in a hyprid kernel it would separate protected process but run in kernel mode to optimise on speed.  So if they were written for a diffrent operating system they wouldn't be of any use.

The device drivers in linux are a part of the linux kernel (because its a monolithic kernel), and are and are generally written as a part of the kernel.  The linux kernel can also load, kernel modules which will form part of your kernel when loading, but usually this only applies to graphics cards and sound cards.

Most often your motherboard device drivers will be already written and contained within-side the linux kernel.

---

### Post by Ion Lowell on 2009-10-26
The Mobo is a MSI 7061 KM400
Processor is an AMD Sempron 2600+
System information says i only have 192mb ram, it also says i only have 31gb HD space, But the information on the case of the HD says 80gb , and the BIOS recognizes 80gb
Think when i install Ubuntu it'll fix that error?
And i read something about Wine being only for Intel X86 processors, would it work on my AMD?

---

### Post by fancypiper on 2009-10-26
> **themusicalduck said:**
> Then again if you're computer is quite old, it'll probably need a minimum of 512MB of ram for it to load off the CD.
I have an old 1 mhz emachines box with 256 MB memory running Ubuntu 9.10.

It would run off the CD (but slowly).

---

### Post by themusicalduck on 2009-10-26
> **fancypiper said:**
> I have an old 1 mhz emachines box with 256 MB memory running Ubuntu 9.10.

It would run off the CD (but slowly).

I tried loading 9.04 off the CD on a laptop with 256MB ram once and it couldn't even get past loading the background image. In fact loading Xubuntu was really slow too and I settled for LXDE in the end. Maybe it was a driver problem on that particular laptop or something..

---

### Post by martrn on 2009-10-26
> **Ion Lowell said:**
> The Mobo is a MSI 7061 KM400 Processor is an AMD Sempron 2600+ System information says i only have 192mb ram, it also says i only have 31gb HD space, But the information on the case of the HD says 80gb , and the BIOS recognizes 80gb Think when i install Ubuntu it'll fix that error? And i read something about Wine being only for Intel X86 processors, would it work on my AMD?

Yes ubuntu will work with the via KM400A chipset, regardless of weather its msi or otherwise, ubuntu (and all the software) will work with all processors above the pentiumII or the K6-III's so will work well with AMD Sempron.   192MB of ram is not much, the linux kernel is massive, best to have 256MB or more for gnome, xubuntu might be better if you intend to do too much with it, although you might get away with 192MB.   You have enought disk space, and if your motherboard regognises 80GB of hard dirve then ubuntu linux will recognise whatever the BIOS will.  Ignore what windoze says about your Hard drive space, as it doesn't calculate it properly anyway.  Wine will run happily on AMD processors, as it will on intel, although intel processors will have better frames per second, if you are playing games or the like.  You will only need wine for games, and there are GB's of application written for ubuntu in the repository's to do everything you need on your computer.

---

### Post by Ion Lowell on 2009-10-26
Well I found out that the ram is low because 64mb of it is dedicated to video memory.
I was only going to use Wine for maybe 3-4 games, MS Hellbender, Age of Empires 2,Starcraft, and maybe WoW, but i doubt i'll install wow on this machine.
Btw, it's not KM400A, it's KM400
I doubt that will make a difference, but i'm very new to Ubuntu.

---

### Post by martrn on 2009-10-26
> **Ion Lowell said:**
> Well I found out that the ram is low because 64mb of it is dedicated to video memory. I was only going to use Wine for maybe 3-4 games, MS Hellbender, Age of Empires 2,Starcraft, and maybe WoW, but i doubt i'll install wow on this machine. Btw, it's not KM400A, it's KM400 I doubt that will make a difference, but i'm very new to Ubuntu.

[http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html]("http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html"). (3D)
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome") (2D).
It might take you quiet a bit to get your graphics card set up properly.

192MB is not brillent but ok for ubuntu.

Check the wine compatability database for compatability for your games.
[http://appdb.winehq.org/]("http://appdb.winehq.org/").  Wow should run fine as it would in windowze.

Ubuntu works fine with your chipset VIA KM400 -(et.al..)  chipset!
You should try a distribution of linux such as ubuntu !!

---

### Post by anewguy on 2009-10-26
I would follow the advice for a lighter Linux, perhaps even puppy linux or damn small linux.

As far as drivers for your motherboard and your disk drive size, there are a couple of things to know:

- usually when one talks about motherboard drivers, one is talking about the special things needed for a given chipset.  In your case, you mention your network adapter - this is considered a device, and as such uses what is more commonly referred to as a device driver.  So, for your network adapter, chances are it will be supported right out of the box with Ubuntu.  There are exceptions, some being some PCMCIA, USB and in particular wireless and video adapters.  However, there is a large support base, as you will find through this forum, of drivers available even if they aren't included "in the box" with Ubuntu.  Chances are things will work fine, except your video may be a bit of a challenge to get set up - you may want to research it first.  As far as your disk drive size goes, Windows is only reporting 31gig because you are using Windows 98, and that was the max size it could "see".  You will be fine in Ubuntu, and the entire space of your disk drive will be available (assuming you delete Windows first!).

Welcome aboard - hope you enjoy the ride!

Dave :)

---

### Post by misfitpierce on 2009-10-26
As said on Ubuntu/Linux almost all hardware is built into it via the kernel which is always updated each release to support newer and newer hardware. Another reason I love Ubuntu/*Nix

---

