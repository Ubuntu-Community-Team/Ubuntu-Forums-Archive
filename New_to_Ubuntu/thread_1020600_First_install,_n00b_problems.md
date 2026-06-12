---
title: "First install, n00b problems"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by elliottj85 on 2008-12-24
Hi guys,
I've taken the plunge and finally got rid of a slow and bloated windows installation and gone with ubuntu.
I am having a whole load of problems with getting various things set up. I installed ubuntu 3 days ago and since then I've been trawling the boards for answers to my problems, but no luck.
anyway, these are the issues.

firstly, I cant find any driver for my video card, theres nothing in the system-administration-drivers list and I cant switch on desktop effects.

second, when I try to play a dvd in totem, the disc loads to the choose language section but then theres no cursor on screen and i cant press play, choose a chapter etc.

thirdly, my webcam light lights up when i plug it in but i cant see any image in skype or ekiga.

any help would be hugely appreciated, i want to stick with linux but i need the functionality.

---

### Post by newbee70 on 2008-12-24
> **elliottj85 said:**
> Hi guys,
I've taken the plunge and finally got rid of a slow and bloated windows installation and gone with ubuntu.
I am having a whole load of problems with getting various things set up. I installed ubuntu 3 days ago and since then I've been trawling the boards for answers to my problems, but no luck.
anyway, these are the issues.

firstly, I cant find any driver for my video card, theres nothing in the system-administration-drivers list and I cant switch on desktop effects.

second, when I try to play a dvd in totem, the disc loads to the choose language section but then theres no cursor on screen and i cant press play, choose a chapter etc.

thirdly, my webcam light lights up when i plug it in but i cant see any image in skype or ekiga.

any help would be hugely appreciated, i want to stick with linux but i need the functionality.

have you loaded ubuntu-restricted?

if not add/remove :search all packages for ubuntu, the first on the list will be the restricted modules.

---

### Post by albinootje on 2008-12-24
> **elliottj85 said:**
> 
firstly, I cant find any driver for my video card, theres nothing in the system-administration-drivers list and I cant switch on desktop effects.


Can you post the output of the following commands in a terminal with your webcam plugged in :
```

sudo update-usbids
lspci
lsusb
lshw -c display

```
Thanks in advance.

---

### Post by elliottj85 on 2008-12-24
thanks for the speedy response

I just tried it but I got:

Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I wonder what is conflicting with it?

---

### Post by freesitebuilder on 2008-12-24
These two sites give hardware support info, where you can check if your hardware is supported:
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

My nvidia card was OK on 8.04, but the driver for 8.10 causes problems, so I'm making do without special effects at the moment - you may have a similar situation with your card. What is it?

My webcam is listed as supported, but I haven't managed to get it working properly yet, although I know others that have - again, what is it?

---

### Post by taurus on 2008-12-24
1.  Which graphic card do you have?

```
lspci | grep VGA
```

2.  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by taurus on 2008-12-24
> **elliottj85 said:**
> thanks for the speedy response

I just tried it but I got:

Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I wonder what is conflicting with it?

Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by elliottj85 on 2008-12-24
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://blognux.free.fr/ubuntu hardy main

