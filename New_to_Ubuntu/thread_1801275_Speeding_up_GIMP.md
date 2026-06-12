---
title: "Speeding up GIMP"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by stalkier on 2011-07-10
Ok I am running the latest stable release of GIMP in the repos. It loaded at a reasonable speed. Afetr I imported my brushes into the .gimp/brushes folder it takes forever to start up. After doing a bit of research I came across an older post on a different website.

> The GIMP takes too long to load - how can I speed it up?

The main things are to make sure you are running at least version 1.0, and make sure you compiled with optimization on, debugging turned off, and the shared memory and X shared memory options tuned on.

Or, buy a faster system with more memory. 8^)

If it's still too slow for you, the easiest speedup is to invoke the GIMP with the "--no-data" option. This prevents the GIMP from loading patterns, brushes, and similar resources when it starts. You may benefit slightly from the "--no-splash" option as well; you might want to time that one to see if it really helps enough to be worthwhile.

On a Dell 100MHz 486 server box, the GIMP comes up in the following times:
Command	Time
gimp	18 seconds
gimp --no-data	11 seconds
gimp --no-data --no-splash	8 seconds
gimp --no-splash	16 seconds 

Obviously it is stating version 1. I was wondering how I can speed it up on a AMD Athlon XP+ 2.19 GHrz, 1GB DDR, 80GB hdd, 128MB AGP NVidea card. I know its an older system, but I use it sometimes to do editing on photos. Please help if posible. Thanks.

---

### Post by I2k4 on 2011-07-11
Hate to say it, but I'd be suspecting 11.04 is too slow for your older machine.  I tried it on my Atom netbook and went back to Lubuntu 10.10 (on live USB).

I'm running GIMP 2.6 with UFRaw, all the documentation and the extra brushes from the Synaptic repository, and it loads in under 10 secs.

Your complaint seems to be about boot time rather than processing time for large image files:  on that, you'll find various tweaks in Edit > Preferences to reduce or increase resource demands.  A good old Photoshop trick is to set the Folders Temp and Swap caches to a fast external drive instead of the HDD.

---

### Post by LowSky on 2011-07-11
That is an older system, not much you can do but maybe switch to classic mode, or even xfce or lxde to save some resources.

Other options are using a lighter program for editing like Shotwell or F-Spot. Especially if it is just simple editing. while away from your better machine.

---

### Post by stalkier on 2011-07-11
I'm running the machine in classic mode. The only thing that I am concerned about is the startup time of GIMP. It processes fine etc. Plus I understand the machine is old, I have a lot of patience and understanding with these things. (It was free after all) :) But is there a way that I can eliminate the loading of documents, splash, etc. Ive been using Linux a long time but I never remember the commands etc. 

Thanks for the help guys.

---

### Post by AlphaLexman on 2011-07-11
Try this:
```
gimp --no-data --no-fonts --no-splash
```

---

### Post by stalkier on 2011-07-13
> **AlphaLexman said:**
> Try this:
```
gimp --no-data --no-fonts --no-splash
```

If I type with in the terminal or ALT + F2 once will it start like that from then on out? If not, how would I set it up to?

---

### Post by Blojic on 2011-07-13
> **stalkier said:**
> If I type with in the terminal or ALT + F2 once will it start like that from then on out? If not, how would I set it up to?

No. You could create a launcher to do it though. Right-click on the icon and select "add to panel". Right click on the launcher in the panel and select "properties". Then you can add --no-data --no-fonts --no-splash into the "Command" dialog box.

BTW, it didn't seem to make any appreciable difference to GIMP start-up time on my machine - both about 8 seconds (Duron 1400Mhz, 512MB RAM dinosaur).

---

### Post by I2k4 on 2011-07-13
I'd suspected Blojic's conclusion - that it seems doable by altering the command line in the icon "Properties" dialog.  Haven't tried it. 

Also note that at section 1.3 of the GIMP 2.4 Help manual there is a long list of command line alternatives, including the three above.  Some others might affect the boot up.

---

### Post by jtarin on 2011-07-13
Adding brushes to your home folder adds boot time. I would have just placed them in /usr/share/gimp with the others.(with correct permissions).

---

