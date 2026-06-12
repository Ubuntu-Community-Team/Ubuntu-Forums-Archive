---
title: "Ubuntu or xubuntu"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by bigtel on 2009-08-24
I have a low spec laptop which I would like to load the Ubuntu operating system onto. My question is, would it be better to load up the Xubuntu version?, as I read this is for older and slower running machines? If I do load up Xubuntu, then what will I be missing out on from the normal version of Ubuntu??

(My laptop spec is 1 GB Memory, 1.4GHz AMD processor 100GB Hard drive)

Thanks.

Bigtel

---

### Post by longtom on 2009-08-24
Xubuntu is not really that much lighter (if at all) than the normal Ubuntu.  It is just the desktop interface which is different and you won't be missing anything either way.

There are light distributions out there like puppy linux, AntiX, damn small linux, SliTaz.  Just google if you are looking for that.

Having said that, with your specs I reckon Ubuntu should just run fine.

Good luck and welcome!

---

### Post by Katalog on 2009-08-24
> **longtom said:**
> Xubuntu is not really that much lighter (if at all) than the normal Ubuntu.  It is just the desktop interface which is different and you won't be missing anything either way.

That is my understanding as well, although I have never used Xubuntu, that it is bogged down to the point now that it's almost no different than installing Ubuntu. And to echo longtom, welcome!

---

### Post by Perfect Storm on 2009-08-24
I think you should start with Ubuntu, and the specs you gave us it shouldn't be a problem. You can thereafter decide if you give xubuntu a go.

When you have Ubuntu up and running I suggest that you install an application called "bum" (you'll find it in add/remove), to enable/disable stuff you use. You might get it more smoothly that way.

---

### Post by DJonsson2008 on 2009-08-24
I find Xubuntu much snapier on on my lower speed drives 40 - 80 MB drives.

Bear in mind I simply load the Xfce4 desktop component
after installing Ubuntu.

sudo aptitude install xfce4

Then I log out and choose xfce4 session.

This way I've the lighter version of Xfce4 as well as Ubuntu
underneath. If I want to use an ubuntu component I simply search
for it with the Xfce4 appfinder. 

The preference of use for Xfce4 is as mentioned above though for many a matter of a preference for the elegance of xubuntu over ubuntu, on slower machines though a lighter install of xfce4 seems is faster from my experience on older gear.

---

### Post by DJonsson2008 on 2009-08-24
Per the above advice, I agree get your machine working first with
Ubuntu ie Lan/Audio/... then drop down to Xfce4 for snappier performance for daily use. One big reason is that there is more discussion of getting the Ubuntu interface going than that of Xfce4, Ubuntu is a more frequent point of reference in these discussions.

---

### Post by Bigtime_Scrub on 2009-08-24
You don't *need* Xubuntu or Xfce4 with those specs. I run Ubuntu just fine with 512 Mb of RAM no problems. If you think its a bit slow you always always add xfce or Xubuntu on later.

---

### Post by Ji Ruo on 2009-08-24
You will have no problems at all running Ubuntu with those specs. Starting with standard (GNOME) Ubuntu and then experimenting with XFCE if you want to is a good idea.

In my experience there is no difference between the performance of Ubuntu and Xubuntu on low-end hardware (lower than what you have), but choosing ext4 instead of ext3 for the filesystem does increase speed.

---

### Post by argos3016 on 2009-08-24
On this prestations , I'm  running ubuntu with compiz good and I not have problems

---

### Post by XubuRoxMySox on 2009-08-24
I had no problems using Ubuntu on a 512 RAM machine. I sped things up by installing and using the LXDE desktop environment (*much* lighter than Xfce, simple, pretty, graphical interface). LXDE is much more independent, meaning it doesn't pull in nearly so many dependencies and libraries and stuff. 

A minimal (command-line only) install of Ubuntu + LXDE absolutely flies at mind-bending speed on my old 256-RAM machine!

-Robin

---

### Post by SunnyRabbiera on 2009-08-24
1GB of ram will do fine with ubuntu, I run 1GB of ram myself without issue.
And your comp is far from low spec, it might be low spec with Vista but with ubuntu its fairly decent spec.

---

### Post by raydator on 2009-08-24
I agree with everyone saying you should be able to run Ubuntu fine with those specs.

Up until earlier this year I had been running a Pentium III 733MHz, 512MB RAM with 120GB Hard Drive, and it ran Xubuntu no problem.  I did try Ubuntu on it as well, and although it ran fine it was noticeably slower than Xubuntu.

---

### Post by bigtel on 2009-08-24
Thanks for all your replies.

Once I have installed Ubuntu, where do i go for the LXDE or Xfce programs?

---

### Post by blazemore on 2009-08-24
In my experience, XFCE is not that much lighter than Gnome, and is far less attractive, easy to use etc.
Plus, although Kubuntu/Xubuntu are official, the Gnome version is the "main" version, like it or not, and will always have the edge in terms of support.

---

### Post by Possum Films on 2009-08-24
In my experience, Xubuntu is just as fast as Ubuntu but it uses less RAM. Given that you have 1 GB of RAM you should have no trouble at all running _U_buntu. Xubuntu has slightly less features than Ubuntu so if your computer can run Ubuntu I'd recommend using it.

---

### Post by abhilash82 on 2009-08-24
> **bigtel said:**
> I have a low spec laptop which I would like to load the Ubuntu operating system onto. My question is, would it be better to load up the Xubuntu version?, as I read this is for older and slower running machines? If I do load up Xubuntu, then what will I be missing out on from the normal version of Ubuntu??

(My laptop spec is 1 GB Memory, 1.4GHz AMD processor 100GB Hard drive)

Thanks.

Bigtel

Go for Ubuntu, it should work fine.. it worked fine with my PC which had a lower configuration than yours. Even Compiz worked!!

---

### Post by Perfect Storm on 2009-08-24
> **bigtel said:**
> Thanks for all your replies.

Once I have installed Ubuntu, where do i go for the LXDE or Xfce programs?

I suggest that you get familiar with Ubuntu first and learn the basics about Ubuntu and Linux in general. It will make the transaction from Windows to Ubuntu/Linux more easier. It's two completely diffrent worlds.
Most guides you'll find on this forum and on the web is geared towards Ubuntu.


Just my opinion.

---

### Post by snowpine on 2009-08-24
> **bigtel said:**
> Thanks for all your replies.

Once I have installed Ubuntu, where do i go for the LXDE or Xfce programs?

LXDE, Xfce, and much, much more can all be installed from the gigantic "Ubuntu repository." This is a trusted and tested software source with several "front end" applications for finding and installing apps: Synaptic Package Manager, Add/Remove Applications, or the command line (apt-get or aptitude). 

For example, the following terminal commands will download and install LXDE:

```
sudo apt-get update
sudo apt-get install lxde
```

It's that easy!

---

### Post by cascade9 on 2009-08-24
> **Katalog said:**
> That is my understanding as well, although I have never used Xubuntu, that it is bogged down to the point now that it's almost no different than installing Ubuntu. And to echo longtom, welcome!

Well....sort of. Like other people have said, its not that much lighter than gnome. Pity that the ubuntu team packs it with gnome apps (file-roller not xarchive, etc)
 
bigtel- I wouldnt call that 'low spec'. Should be more than fine for ubuntu or xubuntu ;)
[U]


