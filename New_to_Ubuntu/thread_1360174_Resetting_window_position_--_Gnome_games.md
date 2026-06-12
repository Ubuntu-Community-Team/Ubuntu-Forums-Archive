---
title: "Resetting window position -- Gnome games"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by 655 on 2009-12-20
Hello all,

Visiting my folks for the holidays.  They are running Ubuntu on their home machine, and play the pre-installed "Five or More" Gnome game with frequency.  Somehow, they have managed to permanently lock the game at fullscreen, with the titlebar beyond the boundaries of the screen.  They want to play it at a smaller size.  

Attempting to leave fullscreen via the menu doesn't work.  Attempting to manipulate the window border using Alt-F8 doesn't work.

According to what I read in the Gnome documentation, individual apps store window position and size information, whereas the window manager stores window placement data.  

So, I tried removing and purging the packages gnome-games and gnome-games-data and reinstalling, but the maxed-out window size is remembered.  So I'm guessing this value is stored somewhere else.  I couldn't determine where.

How can I reset this to a "default" size?  It's ok if the change affects other windows as well.

---

### Post by brookie on 2009-12-20
F11

---

### Post by 655 on 2009-12-20
To clarify, F11/toggling the same thing via the menu does not work.  The window is locked in this position, i.e. this is a glitch of some sort.

I spend all of my time in the terminal so I don't know where the low-level configs for window management and such are housed.

---

### Post by brookie on 2009-12-20
i'm running karmic and i opened System>Preferences>Keyboard Shortcuts

Under Window Management I found these to be enabled:
Activate the Window Menu - Alt + Space
Toggle maximization state - Alt + F5
Close Window - Alt + F4
Minimize Window - Alt + F9
Move Window - Alt + F7
Resize Window - ALt + F8
Hide all normal windows and set focus to desktop - Ctrl+Alt+D

One of these may help you to get to terminal. If you can open terminal type in xkill and select the Five or More game and kill it. 
When you restart the game it should be in normal size.

---

### Post by 655 on 2009-12-20
Thanks for your ideas.
**brookie**, I'm not *stuck* inside of the game.  I can close it and manipulate other windows, alt-tab, etc.  However, the game will always launch in fullscreen.  As a consequence, all of the Alt-F7, Alt-F8 and other key combos do nothing, because those assume the window is not in fullscreen.

Sorry for the confusion.  It's not as though I can't access a terminal or get out of the game.  It's just that it is erroneously remembering these settings and always launching stuck in fullscreen.  As mentioned, even purging the package through apt and reinstalling still launches it this way.

---

### Post by brookie on 2009-12-20
sorry about that. I checked Synaptic and the game is called glines. I did a search on my filesystem and there are lots of glines files.

some glines folders here that apt purge maybe left behind:
/usr/share/gnome-games
/usr/share/doc
/usr/share/gnome/help
/usr/share/omf

it looks that apt purge left a config file behind so maybe you could search for glines and remove everything related to it, then re-install. 

good luck.

---

### Post by 655 on 2009-12-20
Brilliant!  I had tried looking for the game using apt-cache search, but I missed it.  glines is exactly what I was looking for.

I found the offending file: in ~/.gconf/apps/glines there was a gconf.xml with a boolean value set to true for fullscreen (among other things with erroneous settings).  Took that out and reinstalled for good measure.  Back to normal!

Thanks again!

---

### Post by chaanakya_chiraag on 2009-12-20
For the future: when something like this happens, hold the [Alt] key and click on the window.  You should be able to drag it out of the annoying position :)

---

### Post by 655 on 2009-12-20
^ I suggest you read the whole thread first

---

### Post by chaanakya_chiraag on 2009-12-20
Sorry!  Just realized that didn't work :(

---

