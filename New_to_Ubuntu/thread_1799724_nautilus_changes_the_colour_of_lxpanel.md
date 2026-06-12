---
title: "nautilus changes the colour of lxpanel"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by mr.akik on 2011-07-08
I am using ubuntu 11.04. I have installed lxde and it's running fine.When I use pcmanfm, there's no problem but when I open nautilus, lxpanel loses its own color and gets the color of the wallpaper of my gnome desktop. Moreover, when I right-click on the desktop, the same menu appears when right-click on gnome desktop.How can I solve this? Please help.

---

### Post by life in color on 2011-07-08
Only a guess but did you try opening Synaptic then opening Appearance and changing the theme to see if Synaptic looks any different in a different theme?

---

### Post by mcduck on 2011-07-08
First thing to try is starting Nautilus with the "--no-desktop" option, otherwise it will take over the task of managing the desktop like it would do when used in Gnome.

I don't know if it has anything to do with lxpanel's appearance, though. But it will at least solve the problem with the desktop menu.

So, just edit whatever launcher or menu entry you are using to start Nautilus:
```
nautilus --no-desktop
```

---

### Post by mr.akik on 2011-07-08
thank you very much. it works.

---