```

---

### Post by elliottj85 on 2008-12-24
Im on a sony vaio laptop, model is pcg-fx602
its about 6 years old

the graphics card is 
 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

---

### Post by taurus on 2008-12-24
Any reason why you have a hardy's repo in your /etc/apt/sources.list (last line)?

```
deb http://blognux.free.fr/ubuntu hardy main
```

---

### Post by elliottj85 on 2008-12-24
> **taurus said:**
> Any reason why you have a hardy's repo in your /etc/apt/sources.list (last line)?

```
deb http://blognux.free.fr/ubuntu hardy main
```

I'm not sure, I don't really know what that is. The whole terminal thing is new to me as well.

Should I have that there?

---

### Post by elliottj85 on 2008-12-24
my card is listed on the ubuntu wiki as supported but i cant find my web-cam (pc-line pcl-300n)

---

### Post by elliottj85 on 2008-12-24
bump

---

### Post by chewit on 2008-12-24
I would not use Totem for DVDs, install VLC. It will play DVDs with no issues, it is also a very good replace ment for totem since it plays all file formats.

Have you tried going to System > Administration > Hardware Drivers. You may be able to sort your graphics driver problem from there.

---

### Post by elliottj85 on 2008-12-24
I'll install that video software straight away.

Theres no drivers listed on the system->administration->hardware drivers.

---

### Post by elliottj85 on 2008-12-24
installed vlc, the dvd loaded, I clicked on play movie but then it crashed

---

### Post by elliottj85 on 2008-12-24
so, can anyone give me help with the video drivers? my card is listed as supported but i have no drivers. i installed the restricted package from add-ons but that hasn't fixed it.
any ideas?

---

### Post by ColBuendia71 on 2008-12-24
Ok, the dvd issue is best resolved by adding the medibuntu repositories. There is a guide to doing so here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you install that repo, open up Synaptic and hit reload. There should be a button on the bottom left that says "Origin." Click that and it should bring up a list of your repositories. Click on the medibuntu list and look through the packages to find the ones that suit your needs. There are a lot of good things in there and I'd recommend taking your time and looking through.

As for the video card, that stymies me. Are you using Intrepid? I installed Intrepid on my wife's very similar Vaio with what sounds like the same video card and compiz worked on first boot. Maybe try installing envy-ng qt through synaptic.

---

### Post by elliottj85 on 2008-12-24
update (this is starting to drive me crazy)

i installed medibuntu and went through the list, installing everything that said 'restricted' or 'ati'. i restarted and now i have low graphics mode and still no video drivers.

can you suggest something else please

---

### Post by elliottj85 on 2008-12-24
bumpety

---

### Post by ColBuendia71 on 2008-12-25
Ok, let me go down and look at that other Vaio I was talking about and see what driver it has on it. I just gave it as a Christmas gift, but I still have access to it for the day.

---

### Post by elliottj85 on 2008-12-25
thanks, any luck?

---

### Post by ugm6hr on 2008-12-25
For display driver - post output from:

```
lshw -class display
```

For DVD / media probs, see the Multimedia link below.

---

### Post by Krisando on 2008-12-25
Ubuntu is far from user friendly, it makes my computer as useful as a brick.

---

### Post by elliottj85 on 2008-12-25
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage Mobility P/M AGP 2x
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8

checking multimedia link now. thanks for the help

---

### Post by ColBuendia71 on 2008-12-25
Ok, that Vaio I just gave away has xserver-xorg-ati and xserver-xorg-radeon. If that's the same video card in your Vaio which it sounds like it is then make sure those are installed.

Did you get the DVD player working?

---

### Post by ugm6hr on 2008-12-26
Your lshw suggests you are using a generic display driver.

For example, mine has (in configuration):
```
configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx

```

If there are no options in Hardware Drivers, perhaps the latest ATI drivers might work, although I can't find the card on [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) - but then I can't find it in the XP list either.  It must go under a different name too - if you can find it there, envy will install the latest driver for you.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti) says it is compatible, but neglects to mention what driver is used.

---

### Post by elliottj85 on 2008-12-26
thanks, ill give those a go and report back. 
some dvds are playing and others aren't the ones which don't play, load up but when i try to click on 'play', 'choose chapter' etc, the video player goes black screen and becomes unresponsive.

---

### Post by Sealbhach on 2008-12-26
> **Krisando said:**
> Ubuntu is far from user friendly, it makes my computer as useful as a brick.

If it doesn't work for you just go back to what works. maybe it's not for you, due to your hardware being problematic or something.

It works for me and I find it very user friendly. Just do what works for you.


.

---

