---
title: "how to reinstall gnome desktop environment"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-23
i am mistakenly uninstalled gnome 
after that terminal is not loaded when i restart the system only terminal mode works (by pressing clt+alt+F1) 
when is type
sudo apt-get install gnome* 
it doesnt  work saying some dependency in installing
this command
sudo ap-get install gnome-desktop-environment
also doesnt work
help me thanks in advance

---

### Post by Kobalt on 2009-02-23
Did you try ```
sudo aptitude install ubuntu-desktop
```

---

### Post by gkraju on 2009-02-23
> **Kobalt said:**
> Did you try ```
sudo aptitude install ubuntu-desktop
```

are you sure this will work i havent tried it yet

---

### Post by Michael.Godawski on 2009-02-23
hi,

the ubuntu-desktop package is a metapackage which will "draw" many packages after it so to speak 

[http://packages.ubuntu.com/intrepid/ubuntu-desktop](http://packages.ubuntu.com/intrepid/ubuntu-desktop)

The packages which will be installed with the meta-package are listed above. 
Just try it out, nobody is an oracle here. :D

---

### Post by Metallion on 2009-02-23
I'm a bit worried by that dependency thing he's saying though.  Otherwise apt-get install gnome should also work and just install a bit more apps than ubuntu-desktop would. I suggest you try this command first to solve broken dependencies.
```
sudo apt-get -f install
```
Next install gnome with the command the others have given you.
```
sudo apt-get install ubuntu-desktop
```
Let us know if it works. ;)

---

### Post by gkraju on 2009-02-23
thanks everybody i installed it 
thanks Kobalt
i am about to reinstall ubuntu but now no problem  thanks everybody

---

