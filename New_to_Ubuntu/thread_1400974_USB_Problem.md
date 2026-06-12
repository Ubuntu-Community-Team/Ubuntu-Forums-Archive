---
title: "USB Problem"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Periswell on 2010-02-07
Hello
I have been a bit of a idiot and screwed up my computer. I was trying to free some space and get my computer to boot quicker by deleting programs I don't use in synaptic, but I think I've deleted something I shouldn't have by mistake. No USB drives will mount in nautilus. Certain programs such as 'Disk utility' recognise its there, but in nautilus, nothing shows up. I can't find it in /media, and it doesn't show in the side bar. Any thoughts, maybe you know what I uninstalled so I can install it again. Thank you.

-joshua

---

### Post by mushwars on 2010-02-07
```
sudo apt-get install gnome-volume-manager
```


btw, deleting stuff will not make your computer start faster or run faster, hardly anything is running its not like winblows.. you can see whats running by doing

```
top 

-or-

ps aux
```

---

### Post by Periswell on 2010-02-07
already installed, but cheers :)

-joshua

---

### Post by mushwars on 2010-02-07
hrm already installed, well its not working so we are going to purge all the settings and start over

```
sudo apt-get purge gnome-volume-manager
sudo apt-get install gnome-volume-manager
```

---

### Post by Periswell on 2010-02-07
im afraid no change :/

-joshua

---

### Post by nhasian on 2010-02-07
i dont know what you deleted that that pervents the automounting of the usb drives, but i know you can mount it manually

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

