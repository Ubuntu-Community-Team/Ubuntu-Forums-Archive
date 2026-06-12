---
title: "An issue with Ubuntu and right clicking wine windows."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Kinglink on 2009-07-22
Hey guys.  First I have to say Ubuntu is the perfect Linux variant in my opinion.  I ran linux about 5 years ago in college and while I got into it, I never found a variant that I would recommend to anyone outside of other computer science majors.  Ubuntu changed my mind on that.

Anyways Here's an issue I'm having, and I've been having a problem googling it.   When I right click in World of Warcraft and move my mouse left and right to look around, the world starts having graphical issues, if I use the a and d keys to look around the game performs normally.  When I'm running Diablo and I alt click (or is it alt right click) Ubuntu grabs the window and tries to move it.  Basically it looks like Ubuntu is trying to do some advanced mouse commands but I really don't want that to happen.  So what's going on here?

I am running Wine like I mentioned, but I didn't see any configuration under the winecfg to set this up so I'm imagining it's the Linux OS underneath trying to do something.  Any idea what might be getting in my way here?

---

### Post by AndThenWhat on 2009-07-22
Alt+Click+Drag moves windows. I think you might be able to turn it off in Compizconfig-settings-manager. As for the World of Warcraft problem, if it is really a big issue to you then you could installing a different version of WINE to see if that fixes the problem.

---

### Post by NightwishFan on 2009-07-22
Try to run wine ignoring the window manager. The option to do so is under graphics in winecfg.

Also check the app database for any fixed or tweaks. Good luck!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)


EDIT: Please disable compiz when running opengl apps. It might save you some trouble.

---

