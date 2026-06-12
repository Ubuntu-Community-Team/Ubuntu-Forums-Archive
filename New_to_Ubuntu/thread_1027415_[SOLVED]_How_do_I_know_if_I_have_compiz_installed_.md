---
title: "[SOLVED] How do I know if I have compiz installed and if its working?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by scotttie on 2009-01-01
Hi everyone,
How do I know if I have compiz installed and if its working, also how would it be switched on and off (if there's problems that is!):confused:?

---

### Post by 5BallJuggler on 2009-01-01
open a terminal and type "ccsm"
if you don't have it will tell you what to do, if you do it will open the compiz settings manager

---

### Post by jboy012000 on 2009-01-01
As far as I can tell Compiz controls the graphics on your desktop and some other applications HOWEVER, it is causing problems for programs like Google Earth.

If you goto SYSTEM>PREFERENCES>APPEARANCE>CLICK THE VISUAL EFFECTS TAB

you are given three options

NONE

NORMAL

EXTRA

NONE: is just a simple basic desktop (Visually) there is no fancy effects or anything.

NORMAL: is not much different it says it improves usability and appearence but I can't tell any different

EXTRA: requires a decent graphics card and does give you some cool graphics on your desktop, but this does stop Google Earth working and may cause some other problems, I just don't use compiz it seems a bit of a waste of time.

Hope this helps

Have a play yourself and make up your own mind.

Cheers

John

---

### Post by drs305 on 2009-01-01
compiz is installed by default in intrepid. The Compiz Configuration Settings Manager (ccsm) is in the universe repository and may not be installed. If it is, you will find it in System, Preferences, CompizConfiguration Settings Manager, or by typing "ccsm" in a terminal.

To install ccsm if it is not installed:
```

sudo apt-get update
sudo apt-get install ccsm

```

There are several ways to turn it on and off. To 'downgrade' to metacity, you can run this:
```

metacity --replace  # note - reverse this with ' compiz --replace '

```

You can also go to the menu and System > Preferences > Appearance, Visual Affects tab and select none.

Another option is to go to CCSM, once installed (System > Preferences > CompizConfiguration Settings Manager) and select/deselect individual compiz settings.

---

### Post by scotttie on 2009-01-01
OK thanks all,
I have checked and it is not installed, I don't have any problems with graphics so I think I will leave it alone (if it aint broke don't fix it!) Thanks for all the info.
regards
Scottie

---

### Post by Ben Page on 2009-01-01
> **jboy012000 said:**
> 
EXTRA: requires a decent graphics card and does give you some cool graphics on your desktop, but this does stop Google Earth working and may cause some other problems, I just don't use compiz it seems a bit of a waste of time.

Hope this helps

Have a play yourself and make up your own mind.

Cheers

John

I havent noticed any problems using full effects in Compiz with google Earth. You dont need extra graphics power to run Compiz smooth, even on my old rig (ati radeon AGP 9600Pro 256MB VRAM - 512RAM) it work just fine without any bugs. It must be your settings or hardware setup.

---

