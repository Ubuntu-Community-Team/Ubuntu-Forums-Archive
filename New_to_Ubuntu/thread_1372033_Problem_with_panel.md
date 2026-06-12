---
title: "Problem with panel"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by antonio_ing on 2010-01-04
Hi guys

i had recently a problem with panel. Sometimes, when I boot my laptop, the upper and lower bars are empty (i.e. without the application menu and so on). If I reboot everything goes ok. Before the reboot there is an error message which says that panel is still running. How can I solve this problem?

Thanks in advance

---

### Post by lotharmat on 2010-01-04
Try this: (in a terminal)

```
sudo apt-get remove gnome-panel & apt-get install gnome-panel
```

---

### Post by antonio_ing on 2010-01-04
I run the terminal commands, but they stopped after a while even as root.
still got the same problem.

---

### Post by MeanEYE on 2010-01-04
I'd suggest you to open terminal and then type
```
gnome-panel --replace
```

It might tell you where's the problem. My guess is something with config is not quite right or you installed some widgets which are not compatible with your current version...

---

### Post by antonio_ing on 2010-01-04
it worked, but if I close the terminal it disappears and it i move the mouse far from the panel, all the icons disappear, and reappear when i move the mouse closer. I did not install anything new except the updates.

but thank you very much. At least now it is working a little bit

---

### Post by MeanEYE on 2010-01-04
> **antonio_ing said:**
> it worked, but if I close the terminal it disappears and it i move the mouse far from the panel, all the icons disappear, and reappear when i move the mouse closer. I did not install anything new except the updates.

but thank you very much. At least now it is working a little bit

Hm, I had the similar problem. For me panel wouldn't start at all. Just icons without panels. In the end I solved it by adding gnome-panel to startup applications.

As for your problem, I know :) once you closed the terminal panel was gone to. I was more interested in, whether there was some error printed in the terminal during the panel startup?

Edit:
If you want a dirty solution, start gnome-panel from the terminal, just like you did the last time. Go to System -> Preferences -> Startup Applications. Once in there, add a new startup application with command "gnome-panel --replace".

For your convenience I've attached screenshot ;)

I say 'dirty' because it will start your gnome-panel two times, second instance will replace the first one. System is never meant to be run this way and I don't like it :) but it'll most likely make your desktop usable again. :D

Let me know if you have any more questions...

---

### Post by tom.swartz07 on 2010-01-04
heres one way that I always use to fix any panel problems.

in your terminal type

```
rm -rf ~/.gconf/apps/panel
```
and logout/login.

This will remove any customizations or changes you have made to your panel, and a brand-y new 'fresh-install' panel will be created when you log back in.

---

### Post by MeanEYE on 2010-01-04
If you are to remove any customization you've done, at least backup it :) 

```

gconftool-2 --dump /apps/panel > panel_settings

```

To restore backup, use:
```

gconftool-2 --load panel_settings

```

---

### Post by antonio_ing on 2010-01-08
Thanks guy 
now, after deleting panel, everything is working perfetly.

---

