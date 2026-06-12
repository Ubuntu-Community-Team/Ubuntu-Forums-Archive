---
title: "Installed Ubuntu 9.04, how come it's running slower than Vista??"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by richdav on 2009-11-20
I have just installed Ubuntu 9.04 (it was a magazine cover mounted CD) on my new laptop (only 2 months old). This is my first foray into Linux and I'm a complete newbie.

Having installed without problem, when it opens a page (either an app or a webpage), it  renders the page slowly. Instead of a webpage opening near instantaneous, it takes 3-4 seconds to render or update the screen.

My laptop is Compaq Presario CQ60 running Vista Home Basic. I am running on an AMD 2.1 Ghz Sempron processor with 2GB of RAM. My graphics are on-board (I think), looking at the System Device Manager it states 'NVIDIA GeForce 8200M G'

All help massively appreciated, thanks in advance (please keep it simple, I'm a Linux/Ubuntu virgin!!)

Rich

---

### Post by philinux on 2009-11-20
System>admin>update manager. Then hit the Check button. This will update your system. After that System>admin>Hardware drivers. see if it offers to install a graphics driver for your card. That may be all that needs doing.

Dont choose distribution update.

---

### Post by jimmy the saint on 2009-11-20
How did you install it?  Are you sure you aren't running it from a the Live CD?  That will run a lot slower as it needs to load everything from a slow CD drive.

---

### Post by lotharmat on 2009-11-20
Potentially dumb question.

Have you actually installed it or just run the 'live cd' - You can tell if you this is the case by the fact you may still have an 'Install Ubuntu' icon on your desktop.

---

### Post by adaucourt on 2009-11-20
> **richdav said:**
> I have just installed Ubuntu 9.04 (it was a magazine cover mounted CD) on my new laptop (only 2 months old). This is my first foray into Linux and I'm a complete newbie.

Having installed without problem, when it opens a page (either an app or a webpage), it  renders the page slowly. Instead of a webpage opening near instantaneous, it takes 3-4 seconds to render or update the screen.

My laptop is Compaq Presario CQ60 running Vista Home Basic. I am running on an AMD 2.1 Ghz Sempron processor with 2GB of RAM. My graphics are on-board (I think), looking at the System Device Manager it states 'NVIDIA GeForce 8200M G'

All help massively appreciated, thanks in advance (please keep it simple, I'm a Linux/Ubuntu virgin!!)

Rich

Did you install any other apps that would have caused this?  Did you update your system?  I would install Karmic 9.10 if you have not done too many personalizations.  You can download it from the official Ubuntu website.  All though really you shouldn't be having any problems with the hardware you specified.

---

### Post by dca on 2009-11-20
I know people will disagree but I've found 9.10 to be more spry than 9.04 on HP laptop, judging by the CPU you'll have to stick with the 32bit install.  9.10 also offers a newer vers of Firefox.  Whatever you do, I don't suggest doing a distribution upgrade, just go to ubuntu website and download latest (9.10) desktop CD and install clean.
 
If you still have latency issues after that, go to System -> Preferences -> Appearance and last tab I think, turn off all desktop effects until it can be determined that you require a better graphics driver or maybe it's a slow network connection or maybe...  You know, gotta' try an isolate absolute cause...
 
Enjoy Ubuntu...

---

### Post by dca on 2009-11-20
Holy s***, did it take me that long to type and have five people respond before me... Geez, *apt-get installing typing tutor software*

---

### Post by coffeecat on 2009-11-20
Are you connecting wirelessly or with an ethernet cable. The slow wepage rendering may be down to wireless issues. Most wireless chipsets work just fine, but a few have buggy drivers.

If you are connecting wirelessly, open a terminal (Applications > Accessories) and post the output of:

```
sudo lshw -C network
```

---

### Post by richdav on 2009-11-22
Thanks for the suggestions, much appreciated. Not had chance to test them yet, but will let you know.

Rich

---

