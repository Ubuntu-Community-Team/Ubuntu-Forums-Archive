---
title: "Location of installled Softwares"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by kapmsd on 2010-01-29
hi guys

i wanna know where the installed softwares gets stored in ubuntu
i mean the folders in which the files gets stored... like usr, var,etc..

---

### Post by danking12 on 2010-01-29
Good question. It can be installed all over the place. If you want to find the executable you can use the command

```
which <insert program here>
```

Other parts of applications can be installed in many places. User configuration files for programs will be hidden files/folders within each users home directory.

All in all there is no one or simple answer to this question. The best shot is consider a certain application and search for that when you may need it.

Hope that helps.

Dan

---

### Post by bogdan.veringioiu on 2010-01-29
You can see where a program is installed (where are the files spread) with these steps:
-open synaptic, search your program name (example: gedit), right click on it, choose "Properties", and then go to "Installed files" tab.
or
-open a terminal, and type:
> dpkg -L gedit

Cheers.
Bogdan

---

