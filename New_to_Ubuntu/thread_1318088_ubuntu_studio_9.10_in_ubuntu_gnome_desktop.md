---
title: "ubuntu studio 9.10 in ubuntu gnome desktop"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by parminder_mangat on 2009-11-07
hello frnds i am going to install ubntu 9.10 . I want to use ubuntu studio too. can i download ubuntu studio on my ubuntu desktop, as we install KDE on gnome. if yes, is there a way to download it separately and install it my ubuntu gnome. Thanx.

---

### Post by quickdraw on 2009-11-07
Forgive me for sounding rude, but why not just download and install Ubuntu Studio from the get go? I suppose I don't understand the question fully, or why you would need to run Ubuntu Studio "within" Ubuntu.

---

### Post by parminder_mangat on 2009-11-07
does ubuntu studio has all the features of ubuntu gnome?

---

### Post by Shpongle on 2009-11-07
as far as i know it does its just apps and the theme that are different i think

---

### Post by parminder_mangat on 2009-11-07
which apps are different does it has all app of ubuntu 9.10 like empathy, openoffice, firebox etc.

---

### Post by dkh503 on 2009-11-07
> **quickdraw said:**
> Forgive me for sounding rude, but why not just download and install Ubuntu Studio from the get go? I suppose I don't understand the question fully, or why you would need to run Ubuntu Studio "within" Ubuntu.


The main reason I for one resist full-on ubuntustudio installs is that it sucks at detecting my wireless network card. I have installed vanilla Hardy, Intrepid, and Jaunty and they never had a problem detecting my wireless; just reboot and start surfing. I recently experimented with the live vanilla Karmic CD, and yep, it too detects my wireless.  But in the past, the unbuntustudio packages refuse to recognize this very same card, and it is a pain because, even after the tedious installation process, I still need to go out and get the various updates, and there are a number of command line programs I like to use that I need to download via synaptic, which of course is impossible if I can't actually get on-line. And since u-studio doesn't have a live CD, I can't experiment beforehand. So, I have had to install vanilla Ubuntus, then load in the unbuntustudio modules on top. Be forewarned, I am battling Karmic to force this to work, and as far as I can tell, it never actually will. So I am contemplating a full-on u-studio install but I am dreading the thought of wasting any more time on this project. (see my posts re: no sound under Karmic, as well as those of many many others who can't get the new version to work properly either.)

The latest karmic version of u-studio indicates that the standard netmanager app is included in the package (tho not loaded by default). Does anyone out there know if this is actually true and does it actually work?

dave

---

### Post by snowpine on 2009-11-07
Open the Synaptic Package Manager and search for "ubuntustudio". There are metapackages to install the audio apps, audio plugins, video apps, etc. You can install these packages within a "regular" Ubuntu install. You might also want to install linux-rt (the real time kernel) if you need it for low latency audio production.

---

### Post by dkh503 on 2009-11-07
> **snowpine said:**
> Open the Synaptic Package Manager and search for "ubuntustudio". There are metapackages to install the audio apps, audio plugins, video apps, etc. You can install these packages within a "regular" Ubuntu install. You might also want to install linux-rt (the real time kernel) if you need it for low latency audio production.


On paper, this is a great idea. Unfortunately, Karmic appears extremely buggy with regard to audio. Check out the support forums before doing this; you will see I am not the only one having problems. If you have a windows or mac box to do your serious recording work, go ahead and experiment with another PC and see if you have better luck than the rest of us loading ubuntustudio audio packages into a standard Karmic install (or God forbid, a Karmic upgrade of Jaunty). Meanwhile, I am going back to n-Track under Vista until this situation improves, I have stuff to do.

dave

---

### Post by parminder_mangat on 2009-11-09
actually i don't want it for production purposes i thought ubuntustudio may have good music and video players so i wanted to give it a try.

---

