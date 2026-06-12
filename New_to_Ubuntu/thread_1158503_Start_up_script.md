---
title: "Start up script"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by ads98765 on 2009-05-13
I want to make a script so when i boot up these 5 commands are typed into the terminal. 

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

How would i go about this thanks

---

### Post by kerry_s on 2009-05-13
put them in a script:

gedit .my-script

```
#!/bin/sh
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600
```

right click> properties> permission, check the execute

then just add your script to the session startup(preferences> session)
click add then pick your script.

---

### Post by ads98765 on 2009-05-13
thanks alot im just stuck on the last bit i cant find preferences>session its not even in main menu to try and add it

---

### Post by kerry_s on 2009-05-13
> **ads98765 said:**
> thanks alot im just stuck on the last bit i cant find preferences>session its not even in main menu to try and add it

sorry, system> preferences> sessions
i think, i'm still installing my gnome system so i can't look yet.

---

### Post by Ragnar Bocephus on 2009-05-13
System>Preferences>Startup Applications

---

