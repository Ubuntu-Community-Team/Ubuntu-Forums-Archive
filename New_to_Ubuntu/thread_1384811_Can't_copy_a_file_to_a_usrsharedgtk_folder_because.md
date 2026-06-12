---
title: "Can't copy a file to a usr/shared/gtk folder because of permissions."
date: 2010-01-18
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-18
I realize that I have to sudo or something like that. But I have no idea how to do that. How can I create an elevated instance of Nautilus? (Will that do the trick)

---

### Post by papuccino1 on 2010-01-18
Turns out in Gnome-Terminal:

sudo nautilus.

Worked sexily. :3

---

### Post by Miljet on 2010-01-18
Although that will work, you really should use "gksudo nautilus". See the following link for explanation.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lidex on 2010-01-18
I wouldn't recommend sudo for that, gksudo more appropriate.

You may find this tool useful - it adds a right-click option in nautilus to "Open as Administrator". You seem familiar with the terminal:
```
sudo apt-get install nautilus-gksu
```

Will require a restart of nautilus to enable:
```
nautilus -q
```

---

### Post by NewDisciple on 2010-01-18
I don't use the terminal enough to remember which commands but I have learned to rely on nautilus scripts.  (Scripts are available from [http://gnome-look.org/]("http://gnome-look.org/"))
The main script I use is "Rootilus".  Go to the page you desire to change permissions at, right click, choose scripts, scroll down to Rootilus and left click on it.  A box will appear asking for your password.  Fill it out & enter.  A root page will appear.  Right click on the item you wish to change & pick properties.  A new box will open, choose permissions and change at will.
Sounds like a lot of steps but once you have the script installed it's a breeze to use and has saved my butt many, many times.
Make sure you have created a "nautilus scripts" folder in ./gnome 2 (hidden file) in your home folder.

---

