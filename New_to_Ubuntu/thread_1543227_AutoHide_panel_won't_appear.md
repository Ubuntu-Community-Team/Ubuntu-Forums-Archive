---
title: "AutoHide panel won't appear"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by DayLite on 2010-07-31
I am using Ubuntu 10.4 on my Dell Latitude D600 XP Professional Laptop. I chose, 'autohide' to my panel and now I can't get it to view. I put the curser over it and it won't pop out.

(It was on the bottom and  I moved it to the left side. Contains the trash and current active programs that are minimized).

Please tell me how to correct this so it can be seen.

---

### Post by cariboo on 2010-07-31
Try pressing Alt-F2 and typing:

```
killall gnome-panel
```

to see if that brings your panel back.

---

### Post by DayLite on 2010-07-31
> **cariboo907 said:**
> Try pressing Alt-F2 and typing:

```
killall gnome-panel
```to see if that brings your panel back.


It doesn't work.  It did lock up my computer and I couldn't launch anything, just the curser moved. After rebooting 3 times it is back to 'normal' which includes the left panel still hidden.

Found solution: I disabled everything on 'Desktop' in CompizConfig. I then was able to see the panel.

Thank you for trying to help.

---

### Post by sagewells on 2010-09-21
I'm rather new to Ubuntu, and recently right clicked on my tool bar and saw an "auto-hide" feature, so I clicked on it (have a small screen).  Since I was used to Windows, I thought it would just pop up when I moved the cursor down to the bottom of the screen....but Nothing!  I have only my wallpaper and a blank bar at the bottom.
I've viewed many posts about this, and have tried many fixes as well, but can't seem to find the solution.  I've tried to simply right click on the toolbar and desktop, but nothing.  I've tried clicking "alt + F2" to type in some commands I saw posted, but nothing happens - absolutely nothing.

I got to here by accidentally pressing F1 a couple of times and found "get more help online"....so here I am.  PLEASE HELP!!!

---

### Post by michaelzap on 2011-02-06
This is an old thread, but this also just happened to me so I thought I'd post to it...

Basically I set a Gnome panel to autohide and it hid and then wouldn't reappear. Pressing Alt+F2 and running gconf-editor lets you uncheck autohide (in apps -> panel -> toplevel -> top, bottom, or whatever other panel). That gets you the panel back again, but without autohide working, of course.

I started turning off things in Compiz config settings, and it seems like it's the window decorations plugin that causes this conflict for me. But strangely, I can't uncheck window decorations without it rechecking itself almost immediately thereafter. I assume something else I'm doing in Compiz requires it, but usually I would expect to see a dialog about this, rather than it just rechecking itself to spite me. If I uncheck it and move the mouse quickly to the panel, it unhides, but I only have a split second to do this.

This isn't something that I really care all that much about, so I'm just going to leave it there for now. But I thought this info might be helpful to someone who really wants to make this work.

---

### Post by Lkm on 2011-07-03
I just had this problem too where I couldn't right-click on the panel and alt+f2 didn't do anything so I thought I'd post what I did.
Right-Clicked on the desktop, created a new Launcher and put "gconf-editor" as the command. Double clicked on the icon it made then navigated to apps > panel > toplevels and unchecked autohide under the appropriate panel. Rebooted and was back to normal :)

---

### Post by Alex.Pi on 2012-01-27
Hi. I had the similar problem, with auto hiding. Before this happened I had switched on the Cube plugin in Compiz. So, I just switched it off and the auto hiding works again. Good luck!

---