[/U]

---

### Post by bigtel on 2009-08-25
I have installed Xubuntu as I had gone to the trouble of dowloading it and burning the ISO to disk. I will give it a try and as long as it does what I need it to do it should be fine.

Is there a way to change it to the normal Ubuntu OS if I need to?

---

### Post by Ji Ruo on 2009-08-25
> **bigtel said:**
> I have installed Xubuntu as I had gone to the trouble of dowloading it and burning the ISO to disk. I will give it a try and as long as it does what I need it to do it should be fine.

Is there a way to change it to the normal Ubuntu OS if I need to?

Enter this in the terminal -```
sudo apt-get install ubuntu-desktop
```Then restart the computer, and at the login screen you can select the desktop you want to use by entering options.

---

### Post by bigtel on 2009-08-25
Thank you for your help.

---

### Post by Caraibes on 2009-08-25
It doesn't really matter which *buntu you have installed...

Now you shall apt-get install Fluxbox, PCManFM, Opera, Exaile etc...

It will run much faster with Fluxbox !!!

---

### Post by thegrey on 2009-08-27
Just wanted to share an experience with (X)Ubuntu, and this was the most relevant thread I found that I am allowed to post to (others are too old).

I have this (lspci) hardware:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
06:00.0 Ethernet controller: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

It's an old Toshiba Satellite Pro 4300 PIII 700mhz, 256gb ram, 30gig disk(newer than the rest).
Installed Xubuntu(9.04), and had a hard time doing anything, xfce4 using at least 30% cpu as soon as I used the kb or mouse, Firefox just lagged, load was between 2 and up to 6.
Didn't really do a lot to find out what the load really was, so just installed ubuntu-desktop (sudo apt-get install ubuntu-desktop), logged off, chose Gnome as session, and logged on again.
It's like getting a new machine. Everything is responsive, and load is something like 0.20, even with 5 firefox tabs and a few terminals and some stuff running.
Like night and day.
So... maybe xfce4 is more lightweight, but it sure didn't work with my hw.
I still have the Xubuntu menus and some other xfce4 processes running.
Considering installing a fresh ubuntu to see if there is a diff, but I guess it shouldn't be any difference.
Cheers!

---

