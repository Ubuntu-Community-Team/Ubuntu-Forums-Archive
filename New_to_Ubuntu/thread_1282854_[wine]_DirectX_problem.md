---
title: "[wine] DirectX problem"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by Alpha C on 2009-10-04
I know you all probably get sick of everyone asking the same (or similar) questions over and over, and I'll apologize up front about this one.

I'm trying to run an old game of mine (Star Wars Rogue Squadron 3D) and it installed fine on Wine, but when I try to run it through the launched, it tells me that DirectX needs to be installed, so I click through the options and install it, go back to the launcher and it tells me that DirectX needs to be installed yet again. 

Sorry to be a complete noob, just wondering if anyone could help me out with this problem.

---

### Post by tuxxy on 2009-10-04
Have you tried Wine-HQ, they should have some information on this game.

---

### Post by Mark Phelps on 2009-10-05
If you're running version 1.2.0 of the game -- you're out of luck.  It simply won't work. Version 1.3.0 get's a slightly better rating -- but not much.  See the CodeWeavers Application Compatibility db link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3258]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3258")

---

### Post by Thelasko on 2009-10-05
Don't install DirectX in Wine!  Wine has DirectX compatibility built in.  Installing DirectX in Wine breaks it!

---

