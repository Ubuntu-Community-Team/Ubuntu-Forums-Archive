---
title: "Titlebar buttons rearranged by mac4linux"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by xplodersuv on 2009-08-15
My titlebar buttons (close, maximize, minimize) where swapped to the left side of the titlebar after installing mac4linux, how do i put them back to the default.  Running the uninstall script did not do anything.  I've done compiz --replace a few times as well.

---

### Post by davmac on 2009-08-15
Not sure for definite, because I've not tried installing/uninstalling mac4linux, but I'd start with System -> Preferences -> Appearance.

Select the theme you want and of that doesn't do the trick, click the "Customise..." button and then the "Window Border" tab and see if you can select what you need.

Hope this helps,

Dave Mac

---

### Post by fela on 2009-08-15
Press alt+F2 and run gconf-editor.

Now navigate to apps > metacity > general. There should be something like close,minimize,maximize:menu or something. Change it to menu:minimize,maximize,close.

That's the general idea, the actual words might be slightly different (I forget).

Hope this helps :)

---

### Post by CatKiller on 2009-08-15
If mac4linux uses Emerald (no idea, haven't used it) then you'll need to change Emerald's settings rather than Metacity's. System &#8594; Preferences &#8594; Emerald Theme Manager &#8594; Edit Themes &#8594; Titlebar.

---

### Post by xplodersuv on 2009-08-15
> **fela said:**
> 
Press alt+F2 and run gconf-editor.

Now navigate to apps > metacity > general. There should be something like close,minimize,maximize:menu or something. Change it to menu:minimize,maximize,close.

Hope this helps :)

Thanks!  That did the trick.  I'm using compiz as my window manager, does it inherit settings from metacity?  I noticed there was no similar conf options under the compiz dir.

---

### Post by fela on 2009-08-16
> **xplodersuv said:**
> Thanks!  That did the trick.  I'm using compiz as my window manager, does it inherit settings from metacity?  I noticed there was no similar conf options under the compiz dir.

Glad it worked. Compiz can either use the same window decorator (/usr/bin/gtk-window-decorator) as metacity - actually it uses that as default in ubuntu - or it can use the emerald window decorator (/usr/bin/emerald). If it uses emerald then all the settings for that are in emerald theme manager.

If you want to change to emerald, first install emerald of course and then go to the window decoration plugin in ccsm. You should be able to change compiz-window-decorator (or whatever it is) to just emerald, then run emerald --replace and it should work.

---

