---
title: "Accidentally deleted (*i think*) my toolbar"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-02-17
So a few weeks ago I accidentally deleted (or I think I did - I was clicking around and all of a sudden it was gone) my main toolbar.  I figured, easy enough, I'll just add a new one.  I had to go through and re-add icons/menus/etc. but I can't seem to find the ones I need, and I've lost some functionality.  For example:

It no longer prompts me at the top when I need to install updates.  I can't for the life of me find a 'Network Connection' manager that tells me what wireless networks I'm connected to or are available.  I can only find one that tells the status of wlan0, eth0, lo, etc.  

Also, one of my favorite programs "CheckGmail" seems to be running, but now instead of appearing on my toolbar it just displays a popup window and then disappears  as if the normal icon is "behind" it.  Same goes for when my battery is low.  I hope this is clear enough.  Please help

---

### Post by dzark on 2009-02-17
Right click on a blank area of the "toolbar" (actually called a Panel or gnome-panel) and you can select "Add to Panel". What you're missing is called "Notification Area" ;)

---

### Post by UbuntuNerd on 2009-02-17
type this in a terminal to reset your panels like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by TMcKSmith on 2009-02-17
> **UbuntuNerd said:**
> type this in a terminal to reset your panels like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

worked perfectly!  thank you so much

---

### Post by UbuntuNerd on 2009-02-17
your welcome :)

---

