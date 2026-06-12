---
title: "Ubuntu stangeness..."
date: 2009-03-23
forum: New to Ubuntu
---

### Post by xg7 on 2009-03-23
I unchecked alerts and sound effect and also unchecked gnome login sound, however I still get the "drum roll" at the login screen.  Also, unchecked the "tool-tips enabled" box - but both these functions persist!

What's going on here?

Side note: what is the gnome splash screen?  Thanks

---

### Post by gitpik on 2009-03-23
> **xg7 said:**
>  however I still get the "drum roll" at the login screen. 

Look in System >> Administration >> Login Window. On the Accessibility tab see the Sounds section and uncheck "Login screen ready:"

---

### Post by mcduck on 2009-03-23
Disabling sounds from your personal desktop settings only affects your user, not the whole system. If you wish to disable the sound in the login screen you need to do that in GDM setup (System/Administration/Login Screen).

And the "tooltips-enabled"-box (I assume you mean the one in gconf, at /apps/panel/global/tooltips_enabled). That setting only affects the panel itself, and not even all applets in the panels, so it won't disable *all* tooltips.

As far as I know there isn't any setting that would allow you to disable tooltips in all programs.

If you are using Compiz (the "Desktop effects"), you can use it's opacity plugin to make tooltips invisible.

Edit: The Gnome splash screen shows after logging in, while your desktop is loading. It's disabled by default in Ubuntu since the loading time is so short, but if you want you can enable it with gconf-editor, just enable apps/gnome-session/options/show_splash_screen.

---

### Post by xg7 on 2009-03-23
Excellent - thanks everyone for the great help! :)

---

