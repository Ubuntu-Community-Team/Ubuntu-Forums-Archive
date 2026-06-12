---
title: "How do you remove the gnome desktop completely?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by cptrohn on 2009-02-15
I started out with Ubuntu 8.10 but really just prefer the KDE desktop to Gnome... is there a way to completely remove gnome like when I added KDE?

would it be something like this ```
sudo apt-get remove Gnome-desktop
```?

---

### Post by Tibuda on 2009-02-15
```
sudo aptitude remove ubuntu-desktop
```but it will only work if you installed it from a kubuntu system with aptitude not apt-get or adept

---

### Post by cptrohn on 2009-02-15
> **danielrmt said:**
> ```
sudo aptitude remove ubuntu-desktop
```but it will only work if you installed it from a kubuntu system with aptitude not apt-get or adept

Ahhh so since I started out with ubuntu 8.10  then gnome is on there for good then?

---

### Post by RomeReactor on 2009-02-15
Hi. You can follow the instructions listed [here]("http://www.psychocats.net/ubuntu/purekde").

---

### Post by kansasnoob on 2009-02-15
> **RomeReactor said:**
> Hi. You can follow the instructions listed [here]("http://www.psychocats.net/ubuntu/purekde").

+1!

It explains what's really going on! Aysiu did a great job!

---

### Post by cptrohn on 2009-02-15
> **RomeReactor said:**
> Hi. You can follow the instructions listed [here]("http://www.psychocats.net/ubuntu/purekde").

Hey thanks, that works great.

---

