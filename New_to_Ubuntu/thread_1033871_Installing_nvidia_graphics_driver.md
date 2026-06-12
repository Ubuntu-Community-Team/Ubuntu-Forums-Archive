---
title: "Installing nvidia graphics driver"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by monton on 2009-01-07
Greetings
I just downloaded the nvidia Linux driver from their website. Next I downloaded a file to help install it. 
I have no idea how to proceed from here. I tried the command line parameters provided in terminal but no luck. 
What is X-server and how do I launch it?

Any  help or guidance would be appreciated.

Compiz installed and working

Thanks, Monton

Nvidia 6800 gpu 128mb vram
AMD XP3200
512MB RAM
ASUS A7NE  MB

---

### Post by Crafty Kisses on 2009-01-07
If you go to, **System -> Administration -> Drivers Manager** you can grab the drivers from the repo's and it will install them for you.

---

### Post by dadozgb on 2009-01-07
> **monton said:**
> 
What is X-server and how do I launch it?



[http://en.wikipedia.org/wiki/X_server](http://en.wikipedia.org/wiki/X_server)

startx od via xdm/kdm/dm...

---

### Post by Frak on 2009-01-07
Use the restricted drivers manager (as stated above). The X Server is the most basic GUI suite (in simple terms). To start it, you type

```
startx
```

at the terminal. Though, to start X and your favorite DM (desktop manager) use the corresponding commands.

```
sudo /etc/init.d/gdm start #GNOME
sudo /etc/init.d/kdm start #KDE
sudo /etc/init.d/xdm start #XFCE
```

That will launch Gnome/KDE/XFCE respectively as well.

---

