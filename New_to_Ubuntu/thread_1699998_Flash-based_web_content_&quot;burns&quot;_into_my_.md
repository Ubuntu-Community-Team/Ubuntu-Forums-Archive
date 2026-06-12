---
title: "Flash-based web content &quot;burns&quot; into my screen"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by diablo75 on 2011-03-04
I'm using the term "burn" to mimic what used to happen on old CRT monitors when you left the same image on them for days; that image would literally burn into the screen.  So I don't mean it literally; there's some glitch happening that causes instances of former flash media to stick on the screen, even after I close all instances of Firefox.

I am running 10.10 32-bit with Firefox and Flashaid, and I have Compiz disabled.  Enabling compiz didn't solve the problem.  I've also found that if you take a screenshot, the image captured looks normal without the glitch.

Any ideas what might cause this or how to fix it?

---

### Post by bigwest on 2011-03-07
I'm getting the same issue on my media center with mythbuntu 10.10. Have you found a solution?

---

### Post by diablo75 on 2011-03-07
Nope.  I rarely use Ubuntu any more (usage habits have changed a lot in the last 6 months or so) and I rarely boot into it any more.  Probably just reinstall it down the road after 11.04 comes out.  I don't know if I'm going to like the new Unity interface though...

---

### Post by oldos2er on 2011-03-07
Not sure, but check you're using the latest video drivers for your video card.

I used to see this problem occasionally with Gnome, mainly menu artifacts left onscreen, but since I've switched to KDE, it hasn't happened at all. Whether that's in any way related to your problem, I can't say.

---

### Post by diablo75 on 2011-03-07
According to Additional Drivers Manager (jockey) I am using the "recommended" version (whatever the heck that is; you'd think it'd say, the way it does for the implied "not recommended" version it has listed right next to it).

I'm running with a nVidia GeForce 9600 GSO.

---

### Post by tgm4883 on 2011-03-07
Are you sure it's flash content and not just any high contrast image that is left on the screen? 

Does the "burn in" disappear after a few days?

I ask, because it may be the display. I have the same issue on my Xbox 360.

---

### Post by diablo75 on 2011-03-07
> **tgm4883 said:**
> Are you sure it's flash content and not just any high contrast image that is left on the screen? 

Does the "burn in" disappear after a few days?

I ask, because it may be the display. I have the same issue on my Xbox 360.

As I said in the OP, I don't mean that the image is literally "burned" into the LCD screen that I'm using; my monitor has nothing to do with this.  This is video being sent to the screen that is a remnant of flash content that was on the screen just moments before.

Another way of describing it is... You know how in some operating systems it's possible to tell a window to "Always be on top"?  That's what this is.  It's junk data in X that's being sent to the video card as if it's suppose to be on the screen when it's not.  So I could scroll something up and down in a web browser but there will be this box of stuff that came from a flash object that is a copy of where it came from that stays in place on top of EVERYTHING else.  You scroll up and down and the parent object this thing came from will move but this "always on top" static image that was duplicated from the first frame will remain in the way.  Resetting the computer is the only way to clear it out.  This has never happened in Ubuntu before and I has not happened in Windows at all.

---

### Post by Deeack on 2011-03-08
Hey, I was having the same problem it just started recently I left it thinking it was a wide spread bug that would be fixed in an upcoming patch but apparently not everyone's getting it.

The solution may be to remove the flash plugin and reinstall it, I've just literally done it myself and loaded a few youtube videos up and I'm not getting the problem any more however when it happened it was seemingly random so I may just not have been able to recreate the bug yet.

sudo apt-get purge flashplugin-installer
reboot (probably not necessary but I did it anyway)
sudo apt-get install flashplugin-installer

I hope it fixes the problem for you as well as me! Next to find out why flash isn't working in chromium at all! :P

Good luck!

---

