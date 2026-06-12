---
title: "Gnome-do and custom applications"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by azidioN on 2010-05-05
Hi. (Ubuntu 10.04, newest gnome-do)

I've installed Teamspeak 2 RC2, however, it isn't installed as a normal application is. It creates a directory and i have to start the program from there.

I did a little research and realized that i could make a new application in the main menu. I've made the application, works like a charm.

The real problem exists in gnome-do not recognizing this newly made application. I have not been able to find a way to force gnome-do to acknowledge the application.

Hope there's some of you, who can help me.

Thanks, azidioN.

---

### Post by cak3 on 2010-05-05
gnome-do probably looks for .desktop files in "/usr/share/applications" so you may create one for it in there (look at the others in there for examples of the format, its pretty straightforward). It might look for them in "~/.local/share/applications" as well, although I think that is usually where the .desktop file would be created if you used a menu editor, like alacarte (not sure if that is how alacarte works though).

---

