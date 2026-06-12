---
title: "Turn off Compiz in 11.04"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by vtnick on 2011-05-17
Hey guys,

I wanted to upgrade to 11.04 and its unity desktop, but for one of the programs I use frequently, Abaqus CAE, compiz and metacity compositing must be disabled while it is running. Currently in 10.10 and 10.04 I could just use metacity compositing and have panel buttons to turn it on and off when I needed to run the program. Is there any way to do this in 11.04? From what I have read unity is built on compiz so this might be a mute point. I just don't want to upgrade and have things not work and have to downgrade. Thanks for the help.

---

### Post by r-senior on 2011-05-17
You'd have to log out of Unity and back in to "Classic No Effects" desktop at the login screen. Out of the box, Unity-2D should work too.

---

### Post by ridgeland on 2011-08-26
Thanks.
I switched to Classic then expected to find
Visual Effects
in Menu -> System -> Preferences -> Appearance
Its not there.
Using Synaptics to remove Compiz will take out Unity.

I don't see any way to run Unity without Compiz or to turn the Compiz setting to None like in 10.10

Compiz was causing jerky motion on my HTPC running MythTV in high def.  Using Ubuntu Classic (no effects) solved it.

---

### Post by LowSky on 2011-08-26
you need to use ccsm

there is a box called legacy mode that you need to check.. sorry i'm drawing a blank on the step, and I'm on Windows at the moment.

---

### Post by Frogs Hair on 2011-08-26
If you want to run Unity with out effects you will have to install Unity 2D from the software center . Unity 3d is a Compiz plug-in . You can also run Ubuntu no effects by selecting it from the session list below the greeter box at login . You may want to wait for LowSky because I don't see the option in Compiz that he/she wrote about .

---

### Post by ridgeland on 2011-08-26
Thanks again.

In Synaptics I found ccsm - Compiz Configuration Settings Manager.  I launched if from the terminal and turned off the effects.  MythTV is better, still not as smooth as without Compiz so I'll play some more with the settings.

Unity - No effects --- Does not exist in login window settings or at login screen.  Only Ubuntu Classic (Gnome) has that option.

I installed Unity 2D.  Now the HTPC seems smooth.  Compiz was number two in CPU using TOP with Unity 3D.  Now it's not running.  Thanks.  But now a new issue for another thread - with Unity 2D I cannot drag an item (i.e. MythTV) from the applications window over to the vertical panel (dock?).  With Ubuntu (Unity) it was just a click and drag.  Oh the joy of relearning.  

For now I'll just stay with Classic (Gnome) with visual effects turned off.

---

### Post by Frogs Hair on 2011-08-26
Ubuntu no effects is on the session list (Gnome no effects) , but not Unity is not .

---

### Post by ridgeland on 2011-08-26
Yeah, the naming makes it even more confusing.
In the logon manager:
Ubuntu == Unity
Ubuntu Classic == Gnome
Unity2 == Unity2  Surprise!
Brings me back to the old issue of is this a Coke or a Coke Classic which is what Coke used to be.

---

### Post by dewdrop_world on 2012-07-08
There's a classic mode? Sweet! It didn't take long before I started to hate the new desktop...

(The visual effects make it really unreliable to run realtime audio synthesis, so the fact that it's harder to bring compiz under control is a bit of a fail IMO)

Update: Enough of that, I'm installing gnome. I need an unobtrusive, fast interface. Unity gives you a choice: Speed or configurability. No thanks. Ubuntu missed the boat on this one.

---

### Post by wildmanne39 on 2012-07-08
Old thread closed.

---

