---
title: "Default File Browser"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-11
How do I change the default File Browser?

Currently, it's Nautilus . . . which as I understand it is the GNOME default out of the box.

In any case, as I said, my default is currently Nautilus.

I have Krusader, Dolphin, and GNOME Commander in my menu (I downloaded and installed them).  I'm not sure which one I want to change the default to, but I'm leaning toward Dolphin.

Both Dolphin and Krusader have a "Move To . . . " dialog, which is the primary feature that I want . . . though there are other features that are attractive too, like dual panes.  All of them seem more feature-rich than Nautilus.

So, how do I go about changing the default so that, for example, when I click on a media icon on my desktop it opens up in my chosen default file browser.  (Not looking to do a right click and "Open with . . . " either.  Just want to change the default).

---

### Post by mcduck on 2009-08-11
Right-click->Properties->Open With.

Right-click->open with uses the selected program that time, done through Properties it sets the default program.

Edit: You can also set the default file manager for Gnome through gconf-editor, the setting is in desktop/gnome/session/required_components/filemanager.

---

