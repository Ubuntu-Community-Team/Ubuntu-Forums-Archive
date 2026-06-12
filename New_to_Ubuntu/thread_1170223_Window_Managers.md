---
title: "Window Managers?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Corelogik on 2009-05-26
I'm a little confused about what they are, how they are used and the differences between them. I see posts about Compiz, Beryl, Metacity, GTK 1, GTK 2 etc,... When you go to a site like Gnome look or KDE look you see option for all of the different ones, and I have no idea what I should be looking at or for.

I don't use Ubuntu or Kubuntu yet, but I need to get a handle on what these things are.

Can some explain to a newbie what these are all about please?

TIA

---

### Post by OutOfReach on 2009-05-26
Well I think [Wikipedia]("http://en.wikipedia.org/wiki/Window_Manager") does a pretty good job at explaining it. It basically manages your windows, controls their appearance (i.e. titlebars) it controls how you move them, where they are placed when the app starts, etc.

Well some differences between Window Managers is that some might be more heavy weight than others (e.x. Compiz and OpenBox), they might manage your windows differently (e.x. stacked window managers and tiled window managers) or they just might have more shiny effects (Compiz).

---

### Post by Corelogik on 2009-05-26
OK, but I thought Gnome and KDE were the DE/Window Managers,... or had Widnow managers built in to them for the purpose,...

I'm having a difficult time articulating what I'm not understanding I guess.

---

### Post by kerry_s on 2009-05-26
basically there just like having different themes, the window manger is different from the desktop's as the wm can be used all by itself, while the desktop provides most of the things you would find on a desktop all bundled together.

Compiz & Beryl,  are mainly used with desktop's to provide the fancy effects, you can only run 1 window manager at a time.

GTK 1 & GTK 2, are like the decorations, gtk1 is not really used anymore, everything is usually gtk2.

gnome & kde, are 2 different desktops, gnome is built on gtk2, kde is built on qt, they both have different ways of doing things, but provide the same thing in different ways.

---

### Post by s.fox on 2009-05-26
Here is a simple definition of a Window Manager:

A program that manages a graphical user interface, determining the appearance of windows (by providing standard elements such as title bars, for example) and determining the response to operations such as clicking on the desktop.

-Ash R

---

### Post by ad_267 on 2009-05-26
Gnome and KDE are desktop environments. They provide a whole range of applications like text editors, multimedia players, office suites, and do things like manage your desktop and provide a panel and menus. 

Gnome and KDE both have their own default window managers, Metacity and KWin. Compiz is another Window manager that provides more effects than Metacity.

You can also run a window manager without a desktop environment. This is quite popular with basic window managers like OpenBox of FluxBox. In that case you have to use some other application to provide a menu and a panel for listing your open windows.

GTK and Qt are widget libraries for creating applications. The gtk theme controls things like scroll bars and buttons.

---

### Post by Anzan on 2009-05-27
Actually, Fluxbox provides a root menu on right click which can easily be arranged however suits the user by editing a flat text file.

And it has a panel (task bar) that shows iconified/minimized windows, a notification area, workspace switcher, and clock.

But one needs a file manager like Thunar or Nautilus and various services. But if Fluxbox is run on a system that has GNOME or KDE installed, most of the services are run automagically. Those that aren't can be easily added.

---

