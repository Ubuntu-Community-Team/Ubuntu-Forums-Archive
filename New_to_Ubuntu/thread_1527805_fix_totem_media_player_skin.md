---
title: "fix totem media player skin"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by libihero on 2010-07-09
i used an installer for the wasp gtk theme, and it added a skin i think to totem.  how can i revert it back to default?

---

### Post by jtarin on 2010-07-09
The GTK them you installed is system wide.You can specify a GTK application to use a specific GTK theme/gtkrc file as follows (eg. gimp-2.3):
```
GTK2_RC_FILES=$HOME/.themes/name_of_theme/gtk-2.0/gtkrc gimp-2.3
```

---

### Post by libihero on 2010-07-09
how do i make it so that the gtk goes with the theme that i'm using automatically?

---

### Post by jtarin on 2010-07-09
Are you asking how to revert all aplications to default theme?

---

