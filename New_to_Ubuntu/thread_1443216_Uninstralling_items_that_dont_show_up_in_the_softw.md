---
title: "Uninstralling items that dont show up in the software center?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Scris101 on 2010-03-30
I installed docky and i just dont like it, how would i uninstall it. its not showing up in the Software Center

---

### Post by kokkus on 2010-03-30
system> admin > synaptic package manager. This is where all the packages (everything you have installed on your pc) can be found.
The software center is just a collection of software tested by the ubuntu team. Not always the newest versions but the most recommended versions with less bugs.

---

### Post by mltucker on 2010-03-30
Docky is a part of gnome-do... if you remove gnome-do, docky will be removed as well.  One way to remove gnome-do is with apt-get.  Enter the following in a terminal:

```

sudo apt-get remove gnome-do

```

---

### Post by Scris101 on 2010-03-31
> **kokkus said:**
> system> admin > synaptic package manager. This is where all the packages (everything you have installed on your pc) can be found.
The software center is just a collection of software tested by the ubuntu team. Not always the newest versions but the most recommended versions with less bugs.
yes! that worked thank you!

---

### Post by theozzlives on 2010-03-31
Also, for future reference, you can do
```
sudo dpkg -r <package name>
```

---

### Post by willhe3rd on 2010-04-02
Im trying to uninstal wallpapoz. Synaptic package manager cant find it and when I use the comand 
sudo dpkg -r wallpapoz it tells me its not installed. Any help would be awesome!

---

### Post by da burger on 2010-04-02
> **willhe3rd said:**
> Im trying to uninstal wallpapoz. Synaptic package manager cant find it and when I use the comand 
sudo dpkg -r wallpapoz it tells me its not installed. Any help would be awesome!

How did you install wallpapoz? I can't find it in the repositories.
Also try```
dpkg -l | grep wallpapoz
``` in a terminal to see if it is installed.

---

### Post by willhe3rd on 2010-04-02
It had a set up icon in its folder. I dbl clicked it and it installed it self. It stored it in /usr/local/share. When I try the comand,```
 dpkg -l | grep wallpapoz 
```, it tells me nothing. Sorry, I mean it just gos back to the command promt

---

