---
title: "adding KDE"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-02-17
Im currently using ubuntu 8.04 and I would like to add the KDE desktop. Unfortunately downloading KDE from the the repositories isnt an option because Im deployed and our download speeds are crap but I have a kubuntu install disc, can I install KDE from the kubuntu disc without having to wipe my ubuntu install...

---

### Post by taurus on 2009-02-17
You could try to see if you can install kubuntu-desktop from the CD.  Insert it into a drive.  Then open a terminal and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by Loki57701 on 2009-02-17
I ran into some errors:

E: couldnt find package kubuntu-desktop

and apt-get tried to download the package from the internet. If it wouldnt take literally a week I'd probly do it that way.

---

### Post by taurus on 2009-02-17
Did you have the Kubuntu alternate CD?

---

### Post by kansasnoob on 2009-02-17
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

