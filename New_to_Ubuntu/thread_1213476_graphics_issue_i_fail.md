---
title: "graphics issue/ i fail"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Acid44 on 2009-07-14
i just set up a dual boot between winXP and ubuntu 9.04 and while trying to get it looking the way i want i messed up my graphics settings...

in the compiz config i turned on the bicubic filtering and then found out my comp cant handle it... now whenever i boot into ubuntu it loads but as soon as i click a drop down menu the space covered by the menu, including the menu itself, goes black... or if i rotate the desktop cube, the whole screen goes black...

anyone know a way to fix this or do i have to reinstall?

---

### Post by Acid44 on 2009-07-14
anyone?

---

### Post by CatKiller on 2009-07-15
You almost never need to reinstall.

What you want to achieve is removing the "bicubic" from the GConf key /apps/compiz/general/allscreens/options/active_plugins. There are a couple of ways to do this, depending on quite how difficult your computer is to use in this state.

The easiest is probably to press Alt-F2 to get the Run dialogue. From your description, this may be completely black, but should still take input. Type in ```
metacity --replace
``` (and press Enter) which will temporarily disable Compiz. Then you can run CCSM to uncheck the Bicubic filter plugin. When you've done this, ```
compiz --replace
``` will restart Compiz again.

The second easiest would be using the command line from a virtual console (Ctrl-Alt-F1) to use gconftool-2 to automatically change the GConf value. Unfortunately, I don't have the experience to tell you exactly what that command should be.

Which brings us to the third easiest. GConf key values are stored in XML files in your Home directory. You could edit this file by hand from a virtual console to remove the bicubic list entry. You'd edit the appropriate file with ```
nano ~/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
```

---

