---
title: "Any shortcut keys are not working."
date: 2011-01-28
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-01-28
Hi!
I accidently deleted my home folder, due to which all the setting and configuration files are lost...
I managed to recover almost all the thing somehow..
But none of mine shortcut keys are working like Alt+enter to check properties....
Can anyone please tell me what's needed to done in order to get these working..
Thanks!

---

### Post by CryNGRoad on 2011-02-05
If you can't set any shortcuts using System > Preferences > Keyboard Shortcuts, then I suspect a bigger problem, but you could try resetting them with gconf-editor. Start gconf-editor from a terminal, then navigate to this Key:

**/apps/gnome_settings_daemon/keybindings/**

You should see all the shortcut keys listed on the right. Try right-clicking on one of the keys and click Unset key to reset it to its default.

---

