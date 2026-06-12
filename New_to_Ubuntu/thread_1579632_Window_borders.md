---
title: "Window borders"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-09-22
I had a problem with missing window borders and posted it on the forums.  (I didn't know that there was a collective name for the title, buttons, etc. for an application. Though now I feel stupid.)

Now, I've got the window borders back with metacity--replace. Is there any way to make this permanent, or do I have to open a terminal and run it each time I log in?

---

### Post by mcduck on 2010-09-22
First open a terminal and run "gconf-editor" & use it to make sure that desktop/gnome/session/required_components_list is set to "windowmanager,panel,filemanager" and desktop/gnome/session/required_components/window manager is set to "gnome-wm".

That *should* be enough to get Metacity started automatically.

If it doesn't, then you could try changing the desktop/gnome/session/required_components/windowmanager to "metacity". (if you don't want to use desktop effects)

..and if all else fails then go to System/Preferences/Startup Applications and add "metacity --replace" there. Although that's a bit of a hack when simply having correct options in gconf should be enough.

---

### Post by Fifthmarch on 2010-09-22
It worked. Thanks a lot!

---

