---
title: "my default file manager changed, i want Nautilus back!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by jmcgovern on 2008-12-17
hey folks,

Somehow, probably when i was messing with KDE, something got changed so that Nautilus no longer opens when I browse folders from 'Places'  Now, i get Konqueror whenever i open a folder from 'places'.  If I open a folder from the desktop, I still get Nautilus.  How do I fix this so that everything uses Nautilus?

---

### Post by sayems on 2008-12-17
**[SIZE="4"]How to restore Gnome default value[/SIZE]**

As a new Ubuntu (Linux) user (like I am), there are times where you would want to mess with your Gnome, playing around with it and start adding/removing stuffs here and there.

If you have, somewhat, intentionally broken your Gnome settings (for instance, missing window buttons, disappearing application menu, or even worse, crashing gnome-panel), there is still a solution.

All you need to do now is to restore the Ubuntu/Gnome default settings.

To give you an idea, all Gnome settings are stored in folders, and they are user specific. That said, by simply removing these customization folders, you will be able to get back the fresh settings!

Type the following into your command : Alt+F2

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Eventually, do a restart and you should get back the default Ubuntu/Gnome settings!

And it's time to start playing with the Gnome customizations again ;)

---

