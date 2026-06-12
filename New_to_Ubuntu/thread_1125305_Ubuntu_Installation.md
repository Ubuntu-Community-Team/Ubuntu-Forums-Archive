---
title: "Ubuntu Installation"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by JupiterMike on 2009-04-14
I am frustrated and disappointed.  As a computer idiot and a ubuntu newbie I have tried to install Ubuntu as a folder in Windows.  I've tried my 8.10 DVD, my 8.04 DVD and I've tried WUBI.  I get to the point where the screen says "loading"and the term <initramfs> then it won't go any furthur. I've checked the forums, both "beginner" and "installation" and it appears that lots of persons have same problem. As a computer idiot I don't know how to do all the ins and outs of "go here and enter this etc". As guess I have to give up.  Sorry about that.

---

### Post by steve101101 on 2009-04-14
solution is here ...

[http://ubuntuforums.org/showthread.php?t=804713](http://ubuntuforums.org/showthread.php?t=804713)

---

### Post by clive littlewood on 2009-04-14
Hi

Does it work as a "Live CD"  ?

How are you trying to install ? in Wubi, as a dual boot or standalone.

With more info we will be able to help.  :p

Clive

---

### Post by swoody on 2009-04-14
Good morning JuipiterMike :D

You don't have to feel bad about being a "computer idiot", we are all computer idiots at one time or another. Nobody was born knowing how to use the command line, or to compile programs, or repartition hard drives (well maybe except for Linus Torvalds ;)) but we all just help each other out, and learn it as we go along :)

So I take it you have only tried installing Ubuntu as a Wubi installation? Is there any reason you haven't tried setting up a dual-boot on your comp? I have found that a lot of people who have problems with Wubi haven't encountered the same diffuculties when dual-booting.

Fill us in a bit more about your computer. What you use it for, what Windows OS you are running, what you'd like to use Ubuntu for, etc. The more info you can pass our way, the better we'll be able to help you setup Ubuntu, and get it working the way you'd like it!

I truly hope you'll give us (and Ubuntu) another chance to help you out here :D

---

### Post by JupiterMike on 2009-04-14
> **swoody said:**
> Good morning JuipiterMike :D

You don't have to feel bad about being a "computer idiot", we are all computer idiots at one time or another. Nobody was born knowing how to use the command line, or to compile programs, or repartition hard drives (well maybe except for Linus Torvalds ;)) but we all just help each other out, and learn it as we go along :)

So I take it you have only tried installing Ubuntu as a Wubi installation? Is there any reason you haven't tried setting up a dual-boot on your comp? I have found that a lot of people who have problems with Wubi haven't encountered the same diffuculties when dual-booting.

Fill us in a bit more about your computer. What you use it for, what Windows OS you are running, what you'd like to use Ubuntu for, etc. The more info you can pass our way, the better we'll be able to help you setup Ubuntu, and get it working the way you'd like it!

I truly hope you'll give us (and Ubuntu) another chance to help you out here :D
Computer is running XP w/service pack 3, Intel Pentium 4, 120GB Harddrive with 77GB free, 512mb memory.
I tried option to instal Ubuntu WITHIN Windows.  Trial #1-Wubi, Trial #2-Ubuntu 8.10 DVD, Trial #3-Ubuntu 8.04 DVD.  Results were always the same
<initramfs> and computer freezes, screen goes blank after a few minutes.  Must reboot computer to resume working.  Shows 2 choices on reboot 1)Wndows 2)Ubuntu. Choosing Ubnutu starts the cycle all over again.

---

### Post by halitech on 2009-04-14
with the live cd/dvd, will it start and run?

---

### Post by swoody on 2009-04-14
> **JupiterMike said:**
> Trial #1-Wubi, Trial #2-Ubuntu 8.10 DVD, Trial #3-Ubuntu 8.04 DVD

Do you mean running the Live CD's for 8.10, and 8.04 by themselves gave you this same error? Did you uninstall Wubi completely before trying these live cd's? If not, backup any and all data from Windows you wouldn't want to lose (just in case;)) and **uninstall Wubi completely**. Then reboot into the live disc, and try to install the typical way allowing the live cd to shrink your XP partition, and automatically repartition the new free space.

