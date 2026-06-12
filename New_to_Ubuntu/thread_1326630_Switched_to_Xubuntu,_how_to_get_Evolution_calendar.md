---
title: "Switched to Xubuntu, how to get Evolution calendar in panel?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Razmear on 2009-11-14
After seeing a slowdown with 9.10 I switched to xubuntu via synaptic by installing the xubuntu-desktop. 
The system is running a whole lot faster now and everything works perfect except for a few tweaks. 
I'm trying to get the Evolution calendar to be the clock on my panel, as it was in Gnome. Is there a way to do this? 
Thanks,
eb

---

### Post by coldReactive on 2009-11-14
Xubuntu takes up more RAM than Ubuntu, just so you know.

---

### Post by werecatomega on 2009-11-14
Evolution, the last time i checked, isn't in Xubuntu. xubuntu uses thunderbird. if you did install evolution, i'm not sure how to answer than.

---

### Post by Razmear on 2009-11-14
Evolution has been installed for years. I just switched the shell from gnome to xfce. Evolution is working fine I just can't figure out how to get the little calendar app on the panel for the clock. 
No big deal if it can't be done, but seems like there should be a way. 

The Gnome interface in 9.10 is slow on my 512ram pc, xfce is running much faster and smoother. 

info here: 
[http://xubuntu.org/get](http://xubuntu.org/get)

eb

---

### Post by coldReactive on 2009-11-14
> **Razmear said:**
> Evolution has been installed for years. I just switched the shell from gnome to xfce. Evolution is working fine I just can't figure out how to get the little calendar app on the panel for the clock. 
No big deal if it can't be done, but seems like there should be a way. 

The Gnome interface in 9.10 is slow on my 512ram pc, xfce is running much faster and smoother. 

info here: 
[http://xubuntu.org/get](http://xubuntu.org/get)

eb

You also might want to remove firefox and install midori. Also, remove mousepad and install leafpad.

Whatever you do, don't remove brasero, xfburn doesn't work with 9.10 due to lack of complete hal support.

---

### Post by Razmear on 2009-11-14
Got it working. 

First run: 
```

sudo apt-get install xfce4-xfapplet-plugin

```

Then do a rightclick, add to panel, and select XfApplet

Then you get a panel icon you click on that lets you add any of the old Gnome apps, including the evolution clock/calendar. 

eb

---

