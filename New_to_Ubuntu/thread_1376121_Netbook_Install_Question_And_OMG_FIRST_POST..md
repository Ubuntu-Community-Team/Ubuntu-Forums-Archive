---
title: "Netbook Install Question And OMG FIRST POST."
date: 2010-01-08
forum: New to Ubuntu
---

### Post by BFL DreamWorks on 2010-01-08
Hi I just got a new netbook.   An Emachine 250-1162 with the Atomic N270 CPU and a gigawoot of ram.

It doesn't have a media drive but it does have several USB ports.


Now...   This frigging Windows 7 Starter (Now with MORE FAIL) has to go.      What is involved in putting Ubuntu on a thumb-drive and installing it from the thumb-drive?

---

### Post by tom.swartz07 on 2010-01-08
> **BFL DreamWorks said:**
> Hi I just got a new netbook.   An Emachine 250-1162 with the Atomic N270 CPU and a gigawoot of ram.

It doesn't have a media drive but it does have several USB ports.


Now...   This frigging Windows 7 Starter (Now with MORE FAIL) has to go.      What is involved in putting Ubuntu on a thumb-drive and installing it from the thumb-drive?

Its really easy. Head to [www.pendrivelinux.com](www.pendrivelinux.com) to find some guides to get Ubuntu running on a USB key for you to install from.


If you have any problems, post back and Ill help!
Good luck! Congrats on giving Windows the finger! :lolflag:

---

### Post by BFL DreamWorks on 2010-01-08
My previous laptop was a dual boot IBM R40 and it was a great system until it overheated and died overnight... dunno what happened.   I had it rendering something and when I woke up it smelled burnt and wouldn't turn on anymore.      

Anyway.    The Emachine has the same CPU power as the R40,  but it can barely handle Win-7.     On top of that...   on top of that (deep breath) YOU CANNOT CHANGE THE WALLPAPER OMG RAGE UNLEASHED!!!

Seriously,  you can change colors, system sounds...    but you cannot change the frigging wallpaper!    My urge to crush kill AND destroy is rising.

I can deal with slow.   I can deal with "new" and shiny.    I cannot deal with crippling a feature as minor yet important as that.    

Time to Ubuntu the hell out of it.   *grin*

---

### Post by jr3us on 2010-01-08
> **BFL DreamWorks said:**
> My previous laptop was a dual boot IBM R40 and it was a great system until it overheated and died overnight... dunno what happened.   I had it rendering something and when I woke up it smelled burnt and wouldn't turn on anymore.      

Anyway.    The Emachine has the same CPU power as the R40,  but it can barely handle Win-7.     On top of that...   on top of that (deep breath) YOU CANNOT CHANGE THE WALLPAPER OMG RAGE UNLEASHED!!!

Seriously,  you can change colors, system sounds...    but you cannot change the frigging wallpaper!    My urge to crush kill AND destroy is rising.

I can deal with slow.   I can deal with "new" and shiny.    I cannot deal with crippling a feature as minor yet important as that.    

Time to Ubuntu the hell out of it.   *grin*

All you need to do is boot from a live ubuntu cd on a different machine, and run the System ->Administration->USB Startup Disk Creator.   All you will then need is a 1GB or larger memory stick!

---

### Post by BFL DreamWorks on 2010-01-09
Ok I have a 250 gigawoot harddrive on this netbook.    Question is,  can I partition it and set up a dual boot with Win Seven and Ubuntu or is any alteration I make going to piss off Seven to the point of non-operationalness?

---

### Post by J V on 2010-01-09
Yes, overwriting it :)

Windows isn't operational by default, so that won't be a problem... after the resize it will run scandisk and then boot, other than that you can just install ubuntu in the other space...

I suggest giving 7 enough space for OS + AV + FW + 5 or 6 games, then leave the rest for ubuntu...

2 gig swap
8 gig /
and rest in /home is the perfect setup imo...

Edit: OMG THREEHUNDREDANDFIFTYFIFTH POST!

---

### Post by BFL DreamWorks on 2010-01-09
Now will the install of Ubuntu take care of the bootloader or will I have to set that up manually.    By default I want it to boot to a menu and load Ubuntu if I don't select anything and Seven if I am drunk, stupid or have old people who are afraid of the internet using my computer (Hi mom!!).      

When I did this with XP everything was "taken care of" but then again I had the XP disk and a DVD drive... the netbook has no restore discs,  no drive and no easy way to restore it to life if my pendrive install goes bad.

---

### Post by J V on 2010-01-09
it will take care of it, by default the timer is at 10 seconds, you can install startupmanager to change that (mines at 1)

---

### Post by BFL DreamWorks on 2010-01-09
One last question,  can I trust the partition tool that runs when I install to move things around or should I presetup my partitions before installing using Partition Magic or the like?

---

### Post by tom.swartz07 on 2010-01-09
> **BFL DreamWorks said:**
> One last question,  can I trust the partition tool that runs when I install to move things around or should I presetup my partitions before installing using Partition Magic or the like?

The partition editor from the installer cd is really good.
If you need any partition editors after you install, Gparted is really really good.

---

