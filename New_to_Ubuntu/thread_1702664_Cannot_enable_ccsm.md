---
title: "Cannot enable ccsm"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by mrtn474 on 2011-03-08
Hi,

I noticed that Ubuntu has some pretty appealing eye candy which realized I did not have. I initially installed ubuntu netbook remix, but i really didn't like it. It was so simple and it seemed to be a bit slow so I switched to the desktop version with the settings from Login Screen. 

I noticed that I have mutter and metacity installed, which is what makes the netbook edition look the way it does, right? What if I uninstall them? Will I regret it?

I've searched this forum for answers, but I've found none :\

Also, i downloaded compiz and ccsm already, which as I understood from some post that they run together, right?

---

### Post by mcduck on 2011-03-08
Uninstalling Mutter would only gain you a bit of disk space, not really even enough to make it worth the trouble. You probably should leave Metacity alone, removing it would quite likely take quite a few Gnome components with it.

Have you simply tried starting Compiz? Open a terminal and try running "compiz --replace". If you get any errors, post them here.

(Compiz is the window manager that provides all the visual effects, CCSM is just a tool for configuring those effects)

---

### Post by mrtn474 on 2011-03-08
> libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_1"


The thing says that compiz doesn't exist, right? Compiz is in my list of installed software tittled:

Compiz: OpenGL window and compositing manager.

Note: also, ubuntu is intsalled using wubi

---

### Post by mrtn474 on 2011-03-08
On a side note (no need to really answer), can I access my files saved under windows through Ubuntu?

---

### Post by garvinrick4 on 2011-03-08
> **mrtn474 said:**
> On a side note (no need to really answer), can I access my files saved under windows through Ubuntu?File system:  /host

---

### Post by mrtn474 on 2011-03-08
> File system: /host

Thanks :)

---

### Post by mrtn474 on 2011-03-08
So, does anyone have any idea on what I should do about compiz?

---

### Post by Daveth on 2011-03-08
where did you source your compiz etc from? Via synaptic, or did you grab it from somewhere else?

---

### Post by mrtn474 on 2011-03-08
> **Daveth said:**
> where did you source your compiz etc from? Via synaptic, or did you grab it from somewhere else?
I just used the ubuntu software center to install it.

---

### Post by garvinrick4 on 2011-03-09
You did install ccsm and not just compiz?

Ubuntu software center:
Type ccsm in the upper right corner box and install.
Advanced Desktop Effects Settings (ccsm)

Terminal:
```
sudo apt-get install compizconfig-settings-manager
``````
rick@rick-HP-G71:~$ aptitude show compizconfig-settings-manager
Package: compizconfig-settings-manager   
State: installed
Automatically installed: no
Version: 0.9.4-0ubuntu1
Priority: extra
Section: universe/x11


Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,894 k
Depends: python, python-central (>= 0.6.11), python-compizconfig (>= 0.9.0),
         python-gtk2
Description: Compiz configuration settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
 
 This package contains the compizconfig settings manager.

**Below installs compiz from terminal:
[CODE]sudo apt-get install compiz
```rick@rick-HP-G71:~$ aptitude show compiz
Package: compiz                          
State: installed
Automatically installed: no
Version: 1:0.9.4-0ubuntu4
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 53.2 k
Depends: compiz-core (>= 1:0.9.4-0ubuntu4), compiz-plugins (>=
         1:0.9.4-0ubuntu4), compiz-gnome | compiz-kde, compiz-plugins-main (>=
         0.9), libcompizconfig0 (>= 0.9)
Suggests: compizconfig-settings-manager
Provides: x-window-manager
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users with
 special needs. 
 
 This metapackage provides the components necessary for running compiz. It
 provides the compiz core, a set of standard plugins, a window decorator using
 the Gtk toolkit and the files necessary to integrate compiz with the GNOME
 desktop environment.

rick@rick-HP-G71:~$ 

[/CODE]

---

### Post by mrtn474 on 2011-03-09
> **garvinrick4 said:**
> You did install ccsm and not just compiz?

Ubuntu software center:
Type ccsm in the upper right corner box and install.
Advanced Desktop Effects Settings (ccsm)

Terminal:
```
sudo apt-get install compizconfig-settings-manager
``````
rick@rick-HP-G71:~$ aptitude show compizconfig-settings-manager
Package: compizconfig-settings-manager   
State: installed
Automatically installed: no
Version: 0.9.4-0ubuntu1
Priority: extra
Section: universe/x11


Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,894 k
Depends: python, python-central (>= 0.6.11), python-compizconfig (>= 0.9.0),
         python-gtk2
Description: Compiz configuration settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
 
 This package contains the compizconfig settings manager.

**Below installs compiz from terminal:
[CODE]sudo apt-get install compiz
```rick@rick-HP-G71:~$ aptitude show compiz
Package: compiz                          
State: installed
Automatically installed: no
Version: 1:0.9.4-0ubuntu4
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 53.2 k
Depends: compiz-core (>= 1:0.9.4-0ubuntu4), compiz-plugins (>=
         1:0.9.4-0ubuntu4), compiz-gnome | compiz-kde, compiz-plugins-main (>=
         0.9), libcompizconfig0 (>= 0.9)
Suggests: compizconfig-settings-manager
Provides: x-window-manager
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users with
 special needs. 
 
 This metapackage provides the components necessary for running compiz. It
 provides the compiz core, a set of standard plugins, a window decorator using
 the Gtk toolkit and the files necessary to integrate compiz with the GNOME
 desktop environment.

rick@rick-HP-G71:~$ 

[/CODE]
Are those instructions you gave me to run on the terminal to install ccsm and compiz? because I already installed them both myself.

As a reminder, I installed Ubuntu using Wubi.

---

### Post by mcduck on 2011-03-09
> **mrtn474 said:**
> So, does anyone have any idea on what I should do about compiz?

The error looks like you have the Compiz package installed, but are still missing other related packages.

Try running this,. it should make sure you ave all the required stuff (+ the settings manager) installed:
```
sudo apt-get install compiz compiz-gnome compiz-plugins compiz-fusion-plugins-main compizconfig-settings-manager
```

edit: And no, it makes no difference if you used Wubi or not. The fact that you installed Network Remix is a lot more relevant, though, as Compiz and all the required stuff would have been included by default on the Desktop version. They *should* be installed if you have the *ubuntu-desktop* package installed, though.

---

### Post by mrtn474 on 2011-03-09
Awesome, it seems to have worked, I think :D except that the ccsm window is acting weird. I can't click on anything. When I click on something, the whole window shifts up. I click again (anywhere on the window) and it shifts back down.

And yeah, I installed Ubuntu Netbook Remix. It lets me use the desktop version and I like that more, so I'm using the desktop version instead.

---

