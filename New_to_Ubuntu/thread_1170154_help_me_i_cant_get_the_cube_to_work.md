---
title: "help me i cant get the cube to work"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by manitas on 2009-05-26
i tryed to install it on the terminal the compiz setting manger in differnt ways but all i get is

[COLOR=Black][U][B]manitas@manitas-desktop:~$ sudo apt-get install compizconfig-settings-manager 
[sudo] password for manitas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
manitas@manitas-desktop:~$ sudo apt-get install python-compizconfig compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-compizconfig
manitas@manitas-desktop:~$ 
[/B][/U][/COLOR]

---

### Post by Therion on 2009-05-26
Try searching for "CCSM" in Add/Remove in the Applications menu.  Make sure you have "All available applications" showing in the drop-down menu.

---

### Post by RedSingularity on 2009-05-26
Have an internet connection?

---

### Post by Jazzy_Jeff on 2009-05-26
Did you check in the Synaptic Package Manager to see if the package was listed?

---

### Post by raymondh on 2009-05-26
> **jazzy_jeff said:**
> did you check in the synaptic package manager to see if the package was listed?

+1

---

### Post by _Purple_ on 2009-05-26
Can you post the output of
```
gedit /etc/apt/sources.list

```

---

