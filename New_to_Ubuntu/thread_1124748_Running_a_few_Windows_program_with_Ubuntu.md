---
title: "Running a few Windows program with Ubuntu"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Ocean Machine on 2009-04-13
Hey all, I've been using Ubuntu for a little over a year on a small System76 Daru2 and have found it to be pleasant enough of an experience to move to it as my main system. I'm anxiously waiting the arrival of my brand-new Serval Performance:p! 

In the meantime, I will have the need to run a few Windows programs on this computer. I'll need to use Microsoft Office; OpenOffice is good, but it simply can't compete with Excel, OneNote, and Word. Also, I have a Zune and a Blackberry, so I'll have to sync those using Windows. Finally, Google Earth works much much better in a Windows environment. 

I've heard of a couple different options for doing this, and was hoping to get some recommendations. I know Wine lets you run an emulated Windows under Ubuntu. I tried using it a little at one point but it wasn't easy enough to hold my attention. I've also heard of something called VirtualBox, but have no idea what it is or whether it would work in my situation. Finally, I could always partition a portion of the disk for Windows under a FAT32 if need be.

I'd love to get some advice from those who have attempted doing something like this in the past...thanks!

---

### Post by Zummy on 2009-04-13
I suggest Wine, I know you said that it wasn't easy, but if you can get over that intial bump it will do you well. Wine is amazing and can run most everything, well.

Try getting wine again and see if you can't get it to work.

---

### Post by sgosnell on 2009-04-13
If you want to run the full MS Office, you need Windows.  Wine won't cut it.  Personally, I've never seen anything that Open Office couldn't do as well as MS, but I haven't done everything possible.  The only way to run everything you want is to fork over the money and buy a copy of Windows.

---

### Post by SunnyRabbiera on 2009-04-13
I never had an issue with Openoffice, I say stick with Openoffice for word processing and Databases
For spreadsheets you may want to try gnumeric, if its one thing that is lacking in Openoffice its spreadsheets but Gnumeric seems to handle itself better.
Really I rather use Open Office then MS Office, especially 2007 with its crap ribbon.
For Zune, there isnt much hope there though, Microsoft hates us so no real support for Zune in the near future.
You can try XP in a Vbox though.
As for Google earth, meh I dont use it...
Its not vital to my productivity.
Wine is more simple then you think, as is Vbox, if you needd help setting it up just ask :D

---

### Post by halitech on 2009-04-13
> **Ocean Machine said:**
> Hey all, I've been using Ubuntu for a little over a year on a small System76 Daru2 and have found it to be pleasant enough of an experience to move to it as my main system. I'm anxiously waiting the arrival of my brand-new Serval Performance:p! 

In the meantime, I will have the need to run a few Windows programs on this computer. I'll need to use Microsoft Office; OpenOffice is good, but it simply can't compete with Excel, OneNote, and Word. Also, I have a Zune and a Blackberry, so I'll have to sync those using Windows. Finally, Google Earth works much much better in a Windows environment. 

Depending on the version of MS Office you want to install, WINE may or may not work for you. Same with the ZUNE and blackberry software.

> I've heard of a couple different options for doing this, and was hoping to get some recommendations. I know Wine lets you run an emulated Windows under Ubuntu. I tried using it a little at one point but it wasn't easy enough to hold my attention. I've also heard of something called VirtualBox, but have no idea what it is or whether it would work in my situation. Finally, I could always partition a portion of the disk for Windows under a FAT32 if need be.

WINE - Wine is Not an Emulator. WINE only acts as an API layer between the windows app and linux and in a lot of cases, if you need to communicate with usb hardware, it doesn't always work well. VirtualBox sounds like a better option to me although that may not work 100% either. You wouldn't need to use FAT32 to install windows if you go that route, linux will read NTFS quite well, writing was flaky but seems much better now.

> I'd love to get some advice from those who have attempted doing something like this in the past...thanks!

I haven't really tried it myself but I've seen alot of posts where people have and VB in most cases is better then WINE and dual booting is better then VB

---

