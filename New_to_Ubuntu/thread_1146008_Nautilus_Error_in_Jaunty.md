---
title: "Nautilus Error in Jaunty"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-02
I just installed jaunty and when i tried to start comouter from places  , nothing happened so i tried it with terminal 
by typing 
sudo nautilus

and i got this error
Segmentation fault

ps. i installed jaunty yester day and it worked fine , and today i removed and installed it and got this problem

---

### Post by ajgreeny on 2009-05-02
It should be ```
gksudo nautilus
```  Always use gksudo for gui applications.  sudo is for terminal applications and utilities only.
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)
If that does not help, I don't know where else you should look.

---

