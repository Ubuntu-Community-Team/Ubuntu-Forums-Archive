---
title: "ATI Radeon 9600 (RV350 AP) - no support in Ubuntu 9.10"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by maxzero on 2010-08-29
Hi, I am currently dealing with a lot of issues here with Ubuntu 9.10 Karmic (yea, I know I have a very very old distribution...oh well). Anyways, my current computer specs are running Ubuntu 9.10 very very sluggishly. But to top that off, I find out that there are no ATI drivers for my ATI Radeon 9600 card in Ubuntu 9.10. Because I type in "aticonfig" I get the message of "No supported adapters detected" while the device manager is able to detect my card. I installed ATI Control Center, that says I don't have ATI device driver installed. 

So, in the end, I need solutions to my problems, problem 1 being the ATI driver and problem 2 being the sluggish running of Ubuntu.

Truth be told, my system is way way way past it's prime, so I don't really blame Ubuntu for that.

Specs :

AMD 2800+ 1.8 GHz
ASUS K8S-MX
1.5 GB RAM
ATI Radeon 9600

Just as a side note, I wanted to do the Mac OSX theme for Ubuntu with Cairo dock and I wanted to Overclock my system. So if anybody knows any guides, or tutorials for either or for both, your assistance would be greatly appreciated.

Thanks.

---

### Post by Talon2 on 2010-08-29
I have a box here that has a 9600 in it.  I ran it with 9.10.  It now runs with 10.4.  The included open source driver does a great job.

What is it that makes you think there is no driver installed?

---

### Post by Famicube64 on 2010-08-29
Binary driver support for that card was dropped a long time ago, stick to the open source driver.

---

### Post by Perfect Storm on 2010-08-29
As other said. ATI dropped the support of older cards (known as restricted drivers), so you have to go with the Open Source driver that comes with Ubuntu.

---

### Post by maxzero on 2010-08-30
so can anyone tell me how to get open source driver for ATI Radeon 9600 for Ubuntu 9.10...Please?

---

### Post by Perfect Storm on 2010-08-30
The driver is installed by default (you may have better luck with ubuntu 10.04 which comes with a open newer driver).

So it may need tweaking (You might want to search the forums or google for that, as I swear to nvidia cards)

But lets see if xorg picked up your card;
```
cat /etc/X11/xorg.conf
```

There should be something like this;
```
Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection
```

---

### Post by mastablasta on 2010-08-30
There is no need for tweaking.
 
Opensource is automaticly installed and you can run games and everything normally with 9600 (well at least i haven't hit anythign strange yet...). 
 
Why not upgrade to 10.04?

---

### Post by maxzero on 2010-08-30
Well Artificial Intelligence, I did the command line you gave and it yielded the following result :

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2560 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

I don't know if its worth mentioning, I have two LCDs. All I want is to get 3D Acceleration of my card activated or enabled so that I can work in Blender 3D and increase the screen resolution from 1280 x 1024 to something higher. And to end the choppy and flickering of flash videos (Sorry...I have a huge list of problems :neutral:).

---

### Post by Mark Phelps on 2010-08-30
> **maxzero said:**
> All I want is to get 3D Acceleration of my card activated or enabled...

Well, given that as several folks have already told you, proprietary driver support for you card was dropped a long time ago, and you are now stuck with using the open-source driver, you're simply NOT going to get other than very minimal 3D acceleration.

IF you're seeing a graphical desktop, the open-source drivers are already installed -- and that is ALL THERE IS for your card.

---

### Post by mastablasta on 2010-08-30
how would you test in linux how much acceleration can you get? any engine out there free to test it?
 
9600 on Windows runs Oblivion on medium.
 
Flash can be a problem in processor not GPU.

---

