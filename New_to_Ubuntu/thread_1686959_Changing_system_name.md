---
title: "Changing system name"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by uaebuntu on 2011-02-13
I started out with a standalone machine when I installed Linux. I now want to add it to a network, however I would like to change the name I gave it at install time before I do so as there is another computer with the same name. 

Can I do this without re installing from scratch?

---

### Post by Rubi1200 on 2011-02-13
If you mean changing the name you see in the terminal e.g. ubuntu@[COLOR=Red]ubuntu[/COLOR], then yes you can change it.

```
gksudo gedit /etc/hostname
```

change to whatever you want, save, reboot.

---

### Post by uaebuntu on 2011-02-13
Thanks....

---

### Post by Rubi1200 on 2011-02-13
No problem, you are more than welcome :)

---

