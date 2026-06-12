---
title: "Completely black screen on login: Gnome's fault?!"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-20
Hi all!
After installing a package that required system reboot I got a completely black screen on login. I understand it's login cause of system sounds, and if I do login, with username and password, I manage to login...but to a black screen. Only system sounds let me know that I'm in.
Recovery also gives me same black issue. I can use terminal...but I dont know the commands, I would try to remove and reinstall gnome desktop...what you think?

---

### Post by arrange on 2009-09-20
Have a look at the */var/log/apt/term.log* file and find the appropriate package and the info associated with it - this could give us a clue what went wrong.```
gksudo gedit /var/log/apt/term.log
```

---

### Post by webwiller on 2009-09-20
Ok I try it.
It takes me a bit cause I have a dua boot and have to shut down and start up in windows each time!

---

### Post by webwiller on 2009-09-20
Remember I'm in recovery mode, dont have a GUI at all, but just the black scree with a terminal, and got this reply:
> 
(gksudo:2643) Gtk-WARNING ** cannot open display

---

### Post by arrange on 2009-09-20
OK, I didn't know, you could have used LiveCD or such, so then run ```
sudo less /var/log/apt/term.log
``` or use *nano* instead of *less*. Note down the name of the package and any errors you may see during the package install/configuration.

---

