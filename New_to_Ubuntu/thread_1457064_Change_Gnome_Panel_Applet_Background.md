---
title: "Change Gnome Panel Applet Background?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Saudrapsmann on 2010-04-18
[IMG]http://i39.tinypic.com/30bp9vl.png[/IMG]

As you can see in the picture, I have a background image set for the gnome panel, but the applets refuse to follow suit.

Is there anyway I can get the applet to match the panel at all? I can't find anything. Basically I want it to be one even panel image for that perfect look.

Any help is appreciated.

---

### Post by mcduck on 2010-04-18
Your problem is that the GTK theme you are using defines a background for the panel applets, and that always overrides whatever panel background you try to set yourself.

The only way to fix that is to edit the GTK theme and remove anything panel-related from it. If you are lucky, the theme you are using has a separate panel.rc or similar file, in which case you can just rename/delete that file. If that's not the case, you simply have to work trough the actual theme rc file and try to comment out or remove panel theming from it.

---

### Post by Saudrapsmann on 2010-04-18
You're a life saver thank you! I found the place to edit it in /usr/share/themes/Shiki-Wise/gtk-2.0/panel.rc

---

