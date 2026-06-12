---
title: "Editing / moving files to etc/x11"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Jarlo on 2009-11-29
Greetings! 
I have just installed Ubuntu for the first time, and apparently there is a bug with the driver for my laptop, so my desktop resolution exceeds it physical screen (1600x1200) while it should be 1280x800. 
Anywho, after some searching i found that the solution is adding a xorg.conf file i've found in the x11 folder.

So my question is, how do i put it there, seeing as i don't have root privileges?
 :oops:

---

### Post by ranch hand on 2009-11-29
In terminal run;
```

gksudo gedit /ext/X11/xorg.conf

```

---

### Post by halitech on 2009-11-29
just in case you are working from the CLI, you can do this
```
sudo touch /etc/X11/xorg.conf
```
```
sudo nano /etc/X11/xorg.conf
```

if you have an existing xorg.conf file you want to copy in, you can do this
```
sudo mv /path/to/original /etc/X11/xorg.conf
```

note: x11 is not the same as X11 so make sure you put it in correctly

---

### Post by Jarlo on 2009-11-29
Thanks a million!! Really made my day, horrible not to have the screen working properly when learning a new OS for the first time! :D

---

