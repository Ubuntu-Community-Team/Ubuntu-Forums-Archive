---
title: "Screen Resolution Default"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Gameboyman99 on 2010-11-25
Hey guys, I got a question:

Anywhey, I got Kubuntu 10.10 on two desktops, *but* one has no  problems with resolution(note: different monitors; obvious problem  source), but the other does: It doesn't keep my resolution; ever. When I  log out or restart, it's reset to too big(640x400). Almost too big to  reset the res, but just barely not. I need my default res at 1024x768.

**So how do I change the default to 1024x768?**

I couldn't find a post like this anywhere, but if there is, then link it  to me plz. Also, if the 'Change default' button or whatever is right in  front of my face, tell me...
P.S. I don't really mind the terminal; don't think I don't know what I'm doing.

Hasta luego,

---

### Post by Foxheadz on 2010-11-25
System>preferences>monitors

Set resolution click apply and make default.

---

### Post by Foxheadz on 2010-11-25
Wait im not familiar with kubuntu but open the monitors app (im guessing you should have it anyway

---

### Post by sandyd on 2010-11-25
if it doesn't show in the monitor section, you can force the resolution.

adding a modeline is best thing to do.

Press CTRL+ALT+F1
login
Run this


```
sudo killall gdm
sudo killall kdm
sudo X -configure
sudo gdm
```
login (again)


```
kate /etc/X11/xorg.conf
```
Ill make the mods for you. (Adding a 'Mode "horizontalxvertical"' should be sufficient in the current version of xorg)

---

### Post by Gameboyman99 on 2010-11-25
xorg.conf is blank... nothing in it. BTW I don't have gedit, I have kate or notepad w/ Wine. And maybe I'm wrong but I think xorg.conf isn't used anymore...

---

### Post by sandyd on 2010-11-25
> **Gameboyman99 said:**
> xorg.conf is blank... nothing in it. BTW I don't have gedit, I have kate or notepad w/ Wine. And maybe I'm wrong but I think xorg.conf isn't used anymore...

fixed.
forgot the code tags so it looked like the only commands that were shown were gedit

---

### Post by Gameboyman99 on 2010-11-26
Uhh... Somethings wrong... I don't even have a xorg.conf file...???

---

