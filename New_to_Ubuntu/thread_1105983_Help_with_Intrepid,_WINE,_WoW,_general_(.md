---
title: "Help with Intrepid, WINE, WoW, general :("
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Malacki on 2009-03-25
Okay, Windows XP died on me, so I decided to try out Ubuntu.  I'm not new to computers, way back when it was relevent I was MS Certified in Dos 6.x and Windows 3.1x.  I know my way around a command prompt and computers in general.  Ubuntu has me semi stumped, and I think it's just unfamiliarity with the OS.  I keep having crashes when I try to add or remove software.  It took me three tries to do the recommended updates after initial install (something like 287 updates).  I installed WINE to try to run WoW, and WoW keeps crashing when I launch it.  I don't get to the log in screen or anything, it just crashes on me.  I tried uninstalling WINE figuring I would get one of the other recommended emulators, and WINE has been uninstalling itself since 2330 last night (it is currently 0940).

So far, I've been following the 'getting started' and 'running WoW' guides and all that, and nothing is working for me.  The repetitive system crashes are more irritating to me than the WoW problems.  I have no idea where to go from here, or how to even try to figure out what is causing system crashes.  Any guidance that you kind folks could offer would be greatly appreciated.

Specs at a glance -

AMD Athlon X2 64 bit processor
4 gig RAM
Ubuntu 32 bit installed on IDE 250 gig HDD
Everything else on SATA 500 gig HDD
XFX PVT84JYDF3 GeForce 8600 GT 512MB 128-bit GDDR3 PCI Express x16 with recommended Ubuntu drivers
ASUS motherboard

---

### Post by UbuntuNerd on 2009-03-25
are you uninstalling "Wine" from add/remove programs or synaptic package manger?

---

### Post by Malacki on 2009-03-25
> **UbuntuNerd said:**
> are you uninstalling "Wine" from add/remove programs or synaptic package manger?

I think the first one, but I'm not 100% certain.

---

### Post by Malacki on 2009-03-25
Any thoughts from anyone?

---

### Post by decoherence on 2009-03-25
Yeah, if you're getting regular crashes, something is very wrong. Can you describe the crashes that happen when you try to run the updates? Does the Add/Remove program die? Does the mouse lock up? Does the mouse stay responsive but the rest of the system goes braindead? If you type Ctrl Alt F1 do you get a command line? (Ctrl Alt F7 to get back to the GUI) If you hit Caps Lock, does the light come on on the keyboard?

The specific behavior of a crash often gives you significant clues as to its cause (or at least, where to start looking for the cause)

Also, log files are located in /var/log. /var/log/messages would be a reasonable place to start, i think.

---

### Post by PriceChild on 2009-03-25
There is official Ubuntu documentation for installing and playing wow at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by odinb on 2009-03-25
Have you tried these 2 commands?

Fix minor errors in install:
sudo dpkg --configure -a

Fix broken packages in install:
sudo aptitude update && sudo aptitude upgrade

They have helped me on several occasions when my installs/uninstalls got stuck.

---

### Post by Malacki on 2009-03-25
@Deco - Normally the system just locks up.  I haven't tried any of the Ctrl-Alt combinations, I didn't know what they were.  Generally, the only way I've been able to recover from them was to power cycle.  Total system lock up.  When I left my PC this morning, it was still sitting at Add/Remove, NumLock was responsive, the mouse cursor was responsive, but nothing else was.

@Price - Thanks, I've been trying to follow that, and I have most of it printed out for reference.  However, it doesn't seem to address the problem I'm having with WoW, or the problems I'm having with Ubuntu updating.

@Odin - I've used 'sudo dpkg --configure -a' with some success.  I have no idea what it's doing, but it seemed to work.  Had to do it two or three times to get all the updates to install.  Is 'sudo aptitude update && sudo aptitude upgrade' used as all one line?

---

### Post by odinb on 2009-03-25
> **Malacki said:**
> 
@Odin - I've used 'sudo dpkg --configure -a' with some success.  I have no idea what it's doing, but it seemed to work.  Had to do it two or three times to get all the updates to install.  Is 'sudo aptitude update && sudo aptitude upgrade' used as all one line?

Yep, one line!

Also, for Intrepid you should use "safe-upgrade" instead of "upgrade", so the line would be:

sudo aptitude update && sudo aptitude safe-upgrade

No harm in running the old one, but it will tell you to change.

The 'sudo dpkg --configure -a' basically configures the packages after install if needed. Normally the install/update takes care of this.

---

### Post by Malacki on 2009-03-25
Update 2: Found a solution for this error on Ubuntu Forums.  Fixed WINE, ran WoW.  Tried to make Ventrilo work.  Tried to configure extra buttons on mouse.  Something broke, WoW won't run anymore. :(

Update: Tried the suggestions.  Here is the result.  This same error message returned through Synaptic when I tried removing & reinstalling Wine.

user@computer:~$ sudo dpkg --configure -a
[sudo] password for user: 
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
user@computer:~$

---

