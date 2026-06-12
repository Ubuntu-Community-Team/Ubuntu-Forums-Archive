---
title: "turn kubuntu in to ubuntu"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Williamthecg on 2009-05-12
I am HATING kubuntu do any of you have any idea how to SAFELY install ubuntu and DELETE kubuntu but keep my apps?in am :confused: and clueless in kubuntu but verry good in (gnome) ubuntu

---

### Post by MontelEdwards on 2009-05-12
i love these supper dooper easy posts.
they're funn
```
sudo apt-get install ubuntu-desktop
```


uh and then log out, then click "sessions" i think and select Gnome.
then run this command
```
sudo aptitude remove kubuntu-desktop
```

and i would autoremove too and other but idc

---

### Post by Skripka on 2009-05-12
Installing Ubuntu on top of Kubuntu:
[http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome)  

Removing KDE (Kubuntu):

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by Williamthecg on 2009-05-12
when people said that this fourm was FAST they meant it:)

---

### Post by Skripka on 2009-05-12
> **m.deonte said:**
> 
```
sudo aptitude remove kubuntu-desktop
```

and i would autoremove too and other but idc


kubuntu-desktop is ONLY a metapackage.  Removing it does nothing to remove KDE from one's system.  You must use the massive command listed in the link I posted above.

---

