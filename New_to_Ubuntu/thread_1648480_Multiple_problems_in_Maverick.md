---
title: "Multiple problems in Maverick"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by shadowmane on 2010-12-18
First off, I'm an Ubuntu newb.  I've been on Windows XP for the last two years on a laptop.  Before that, I ran SuSe.  In fact, I tried SuSe 11.2, but couldn't get it to get my wireless card (on my desktop, not my laptop) going, so I ditched it.  I have Maverick on an AMD Sempron 2800+ desktop.  I can't remember what the 3d card is, but its Nvidia and it detected the drivers.  The wireless card (in case your wondering) is a netgear wg311v3.

Now, I have multiple problems that have developed, and they did it on two different installs (yes, I have reinstalled and am still having the same problems).  First of all, Firefox regularly crashes on me.  I can only get the update manger working half the time, the other half, it crashes on me.  I can't get Synaptic Package Manger to work but half the time.

I took the base system, and installed the non-oss codecs.  I installed openBVE.  I also tried to install chromium, but it crashed in the middle of installing it, and hasn't been the same since.

I've used the sudo fixes and the dpkg fixes:

> sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a
sudo dpkg --clear-selections
sudo rm /var/cache/apt/*.binSometimes they allow the update manger to run, others, they don't.  And now, Nautilus don't even work.  I need some help troubleshooting my system to try to correct whatever is mucking things up.  I really want to enjoy Ubuntu, but right now, Maverick, for me, is a buggy monster.

---

### Post by shadowmane on 2010-12-19
bump

---

### Post by admiralspark on 2010-12-19
Have you checked the CD integrity? When you boot from the install CD, use the option "check cd integrity".
If that checks out, it's possible that the .iso itself was bad. You can check the md5 hash against the known good to see if that's the problem.

---

### Post by Hippytaff on 2010-12-19
Hi and welcome!
Might be worth reburning the iso at the slowest speed once you've chcked the md5sum as suggested above. As far as the wireless goes can you post the output of
```

lspci

```

---

### Post by shadowmane on 2010-12-19
CD integrity checked out.  I actually checked the md5sum before I used it.  And the wireless isn't the problem.  I got that working with ndiswrapper.  For some reason, chromium was hanging up on me.  I finally went in and deleted the .deb file by typing

```
sudo rm /var/cache/apt/archives/chromium-browser_8.0.522.224`r68599-0ubuntu0.10.10.1_i386.deb
```Then I put in ```
sudo apt-get clean
``` then ```
sudo apt-get -f install
```It actually finished the hung install.  Now the problem continues to be that firefox crashes on me regularly, as well as the computer freezing up completely from time to time.  Its only been about 30 minutes since I did that, and the system seems to be stabilizing.

edit:  Actually, I did a little more.  I had to use gedit to change the version of gstreamer from -2 to 2 before it would work.  ```
sudo gedit /var/lib/dpkg/status
```  I forgot about that step.

---

