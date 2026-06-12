---
title: "Graphics Refresh"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-03
Ahh, had a quick search, but don't really know what I'm looking for I guess. I can only explain it that, I've been messing with the simple ubuntu appearance customisation, and then reset to default, but graphical inconsistencies still lie around the desktop which were the object of the tweaking. How can I just do a desktop toilet flush and refresh the page? 

sigh.
Thanks for considering.
Robin

---

### Post by kpkeerthi on 2009-04-03
What do you mean my graphical inconsistencies? A bit more detail might help.

---

### Post by hungryOrb on 2009-04-03
Thanks for reply!
Please check the screenshot
Pictures are better than words :D

---

### Post by kpkeerthi on 2009-04-03
Try reverting back to default Ubuntu theme from System -> Preferences -> Appearance.

---

### Post by hungryOrb on 2009-04-03
Thanks, I tried that :(
The application bar at top, well, the one with the active windows on, doesn't report accurately what's open. In fact, it doesn't show anything, just the stuff which was open when I was customising, and then it's frozen like that. I know I could just restart, but.. wondering if there is a simple command I can do, to reload the UI? A big fat refresh flush?

---

### Post by Praxicoide on 2009-04-03
A quick, easy way is to just delete the configuration files and then log out. They will revert to default when you log back in. Of course, this means that A LOT of gnome stuff will revert back to default, so I don't know if that's what you want.

If you want to do this:

Open Nautilus on your personal folder (/home/yourusername).

Press the Cltrl and H keys together, this will make the hidden folders appear (they are transluscent and have a "." before their name)

Delete the .gnome .gnome2 .gconf gconfd .metacity folders

Close nautilus and log off or reboot.

---

### Post by kpkeerthi on 2009-04-03
> **hungryOrb said:**
> Thanks, I tried that :(
The application bar at top, well, the one with the active windows on, doesn't report accurately what's open. In fact, it doesn't show anything, just the stuff which was open when I was customising, and then it's frozen like that. I know I could just restart, but.. wondering if there is a simple command I can do, to reload the UI? A big fat refresh flush?

```
killall gnome-panel
``` should restart the panels.

---

### Post by Praxicoide on 2009-04-03
Yeah, definiely try that first. If you haven't even restarted, then you probably don't need to delete any configuration directories.

Actually, you could switch to a tty (press Cltrl + Alt + F1) and then return to X (press Cltrl + Alt + F7).

---

### Post by hungryOrb on 2009-04-03
Thanks guys :)

---

### Post by CatKiller on 2009-04-03
I can't offer you any advice, but that wallpaper is **cool**...

---

