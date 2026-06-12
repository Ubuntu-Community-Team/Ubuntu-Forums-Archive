---
title: "Resetting/removing a keyboard shortcut"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by h_howee on 2010-02-06
I was playing around with Keyboard Shortcuts and accidentally set the eject shortcut to another key. The key it was originally on didn't exist so I couldn't set it back to that key, and the Remove button is greyed out for any non-custom shortcuts. I can't find it in gconf-editor either. How do I remove/reset it?

[edit]
I just realized backspace disables it. Can I find it on gconf-editor though?

---

### Post by CryNGRoad on 2011-02-05
In gconf-editor look under **/apps/gnome_settings_daemon/keybindings**

The original key name/value was eject/XF86Eject, which you can restore by Right-Clicking on the key name and clicking Unset key.

---

