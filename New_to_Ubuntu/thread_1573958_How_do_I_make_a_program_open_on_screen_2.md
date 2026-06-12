---
title: "How do I make a program open on screen 2?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by necronom on 2010-09-13
I have been using Ubuntu since Friday, and it's mostly going well (apart from finding certain software), and I have DigiGuide running on startup using Wine.  The problem is that it opens on my left (Primary) screen, when I want it on the right one.

Since Linux has multiple desktops as standard and supports multiple screens, I'm surprised that I can't find an easy way to make it open on workspace 1, screen 2.  It will get annoying having to manually drag it across every time.

I have CompizConfig installed, and that sort of looked like it might do what I want, but I didn't understand some of the settings and what they do.

Can anyone help?

---

### Post by josephpmh on 2010-09-13
To open an app in a second "desktop," goto the the desktop and open the app while there.

To move an app from one desktop to another, right-click on the top frame of the app, and move it to the workspace you want to move it to.

Compiz configuration is a little more complicated, but loads of fun.  If you haven't already installed the ccsm (compiz configuration settings manager), goto your software center and search compiz and install Advanced Desktop Effects Settings (ccsm).  

While that's downloading, goto your desktop, right-click for the menu and click Change Desktop Background.  A dialog box will open with multiple tabs.  Click on the Visual Effects tab, and click on Extra.  (Your system may not be able to do Extra effects (low graphics capability).  If it doesn't allow it, goto System --> Administration --> Hardware Drivers to see if you need to add a driver for your graphics.  You may have to reboot.)

OK, now goto System --> Preferences --> CompizConfig Settings Manager.

Here are the things I have checked:

Gnome Compatability
Desktop Cube
Rotate Cube
Viewpoint Switcher
3D Windows
Animations
Cube Reflection and Deformation
Fading Windows
Login/Logout
Windows Decoration
All the items in Image Loading
Dbus
Mouse Pointing polling
Resize Info
Regex Matching
Scale Addons
Session Management
Video Playback
Workarounds
Extra WM Actions
Move Windows
Place Windows
Resize Windows
Scale 
Snapping windows
Ring Switcher

There are tweaks in many (if not most) of these.  

If there are conflicts w/ some of the default settings, the settings manager will help you resolve them.

Now play!  Ctl-Alt-rightarrow should give you a box or sphere or cylinder rotating your desktops.  Ubuntu-button-Tab should show you a ring of the apps you have open on a given desktop. (OK, some call it the Windows button, other the Super button, but with a little sticker help, it's become the Ubuntu button.)  We're talking serious eye-candy here that windoze aero can't touch.

Have fun.

---

### Post by dannyboy79 on 2010-09-13
i believe this is what you want but don't use it myself

[http://live.gnome.org/DevilsPie]("http://live.gnome.org/DevilsPie")

---

### Post by necronom on 2010-09-13
> **dannyboy79 said:**
> i believe this is what you want but don't use it myself

[http://live.gnome.org/DevilsPie]("http://live.gnome.org/DevilsPie")

That did it perfectly!  Thanks.  I just had to tell it to offset the program window by +1281 pixels (both screens are classed as one wide workspace), then to maximise. :D

josephpmh: I was playing with all that yesterday.  It's great fun, though I now have to remember all the things I set up :lol:

---

### Post by bodhi.zazen on 2010-09-13
You can probably also do it with the -display option

-display 0:0 vs 0:1

the first digit ( 0 ) is the X session, the second digit is the screen.

This would be application dependent, how to specify the display on the command line.

---

