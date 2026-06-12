---
title: "Main system menu bar lost &amp; found"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by badgames on 2010-09-15
I'm relatively new to Ubuntu and Linux (I've tried it before and had to put it aside while attending to other things), and since I go all the way back to punch cards and paper tape, a mere command line is not intimidating, just I'm not familiar with what to do with this one.

At any rate, I just installed 10.4 on an old HP Pavilion 6370 (600MHz Celeron with built-in VGA).  All fine.  Ran updates, system came back, but without the upper and lower system menu bars. They are not hidden, they are completely unavailable.  After looking around through existing threads I was able to launch gconf-editor, and tickle the auto-hide settings for the bars (Alt+F2, gconf-editor, apps > panel > toplevels > bottom_panel_screen & top_panel_screen) and they would then duly appear (or disappear).

Reboot the machine, and I'm back to square one (except now I know my way through that part of the maze).  How can I fix this on a more or less permanent basis? The cheese was good, thank you very much, but it is gonna have to be real good to keep doing this.

---

### Post by lkjoel on 2010-09-15
> **badgames said:**
> I'm relatively new to Ubuntu and Linux (I've tried it before and had to put it aside while attending to other things), and since I go all the way back to punch cards and paper tape, a mere command line is not intimidating, just I'm not familiar with what to do with this one.

At any rate, I just installed 10.4 on an old HP Pavilion 6370 (600MHz Celeron with built-in VGA).  All fine.  Ran updates, system came back, but without the upper and lower system menu bars. They are not hidden, they are completely unavailable.  After looking around through existing threads I was able to launch gconf-editor, and tickle the auto-hide settings for the bars (Alt+F2, gconf-editor, apps > panel > toplevels > bottom_panel_screen & top_panel_screen) and they would then duly appear (or disappear).

Reboot the machine, and I'm back to square one (except now I know my way through that part of the maze).  How can I fix this on a more or less permanent basis? The cheese was good, thank you very much, but it is gonna have to be real good to keep doing this.
Welcome to Ubuntu Forums!
Try this in a Terminal (Applications->Accessories->Terminal) window:
```
cd ~/Desktop
ln /usr/bin/gnome-panel gnome-panel

```
And every time you log in, simply double click on "gnome-panel" on the desktop. (Assuming you are using GNOME)

---

