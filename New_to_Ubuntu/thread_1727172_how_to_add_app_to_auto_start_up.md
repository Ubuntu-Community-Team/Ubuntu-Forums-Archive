---
title: "how to add app to auto start up?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-12
how can i add a program / app to startup automatically after boot, example firewall. how can i find an apps commend line myself so i can add any app of my choice to startup?

---

### Post by dcsoldschool53 on 2011-04-12
Click Systems > Preferences > Startup Applications. Add the program there.

or in the terminal, type

```
gnome-session-properties
```

---

### Post by rez182 on 2011-04-12
> **dcsoldschool53 said:**
> Click Systems > Preferences > Startup Applications. Add the program there.
yes but i cant add from there, i cannot find the app, dont know where they are stored.

---

### Post by oklokl on 2011-04-12
[COLOR=#333333][FONT=Gulim]apt-get install chkconfig

chkconfig --a [/FONT][/COLOR][COLOR=#333333][FONT=Gulim]test[/FONT][/COLOR][COLOR=#333333][FONT=Gulim] on

del
[/FONT][/COLOR][COLOR=#333333][FONT=Gulim]chkconfig --d test on

update-rc.d


or

[/FONT][/COLOR]apt-get install sysv-rc-conf


sysv-rc-conf

or
[https://launchpad.net/~stebalien/+archive/simple-service-manager]("https://launchpad.net/%7Estebalien/+archive/simple-service-manager")
simple-service-manager

---

### Post by yetiman64 on 2011-04-12
> **rez182 said:**
> yes but i cant add from there, i cannot find the app, dont know where they are stored.

If your apps show up on the panel menus you can right click an entry and choose to "Add this launcher to desktop". Then on the Desktop icon created you can right click and select "Properties". 

Copy and Paste the necessary fields (Name, Command, and optionally, Comment) into Systems > Preferences > Startup Applications > Add, dialog box. Finally click the button "Add" and the app is now in your startup list.

---

### Post by dcsoldschool53 on 2011-04-12
[B][quote=rez128]yes but i cant add from there, i cannot find the app, dont know where they are stored[/quote]

Right click Applications > Edit Menus. Search for the program that you want to add. Click it. Then click properties. When the box opens up, every thing  that you need to copy and paste is there.

Now I am not sure you should add  anything that needs a password there. you may just get another problem.
[/B]

---

### Post by rez182 on 2011-04-12
> **dcsoldschool53 said:**
> [B]

Right click Applications > Edit Menus. Search for the program that you want to add. Click it. Then click properties. When the box opens up, every thing  that you need to copy and paste is there.

Now I am not sure you should add  anything that needs a password there. you may just get another problem.
[/B]
thanks alot, its exactly what i was looking for...i want to add firewall to auto startup, but ill make sure i don startup anything suspicious
thanks everyone...

---

