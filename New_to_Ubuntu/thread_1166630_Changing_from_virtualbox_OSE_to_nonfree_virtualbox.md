---
title: "Changing from virtualbox OSE to nonfree virtualbox?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Vunutus on 2009-05-21
I would post this in the virtualization board but it's more a question about general package management.

I want some of the features offered by the closed source virtualbox, but am using OSE now. When I open up the closed source package it reports a conflict for obvious reasons. If I remove the OSE package will it also remove my configuration folder in the home directory? I don't want to lose my VDI's and such.

---

### Post by Bradtek on 2009-05-21
Usually 
```
sudo apt-get remove "program"
```
will only remove what it installed, and to get rid of configuration files etc you would have to use
```
sudo apt-get purge "program"
```

But it is **ALWAYS** a good idea to **BACK UP** anything you do not want to lose.

---

### Post by TheNosh on 2009-05-22
i switched from open to closed source virtual box a while ago.

if i recall properly (and i may not) it kept my virtual machines

---

### Post by lykwydchykyn on 2009-05-22
It should not touch your virtual machines.  I've done this a couple of times at least.

---

### Post by tacantara on 2009-05-22
Just like "TheNosh", I switched from OSE to the version available at the website.  I found that it had much more to offer (i.e. Guest add-ins for mouse integration).  When I installed the new version, I was pleased to find that the two machines I had set up were still there.

---

### Post by balboost on 2009-05-22
+1

you won't lose your machines. and i think this is a good idea, i really prefer the non-free version.

---

