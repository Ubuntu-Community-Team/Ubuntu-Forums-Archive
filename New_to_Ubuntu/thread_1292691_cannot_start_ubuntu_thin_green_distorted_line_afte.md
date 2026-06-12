---
title: "cannot start ubuntu thin green distorted line after splash screen."
date: 2009-10-16
forum: New to Ubuntu
---

### Post by scrypt on 2009-10-16
Hi All.

I have made a bit of A mess of my Ubuntu installation.

I can NO longer boot into it.

I get past the ubuntu splash screen and then I am just met with a thin distorted green line and then my system seems to freeze.

I have A ATI3650HD graphics card.

Is there anyone who can help me to fix this please??

---

### Post by dvlchd3 on 2009-10-16
Did you recently install proprietary drivers?  It sounds like a graphics driver issue.

If you press Ctrl+Alt+F1 do you get a text login screen?

---

### Post by scrypt on 2009-10-16
I think you are right.

when I pressed cntrl-alt-f1

I got a distorted multi coloured screen and I could only get back with cntrl-alt-f7

---

### Post by HarrisonNapper on 2009-10-16
Boot in to recovery mode and auto-fix graphics problems. Make note of the name and location of the backup file. Might also want to dpkg just in case ;-)

---

### Post by scrypt on 2009-10-16
I have booted into recovery mode but for some reason there is NO option to repair XORG.

Is there another way to do this from the recovery console??

---

### Post by krazyleaf on 2009-10-16
I have the same problem. When you boot into recovery do you have a line item "Fix graphics Problem". It should be the last line item.

---

### Post by scrypt on 2009-10-16
Not exactly.

I dont see that error.

I dont get the option to repir Xorg automatically like older ubuntu disro's recovery mode used to offer.

---

### Post by scrypt on 2009-10-17
Im still struggling to find a fix to this can anyone help me out??

If I run Compiz and sudo aticonfig --initial.
I get this error:

mark@tiple2009-laptop:~$ sudo aticonfig --initial
Could not find configuration file, so create an empty one
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
mark@tiple2009-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by sandyd on 2009-10-17
i have the same green line.
however, if i wait a while, i get to the login screen.
see if waiting a while works.
(im using the drivers from envyng)

---

### Post by scrypt on 2009-10-17
Hi carlee.

you seem to kknow what you are talking about

so can you help me fix this, its getting in a bit of a mess.

when i start ubuntu i get this error message :

Screen isnt compozited. Please run Compiz(Fuzion) or any similar compozite manager.

If I run compiz from my terminal I get this :

mark@tiple2009-laptop:~$ sudo compiz
[sudo] password for mark: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: xterm 
no xterm found, exiting
mark@tiple2009-laptop:~$ 


this all stems from me trying to get my mousepad moving on my Dell Studio 1737.

i cannot even install the ATI propriet driver fron system-administrator-Hardware drivers.

the option to install the driver is no longer there

???????????????

---

### Post by sandyd on 2009-10-17
> **scrypt said:**
> Hi carlee.

you seem to kknow what you are talking about

so can you help me fix this, its getting in a bit of a mess.

when i start ubuntu i get this error message :

Screen isnt compozited. Please run Compiz(Fuzion) or any similar compozite manager.

If I run compiz from my terminal I get this :

mark@tiple2009-laptop:~$ sudo compiz
[sudo] password for mark: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: xterm 
no xterm found, exiting
mark@tiple2009-laptop:~$ 


this all stems from me trying to get my mousepad moving on my Dell Studio 1737.

i cannot even install the ATI propriet driver fron system-administrator-Hardware drivers.

the option to install the driver is no longer there

???????????????

seems that you screwed up your xorg.conf in some way.
normally, i would tell you to post the contents, but since your having so much trouble, and youve done so much stuff to it...
```

sudo dpkg-reconfigure xserver-xorg

```

and its supposed to be 
```

compiz --replace

```
not ```
compiz
```

if that doesn't work, try
```
metacity --replace

```(that is, assuming your using gnome)

---

### Post by scrypt on 2009-10-20
Hi carlee..

I ran the commands but when i ran the
"compiz --replace"
 command i was given this error:

laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by HarrisonNapper on 2009-10-21
> **scrypt said:**
> Hi carlee..

I ran the commands but when i ran the
"compiz --replace"
 command i was given this error:

laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

If your video card was working before on the same driver, my suspicion would be the hardware itself. Have you checked the card to make sure it's seated securely in the slot, fan isn't broken, etc. compiz isn't finding what it needs from the card and changing your window manager isn't necessarily going to fix graphics problems.

Also, if you haven't already, check Administration>Hardware Drivers to make sure you have your (where applicable) restricted driver enabled.

Cheers.

---

### Post by patjcompton on 2009-10-22
Script-
I have the same computer vid card as you and my video also just went haywire the other day.  
 
Question for you since we have the same vid card: Have you had problems expanding videos to full screen or even maximizing?
 
Even when I was able to start Ubuntu, if I maxed the player or heaven-forbid went fullscreen the video would freeze no matter which player I was using.  If I installed a DVD I'd end up having to do a hard shutdown by holding in the power button.  I have ATI proprietary drivers installed btw.
This is the problem I was attempting to fix when things turned much much worse.
 
I don't even get to the splash screen and instead of a thin green line like you, I have a three inch thick band across the top of the screen that looks a lot like those 'Magic Eye' 3D posters from back in the day.
 
I remember I had been doing something with xorg when this all started.  
 
It's not a hardware issue because I can still run with Live CD like a champ (plus I dual-boot Vista with no issue), but I'm so new I don't know how to make changes to my installation from there.  I'm a _complete_ newbie.  Haven't been running Ubuntu for much more than a month yet, so I'm completely at a loss.
 
 
Anyways, I'm rambling...

---

### Post by patjcompton on 2009-10-25
All fixed for me!


Try running this from Terminal:

```
 envyng -t
```choose option #4 to uninstall your ATI driver and then #6 to reboot (I don't actually know if rebooting is required, but it's what I did)

Back to Terminal:

```
envyng -t
```choose to option #3 install ATI driver and #6 reboot again


Seems almost too simple right?  Well is it.  I had to do it many times.  At first I was able to log in to an all white screen minus a thin black bar near the top and bottom of the screen right below and above where my panels are supposed to be.  Eventually I was just able to get to my desktop and it's full up.  Everything's working as it should now.

I was also using envyng -t to restart Xserver (although I have no clue what this is).
I was also booting into Recovery and selecting "attempt to auto fix video problems".

---

