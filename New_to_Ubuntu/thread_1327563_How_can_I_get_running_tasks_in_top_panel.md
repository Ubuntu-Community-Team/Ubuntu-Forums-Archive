---
title: "How can I get running tasks in top panel"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by steve228 on 2009-11-15
I want my top panel to look something like this

[[COLOR="Blue"]Gnome-Look[/COLOR]]("http://www.gnome-look.org/content/preview.php?preview=2&id=92328&file1=92328-1.jpg&file2=92328-2.jpg&file3=92328-3.jpg&name=CONKY-colors")

I would like to remove the bottom panel that has all my running programs, and put them at the top... and I want it to look like the picture ( small icons to preserve space)

Does anybody know what to look for or how to get it looking similar to the picture?

---

### Post by ????123856 on 2009-11-15
Is this netbook remix?

---

### Post by sisco311 on 2009-11-15
That's an [xfce4-panel]("apt://xfce4-panel") (apturl link).

To replace gnome-panel with xfce4-panel press Alt+F2 and run:
```
gconf-editor
```

go to desktop/gnome/session/required_components and change the value of *panel* from gnome-panel to xfce4-panel.

Log out and log back in. Right click on xfce4-panel -> Add New Items... -> Icon Box.

If you want to use Gnome applets inside the xfce4-panel just as they are used inside the gnome-panel, then install [xfce4-xfapplet-plugin]("apt://xfce4-xfapplet-plugin").

---

