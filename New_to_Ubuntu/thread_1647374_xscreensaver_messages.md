---
title: "xscreensaver messages"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-17
is there anyway to stop those 2 xscreensaver messages you get when the program starts up. i have tried most things they have suggested (did many google searches). have the program set to startup when i log in and of course still get those messages. maybe that is just the way it is.

---

### Post by rburkartjo on 2010-12-21
i bumped this thread. lots of people are on the forms from a number of countries when it is late at night, my time.

---

### Post by rburkartjo on 2010-12-23
okay figure out how to do it by trail and error. put this script into your startup folder.
replace xxx with your password



#!/bin/bash
echo xxx | sudo -S  killall gnome-screensaver 
 xscreensaver & xscreensaver-demo

---

### Post by rburkartjo on 2010-12-23
open text editor  and enter

#!/bin/bash
xscreensaver-command -activate
save
make it exe

and you have a way of starting the screensaver when ever you want

change the icon to whatever you want
enjoy

---

