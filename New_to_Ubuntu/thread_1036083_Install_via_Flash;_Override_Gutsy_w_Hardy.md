---
title: "Install via Flash; Override Gutsy w/ Hardy"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by stackman1 on 2009-01-10
Hi Everyone.  Earlier this summer I took my Dell Inspiron 2500 and wiped out XP.  I burned the Gutsy version (7.10) and successfully loaded it but I had no luck getting my Broadcom 4318 network adapter to work with my Linksys router. Got a lot of great help from guys like Kevdog et al doing things like using ndiswrapper etc but I am such a newbie I gave up in frustration after about five weeks.  Guilt has made me return to conquer the beast.

I thought possibly upgrading to Hardy Heron (8.04) might help (thinking maybe a needed broadcom driver was now imbedded in the 8.04 kernel).  But as things go my CD burner crapped out on me, so I found the 'How To' to place my ubuntu-8.04.1-desktop-i386.iso on a flash drive using the Unetbootin utility. I have my flash drive ready to go (I assume) with the 8.04 iso.

I would like to completely overlay/wipe-out my 7.10 and install 8.04; there is nothing I need to save on the current laptop.

_My question is:_ if I place my flash drive into the USB port will 8.04 boot up and do the reformatting before installing or is it better to reformat the machine first (and if so how do I do that understanding the 7.10 kernel is in control)?

Hope I made myself clear.  Thanks Peter

---

### Post by blueridgedog on 2009-01-10
If your system will boot off of the flash, then select an install and elect to format the partitions when you go through the partitioning phase of the install.

---

### Post by stackman1 on 2009-01-10
When I boot the 7.10 machine with the 8.04 flash drive; it goes directly to booting 7.10 from the hard drive. I do have my BIOS boot order:

Removable Devices
CD-Rom Drive
Hard Drive

When 7.10 comes up my USB contents are visible (and the USB lights as soon as restart begins) but for some reason it is being ignored.

---

### Post by Guille Damke on 2009-01-10
Are you sure that "remomable devices" is the option to boot using an USB drive in your laptop? 
First, I would make sure that the USB drive actually works, can you try it in another computer?

---

### Post by stackman1 on 2009-01-10
I don't know for sure that 'removable drives' is the proper one to use but considering the other two options with my PhoenixBios, it is the most likely.  The Flash works as I am using it to move data between this computer (Inspiron 1100) and my Linux machine (Inspiron 2500).

I may have used the wrong version of UNetbootin.  So I am currently transferring via the USB Flash the 8.04 iso (ubuntu-8.04.1-desktop-i386.iso) and the 'Linux' version of UNetbootin (unetbootin-linux-304)to the Linux machine's desktop.  I will then
format my flash and re-run the linux version of UNetbootin and load the output (bootloader + iso contents) back onto the Flash and try to reboot the Linux machine again with the Flash....

---

### Post by stackman1 on 2009-01-10
When I tried to execute unetbootin-linux-304 to create my bootable version of 8.04.....I get a dialog box that says:

                 [B]mtools not found
mtools not found.  This is required for USB Drive install mode.   Install the "mtools" package or your distribution's equivalent.[/B] 

I did a search on the Synaptic Package Manager but could not find _mtools_.

Ideas?

---

### Post by blueridgedog on 2009-01-10
sudo apt-get install mtools

That shouls install them...

---

### Post by stackman1 on 2009-01-10
peter@i2500:~$ sudo apt-get install mtools
[sudo] password for peter:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package mtools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mtools has no installation candidate[/B]
peter@i2500:~$

---

### Post by JoshuaRL on 2009-01-10
You may not have the right repos enabled.  But here is the place to get mtools:
[http://security.ubuntu.com/ubuntu/pool/main/m/mtools/](http://security.ubuntu.com/ubuntu/pool/main/m/mtools/)

---

### Post by stackman1 on 2009-01-10
I went to the site but there were about 20 files....

If I had to guess:
[URL="mtools_3.9.11-1_i386.deb"[/URL] or

[URL="mtools_3.9.11.orig.tar.gz"[/URL]

But I wouldn't know what to do next anyway; I am truly a beginner

---

### Post by JoshuaRL on 2009-01-10
If you have the 32bit version, then yeah.  Get the deb, its the Debian/Ubuntu exe.

---

### Post by stackman1 on 2009-01-11
Hello Everyone. I think I am biting off more than I can chew trying to upgrade to 8.04 via a Flash Drive.  I am a novice and need to do more homework before I nickel and dime you to death.  
I found StarMature's tutorial [http://ubuntuforums.org/showthread.php?t=500020&highlight=adding+pkg]("http://ubuntuforums.org/showthread.php?t=500020&highlight=adding+pkg") and am going through that 

But if I might, I would like to ask 2 questions:

1. As I stated in my original post, this summer I installed Gutsy 7.10 Version from a burned .iso onto my Inspiron 2500.  But I ran into trouble trying to get my wireless card to work.  So after about 5 weeks - I gave up, until the other day.  I decided I would try upgrading to 8.04 hoping the newer kernel would have my broadcom driver.  

But my cd burner crapped out and I ended up on a Flash drive and I realized I need to get back to learning the basics. So I will try to work with my 7.10 version; hopefully my attempts this summer didn't do any damage.  

I am reading StarMature's tutorial and one of the first things he suggested doing presented me with a worrisome result.  He suggested displaying my *source* list via **gksudo gedit /etc/apt/sources.list**

Below is the output - it appears everything but the first line is commented out (btw, while I did my initial install via a CDROM, this output was produced by my booting off of the hard drive -no cd in machine.  Is it likely the current lack of active lines in my source list, why I had so much trouble this summer?  Ideas? 

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```
 
2.  Since I am no longer trying to understand my Flash issue; should I mark this as solved or can I close it somehow.

Thanks to everyone who has helped to date!

---

### Post by blueridgedog on 2009-01-11
An alternative to looking at the raw file is to go to System -> Administration -> Software Sources.

I select the four primary ones, main, universe, restricted, multiverse

---

### Post by blueridgedog on 2009-01-11
> **blueridgedog said:**
> An alternative to looking at the raw file is to go to System -> Administration -> Software Sources.

I select the four primary ones, main, universe, restricted, multiverse

You can also order a cd of 8.1 and I recommend the upgrade.

---

### Post by stackman1 on 2009-01-11
Thanks Blue.  So the fact that I have not accessed these 4 software sources, in effect mean that I am working with little more than the kernel?

In other words, the 7.10 .iso file that I initially loaded is just enough 'theoretically' to get the system up.....and then the normal procedure is to use the Software Services panel to download all the needed libraries from the internet?  Maybe that explains why my wireless card wouldn't work (although I did try using the ndiswrapper procedure but always unsuccessfully).....

So if I order a 8.1 cd - when I boot up with that in the drive - will it allow me to completely overwrite my 7.10 version - or is it just an upgrade?  Because I am almost tempted to re-format my machine if it was easy to do.

Any suggestions on the best place to order the 8.1 CD?

Thanks 
Peter

---

### Post by earthpigg on 2009-01-11
ship it will send you a free ubuntu cd ;)

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

yes, the live cd will wipe your hard drive.

in my case, going from 8.04 to 8.10 made my wireless work out of the box (i gave up on ndswrapper or whatever its called just like you).

---

### Post by stackman1 on 2009-01-11
Thanks for the info.  I will order one from shipit.

Anyone know the proper protocol for closing this thread.  I could mark it 'solved' but I took us off the 'Flash' problem a while back and I never solved it.....anyway to just close a thread?

For the moment I leave open...

---

