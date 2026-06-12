---
title: "Lock a key in gconf-editor?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-03-20
Hey, I was wondering if there was any way I could lock my /apps/gnome-settings/gnome-panel/history-gnome-run so that the only thing there is gnome-terminal?

---

### Post by jimv on 2010-03-25
You can make this file read-only after you change the setting:

/home/you/.gconf/apps/gnome-settings/gnome-panel/%gconf.xml

(There might be a better way, but I don't know it ;)

---

