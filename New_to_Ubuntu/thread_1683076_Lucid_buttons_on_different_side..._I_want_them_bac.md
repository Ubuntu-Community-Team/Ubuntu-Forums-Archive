---
title: "Lucid buttons on different side... I want them back"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Nixarter on 2011-02-07
As the title says, I want the min/max/quit buttons back on the right side (not left).  I recently upgraded and this is absolutely annoying.  I haven't been able to figure it out, though I'm sure it is an easy fix that I'm looking over somewhere (ya know how it is sometimes with things you really want to find...).

So... how do I do it?  Thanks

---

### Post by waynefoutz on 2011-02-07
> **Nixarter said:**
> As the title says, I want the min/max/quit buttons back on the right side (not left).  I recently upgraded and this is absolutely annoying.  I haven't been able to figure it out, though I'm sure it is an easy fix that I'm looking over somewhere (ya know how it is sometimes with things you really want to find...).

So... how do I do it?  Thanks

Easiest way is to install Ubuntu Tweak.


[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Or, you can hit alt+f2 type in gconf-editor then hit enter

navigate to apps/metacity/general and change the value of "button_layout" to "menu:maximize,minimize,close" without the quotes.

---

### Post by beew on 2011-02-07
gconf-editor has a GUI installed by default under Applications > System Tools. However, for some reasons the launcher is not visible when you install Ubuntu. To make the launcher visible, simply go to System > Main Menu, open the left panel to choose "System Tools", on the right panel you should see "Configuration Editor", if the box is not checked, just check it; if it is checked already, uncheck it and recheck it again (I don't remember whether it was checked or not)  The launcher should appear under Applications > System Tools.

---

