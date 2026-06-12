---
title: "Linux Install on 2nd Laptop - Video Issue"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Dark7man on 2010-12-04
Hello everyone,
               I've been using Ubuntu 10.10 (64bit) on my HP Laptop for a month or two now... loving it, decided to install it on an old laptop at home for my siblings, a Fujitsu Siemens Esprimo V5535...

I have tried Ubuntu 10.10 32bit + 64bit + Linux Mint 10.10 and I'm having issues with the SIS671MX Chipset... cant set the resolution over 800x600... tried for hours...many fresh installs etc.  My xorg.conf file turns up blank, tried many of the tutorials - no joy...

I dont want to have to revert it back to Windoze Vista... I cant get my head around configuring manually xorg.conf   - anywhere I can learn how to understand how they work?  So maybe I can make one manually from scratch, I have the same issue with my own HP Laptop - cant get the resolution over 1366x768 ... I can live with it at the min though as I connect to my HDTV and resolutions on that seem fine!

Please help me out...
Many thanks in advance!
:guitar:

---

### Post by jplo on 2010-12-04
Are you running trying to run the Netbook Edition or Desktop Edition on the older laptop?

Try using 10.04 on it instead.

---

### Post by Penguin=) on 2010-12-04
I have no idea what has happened here, but you say you have done many fresh install's, that means that its the computer itself.

You may have to get another ISO and burn it to a CLEAN disk maybe?, if that doese'nt work, im afraid your stuck!

---

### Post by Dark7man on 2010-12-04
> **gerbilschool said:**
> Are you running trying to run the Netbook Edition or Desktop Edition on the older laptop?

Try using 10.04 on it instead.

Tried Desktop edition - 10.10 - Just downloading Netbook Edition now to try... Why 10.04?  Some support for older hw left out on newer builds?

---

### Post by jplo on 2010-12-04
Some very old hardware was dropped in 10.10, but if the laptop came with Windows Vista, it is not going to be affected. (I'm talking 4-bit 8-bit and 16-bit, not 32 and 64-bit)

---

### Post by Dark7man on 2010-12-04
2mins to download of Netboot edition finishes... think I'll have much luck with netbook distro... crazy that these days some hw... such as SIS chipsets are support out of the box... laptop is close to 2years old... everything else seems to run brilliant... :(  That where micros*ft has the upper hand?  BIG CORPORATE NAME so all the manufacturers jump on board - everything else is not important?

---

### Post by jplo on 2010-12-04
Make sure that you have a download of roughly 700mb, as you don't want to waste a CD by burning a corrupt iso file :)

---

### Post by Dark7man on 2010-12-04
Sorted mate - size is spot on - install from USB Flashdrive - quicker to copy iso's across n that with UNetbootin! :) Handy app :)

Thanks for the heads up though mate :)

---

### Post by Dark7man on 2010-12-04
Anyone any tips on how to manually configure xorg.conf?  Like when I run lspci + lshw to get the names the system knows my hw as... and maybe force an output?  So I can go about manually creating a xorg.conf

These files I take have a standard layout, just certain fields are specific to the hw... but I doubt this is impossible to manually force settings etc?

---

### Post by Dark7man on 2010-12-04
could anyone even send me a copy of their xorg.conf    it would give me something to work with... mine are blank on both machines... checked logs but cant make head nor tail of where its getting its settings from :S

---

### Post by Dark7man on 2010-12-04
Didnt get no where - resorting to Vista install - will mark thread as solved though so its ignored - until I better my knowledge of Linux :)  That laptop has escaped the little penguin quiet yet :)

---

### Post by oldfred on 2010-12-04
I have not had to manually edit xorg for a couple of years and then it was chaging nv to nvidia and adding a few modes that were missing.

What video driver does the laptop have.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0
if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

If able to boot to recovery mode & netroot
to get a list of recommended drivers:
jockey-text -l
Install a driver from above list:
sudo jockey-text -e <driver>

---

### Post by jplo on 2010-12-04
Have a look at this:

[http://ubuntuforums.org/showpost.php?p=9279264&postcount=445](http://ubuntuforums.org/showpost.php?p=9279264&postcount=445)

---

### Post by Dark7man on 2010-12-04
I've just killed the install of Windoze - Got Ubuntu loaded onto pendrive.... Quick question... Someone said earlier try 10.04... and I see still a lot of people are still using it (that or they haven't updated their profile :)) Anyway... Should I really just download 10.04 and try it?  It like the last stable version before the update to 10.10 - I know its software....takes time to get the creases ironed out... :)

You know what... while 10.04 is downloading... I'll try that link on 10.10 see if it helps.... I'm sure you guys understand resolution is a deal breaker.. same as sound, or wlan!  I dont think its a problem or something Linux is unable to do... I think also its my lack of knowledge - the old P.E.B.K.A.C too :)

---

