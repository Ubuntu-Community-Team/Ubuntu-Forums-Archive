---
title: "Ubuntu crashing ALWAYS after left untouched for a while"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-09
Hi all and thanks in advance for your kind help!
I have a problem regarding Ubuntu crashing all times when I leave it untouched for some time, while downloading for exemple.
It is a fresh install and I reinstalled it cause of this issue, I thought I did something wrong...
Any clue?
(sry if I dont answer straight away, it's very late night here and I'm soon going to sleep...be right back 2morrow for your answers!)
Ty, ty & t-y!

---

### Post by LowSky on 2009-09-09
you wont get much help because we need a bunch of information.

For instance..
what Kind of computer, and as much knowlege you have of the parts inside it, like what type processor, the amount of RAM, and how old it is.

what are you running when it freezes, how long has it been on for? what settings are you using for power management, and thats what I can think of off the top of my head.

Best thing is to run the mem-test from GRUB or a LiveCd to test your computers ability

---

### Post by webwiller on 2009-09-09
The PC is a notebook Hp6730s, very new one, with 2core processor intel core2duo 1.9mhz, 4gb of ram, when it freezes it normally rums just a download manager, JDownloader, and sometimes I forget Mozilla Firefox on.
That's it.

---

### Post by mcduck on 2009-09-09
Since it crashes when idle it must be related to something the system does when idle. Are you using a screensaver? Some of the screensavers use OpenGL and that might be a problem (enough to crash the desktop) if you have a low-end graphics card or some problems with graphics drivers, for example. In that case make sure you've selected a screensaver that definitely works instead of random screensaver. Or disable the screensaver completely, it's not really saving your screen anyway, quite the opposite. :)

Apart from that it's hard to say. At least without knowing more details about how the system crashes (as in does the whole system freeze or reboot, or does X crash and throw you into login screen..). Still, you might find something related if you search the log files in /var/log and try to find what happened immediately before the crash.

---

### Post by webwiller on 2009-09-09
Attached you find my screen preferencies.

Anyway yes, I used to run a screen saver with last installation but I did not put on one with the fresh one, and ubuntu does not came with one already on!
The PC just freezes, I get the last image I had on screen and nothing at all moves, nor mouse, niether anything else!
I have to keep on/off button pushed for few secs to reboot it.

---

### Post by Zimmer on 2009-09-09
Check your POWER MANAGEMENT settings

Set 'put computer to sleep after...'.  to NEVER , and see if that stops your 'freezes'

---

### Post by webwiller on 2009-09-13
I did set power management options about "put the computer to sleep" on NEVER.
I also turned off all screensavers.
I found out that turning off all 3D desktop animation (compiz-config settings manager=OFF) does help.
I do get troubles with 3D animation also while reproducing a movie. Is that normal? Do I have to cope with these troubles all time?
I do love Ubuntu, and since I tried first time I never log into WinXP again. But with these troubles upsetting me quite often I do ask myself if its just my fault, cause I dont know how to configure Ubuntu properly for my needs...or if Windows is just more "deisgned for" the actual needs of a home user.
Which is which???!!!

---

### Post by SuaSwe on 2009-09-13
In my opinion, Windows is designed for the unimaginative, uninquisitive user. ;)

If disabling 3D effects alleviates the issue (partially or completely, by the way?) it's definitely starting to sound like a graphics problem. What graphics card + drivers are you using, and have you checked if the drivers can be upgraded? Have you checked your system logs to see if there are any clues to be had from them?

---

### Post by K7522 on 2009-09-13
I had this issue on a fresh install of 9.04 64 bit and as you said, disabling all of those things had no affect. I am not 100% sure what happened to resolve the issue, I'm running nVidia's 180 drivers at the moment.

I would suggest doing ```
sudo apt-get update
sudo apt-get upgrade
``` to see if updating all of your packages resolves the issue.

---

