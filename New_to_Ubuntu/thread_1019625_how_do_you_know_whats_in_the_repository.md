---
title: "how do you know whats in the repository"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-23
OK so i wanted to install smplayer and i just decided to try 
#> sudo apt-get install smplayer and it worked so i guess i just lucked out but if i really wanted to go see if smplayer was in the repository how would i do that before trying to install things?

---

### Post by zephyrcat on 2008-12-23
You can search Ubuntu's repositories from this page:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Duck2006 on 2008-12-23
Look in System->Administration->Synaptic Package Manager

---

### Post by evilkastel on 2008-12-23
bought answers will work. keep in mind tough, the http will list packages on the official repositories but the synaptic package manager will list packages from all repositories you have access including third party ones.

---

### Post by tarps87 on 2008-12-23
Don't forget
```
sudo apt-get install sm *(press tab twice for auto complete)*
```
not as easy as the above but helps with spelling :)

---

### Post by mkvnmtr on 2008-12-23
I find I go to the package manager a lot. I will search and spend some time looking an what an app depends on and what it conflicts with. For example if you put "crack" in the search box you will get a lot of cracking apps. File crackers, password crackers. wireless crackers and more. If I just use add/remove or the terminal on installing things I aon't know well I never know what else I might have to download or what it might conflict with. Search is kind of neat, it answers a lot of questions.

---

### Post by mshipman on 2008-12-23
You can also run: sudo apt-cache search [thing-to-search-for] from the terminal.

---

