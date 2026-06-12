---
title: "OK An Absolute beginner !"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by martrum on 2009-01-26
So I've installed the latest Ubunto server and rebooted and held my breath...

It asks me to log in and.....

I get to a command prompt with myUsername@ubunto:$

This is really silly but I expected to see the graphical Windows type display. What have I done wrong ?!!

---

### Post by taurus on 2009-01-26
Server version only comes with a console/prompt, no window manager.  If you want a window manager like Gnome, you have to install the ubuntu-desktop package.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Muffinabus on 2009-01-26
You installed Ubuntu Server, that's why.  I forget the name of the package you can install to get a GUI, hopefully someone will post the name of it soon.

EDIT:  Well there ya go.

---

### Post by damis648 on 2009-01-26
Ubuntu server doesn't have a GUI. If you are looking for a GUI (a desktop) use Ubuntu Desktop.

---

### Post by martrum on 2009-01-26
Thanks. What a dummy !!

---

### Post by albinootje on 2009-01-26
After using "sudo apt-get install ubuntu-desktop" basically the only difference will be that you're still using the server kernel from the server installation.
For the rest it's the desktop installation with the server software parts which you could also have installed after using the desktop installation cdrom. Just FYI ;-)

---

### Post by Sealbhach on 2009-01-26
> **martrum said:**
> Thanks. What a dummy !!

Did you want the server edition or the ordinary desktop edition? I don't know how different they are...


.

---

