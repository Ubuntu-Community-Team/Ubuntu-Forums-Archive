---
title: "How do I disable the idle desktop dimming"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by KinKiac on 2009-07-17
Hello.  Ive just recently switched to ubuntu(sort of, I have a dual boot so my GF can still have her windows) and so far Im loving it.  I do have one problem though.  Im not a fan of the desktop dimming when the computer is idle.  Im finding that when I watch movies about every 30 minutes or so the player switches from fullscreen to windowed and the idle dimmer starts dimming the screen till its black or I hit a button or move the mouse.  Its quite a pain.  Im using an HDTV for my monitor and I normally dont use screensavers or power management/sleep mode settings.  If the monitor is on, Im using it, if Im not using it, the montitor gets powered off manually by me or my GF.  Thats my power management.

  Also, Ive installed the screesaver plugin for compiz, so I want to be able to utilize that without the entire screen going black on me.  Id rather turn on my monitor to see the cube spinning on the desktop than to a black screen.  Id also like it to be able to be left as a kind of display mode so that when I have friends over they will see it and go "wow thats cool" and then Ill go "yeah, this is what you can do when you switch to Linux."

Anyway, Ive tried going into the power settings and Ive set everything I can find to Never, but it just keeps doing it.  Im not sure if Im going into the right place for this setting or not though, Ive even been looking all through compiz to see if there is anything in there that might be controlling this feature but cant find anything, although I dont think it is part of compiz anyway.  

Any help would be greatly appreciated.

Thanks
Kin'

(EDIT) Also I forgot to mention Im using jaunty 9.04

---

### Post by unutbu on 2009-07-17
Open a terminal (Applications>Accessories>Terminal) and type
```

xset -dpms
```

This turns off DPMS (Display Power Management Signaling).
If it works during your current session, you can make it permanent by adding this command  to the list of commands run when you begin a GNOME session. You do that by clicking System>Pref>Sessions.

---

### Post by Raynman37 on 2009-07-17
You can go to System > Preferences > Screensaver then click on Power Management and put "Put display to sleep when inactive for" to Never.  I think that should do it.

---

### Post by KlytusLord on 2009-07-17
In Power Management, there is a checkbox that controls dimming while idle.  You have to uncheck it for each power type, AC Power and Battery Power.

This is NOT the slider that ranges from minutes to never, it is just a small checkbox at the bottom of the Power Management window.

---

### Post by KinKiac on 2009-07-21
Thanks for the help guys.  I ended up getting it to work but none of the suggestion worked exactly as stated.  The xset option didnt work, even for my current session.  I ended up going into my screensaver and setting it to regard screen as idle after 2 hours and that seemed to do the trick.  


> **KlytusLord said:**
> In Power Management, there is a checkbox that controls dimming while idle.  You have to uncheck it for each power type, AC Power and Battery Power.

This is NOT the slider that ranges from minutes to never, it is just a small checkbox at the bottom of the Power Management window.

I dont see that checkbox in my settings.  Is it possible I may need to update my power management app?  Ive seen screenshots showing what other people power management screen looks like and I dont have most of the options they do.  Is this something due to my hardware or do I just need to update something?

---

### Post by KinKiac on 2009-08-01
Ok, so I managed to fix my issue, although i still dont have all the options in my power management screen as are cited by others in this thread.  I ended up having to go to my screensaver settings, set it to not come on for a ridiculous amount of time, 200 minutes or something like that(there was no "never" setting) and then acess my power management screen from there and did the same and I havent had a problem since.  

Thanks to everyone who responded for the help! :)

---

