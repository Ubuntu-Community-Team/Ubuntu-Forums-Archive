---
title: "Why do I have to enter this command in the Terminal every time I start my computer?"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by Krusader3z on 2007-12-01
My wireless "light" on my laptop is on when I boot up, but I cannot see any networks or anything to do with the wireless connection unless I enter 

sudo modprobe ndiswrapper

in a terminal. After I do that it associates with my network and all is good. What gives?

---

### Post by roaldz on 2007-12-01
Just add ¨ndiswrapper¨ in /etc/modules
you can do that bij running ¨gksu gedit /etc/modules¨, add ndiswrapper at the end, and safe.
The next time you boot it autoloads..

---

### Post by Krusader3z on 2007-12-01
Score one for the Netherlands!!

If anyone else stumbles across this in a search and has the same issue, the advice above worked.

---

### Post by roaldz on 2007-12-01
> **Krusader3z said:**
> Score one for the Netherlands!!

If anyone else stumbles across this in a search and has the same issue, the advice above worked.

Besides the legal prostitutes and legal soft drugs, the Dutch have linux too!:)

---

### Post by victorbrca on 2007-12-01
> **roaldz said:**
> Besides the legal prostitutes and legal soft drugs, the Dutch have linux too!:)

hahaha... and beautiful women.. 


Vic.

---

