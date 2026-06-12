---
title: "Login Theme Installation"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by allornothin on 2010-07-14
I'm brand new to Linux (running ubuntu 10.04), so I may be asking some dumb questions over the next days or weeks. I ask forgiveness in advance. 

I was trying to customize my linux theme and visuals by going to system -> preferences -> and appearance then under the themes tab "get more themes online." For starters I thought to change the login screen and ended up looking through [http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter). To make it easy to find for anyone wishing to help, after a failed attempt at learning to install, I picked the first one on the list - brasillinux eye. It is a .tar.gz file. I then followed the directions for theme installation (section 8.2.1.1.2) under the "help" menu in the theme tab of the appearance preferences. It proceeded to tell me that this file is not a valid theme file. I've read other forums and files on how to install things in linux, but I'm still quite confused. I'll be greatly appreciative of anyone willing to tell me what's up or where to go to find out.

---

### Post by jtarin on 2010-07-14
For starters go to [Gnome-Look]("http://gnome-look.org/index.php?xcontentmode=150&PHPSESSID=b381d63d35aa67864cb23b59ebe6a583") for the newest themes as some of those themes at the site you went to are out of date for the version of Gnome yoour running.
[Want to build your own theme? Not difficult.]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes")

The login window is also sometimes called the Gnome Display Manager, or GDM.

    ```
Click System &#8594; Administration &#8594; Login Window. 
```

To install new login screen themes, save the .tar.gz with your theme on it to the directory of your choice. In the Login Screen program, press the Install New Theme button, find your new theme's file, and press the Install button.

Then simply select the new theme from the list of available themes. You can also set it up to pick a random theme on every boot, rather than picking just one theme.

[Other hints]("https://help.ubuntu.com/community/UbuntuEyeCandy")

---

### Post by philinux on 2010-07-14
Unfortunately the Login Screen in 10.04 has very limited customisation options compared to previously. However there is a way using gdm2 setup.

[http://www.webupd8.org/2010/01/gdm2-setup-gets-new-look-and-ubuntu-ppa.html](http://www.webupd8.org/2010/01/gdm2-setup-gets-new-look-and-ubuntu-ppa.html)

[https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

---

### Post by allornothin on 2010-07-14
Thanks for the help!

---

