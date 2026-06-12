---
title: "program panel"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by nene7 on 2009-08-08
hola,
 i want to know how can add in the panel that are aplications, place and system; (when i open a program the show in the down panel) this program show i can add to the upper panel.

---

### Post by coldReactive on 2009-08-08
Right-click the panel, click add to panel, then add "Menu Bar" NOT "Main Menu."

---

### Post by nene7 on 2009-08-08
thanks
 but what i tried to say is; you know in windows when you open a program they apear in the same panel that are the menu bar, i want to create something like that.

---

### Post by Raffles10 on 2009-08-09
Do you mean application launchers on the panel ?

Right-click the panel, select 'Add To Panel' > 'Application Launcher' > 'Forward', then select your app' from the list.

---

### Post by arky on 2009-08-09
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

---

### Post by talsemgeest on 2009-08-09
> **nene7 said:**
> thanks
 but what i tried to say is; you know in windows when you open a program they apear in the same panel that are the menu bar, i want to create something like that.
Assuming you have 2 bars, one on the top, one on the bottom, you just have to add the right one onto the right bar. If you want to have the apps list on the top bar, right click the top bar and click "Add to panel". Scroll down and select "Window list", and click add, then close. If you want the menu on the bottom, do the same thing for the "Menu bar" on the bottom panel.

---

