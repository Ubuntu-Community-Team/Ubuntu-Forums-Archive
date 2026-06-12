---
title: "Desktop icon can't move / remove"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by franklin_m on 2010-04-08
I'm running netbook remix. While in the system screen, I somehow drug an icon to my desktop. It looks like it's sitting on top of the background image, yet it can't be clicked on, can't move, etc.

I'd like to get rid of it.

Thanks,
Frank

---

### Post by lidex on 2010-04-08
I'm not familiar with UNR, but on desktop I would run this command to open nautilus in superuser mode:
```
gksudo nautilus
```
In a terminal or Alt+F2 run dialog if applicable.

Navigate to your desktop and delete from there. [COLOR="Red"]*Be very careful to not alter anything else and close directly after.*[/COLOR]

---

### Post by Paqman on 2010-04-08
Go to "Files and folders", open any location and navigate to /home/username/Desktop, you should be able to get rid of it from there.

You won't need to run Nautilus as root, since you own everything within your home folder, including the desktop.

---

### Post by lidex on 2010-04-08
> **Paqman said:**
> Go to "Files and folders", open any location and navigate to /home/username/Desktop, you should be able to get rid of it from there.

You won't need to run Nautilus as root, since you own everything within your home folder, including the desktop.

Yes, should be able to...I'm just wondering though, if it wasn't something done as root, since he can't click on it.

---

### Post by Paqman on 2010-04-08
> **lidex said:**
> Yes, should be able to...I'm just wondering though, if it wasn't something done as root, since he can't click on it.

He can't click on it because the netbook-launcher interface sits over the top of the desktop, and takes up the whole screen. It's semi-transparent though, so you can see the things underneath it.

---

### Post by lidex on 2010-04-09
Ah, thanks for the enlightenment.

---

