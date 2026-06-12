---
title: "how can you uninstall"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-12-02
what is the best way to uninstall programs can it be done via terminal like limewire for instance i have that and it is more trouble than it is worth so i would like to uninstall it please help

---

### Post by oilchangeguy on 2008-12-02
> **||Z0di4C|| said:**
> what is the best way to uninstall programs can it be done via terminal like limewire for instance i have that and it is more trouble than it is worth so i would like to uninstall it please help

not everything has to be done via the terminal. look in add/remove, or synaptic to see if it's located there. and uninstall it from that location.

---

### Post by adult swim on 2008-12-02
if you installed it through synaptic, add/remove, or the apt-get from the terminal you can remove it with ```
sudo apt-get remove limewire
```

---

### Post by nhasian on 2008-12-03
adult swim,

that will still leave the user files.  to *completely* get rid of it i'd use

```
sudo apt-get remove --purge limewire
```

then

```
sudo apt-get clean
```

---

### Post by Paqman on 2008-12-03
Of course, you don't need to use the terminal to uninstall. Add/Remove and Synaptic can both uninstall packages. Just uncheck and apply. Synaptic can also completely remove a package similar to the --purge, just right click and "completely remove"

---

