---
title: "GDM not working need help!!!"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Dylan 2228 on 2010-12-19
Hey guys I've had Ubuntu for a few days now and I quite liked it until I turned on my computer last night to find that all that shows up is a terminal!!!:mad:
I'm using Ubuntu 10.10 with all the updates and I need to know what to do to get out of this stupid terminal!!!
Oh and by the way please dont say anything too technical as I probably will not understand half of it.

Thanks in advance!!!:)

---

### Post by davidmohammed on 2010-12-19
if you type 

startx

are any messages displayed?

---

### Post by iosuna86 on 2010-12-19
Try CTRL+ALT+F8

That's a way to switch from command line to the desktop.

---

### Post by JC Cheloven on 2010-12-19
> **iosuna86 said:**
> Try CTRL+ALT+F8

That's a way to switch from command line to the desktop.

I believe it's Ctrl-Alt-F7 usually. But surely the problem of the OP is that the graphical environement (Gnome Desktop Manager) is not being actually loaded. So the key combination will lead nowhere.

Can you please log in the command line system you're presented to, and run
```
sudo service gdm start
```

---

### Post by Dylan 2228 on 2010-12-19
> **JC Cheloven said:**
> I believe it's Ctrl-Alt-F7 usually. But surely the problem of the OP is that the graphical environement (Gnome Desktop Manager) is not being actually loaded. So the key combination will lead nowhere.

Can you please log in the command line system you're presented to, and run
```
sudo service gdm start
```
No good I tried ```
sudo service gdm start
```
It says that the gdm is already started!!!
so then I tried Ctrl+ALt+F7 and it says some jiberish and does nothing.
Oh and I also tried startx and it says ```
Fatal Error: No screens found
```

---

### Post by JC Cheloven on 2010-12-21
Ok, if it says GDM is already started try first
```
sudo service gdm stop
```
If it actually stops gdm, please follow by
```
sudo service gdm start
```
And let's see if that gets you into gmd.
Hope this helps.

[INDENT]Note: You can allways press ctrl-alt-F7 or maybe ctrl-alt-F8, to see the graphic environment (if any), and ctrl-alt-F1 (...F6) to go back to a terminal environment. [/INDENT]

---

