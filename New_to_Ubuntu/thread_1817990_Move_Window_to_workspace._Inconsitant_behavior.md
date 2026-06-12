---
title: "Move Window to workspace. Inconsitant behavior"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by ussher on 2011-08-04
I just moved from KDE to Gnome today so am very new to Gnome.

I have assigned the keyboard shortcut alt+left and alt+right to "Move to workspace left" (and right).  

But the issue im seeing is that if i right click and choose "Move to workspace left" just the window goes, while if i use alt+left the window goes AND the current workspace changes to that workspace.  

Why am i seeing the inconsistent behavior?

---

### Post by CatKiller on 2011-08-04
> **ussher said:**
> Why am i seeing the inconsistent behavior?

Because they are currently different things. The keyboard shortcuts you've defined are workspace-switching options, and using the titlebar menu is a window management option.

You haven't said, but assuming you're using Compiz you can install compizconfig-settings-manager and explicitly set your keyboard shortcuts to just move the window if that's the behaviour you want. It's the Put plugin that will do that.

Compiz and the rest of Gnome aren't as well-integrated as Metacity and the rest of Gnome, but it's getting there.

---

