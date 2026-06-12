---
title: "Start a script from Ubuntu menu"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by LtPitt on 2009-01-04
Hello everybody!
To cut the long story short I've installed LightZone and I want to start it from the Ubuntu menu...
This program works if you load a script (a text file that starts with #! /bin/sh).
If I load it from nautilus I get a window:

"Do you want to run Lightzone or display its contents? Lightzone is an executable text file"
And then I can choose "Run in terminal" "Display" "Cancel" and "Run".
The only option that allows me to run the program is "Run in terminal".
I've tried adding it to the ubuntu menu normally, pointing the launcher to this executable text file but it doesn't work.
Any hints?

Thanks!

btw the program is great, a true lightroom substitute

---

### Post by evilkastel on 2009-01-04
You can add ```
sh /the/route/file.sh
``` in the command section of the launcher, once you select "new element" when editing the menu. 
So in order, right click on GNOme menu, edit menus, new element and there where says command write as instructed above. Hope this helps-.

---

### Post by LtPitt on 2009-01-06
Great! :D

Thanks!

---

