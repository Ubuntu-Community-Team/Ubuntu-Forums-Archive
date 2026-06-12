---
title: "Installing Linux command-line, graphics issue"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by ThePilch on 2011-07-17
Hi,

I've never touched linux before, yet i have got it into my head that i can somehow turn a new PC into a host for a VPN, as well as the dedicated host for some old-school games (pre 2005) such as unreal tournament, etc.

Also as a web design test environment, and a website host.

So i've installed command-line ubuntu from the ALT CD 64 bit, with the intention of building up from there and seeing what i get. I want it to do only what i want it to do (hence linux) and getting there will be a good experience for me ^.^

BUT

After installing command line linux, when it loads, my screen has a load of lines across it (as if i had bad drivers) and i cant even see the flashing line cursor. (yes, the hardware is 64bit capable - i recently installed ubuntu server 64 and desktop 64 no issues...but neither did what i wanted.)

What do i do?

Much Love,

Richard

---

### Post by SkippoGuangiacomo on 2011-07-17
I've never tried the alternate cd.. and even if what I'm going to say is ubuntu unfriendly I was very happy with how the command line interface of slackware worked... maybe you wouldn't mind giving a try to that?

---

### Post by Mark Phelps on 2011-07-17
Lines across the screen is a general indicator that there is no working Linux driver for your PC.

You need to run the following command "lspci" and look for the line containing "VGA".  Post that line here.  It will tell us what make and model video adapter you have on your PC.

---

### Post by ThePilch on 2011-07-17
Strange, there was a working linux driver for it when i installed ubuntu server and desktop, but not the alt CD.

It's an ION ITX-P-E mobo, but im afraid i cant run any commands because my screen is screwy.

Richard

---

### Post by wep940 on 2011-07-17
Try choosing the recovery option from the boot menu.

---

### Post by ThePilch on 2011-07-17
Well i'm doing a system rescue from the disc...i have no idea what i'm supposed to be doing!

At this rate, windows server is going to be the better choice for me...

Richard

---

### Post by nothingspecial on 2011-07-17
> **ThePilch said:**
>  i recently installed ubuntu server 64 and desktop 64 no issues...but neither did what i wanted.)


It's all the same difference (except for a server optimized kernel). Maybe you burned a bad disk. If you want to build up, try the minimal cd.

---

### Post by ThePilch on 2011-07-17
Is the minimal CD any different from the alt cd, save for needing to download stuff?

Richard

---

### Post by ThePilch on 2011-07-17
I installed from the minimal CD...but once it had finished installing i still have this same issue.

The screen is black, with green, blue and white streaks across it. The bottom quarter is purple.

These are all similar colours to ubuntu's colour scheme, but stretched across my screen.

Please help.

Richard

---

### Post by mastablasta on 2011-07-17
can you boot a live CD? what graphics card are you using?

---

### Post by ThePilch on 2011-07-17
Its a nvidia ION (geforce 9400)

I've booted a live cd, but it thinks i dont have ubuntu installed and asks me to do a fresh install (i want CLI only)

richard

---

### Post by mastablasta on 2011-07-18
yes but even CLI needs to display the command line on monitor so it needs appropriate drivers to do that. it seems strange that generic drivers don't work in this case. perhaps they dont' support your card. so you could try installing proprietary ones via CLI or adding a desktop and then removing it.

---

### Post by nothingspecial on 2011-07-18
Do you have another computer that will allow you to access this one over a network?

---

### Post by wep940 on 2011-07-19
If you boot the LiveCD (can't do that on the alternate disk) and use the try Ubuntu without changing your pc option, is the screen readable?  If so, then you know it is definitely a driver problem as has already been mentioned.  The trick is in getting the driver you need installed from the command line.  You really should be able to boot, even if you can read it, and then do ctrl/alt/f1 to open a terminal window.  Since the terminal is text based, it should be useable.  If not, then boot the using the recovery mode - don't try to recover from the CD - just boot to recovery mode.  *If* I remember correctly, that is purely a text-based session with no X video driver being used so that if it's a driver problem you can still boot and try to correct it.
 
So first we need to get you booted to the command line (terminal), then connect to the internet and try to download a driver.
 
If I might suggest, try putting nomodeset in the boot line in the grub menu and see if that helps.
 
Also, please post back the entire output of:
 
lspci | grep VGA
 
so we can be sure exactly of the model and chipset being used by that model.  There may be specific needs - perhaps even either the newest driver or going back 1 or 2 versions.

---

