---
title: "Can I not load Gnome?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by joshpennington on 2009-01-06
I am building a development web server and I installed Gnome on the server for the few times it is nice to have a GUI up and running on the server.

However I would like to have the GUI not load when I start the OS, but rather load it manually through the command startx.

Does anyone know how I can do this?

Thanks!

Josh Pennington

---

### Post by tuxxy on 2009-01-06
Try removing the **gdm **package and it should boot you into terminal and require you to startx :)

---

### Post by joshpennington on 2009-01-06
Wow... that was a fast response.  Thanks much.  It worked!

Thanks again

---

### Post by tuxxy on 2009-01-06
hehe yes as I loaded the page you had just posted it, not bad eh :)

---

### Post by handydan918 on 2009-01-06
> **joshpennington said:**
> I am building a development web server and I installed Gnome on the server for the few times it is nice to have a GUI up and running on the server.

However I would like to have the GUI not load when I start the OS, but rather load it manually through the command startx.

Does anyone know how I can do this?

Thanks!

Josh Pennington
Edit your /etc/inittab. find the following line:
```
id:5:initdefault:
```
and change it to 

```
id:3:initdefault:
```

To undo, change it back to 5. 
For more info, see man inittab.

---

