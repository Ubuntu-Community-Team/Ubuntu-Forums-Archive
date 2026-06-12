---
title: "Wubi + xmonad attempted: and failed."
date: 2009-11-16
forum: New to Ubuntu
---

### Post by corykendall on 2009-11-16
Hello again,

I just tried to setup xmonad (a tiling windows manager: [http://xmonad.org/](http://xmonad.org/)) with Gnome on Karmic Koala.  What I ran was:

sudo apt-get install xmonad

which went fine, and then:

gconftool -s /desktop/gnome/session/required_components/windowmanager xmonad --type string

If I'm not mistaken, this should have replaced the current window manager (metacity is the default for gnome) with xmonad.  Then I restarted my system.  I can successfully get to the login stage and login.  For a brief second the desktop shows, and then is covered by two grey boxes (full screen, one on the left, and one on the right).  I think this is xmonad trying to tile the two gnome panels (top menu bar and bottom bar).  After that display for a few seconds, All I can see is the desktop with no icons or gnome-panels.  Basically just my desktop background.

From this weird environment I am able to right click and create folders, but unable to view an opened folder (double clicking the folder does nothing).  CTRL+ALT+T does not open a new terminal (I have it set to a keybinding for doing so through gnome).  SHIFT+ALT+ENTER does not open a new terminal (keybinding through xmonad), and so I am unable to do anything other than create folders, select them, right click on things, and hard reset my system :D.

I want to ultimately fix xmonad so that it starts on startup and tiles everything OTHER than the two gnome panels.  Of course if that's not easy, I want to be able to disable xmonad so that I can get back on to my system.

Thanks for any help!

---

