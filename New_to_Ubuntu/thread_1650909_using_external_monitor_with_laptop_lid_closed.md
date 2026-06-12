---
title: "using external monitor with laptop lid closed"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by jysung on 2010-12-22
I have Dell XPS 1340 with external monitor hooked up. In windows7, I usually have laptop lid closed, and it automatically detects there is external screen and I am able to use only the external monitor. I would like to have the same effect. I want to only use the external monitor with laptop closed. I tried setting up separate X and twinview in NVidia X Server Settings. Both works fine with laptop closed, except it thinks laptop screen is also usable. How can I make it so that only the external is usable. But make it go back to laptop screen when I disconnect the monitor. Thanks. I am new to ubuntu, so please explain to me in detail.
btw, I am running ubuntu 10.10 desktop version.

---

### Post by gobbles414 on 2010-12-22
Navigate to the following: System = > Preferences => Power Management => On AC Power and/or On Battery Power => When laptop lid is closed => blank screen.

PS: Some laptops will overheat if the lid is closed during use (e.g. many Apple laptops), so be careful...

---

### Post by Kirboosy on 2010-12-22
> **gobbles414 said:**
> Navigate to the following: System = > Preferences => Power Management => On AC Power and/or On Battery Power => When laptop lid is closed => blank screen.

PS: Some laptops will overheat if the lid is closed during use (e.g. many Apple laptops), so be careful...


You also might have to change the display settings to your external monitor only. System --> Preferences --> Display

Whenever you unplug the monitor Ubuntu should automatically swap back to the laptop screen. 

[COLOR=Red]Welcome to Ubuntu. :)[/COLOR]

---

### Post by gobbles414 on 2010-12-22
Just realized that my first solution won't work. Two other possibilities for you to try:

1. Go to Applications => Accessories => Terminal and enter gconf-editor into the terminal (don't run as sudo, etc). In the new window, navigate to apps => gnome-power-manager => buttons, and enter the word nothing into lid_ac and lid_battery. This will add a "Do Nothing" option to the Power Management control panel which I mentioned in my first reply.

2. As Caboose885 suggests, you can turn off your laptop's built-in monitor while connected to an external monitor by going System => Preferences => Monitor (although you still won't be able to close the lid).

See [http://ubuntuforums.org/showthread.php?t=1467825](http://ubuntuforums.org/showthread.php?t=1467825) and [http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid) for more information.

---