See if this works for you, or if you're still getting the same error. Please post back here, and let us know good or bad :)

---

### Post by abn91c on 2009-04-14
Jupiter what's your video card?

---

### Post by JupiterMike on 2009-04-15
Wubi removed completely.  Both CD's (8.10 Desktop Edition & 8.04 LTS Desktop Edition) have 3 choices 1)Demo and Full Installation, 2)Install inside Windows and 3)Learn more.  I have been using choice 2 for installing.  Problem <initramfs> still exists. On re-boot 2 choices show,  (boot in Windows or boot in Ubuntu.  Choosing Ubuntu starts the cycle all over again.

---

### Post by halitech on 2009-04-15
my advice is forget about the Live CDs, sounds like there is some kind of issue with your video card not being supported very well. Get the Alternate Install CD and try to install with that instead.

---

### Post by JupiterMike on 2009-04-15
I don't know if this is the video card or not.  Radeon 7000/Radeon VE family(microsoft)(Display adapter)

---

### Post by halitech on 2009-04-15
that would be the video card. Some ATI cards aren't well supported out of the box so you may have better luck with the alt install cd

---

### Post by Jakey_TheSnake on 2009-04-15
You can find out your video card with: ```
lspci -v | grep VGA
``` ;) 

I believe Radeon supply drivers for linux on their site, I may be wrong though.

edit: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by halitech on 2009-04-15
> **Jakey_TheSnake said:**
> You can find out your video card with: ```
lspci -v | grep VGA
``` ;) 

I believe Radeon supply drivers for linux on their site, I may be wrong though.

only problem with that is he can't get into a running version of Ubuntu ;)

and yes they do but not all cards are supported and if they are, they need to be installed after the OS is up and running

---

### Post by Jakey_TheSnake on 2009-04-15
> **halitech said:**
> only problem with that is he can't get into a running version of Ubuntu ;)

and yes they do but not all cards are supported and if they are, they need to be installed after the OS is up and running

Didn't read that part of the thread ;) 

I believe you can press F4 for alternate installation options, and an option is safe graphics mode. What happens when you press "Try Ubuntu Without Any Change To Your Computer"?

---

### Post by CatKiller on 2009-04-15
> **JupiterMike said:**
> Wubi removed completely.  Both CD's (8.10 Desktop Edition & 8.04 LTS Desktop Edition) have 3 choices 1)Demo and Full Installation, 2)Install inside Windows and 3)Learn more.  I have been using choice 2 for installing.  Problem <initramfs> still exists. On re-boot 2 choices show,  (boot in Windows or boot in Ubuntu.  Choosing Ubuntu starts the cycle all over again.

So you've just tried with Wubi then? That's what "install inside Windows" means.

You need to boot the computer from the cd to try the live cd, which (if it works, which is a useful test) will give you the option of installing Ubuntu alongside Windows in a separate partition.

The general process is to put the cd in and then boot your computer. You'll then get an Ubuntu menu that will give you the option to try Ubuntu or test the cd for defects, and a bunch of other things that I can't recall at the moment.

It's possible that your computer isn't set to boot from the cd, in which case you would press whichever key the "Press <key> to enter Setup" directs you to press, and set the option to boot from the CD drive before the hard drive. The name of this option changes from motherboard to motherboard, but you should be able to find it OK.

---

### Post by JupiterMike on 2009-04-18
> **clive littlewood said:**
> Hi

Does it work as a "Live CD"  ?

How are you trying to install ? in Wubi, as a dual boot or standalone.

With more info we will be able to help.  :p

Clive
Trying to install within Windows using 8.10 Desktop Edition CD. Tried installing on my laptop, installs OK, but I don't want it on my laptop.

---

### Post by halitech on 2009-04-18
chances are your laptop has different hardware then your desktop and also a good chance that due to the video card, WUBI might just not work and you may have to either dual boot or setup a virtual machine which will be slower while running. 

I would suggest doing a defrag at least twice on your desktop and then partition the drive and use the alt install cd to install. After its installed, then we can worry about trying to get the video card working properly.

---