### Post by djbushido on 2009-04-13
If you want to use a Zune, VirtualBox (virtual pc) is the only way to go. Don't know about the blackberry. Also, I believe Wine does run MS Office, at least 2003.

---

### Post by SunnyRabbiera on 2009-04-13
> **djbushido said:**
> If you want to use a Zune, VirtualBox (virtual pc) is the only way to go. Don't know about the blackberry. Also, I believe Wine does run MS Office, at least 2003.

2007 also works, despite how much I hate it...

---

### Post by halitech on 2009-04-13
results from WINE App database for MS Office

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

---

### Post by eeeandrew on 2009-04-13
Have a go with wine. I must admit I found a flaw in spreadsheet package just this morning while trying to sum sine waves to produce a square wave hence proving the fourier series. The problem I had was that my equation was sin(2*PI*f*t) and the bit in brackets is in degrees. Unfortunately, spreadsheet needs the angles in radians...after much head-scratching and wondering if fourier analysis does actually work I discovered this and fixed it using the toRadian function. In excel it lets you choose your angle units.

I should say other than this, I have never found a problem with open office. Anything I've wanted to do I've been able to although sometimes it has taken a browse of the help file which I feel I must compliment. The documentation is fantastic and more comprehensive than any other word processor I've tried.

Anyway, have a go with wine. 

> sudo apt-get install wine

then pop over to 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

check that your application is compatible. Put in the install disk and use the wine browser. Should be under Applications->wine->browse C: then install it just like any other program. You might first want to change the graphics settings to suit yourself. applications->wine->configure wine.

Hope this is useful,
Andrew

---

### Post by SunnyRabbiera on 2009-04-13
> **halitech said:**
> results from WINE App database for MS Office

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

Though it should be noted that individual results will vary, Office 2007 works for me at least though I only installed it for my hubby when he first used Linux.

---

### Post by Paqman on 2009-04-13
> **Ocean Machine said:**
> I know Wine lets you run an emulated Windows under Ubuntu. 


Actually Wine Is Not an Emulator. ;)

It'll run some apps, but is a bit hit and miss.

> 
I've also heard of something called VirtualBox, but have no idea what it is or whether it would work in my situation. 


VirtualBox is a virtual machine app. It basically creates a complete virtual computer, which you can install an OS into. This lets you run two OSes at once. Obviously you need at least about 2GB RAM and preferably a dual-core or better.

Dual-boot is also a good option. I actually have Wine and a dual-boot and virtualised Windows on my Ubuntu machine. I use the virtualised Windows if i'm just running one app, since I don't want to reboot. The full install of Windows gets used for games, since the performance hit you get in a VM makes gaming a non-starter.

---

### Post by halitech on 2009-04-13
> **SunnyRabbiera said:**
> Though it should be noted that individual results will vary, Office 2007 works for me at least though I only installed it for my hubby when he first used Linux.

of course, what works for you may not work for me and just because something *should* work, doesn't mean it will.

---

### Post by SunnyRabbiera on 2009-04-13
> **halitech said:**
> of course, what works for you may not work for me and just because something *should* work, doesn't mean it will.

Indeed, but everything is worth giving it a shot, wine has surprised me from time to time.

---

### Post by halitech on 2009-04-13
very true, I just find that I seldom need a windows app anymore and the few I do need I use on my laptop which is setup for dual boot so I don't need to interupt my life just to get to 1 app for 2 minutes to support my boss :D

---

### Post by Ocean Machine on 2009-04-13
It sounds like VirtualBox is the thing to try since I'll be doing some hardware/USB stuff. I will definitely come back if I have any questions. And, of course, I can always fall back on the dual boot option, although that's not ideal.

---

### Post by Paqman on 2009-04-13
> **Ocean Machine said:**
> It sounds like VirtualBox is the thing to try since I'll be doing some hardware/USB stuff.


For USB you want to get the non-open source version of VirtualBox. You can get a .deb for Ubuntu off their website, don't use the version in Synaptic.

---

### Post by SunnyRabbiera on 2009-04-13
Like I said if you need help setting it up just ask, suns Virtualbox is very simple to setup though and is perhaps the easiest one to learn.

---

