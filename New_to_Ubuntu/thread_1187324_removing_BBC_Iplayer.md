---
title: "removing BBC Iplayer"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by weverall on 2009-06-14
how do i remove iplayer from Ubuntu Jaunty?

---

### Post by TeoBigusGeekus on 2009-06-14
How did you install it?

---

### Post by weverall on 2009-06-14
downloadeded it from the bbc website

---

### Post by TeoBigusGeekus on 2009-06-14
.deb file or source file?

---

### Post by weverall on 2009-06-14
sorry, im pretty sure it was the .deb file that i downloaded :D

---

### Post by TeoBigusGeekus on 2009-06-14
Then open a terminal and type:
```
sudo apt-get purge iplayer
```

---

### Post by weverall on 2009-06-14
i tried that and got this...

> david@david-laptop:~$ sudo apt-get purge iplayer
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iplayer
david@david-laptop:~$ 


---

### Post by TeoBigusGeekus on 2009-06-14
Ok, then go to
System->Administration->Synaptic Package Manager
and do a search for iplayer.
When you find it, right click it and choose mark for complete removal.

---

### Post by solitaire on 2009-06-14
Was it the AIR package of iPlayer you downloaded?

---

### Post by weverall on 2009-06-14
yeh, got it uninstalled, 

unistalled the air package thing, then just deleted bbc iplayer from my main menu

dont know whther that is right or not lol

---

