---
title: "Firefox not working after upgrade to 10.10"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Catfish Dubois on 2011-01-01
I just upgraded from 10.4 to 10.10.  Now firefox will not work. 

Every time I launch firefox, I get a Mozilla Crash Reporter.  I've tried uninstalling and reinstalling firefox in the Ubuntu software manager.  Any help is appreciated.  The details of the crash report are as follows:

 Add-ons: [email]langpack-en-GB@firefox-3.6.ubuntu.com:3.6,ubufox@ubuntu.com:0.9rc2,{e968fc70-8f95-4ab9-9e79-304de2a71ee1}:0.7.2,{e4a8a97b-f2ed-450b-b12d-ee082ba24781}:0.8.20100408.6,refractor@developer.mozilla.org:1.0b3,{DDC359D1-844A-42a7-9AA1-88A850A938A8}:1.1.10,{2f17f610-5e97-4fed-828f-9940b7b577a4}:1.6.2,{899DF1F8-2F43-4394-8315-37F6744E6319}:1.0.5,LotusDolsPlugin@ibm.com:8.5.1.0,bindwood@ubuntu.com:1.0.4,{E0B8C461-F8FB-49b4-8373-FE32E9252800}:4.0.0.106602,langpack-en-CA@firefox-3.6.ubuntu.com:3.6,langpack-en-AU@firefox-3.6.ubuntu.com:3.6,langpack-en@firefox-3.6.ubuntu.com:3.6,netbook-webfav@ubuntu.com[/email]:1.17,{340c2bbc-ce74-4362-90b5-7c26312808ef}:1.4.3,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.6.13
BuildID: 20101206121845
CrashTime: 1293919594
EMCheckCompatibility: true
Email: [email]carlburkart@hotmail.com[/email]
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1293913669
ProductName: Firefox
ReleaseChannel: default
SecondsSinceLastCrash: 1861
StartupTime: 1293919592
Theme: classic/1.0
Throttleable: 1
URL: [http://www.google.com/](http://www.google.com/)
Vendor: Mozilla
Version: 3.6.13

This report also contains technical information about the state of the application when it crashed.

---

### Post by jcolyn on 2011-01-01
Nothing unusual for upgrades..

You should backup needed files then do a clean install after wiping the drive which is the best and most trouble free way to go to a newer version..

---

### Post by Catfish Dubois on 2011-01-01
Is there any way to avoid a full reinstall? 

My Ubuntu is installed in a usb hardrive.  When I first set it up, it changed the masterboot loader on my laptop, and it took me a long time to fix it.

---

### Post by jcolyn on 2011-01-01
> **Catfish Dubois said:**
> Is there any way to avoid a full reinstall? 

The only option I use is a full install.

> **Catfish Dubois said:**
> My Ubuntu is installed in a usb hardrive.  When I first set it up, it changed the masterboot loader on my laptop, and it took me a long time to fix it.

Someone else will have to help you with this one since I have never installed to a flash drive.

---

### Post by fabricator4 on 2011-01-01
> **Catfish Dubois said:**
> Is there any way to avoid a full reinstall? 

My Ubuntu is installed in a usb hardrive.  When I first set it up, it changed the masterboot loader on my laptop, and it took me a long time to fix it.

Try un-installing Firefox in the Synaptic Package Manager, then re-install it again. (Mark for re-installation may also work)

Go:

System:
   Administration:
       Synaptic Package Manager

Linux may just have lost some dependencies in the upgrade.

I have to say that Google Chrome also works very well.  I had to install it on my wife's computer so she could use Facebook (yuk!) and was quite impressed with Chrome.

I didn't have much luck with upgrading my Ubuntu when I tried it. I think they try to preserve too much, when all they should be doing is using the existing partitions and preserving the home directories.

I'm curious as to why you're booting off a USB - it's really quite slow in use though it's a good way to get a feel for a new release before installing it - checking compatibilities and so on.

Consider doing a Wubi install since I think you must be using Windoze.  It will still be slow to boot, but not as slow as booting off USB memory.  You install the Wubi from within Windows, just as you would any windows program.  It can also be removed just as easily but you probably won't need to - it works very well!  I have one of my laptops set up this way.

Chris

---

### Post by Catfish Dubois on 2011-01-01
My current laptop is a work laptop, so I can't make any major modifications to the operating system, number of partitions, etc.  I wanted to try ubuntu, so I installed it on a 320GB usb hard drive that I had lying around.  My work laptop is a few years old, so I have to use a GRUB 2 CD to get it to boot from the external hard drive, but once it is up and running, everything seems to be ok (it still boots faster than XP).  

Update: I uninstalled "libmoon" in the Synaptic Package Manager, and firefox is now working fine.

---

### Post by jcolyn on 2011-01-01
> **Catfish Dubois said:**
> 

Update: I uninstalled "libmoon" in the Synaptic Package Manager, and firefox is now working fine.

Moonlight has been a major pain since it was introduced. Since I don't access any silverlight files I don't install moonlight..

---

### Post by fabricator4 on 2011-01-02
> **Catfish Dubois said:**
> My current laptop is a work laptop, so I can't make any major modifications to the operating system, number of partitions, etc.  I wanted to try ubuntu, so I installed it on a 320GB usb hard drive that I had lying around. 

Drifting off topic for the subject line but forgive me (all) for evangelizing:

A Wubi install is definitely for you.  It doesn't make any radical changes to the existing OS or the partitions.  Getting rid of it takes only minutes if you have to hand the laptop back.  Just use the external HDD to backup the home directory so you can migrate to a dedicated system later or for backup.

I was a bit dubious about the Wubi install on my work laptop at first, but it works well - you get a choice at boot time to go windows or Ubuntu/Linux.  You can also see your C: data with a bit of tweaking (requires you to mount the HPFS or FAT drive)

Congrats on the Firefox fix.

Chris

---

