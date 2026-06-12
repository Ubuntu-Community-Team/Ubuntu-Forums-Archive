---
title: "Installing a modem to get online..."
date: 2010-09-17
forum: New to Ubuntu
---

### Post by germeten on 2010-09-17
Hi everyone;

I've a dual-boot system, WinXP/Ubuntu, the latter set up by a friend. The XP side logs
on fine but Ubuntu says I need a package, which I downloaded, but when tried to
install, said I need more packages. Some require very specific knowledge of hardware
and it would appear, programming, to get my modem to work. I think it makes linux 
beyond the range of the average user. I'm ready to take responsibility, but need more 
tools. I've read the general FAQ's but as usual, God & the devil are in the details. 
Unsure what version of Ubuntu but know it's current.

System: 

Gateway E-4100 desktop
Pentium IV, i86 2.4Ghz processor 
1272 Mb memory
Lucent Win-modem

Can someone direct me to resources where I can detect and download the necessary 
packages using Windows so I can install and logon using Ubuntu OS? Thank you.

---

### Post by oldsoundguy on 2010-09-17
Win modems = WINDOWS modems .. do not WORK in Linux.

You may have to go with an external .. USRobotics makes modems that work on ALL operating systems .. and they are MUCH faster than any internal modem you can buy.

When I was stuck on dial up, that is the way I went.

---

### Post by ubunterooster on 2010-09-17
If you are using AOL it causes several more steps to get working, see: [http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

---

### Post by lkraemer on 2010-09-18
germeten,
The easiest way to go is to purchase an External US Robotics Hardware
Modem from Ebay and use it with your machine.  That shouldn't take
you more than 15-30 minutes if you follow the guide at:

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial)
Posting #4

But, I also understand that you want to try and use the WinModem that
is already in your machine.  So, you're in for a little work, mostly 
3-5 days with several emails to Marvin and the fine folks at 
[www.linmodems.org](www.linmodems.org)   You need to set your email for PLAIN TEXT, then 
subscribe to their discussion list.  Also you will need to download their
script, execute it, and post the results back for Marvin and those folks
to analyze, then post your method of proceeding.  And all this will need
to be done in Windows, and then the scripts etc, will need to be copied
to USB Flash Drive for xfer to Ubuntu.  It isn't an easy proccess, but
it is possible.  

If you don't have a Dialup account, Look for one that works well
with Linux. Copper.net seems to work fine, as I have used it for
several years now. Search forum for "Linux ISP's"

You ONLY need to download and install the following:
1. wvdial & dependencies......

You need to download wvdial and the following dependencies for 10.04,
or your speciific version.
wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install
using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

2. Gnome-PPP
But wait until you have wvdial working before trying anything with
Gnome-PPP.

Or you can download [http://keryxproject.org/download/](http://keryxproject.org/download/) and use it where you have internet access to get:
Gnome-ppp
wvdial
(and anything else you want before you get dialup working).

Take those downloaded files to your Ubuntu computer on the USB Flash
Drive.

Then proceed to the guide.

lk

---

